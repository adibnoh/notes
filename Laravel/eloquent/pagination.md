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