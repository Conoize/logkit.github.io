---
layout: docpage
title: Rotating File Endpoint
family: 2.0
---

{% include docs/endpoints/rotating-file/overview.md family=page.family %}

{% include docs/endpoints/synchronicity.md family=page.family endpoint_type="Rotating File" %}

## Usage

### Initialization

The following initializers are available for `LXRotatingFileEndpoint`:

{% highlight swift %}
init?(baseURL: numberOfFiles: maxFileSizeKiB: minimumPriorityLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

Name                   | Type               | Description | Default
---------------------- | ------------------ | ----------- | --------
`baseURL`              | `NSURL?`           | The URL used to build the rotating file set's file URLs; see description below | see below
`numberOfFiles`        | `UInt`             | The number of files to be used in the rotation | `5`
`maxFileSizeKiB`       | `UInt`             | The maximum file size of each file in the rotation, specified in kilobytes | `1024`
{% include docs/endpoints/common_params.md family=page.family %}

LogKit will write log entries to the files specified by `baseURL`, with each file's name automatically prepended with an index number indicating its place in the rotation. If the specified file cannot be opened, or if the index-prepended URL evaluates to `nil`, the initializer will fail.

If omitted, the URL defaults to `{AppSupport}/{bundleID}/logs/{number}_log.txt`, where `{AppSupport}` is the system-determined Application Support directory, `{bundleID}` is the host application's `bundleIdentifier` string, and `{number}` is the index of the currently selected file.

As an example, if an `LXRotatingFileEndpoint` is initialized with its default parameter values, it will create a set of files in `Application Support/{bundleID}/logs/` named `1_log.txt`, `2_log.txt`, `3_log.txt`, `4_log.txt`, and `5_log.txt`.

**Returns** an initialized Rotating File Endpoint instance if successful, or `nil` if the file cannot be accessed.


{% include links.md doc_version=page.family %}
