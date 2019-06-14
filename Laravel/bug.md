# Bug

## Invalid method override "__CONSTRUCT"

It's not a bug, you're being scanned for vulnerabilities by someone manipulating the HTTP headers being sent to your server. That exception is thrown when the X-Forwarded-Host header looks suspicious to Symfony

[https://github.com/octobercms/october/issues/4359](https://github.com/octobercms/october/issues/4359)
[https://github.com/symfony/http-foundation/blob/master/Request.php#L1135](https://github.com/symfony/http-foundation/blob/master/Request.php#L1135)