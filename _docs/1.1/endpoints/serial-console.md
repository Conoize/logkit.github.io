---
layout: docpage
title: Serial Console Endpoint
family: 1.1
---

The `LXLogSerialConsoleEndpoint` writes log entries to the console (stdout) on a first-in-first-out basis.

The Serial Console Endpoint is designed to be used in environments featuring heavy concurrency. This [Endpoint][endpoints] will write entries to the console in the order in which they are received **without** overlapping entries from multiple threads. The Serial Console Endpoint does some of its work asynchronously to allow better logging performance.

Because the Serial Console Endpoint takes advantage of asynchronous technologies, log entries written to this [Endpoint][endpoints] may appear in the console slightly after execution has moved on. In other words, if your application attempts to create a log entry directly before it crashes, it may not be delivered before the crash occurs. While debugging your application, if the asynchronous nature of this Endpoint is problematic, consider using a [Console Endpoint][ep-console] instead.

## Usage

### Initialization

The following initializers are available for `LXLogSerialConsoleEndpoint`:

{% highlight swift %}
init(minimumLogLevel: LXLogLevel = .All, dateFormatter: NSDateFormatter = defaultDateFormatter, entryFormatter: LXLogEntryFormatter = defaultEntryFormatter)
{% endhighlight %}

All arguments are optional and may be excluded. By default, the [Endpoint][endpoints] accepts entries of all [Priority Levels][levels]. `dateFormatter` and `entryFormatter` default to their [default formatters][default-formatting] if they are not provided.

Returns an initialized Serial Console Endpoint instance.


{% include links.md doc_version=page.family %}
