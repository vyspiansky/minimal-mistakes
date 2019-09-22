---
title: Does a remote file exist (using get_headers)?
categories: [PHP]
tags: [get_headers, allow_url_fopen]
---

As you probably know, a `get_headers` function in PHP typically returns something similar to:

```
Array
(
    [0] => HTTP/1.1 200 OK
    [1] => Content-Type: image/png
    [2] => Content-Length: 127999
    [3] => Connection: close
    [4] => Date: Thu, 09 Nov 2017 12:16:51 GMT
    [5] => Last-Modified: Wed, 08 Nov 2017 09:12:17 GMT
    ...
)
```

Where the first element of the array contains a response status. With that in mind, let’s use it for our needs.

```php
<?php
function remote_file_exists($url) {
    $file_headers = get_headers($url);

    $not_found_headers = [
        'HTTP/1.1 404 Not Found',
        'HTTP/1.0 404 Not Found',
    ];

    return !in_array($file_headers[0], $not_found_headers);
}

$url = 'https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/PHP-logo.svg/100px-PHP-logo.svg.png';
$res = remote_file_exists($url);
var_dump($res); // Output: bool(true)

// ... and use a fake URL
$url = 'https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/PHP-logo.svg/100px_FAKE-PHP-logo.svg.png';
$res = remote_file_exists($url);
var_dump($res); // Output: bool(false)
```

The first thing to notice is that the response message might have the different version of the protocol: `HTTP/1.0 404 Not Found`, `HTTP/1.1 404 Not Found` etc.

And the second one - `get_headers()` won't work properly in case [allow_url_fopen](https://www.php.net/manual/en/filesystem.configuration.php) is disabled. 

To check if `allow_url_fopen` is enabled or not, you can use `ini_get()`:

```php
<?php
if (ini_get('allow_url_fopen')) {
    echo 'allow_url_fopen is enabled';
}
```

If it's possible edit your `php.ini` file, find `allow_url_fopen` and specify 

```
allow_url_fopen=1
```

In case you don't have access to do this, use the following code in your PHP script (from the very beginning):

```php
<?php 
ini_set('allow_url_fopen', 1);
```
