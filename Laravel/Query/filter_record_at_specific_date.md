# Filter Record at Specific Date

```php

$query->whereRaw('date(created_at) = ?', [Carbon::today()]);
// or
$query->whereRaw('date(created_at) = ?', [date('Y-m-d')]);
// or
$query->where(DB::raw('date(created_at)'), Carbon::today());
// or
$query->where(DB::raw('date(created_at)'), '2019-10-9');

```

## Reference

* [Retrieve records created at a specific date
](https://laracasts.com/discuss/channels/general-discussion/retrieve-records-created-at-a-specific-date)