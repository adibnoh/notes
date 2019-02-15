# Cheat Sheet

## Installer

Install specific version, ie: `5.6.*`

`composer create-project laravel/laravel="5.6.*" <project_path>`

## Query Builder

find empty column

`$query->where('profile', '<>', "");`

### Order By another table

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
$posts = Post::join('posts', 'versions.post_id', '=', 'posts.id')
        ->addSelect('posts.*', 'versions.post_id', 'versions.created_at')
        ->orderBy('versions.created_at', 'desc')
        ->paginate(20);

```

## Listener

Listen when user login and logout

[https://infylife.wordpress.com/2016/08/10/storing-logging-login-activity-in-laravel-application/](https://infylife.wordpress.com/2016/08/10/storing-logging-login-activity-in-laravel-application/)

## Request

Get current url

`$request->fullUrl()`

Get client IP address

`request->ip()`

Get client user agent

`$request->header('User-Agent')`

Get referrer

`Request::server('HTTP_REFERER')`

`request()->headers->get('referer')`

## Reference

* [Laravel Request getting current path with query string](https://stackoverflow.com/questions/31555494/laravel-request-getting-current-path-with-query-string)