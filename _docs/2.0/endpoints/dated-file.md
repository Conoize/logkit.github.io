---
layout: docpage
title: Dated File Endpoint
family: 2.0
---

{% include docs/endpoints/dated-file/overview.md family=page.family %}

## Usage

### Initialization

The following initializers are available for `LXDatedFileEndpoint`:

{% highlight swift %}
init?(baseURL: minimumPriorityLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ------------------------------------------ | -----------
`baseURL`              | _Type:_ `NSURL?` <br> _Default:_ see below | The URL used to build the date files' URLs; see description below
{% include docs/endpoints/common_params.md family=page.family %}

This [Endpoint][endpoints] writes [Log Entries][entries] to the files specified by `baseURL`, with each file’s name automatically prepended with a datestamp in the format `yyyy-MM-dd`. If the specified file cannot be opened, or if the datestamp-prepended URL evaluates to `nil`, the initializer will fail.

If omitted, the URL defaults to `{AppSupport}/{bundleID}/logs/{datestamp}_log.txt`, where `{AppSupport}` is the system-determined Application Support directory, `{bundleID}` is the host application’s `bundleIdentifier` string, and `{datestamp}` is the current date's datestamp.

As an example, if an `LXDatedFileEndpoint` is initialized with its default parameter values and today's date is October 5, 2015, it will create a file in `Application Support/{bundleID}/logs/` named `2015-10-05_log.txt`. At midnight [UTC][utc], Log Entries will automatically begin being written to a new file named `2015-10-06_log.txt`.

**Returns** an initialized Dated File Endpoint instance if successful, or `nil` if the file cannot be opened.


{% include links.md doc_version=page.family %}
