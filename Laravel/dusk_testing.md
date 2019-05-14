# Dusk Testing

## Boilerplate

```php

<?php

namespace Tests\Browser\App\Follow;

use Illuminate\Foundation\Testing\DatabaseMigrations;
use Laravel\Dusk\Concerns\ProvidesBrowser;
use Tests\DuskTestCase;
use Illuminate\Foundation\Testing\RefreshDatabase;

class FollowCompanyTest extends DuskTestCase
{
    use ProvidesBrowser, DatabaseMigrations;

    public function setUp()
    {
        parent::setUp();
        // seed your database here
        // more setup here
    }

    public function tearDown()
    {
        // more teardown here
        parent::tearDown();

        static::closeAll();
    }

    // your test here
}


```

## Run Specific Test

Run test on specific file

`php artisan dusk <path_to_test_file>`

Run test on specific method

`php artisan dusk --filter <method_name> <path_to_test_file>`

## Check if dusk element is visible or not

```php

$browser->assertVisible("@button-create");
$browser->assertMissing("@button-create");

```

## Reference

* [Laravel Dusk: Close All Browsers Between Tests](https://blog.maqe.com/laravel-dusk-close-all-browsers-between-tests-8f9c60cc9806)
* [How to only run a specific Dusk test?
](https://laracasts.com/discuss/channels/laravel/how-to-only-run-a-specific-dusk-test)
* [Laravel Dusk Test assert the element of selector does not exist](https://stackoverflow.com/questions/53190749/laravel-dusk-test-assert-the-element-of-selector-does-not-exist)
