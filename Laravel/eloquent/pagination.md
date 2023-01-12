# Pagination

## Modify collections

```php


$jobs = Job::paginate();

$data = $jobs->getCollection();
$data->each(function ($job) {
    // modify collection here

    $job->title = 'hello';
});
$jobs->setCollection($data);


```

or

```php

$paginator->getCollection()->transform(function ($value) {
    // Your code here
    return $value;
});


```