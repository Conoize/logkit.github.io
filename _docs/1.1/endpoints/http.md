---
layout: docpage
title: HTTP Endpoint
family: 1.1
---

The `LXHTTPEndpoint` uploads log entries to a specified URL.

The HTTP Endpoint is safe to be used in environments featuring concurrency. This [Endpoint][endpoints] does some of its work asynchronously to allow better logging performance. Upload and retry management are also handled asynchronously. Log entries that do not successfully upload will be queued for another upload attempt later. Because network performance is very unpredictable, log entries are not guaranteed to be delivered in the order in which they were generated. It is recommended that developers include a timestamp in this Endpoint's `entryFormatter` to facilitate sorting. The default `entryFormatter` includes the [`dateTime` property][entries].

## Usage

### Initialization

The following initializers are available for `LXHTTPEndpoint`:

{% highlight swift %}
init(URL: NSURL, HTTPMethod: String, successCodes: Set<Int> = Set([200, 201, 202, 204]), sessionConfiguration: NSURLSessionConfiguration = NSURLSessionConfiguration.defaultSessionConfiguration(), minimumLogLevel: LXPriorityLevel = .All, dateFormatter: NSDateFormatter = defaultDateFormatter, entryFormatter: LXEntryFormatter = defaultEntryFormatter)
{% endhighlight %}

LogKit will upload log entries to the specified `URL` using the specified `HTTPMethod`.

Developers may optionally specify which [HTTP response status codes][statusCodes] will denote a successful upload, and what [`NSURLSessionConfiguration`][nsURLSessionConfig] should be used when creating the Endpoint's session. These arguments default to `{200, 201, 202, 204}` and `.defaultSessionConfiguration()` respectively. Both arguments are optional and may be excluded.

All other arguments are optional and may be excluded. By default, the [Endpoint][endpoints] accepts entries of all [Priority Levels][levels]. `dateFormatter` and `entryFormatter` default to their [default formatters][default-formatting] if they are not provided.

Returns an initialized HTTP Endpoint instance.


{% include links.md doc_version=page.family %}
