---
layout: docpage
title: Endpoints
family: 1.1
---

Endpoints are responsible for processing and writing [Log Entries][entries] to the destinations they represent. LogKit includes several ready-made Endpoints for various logging needs, but application developers can also create their own.

Endpoints are specified when a [Logger][loggers] instance is initialized.

## Included Endpoints

LogKit includes the following Endpoints ready for use:

* [Console Endpoint][ep-console]
* [Serial Console Endpoint][ep-serial-console]
* [File Endpoint][ep-file]
* [Dated File Endpoint][ep-dated-file]
* [HTTP Endpoint][ep-http]
* [HTTP JSON Endpoint][ep-http-json]

Each of these included Endpoint types has unique settings and characteristics. View each specific Endpoint's documentation to learn about initializing and using that Endpoint.

## Creating a Custom Endpoint

If the included Endpoint types do not meet your needs, LogKit makes it easy to create a custom Endpoint for use within your application. Simply define an object that conforms to LogKit's `LXLogEndpoint` protocol, and include it when initializing your [Logger][loggers].

### Anatomy of an Endpoint

An Endpoint can be any object that conforms to the `LXLogEndpoint` protocol.  The protocol defines a few properties that control which [Log Entries][entries] the Endpoint accepts and how the Entries are [formatted][formatting], as well as a method for writing Log Entries to the destination the Endpoint represents. A [Logger][loggers] instance can include several Endpoints, and each Endpoint can be configured independently.

#### The Endpoint Protocol

The `LXLogEndpoint` protocol defines the following required properties and methods:

{% highlight swift %}
minimumLogLevel: LXLogLevel
dateFormatter: NSDateFormatter
entryFormatter: LXLogEntryFormatter

write(entryString: String) -> Void
{% endhighlight %}

`minimumLogLevel` is the lowest [Priority Level][levels] that an Endpoint will accept for output. Any of the included Priority Levels, including `.All` and `.None`, may be specified.

`dateFormatter` and `entryFormatter` define how [Log Entries][entries] will be converted into strings. `dateFormatter` specifies how a [Log Entry's][entries] `dateTime` property will be converted to a string. `entryFormatter` defines how the Entry itself will be formatted when converted to a string. Writing custom Date and Entry Formatters is covered in the [Entry Formatting Reference][custom-formatting].

When a [Log Entry][entries] meets an Endpoint's [Priority Level][levels] requirements and has been formatted as a string by the Endpoints formatters, that string is passed the the Endpoint's `write:` method for output to a final destination. In your `write:` method, you should print the `entryString` to the console, append it to a log file, or send it to whatever destination your Endpoint represents.

{% include links.md doc_version=page.family %}
