# Testing

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

## Reference

* [Run only one unit test from a test suite in laravel](https://stackoverflow.com/questions/38821326/run-only-one-unit-test-from-a-test-suite-in-laravel)
* [Factory not found in Laravel unit testing
](https://laracasts.com/discuss/channels/laravel/factory-not-found-in-laravel-unit-testing)