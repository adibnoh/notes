# Redis

View Pending and Running Job

```php

$connection = null;
$default = 'default';

//For the delayed/pending jobs
var_dump( \Queue::getRedis()->connection($connection)->zrange('queues:'.$default.':delayed' ,0, -1) );

//For the reserved/running jobs
var_dump( \Queue::getRedis()->connection($connection)->zrange('queues:'.$default.':reserved' ,0, -1) );

```

Remove all Job in Queue

```php

Redis::connection()->del('queues:myqueue');

```