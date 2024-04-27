# Testing

## Environment

In your `.env` or `.env.testing` please set `APP_ENV=testing`.

## Feature

## Unit

factory helper not working in Unit Testing, move to Feature Testing

## Run Testing

Run unit testing from specific method and from specific file

`phpunit --filter {TestMethodName} {pathToFile}`

example:

`phpunit --filter testExample path/to/filename.php`

command above will run any method that matched any similar substring inside that file.

let's say inside that file contain method `testExampleNew`, when we run command above, `testExample` and `testExampleNew` also executed

Or to run exact method from that specific file

`phpunit --filter '/::{testMethodName}}$/' {pathToFile}`

example:

`phpunit --filter '/::testExample$/' path/to/filename.php`

## Run Testing using Laravel Command

`php artisan test` - this will run all tests and using file `.env` as configuration environment.

`php artisan test --env=local` - this will use `.env.local` as configuration environment.

`php artisan test --env=local --filter test_this_method tests/Feature/ExampleTest` - this will run specific test. We need to specify the method and file path.

## Common Issues

### CSRF Token Mismatch

In your `.env` please set to `APP_ENV=testing`.


## Reference

* [Run only one unit test from a test suite in laravel](https://stackoverflow.com/questions/38821326/run-only-one-unit-test-from-a-test-suite-in-laravel)
* [Factory not found in Laravel unit testing
](https://laracasts.com/discuss/channels/laravel/factory-not-found-in-laravel-unit-testing)