I neeeded to add this to `wp-config.php` after configuring everything and getting error `ERR_TOO_MANY_REDIRECTS`

``` php
$_SERVER['HTTPS'] = 'On';
```