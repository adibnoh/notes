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

## Test database connection

```php
try {
  DB::connection()->getPdo();
  if (DB::connection()->getDatabaseName()) {
    dump('connect to db');
    echo "Yes! Successfully connected to the DB: " .
      DB::connection()->getDatabaseName();
  } else {
    dump('could not find db');
    die("Could not find the database. Please check your configuration.");
  }
} catch (\Exception $e) {
  dump('failed');
  die(
    "Could not open connection to database server.  Please check your configuration."
  );
}
```