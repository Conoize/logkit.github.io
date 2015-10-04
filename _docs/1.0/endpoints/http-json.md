---
layout: docpage
title: HTTP JSON Endpoint
family: 1.0
---

The `LXLogHTTPJSONEndpoint` uploads log entries to a specified URL. The entries are serialized in [JSON format][json].

The HTTP JSON Endpoint is safe to be used in environments featuring concurrency. This [Endpoint][endpoints] does some of its work asynchronously to allow better logging performance. Upload and retry management are also handled asynchronously. Log entries that do not successfully upload will be queued for another upload attempt later. Because network performance is very unpredictable, log entries are not guaranteed to be delivered in the order in which they were generated.

## Entry Formatting

The HTTP JSON Endpoint is hard-coded to include a special `entryFormatter` that converts each log entry into a dictionary, then JSON serializes it for upload. This formatter includes all [properties of a log entry][entries], including the entry's [`userInfo`][entries]. All log entry properties become top-level items in the dictionary. Any top-level items in an entry's `userInfo` will become top-level items with the rest of an entry's properties. Dictionary key conflicts between `userInfo` and an entry's properties will result in `userInfo`'s conflicted items being overwritten by the entry's items. Developer beware.

It is the application developer's duty to ensure that all [`userInfo`][entries] items are JSON-serializable if this [Endpoint][endpoints] is in use. A non-JSON-serializable item will cause the log entry to be skipped in a shipping application (though in a test build, the application will abort).

## Usage

### Initialization

The following initializers are available for `LXLogHTTPJSONEndpoint`:

{% highlight swift %}
init(URL: NSURL, HTTPMethod: String, successCodes: Set<Int> = Set([200, 201, 202, 204]), sessionConfiguration: NSURLSessionConfiguration = NSURLSessionConfiguration.defaultSessionConfiguration(), minimumLogLevel: LXLogLevel = .All, dateFormatter: NSDateFormatter = defaultDateFormatter)
{% endhighlight %}

LogKit will upload log entries to the specified `URL` using the specified `HTTPMethod`.

Developers may optionally specify which [HTTP response status codes][statusCodes] will denote a successful upload, and what [`NSURLSessionConfiguration`][nsURLSessionConfig] should be used when creating the Endpoint's session. These arguments default to `{200, 201, 202, 204}` and `.defaultSessionConfiguration()` respectively. Both arguments are optional and may be excluded.

All other arguments are optional and may be excluded. By default, the [Endpoint][endpoints] accepts entries of all [Priority Levels][levels]. `dateFormatter` defaults to its [default formatter][default-formatting] if it is not provided.

Returns an initialized HTTP JSON Endpoint instance. This Endpoint uses a specialized `entryFormatter` [described above][json-formatting].


{% include links.md doc_version=page.family %}
