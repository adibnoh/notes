# Order By Relationship

## Order by timestamp of relationship

```php

// raw method
// in this example we try sort posts using version
$jobs = DB::table('posts')
        ->join('versions', 'versions.post_id', '=', 'posts.id')
        ->select('posts.*', 'versions.post_id', 'versions.created_at')
        ->orderBy('versions.created_at', 'desc')
        ->take(5)
        ->get();

// or use eloquent
$posts = Post::join('versions', 'versions.post_id', '=', 'posts.id')
        ->addSelect('posts.*', 'versions.post_id', 'versions.created_at')
        ->orderBy('versions.created_at', 'desc')
        ->paginate(20);

```

## Order by sum of relationship

Assume we have Model Post and Comment

```php

    // App/Post
    
    public function comments()
    {
        return $this->hasMany('App\Comment', 'post_id');
    }

    // Usage
    
    Post::withCount('comments')
    ->orderBy('comments_count', 'desc')
    ->get();

    // Usage - distinct by custom column in table comment
    // Example below show that we can sort posts by total of user that comment to single post
    
    Post::withCount([
        'comments' => function($query) {
            $query->select(\DB::raw('count(distinct(comments.user_id))'));
        }
    ])
    ->orderBy('comments_count', 'desc')
    ->get();

```

## Order by sum of relationship (alternative)

Assume we have Model Comment and CommentVote

Setup Comment Model first

```php

    // App/Comment.php

    /**
     * Orders a comment by the sum of the votes that it has in the comment_votes table.
     * Comment votes can have a position of 1, 0 and -1 so the sum of all these entries works as a rank.
     *
     * @param Builder $query Query builder instance
     * @param string  $order asc/desc
     *
     * @return Builder instance
     */
    public function scopeOrderByCommentRank($query, $order = 'desc')
    {
        return $query->leftJoin('comment_votes', 'comment_votes.comment_id', '=', 'comments.id')
            ->groupBy('comments.id')
            ->addSelect(['*', \DB::raw('sum(position) as commentRank')])
            ->orderBy('commentRank', $order);
    }


    /**
     * An alternative relationship with comment votes for DB count queries
     */
    public function commentRankRelation()
    {
        return $this->hasOne('App\CommentVote')
        ->selectRaw('comment_id, sum(position) as rank')
        ->groupBy('comment_id');
    }


    /**
     * @return int the mutator to get the sum of all the comment votes
     */
    public function getCommentRankAttribute()
    {
        // if relation is not loaded already, let's do it first
      if (!array_key_exists('commentRankRelation', $this->relations)) {
          $this->load('commentRankRelation');
      }

       $related = $this->getRelation('commentRankRelation');

      // then return the count directly
      return ($related) ? (int) $related->rank : 0;
    }

```

Sorted comment by sum of comment votes

```php

$comments = Comment::orderByCommentRank('desc')->get();

// Print all the comments in Descending order
foreach ($comments as $comment) {
    echo $comment->text." ($comment->commentRank)";
}

```

## Reference

* [Order By Related Field Sum](https://laracasts.com/discuss/channels/eloquent/order-by-related-field-sum)
* [Using withCount() on a relationship that has distinct()](https://stackoverflow.com/a/55995026)
* [Laravel OrderBy relationship count](https://stackoverflow.com/a/46781121)
