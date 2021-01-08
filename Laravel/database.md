# Database

## TODO

* [ ] Indexing Column Type Text

## Migration

Migrate for different environment; eg env testing and using specific database

`php artisan migrate:fresh --env=testing --database=sqlite`

Available parameter

`--env=` - Choose env

`--database=` - Choose database

`--seed` - Seed your database

## Edge case

### Indexing for column type TEXT

```php

$table->index([DB::raw('column(100)')]);

```