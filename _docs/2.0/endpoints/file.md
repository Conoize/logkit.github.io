---
layout: docpage
title: File Endpoint
family: 2.0
---

{% include docs/endpoints/file/overview.md family=page.family %}

## Usage

### Initialization

The following initializers are available for `LXFileEndpoint`:

{% highlight swift %}
init?(fileURL: shouldAppend: minimumPriorityLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ------------------------------------------ | -----------
`fileURL`              | _Type:_ `NSURL?` <br> _Default:_ see below | The file to write [Entries][entries] to
`shouldAppend`         | _Type:_ `Bool` <br> _Default:_ `true`      | Indicates whether the endpoint should continue appending [Log Entries][entries] to the end of the file, or clear it and start at the beginning
{% include docs/endpoints/common_params.md family=page.family %}

LogKit will write log entries to the file specified by `fileURL`. If the specified file cannot be opened, or if the URL evaluates to `nil`, the initializer will fail.

If omitted, the URL defaults to `{AppSupport}/{bundleID}/logs/log.txt`, where `{AppSupport}` is the system-determined Application Support directory, and `{bundleID}` is the host application's `bundleIdentifier` string.

**Returns** an initialized File Endpoint instance if successful, or `nil` if the file cannot be opened.


{% include links.md doc_version=page.family %}
