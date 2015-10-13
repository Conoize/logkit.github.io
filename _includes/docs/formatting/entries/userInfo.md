{% case include.family %}

{% when 1.0 or 1.1 %}


Each [Log Entry][entries] instance contains a `userInfo` dictionary property. This dictionary's contents are set by the application developer during each [Logger method call][log-methods]. For example:

{% highlight swift %}
log.debug("Hello Internet!", ["year": "2015"])
{% endhighlight %}

Including data in `userData` can be useful in a few ways.

* The developer can supply additional properties to be included in an Entry formatter's string output.

{% highlight swift %}
let myFormatter: LXLogEntryFormatter = { entry in
    let year = entry.userInfo["year"] as? String ?? "unknown"
    return "\(entry.message) The year is \(year)."
}

// Hello Internet! The year is 2015.
{% endhighlight %}

* The developer can supply parameters intended to control an Entry formatter's string output.

{% highlight swift %}
let myFormatter: LXLogEntryFormatter = { entry in
    if let year = entry.userInfo["year"] as? String where year == "2015" {
        return "\(entry.message)"
    } else {
        return "" // No bugs to log in 2016 and beyond!
    }
}
{% endhighlight %}

> Note: Some Endpoints (such as the included [HTTP JSON Endpoint][ep-http-json]) may automatically attempt to include any `userInfo` provided as a part of their `entryFormatter` output string.


{% else %}


Each [Log Entry][entries] instance contains a `userInfo` dictionary property. This dictionary's contents are set by the application developer during each [Logger method call][log-methods]. For example:

{% highlight swift %}
log.debug("Hello Internet!", ["year": "2015"])
{% endhighlight %}

Including data in `userData` can be useful in a few ways.

* The developer can supply additional properties to be included in an Entry formatter's string output.

{% highlight swift %}
let myFormatter = LXEntryFormatter({ entry in
    let year = entry.userInfo["year"] as? String ?? "unknown"
    return "\(entry.message) The year is \(year)."
})

// Hello Internet! The year is 2015.
{% endhighlight %}

* The developer can supply parameters intended to control an Entry formatter's string output.

{% highlight swift %}
let myFormatter = LXEntryFormatter({ entry in
    guard let year = entry.userInfo["year"] as? String where year == "2015" else {
        return "" // No bugs to log in 2016 and beyond!
    }
    return "\(entry.message)"
})
{% endhighlight %}

> Note: Some Endpoints (such as the included [HTTP JSON Endpoint][ep-http-json]) may automatically attempt to include any `userInfo` provided as a part of their `entryFormatter` output string.


{% endcase %}
