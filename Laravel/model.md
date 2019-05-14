# Model

## Update model without updating timestamps

```php

$model->timestamps = false;
$model->body = 'new content';
$model->save();

```

## Event

### Declare Observable only when Model is loaded

```php

trait UserObservable
{
    protected static function boot()
    {
        parent::boot();

        static::saving(function($model){

            // do your stuff

        });
    }
}

class User extends Model
{
    use UserObservable;
}

```

or

```php

trait UserObservable
{
    /**
     * Change your boot function to boot<traitName>
     * This way it will not interfere with boot function from other traits
     * Need to change method to public and remove parent::boot();
     */
    public static function bootUserObservable()
    {

        static::saving(function($model){

            // do your stuff

        });
    }
}

class User extends Model
{
    use UserObservable;
}

```

Refer: [Eloquent Events](https://laravel.com/docs/5.6/eloquent#events)

### Update Model without trigger event

```php

// disable event
$model->unsetEventDispatcher();

...

$model->save();

// re-enable event
$model->setEventDispatcher(new \Illuminate\Events\Dispatcher);

```

### Get fields that changes

```php

$changes = $product->getChanges(); // get field that changes

```

### Get original value

```php

static::updating(function ($product) {
    $product->price; // updated price
    $product->getOriginal('price'); // original price
}

```

## Get Model Table

```php

$table = with(new Model)->getTable();


```

## Ignore Appends

```php

$posts = Post::all();

$posts->each(function ($post) {
  $post->setAppends([]);
});

// or

$posts->each->setAppends([]);


```

## UUID Model

If your model primary key is UUID you can add this trait to help create UUID value when creating your model

```php

<?php

namespace App\Traits\Model;

use Str;

trait UuidAsPrimaryKey
{
    public static function bootUuidAsPrimaryKey()
    {

        static::creating(function ($model) {
            $model->incrementing = false;
            $model->{$model->getKeyName()} = (string) Str::uuid();
        });

    }
}

```

## Initiate Model

```php

$post = (new Post)->newQuery();

```

## Reference

* [https://laravel.com/api/5.7/Illuminate/Database/Eloquent/Concerns/HasAttributes.html](https://laravel.com/api/5.7/Illuminate/Database/Eloquent/Concerns/HasAttributes.html)
* [Laravel Tip: Bootable Model Traits](https://tighten.co/blog/laravel-tip-bootable-model-traits)
* [Laravel, how to ignore an accessor](https://stackoverflow.com/questions/28015039/laravel-how-to-ignore-an-accessor)
* [Using a UUID with Laravel’s Eloquent ORM](https://garrettstjohn.com/articles/using-uuid-laravel-eloquent-orm/#comment-1610987696)