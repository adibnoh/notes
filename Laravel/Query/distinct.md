# Distinct

## Distinct by column

`$query->distinct()->count('your_column_name')`

## Distinct withCount

```php

Model::withCount([
    'logs' => function($query) {
        $query->select(DB::raw('count(distinct `session_id`)'));
    }
])
->orderBy('logs_count')->get();

```