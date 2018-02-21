# Cheat Sheet

## Event

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