---
layout: docpage
title: Rotating File Endpoint
family: 2.0
---

{% include docs/endpoints/rotating-file/overview_2.md %}

{% include docs/endpoints/synchronicity_2.md endpoint_type="Rotating File" %}

## Usage

### Initialization

The following initializers are available for `LXRotatingFileEndpoint`:

{% highlight swift %}
init?(baseURL: NSURL?, numberOfFiles: UInt = 5, maxFileSizeKiB: UInt = 1024, minimumPriorityLevel: LXPriorityLevel = .All, dateFormatter: NSDateFormatter = LXDateFormatter.standardFormatter(), entryFormatter: LXEntryFormatter = LXEntryFormatter.standardFormatter())
{% endhighlight %}

LogKit will write log entries to the file specified by `baseURL`, with the file's name automatically prepended with an index number indicating its place in the rotation. If omitted, the URL defaults to `{AppSupport}/{bundleID}/logs/{number}_log.txt`. If the specified file cannot be opened, or if the index-prepended URL evaluates to `nil`, the initializer will fail.

The number of files to be used in the rotation is specified by `numberOfFiles`, and defaults to `5` if omitted.

The maximum file size of each file in the rotation is specified by `maximumFileSizeKiB`, and is specified in kilobytes. Defaults to `1024` (one megabyte) if omitted.

Log Entries may be filtered based on [Priority Level][levels] using `minimumPriorityLevel`. Only Entries of this level or above will be written to the Endpoint. If omitted, defaults to `All`.

The date formatter is specified by `dateFormatter`, and defaults to `LXDateFormatter.standardFormatter()` if omitted.

The Entry formatter is specified by `entryFormatter`, and defaults to `LXEntryFormatter = LXEntryFormatter.standardFormatter()` if omitted.

Returns an initialized Rotating File Endpoint instance if successful, or `nil` if the file cannot be accessed.


{% include links.md doc_version=page.family %}
