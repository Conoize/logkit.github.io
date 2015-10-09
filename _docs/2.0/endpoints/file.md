---
layout: docpage
title: File Endpoint
family: 2.0
---

{% include docs/endpoints/file/overview.md family=page.family %}

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="File" %}

## Usage

### Initialization

The following initializers are available for `LXFileEndpoint`:

{% highlight swift %}
init?(fileURL: shouldAppend: minimumPriorityLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

Name                   | Type               | Description | Default
---------------------- | ------------------ | ----------- | --------
`fileURL`              | `NSURL?`           | The file to write Entries to | see below
`shouldAppend`         | `Bool`             | Append to data currently in file, or clear and start over? | `true`
{% include docs/endpoints/common_params.md family=page.family %}

LogKit will write log entries to the file specified by `fileURL`. If the specified file cannot be opened, or if the URL evaluates to `nil`, the initializer will fail.

If omitted, the URL defaults to `{AppSupport}/{bundleID}/logs/log.txt`, where `{AppSupport}` is the system-determined Application Support directory, and `{bundleID}` is the host application's `bundleIdentifier` string.

**Returns** an initialized File Endpoint instance if successful, or `nil` if the file cannot be opened.


{% include links.md doc_version=page.family %}
