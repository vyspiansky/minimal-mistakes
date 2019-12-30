---
title: Using Apache Bench for simple load testing
categories: [Testing]
tags: [Apache Bench, Apache Benchmark]
---

The following command runs `100` requests in total with `10` concurrent requests to `example.com`.

```bash
ab -n 100 -c 10 http://example.com/
```

**Note!** ApacheBench (ab) is installed on macOS by default.

Output will contain a lot of useful information. However firstly it's worth paying attention to the following values:

* Requests per second
* Failed requests
* Time per request

The `-H` flag allows you to append extra headers to the request:

```bash
ab -n 100 -c 10 -H "Accept-Encoding: gzip,deflate" http://example.com/
```

The argument is typically in the form of a valid header line, containing a colon-separated field-value pair (ex., `"Accept-Encoding: gzip,deflate"`).

The `-r` flag means don't exit if it gets an error:

```bash
ab -n 100 -c 10 -r http://example.com/
```

To make POST requests with a specific file used as the POST data, run the following command:

```bash
ab -n 100 -c 10 -p data.json -T application/json http://example.com/
```

The `-T` flag allows to specify the content type header like `application/json`. Default is `text/plain`.

Use `watch` to keep on firing `ab` requests at an endpoint. Notice that `watch` isn't available by default on macOS, but can be easily installed with Homebrew:

```bash
brew install watch
```

and run

```bash
watch -n 1 ab -n 100 -c 10 http://example.com/
```