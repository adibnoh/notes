# Laravel

## Magic Method

```php

**
 * @property string type
 */
class User {

}

```

to remove magic method warning add doc property inside class you're having issue with.

## Compile Asset

Exclude public folder when running `npm run watch`

## Variable in blade doesn't support autocomplete

Variable in blade that come from controller doesn't support autocomplete.

```php

/** @var \Type $variable */

```

put line at top of your blade file