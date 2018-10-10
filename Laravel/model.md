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

## Reference

* [https://laravel.com/api/5.7/Illuminate/Database/Eloquent/Concerns/HasAttributes.html](https://laravel.com/api/5.7/Illuminate/Database/Eloquent/Concerns/HasAttributes.html)
* [https://tighten.co/blog/laravel-tip-bootable-model-traits](https://tighten.co/blog/laravel-tip-bootable-model-traits)