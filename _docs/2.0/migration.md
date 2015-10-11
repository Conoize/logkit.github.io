---
layout: docpage
title: Migrating from LogKit 1
family: 2.0
---

Use this document as a guide when upgrading from LogKit 1 to LogKit 2. Although this document touches upon some of LogKit 2's new features, it is meant more as a practical guide to getting up and running quickly rather than an exhaustive introduction to new features. Please refer to the [ChangeLog][changelog] or to the linked documentation to learn about what's new in LogKit 2.


## Initializing Endpoints

In the LogKit 2, the `LXLogger` object functions the same as in LogKit 1. However, many of the built-in [Endpoints][endpoints] have updated initialization methods.

### All Endpoints

The `minimumLogLevel` initialization parameter has been renamed to `minimumPriorityLevel` for all Endpoints.

The `dateFormatter` initialization parameter now requires an `LXDateFormatter` object for all Endpoints ([see below][local_date-formatting]).

The `LXEntryFormatter` object required for the `entryFormatter` initialization parameter has a new type ([see below][local_entry-formatting]).

### Console Endpoints

The Console and Serial Console Endpoints from LogKit 1 have both been replaced by a single [Console Endpoint][ep-console] class called `LXConsoleEndpoint`. This new Endpoint includes all of the positive properties of each previous Endpoint. Developers may indicate whether they would like synchronous output (like the old Console Endpoint) or asynchronous output (like the old Serial Console Endpoint) using the `synchronous` parameter whilst initializing the Endpoint. Neither option allows text to overlap or become jumbled in LogKit 2.

### File Endpoints

The `LXLogFileEndpoint` has been renamed `LXFileEndpoint`, and the `LXLogDatedFileEndpoint` has been renamed `LXDatedFileEndpoint`.

The [File Endpoint][ep-file] includes a new initialization parameter `shouldAppend` that controls whether the log file will be appended to, or cleared upon initialization. Defaults to `true` if omitted.

The [Dated File Endpoint][ep-dated-file]'s initialization parameter `fileURL` has been renamed to `baseURL` to better reflect that the actual file URL will be modified (prepended with a datestamp).

LogKit 2 also includes a new [Rotating File Endpoint][ep-rotating-file], the `LXRotatingFileEndpoint`.

### HTTP Endpoints

The `LXLogHTTPEndpoint` has been renamed `LXHTTPEndpoint`, and the `LXLogHTTPJSONEndpoint` has been renamed `LXHTTPJSONEndpoint`.

The [HTTP][ep-http] and [JSON][ep-http-json] Endpoints now cache pending uploads to persistent storage until the upload completes successfully. These Endpoints are now more resilient when faced with unreliable network conditions. Pending uploads will also persist between application runs, allowing LogKit to upload any remaining Entries at the next run time.

The [HTTP][ep-http] and [JSON][ep-http-json] Endpoints now accept an `NSURLRequest` as an initialization parameter. The request will be copied and used for all Log Entry uploads, allowing the developer more power in defining request parameters. The previous method of providing a URL and HTTP method is still supported as a convenience initializer, and in every case the developer can still provide an `NSURLSessionConfiguration` as well.

#### JSON Endpoint

The [JSON Endpoint][ep-http-json] now uploads multiple Log Entries at once, when possible. Every upload from the JSON Endpoint now consists of a dictionary, with an array of Log Entries under the key `entries`.

The [JSON Endpoint][ep-http-json] now formats `dateTime` properties using [ISO 8601 date and time formatting][iso8601]<br>(`yyyy-MM-dd'T'HH:mm:ss.SSSSSSZZZZZ`) in the [UTC timezone][utc]. In addition, the `logLevel` property of an `LXLogEntry` has been renamed `level`, and the JSON Endpoint honors this by uploading this property as `level`.

Finally, the [JSON Endpoint][ep-http-json] has changed the way the `userInfo` property is included in Log Entry uploads. Instead of adding each of the dictionary's key-value pairs as top-level items, the `userInfo` dictionary itself is included as a top-level value paired with the key `userInfo`.

An example of the LogKit 2 JSON Endpoint's upload format, including all changes noted above:

{% highlight json %}
{
    "entries": [
        {
            "message": "Hello Internet!",
            "userInfo": {
                "my_property": 1,
                "other_property": 2,
            },
            "dateTime": "2015-10-06T02:44:21.112000Z",
            "timestamp": 1444099461.112487,
            "level": "Debug",
            ...
        },
        {
            ...another_entry...
        },
        ...more_entries...
    ]
}
{% endhighlight %}


## Updating Custom Endpoints

[Endpoints][endpoints] have changed slightly in LogKit 2, and custom Endpoints will need to be updated to reflect this.

### The Endpoint Protocol

In LogKit 2, the `LXLogEndpoint` protocol has been renamed `LXEndpoint`. Additionally, the protocol's `minimumLogLevel` property has been renamed `minimumPriorityLevel`. The `dateFormatter` and `entryFormatter` properties now require `LXDateFormatter` and `LXEntryFormatter` objects respectively, instead of the `NSDateFormatter` and entry formatting closures accepted in LogKit 1.

Finally, the protocol has picked up one additional property: `requiresNewlines`. This property should be either `true` or `false` depending on whether you want newline characters appended to each Log Entry before it is written to the Endpoint. For example, the included [File Endpoint][ep-file] sets this property to `true` so that each Log Entry ends with a line break, but the included [HTTP Endpoint][ep-http] sets this property to `false`, as there is no need to append newline characters to Entries being uploaded.


## Priority Levels

The [Priority Level][levels] enumeration `LXLogLevel` has been renamed `LXPriorityLevel`.

As mentioned above, the `minimumLogLevel` initialization parameter has been updated to `minimumPriorityLevel` for all included Endpoints.


## Formatting

LogKit 2 introduces some upgrades to the Log Entry [formatting][formatting] system.

### Date Formatting

LogKit 2 introduces the `LXDateFormatter` object, replacing the `NSDateFormatter` previously used by Endpoints. `LXDateFormatter` is similar to `NSDateFormatter`, but is easier to initialize and includes a few built-in presets. All Endpoints now require the use of an `LXDateFormatter`. See the [formatting guide][date-formatting] for full details.

### Entry Formatting

LogKit 2 upgrades the closure previously used to format Log Entries to an object of its own. The `LXEntryFormatter` object accepts the same closures used in LogKit 1 as its initialization parameter. `LXEntryFormatter` now includes a few built-in presets as well. All Endpoints require the use of an `LXEntryFormatter`. See the [formatting guide][entry-formatting] for full details.

Any custom formatters using the [Log Entry][entries] property `logLevel` should be updated to reflect that this property is now called `level`. In addition, several new properties have been made available, as described below.


## Log Entry Details

The [Log Entry][entries] property `logLevel` has been renamed `level`.

Several new [Log Entry][entries] properties have been made in LogKit 2. These include information on the device type, model, and operating system version of the device running an application, as well as the application's bundle ID. Additionally, vendor and advertising IDs are available for devices that supply them.


[local_date-formatting]: #date-formatting
[local_entry-formatting]: #entry-formatting

{% include links.md doc_version=page.family %}
