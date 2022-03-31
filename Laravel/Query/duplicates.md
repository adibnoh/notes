# Duplicates

## Find duplicates

```php

$duplicates = \DB::table('articles')
    ->select('id', 'title')
    ->groupBy('title') // duplicate column
    ->havingRaw('COUNT(*) > 1')
    ->get();

```