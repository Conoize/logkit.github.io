---
layout: docpage
title: Console Endpoint
family: 1.1
---

The `LXConsoleEndpoint` writes log entries to the console (stdout).

All entries sent to this [Endpoint][endpoints] are written synchronously. This behavior can be both advantageous and disadvantageous. On the positive side, entries will always be written before your app moves on to the next instruction, which is very helpful when debugging. On the negative side, any entries being written concurrently from different threads can become jumbled. In addition, the synchronous nature of this Endpoint eliminates any performance increases available from offloading log processing to another thread.

## Usage

### Initialization

The following initializers are available for `LXConsoleEndpoint`:

{% highlight swift %}
init(minimumLogLevel: LXPriorityLevel = .All, dateFormatter: NSDateFormatter = defaultDateFormatter, entryFormatter: LXEntryFormatter = defaultEntryFormatter)
{% endhighlight %}

All arguments are optional and may be excluded. By default, the [Endpoint][endpoints] accepts entries of all [Priority Levels][levels]. `dateFormatter` and `entryFormatter` default to their [default formatters][default-formatting] if they are not provided.

Returns an initialized Console Endpoint instance.


{% include links.md doc_version=page.family %}
