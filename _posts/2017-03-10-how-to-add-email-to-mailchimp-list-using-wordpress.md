---
title: How to add email to MailChimp list using WordPress
categories: [WordPress]
tags: [MailChimp]
---

```php
<?php

$apiKey = 'your API key';
$dc     = 'MailChimp data center, for example, "us6"';
$listId = 'your list id';
$email  = 'some@email.here';

$url = "https://{$dc}.api.mailchimp.com/2.0/lists/subscribe.json";

$request = wp_remote_post($url, [
    'body' => json_encode([
        'apikey' => $apiKey,
        'id'     => $listId,
        'email'  => ['email' => $email],
    ]),
]);

$result = json_decode(wp_remote_retrieve_body($request));

// some kind of check here ...
```