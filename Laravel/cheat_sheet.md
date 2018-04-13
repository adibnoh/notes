# Cheat Sheet

## Query Builer

find empty column

`$query->where('profile', '<>', "");`

## Event

### Declare Observeable only when Model is loaded

Register your Observer when on the model boot function.

In this way the Observer only load when the model loaded.

```php

class SalesOrderDetail extends Model{
  public static function boot() {
    parent::boot();
    SalesOrderDetail::observe(new SalesOrderDetailObserver());
  }
}

```

Another way is attach as trait (tested and not working yet)

```php

trait Observable
{
    public static function bootObservableTrait()
    {
        if (isset($this->observer)) {
            static::observe($this->observer);
        }
    }
}

class User extends Model
{
    use Observable;

    protected $observer = User observer::class;
}

```

### Update Model without trigger event

```php

// disable event
$model->unsetEventDispatcher();

...

$model->save();

// re-enable event
$model->setEventDispatcher(new \Illuminate\Events\Dispatcher);

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

* [https://stackoverflow.com/questions/31555494/laravel-request-getting-current-path-with-query-string](https://stackoverflow.com/questions/31555494/laravel-request-getting-current-path-with-query-string)
