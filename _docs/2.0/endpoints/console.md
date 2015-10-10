---
layout: docpage
title: Console Endpoint
family: 2.0
---

{% include docs/endpoints/console/overview.md family=page.family %}

## Usage

### Initialization

The following initializers are available for `LXConsoleEndpoint`:

{% highlight swift %}
init(synchronous: minimumPriorityLevel: dateFormatter: entryFormatter: )
{% endhighlight %}

**Parameters**

---------------------- | ------------------------------------- | -----------
`synchronous`          | _Type:_ `Bool` <br> _Default:_ `true` | Specifies whether synchronous writing is desired
{% include docs/endpoints/common_params.md family=page.family %}

If synchronous behavior is selected, the application will wait for each [Log Entry][entries] to be printed to the console before continuing execution. This behavior is very helpful when debugging, but may reduce performance compared to the asynchronous behavior.

If asynchronous behavior is selected, [Log Entries][entries] are not guaranteed to be printed before execution continues. This behavior can significantly improve performance, especially in environments featuring concurrency. However, an application making a logging call directly before crashing may crash before the Entry has a chance to be printed. While debugging an application, it is recommended to specify the synchronous behavior.

**Returns** an initialized Console Endpoint instance.


{% include links.md doc_version=page.family %}
