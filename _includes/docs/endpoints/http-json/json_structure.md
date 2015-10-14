{% case include.family %}

{% else %}


The JSON HTTP Endpoint serializes [Log Entries][entries] in a way that allows multiple Entries to be uploaded at once. The body of each upload request consists of a JSON dictionary. Log Entries are included in an array, found under the `entries` key of the dictionary. Each individual Log Entry is serialized as a dictionary (see [Entry Formatting][json-formatting] below).

> Note: This behavior is different than in LogKit 1, which uploaded Entries individually. Developer beware.

Regardless of the number of Log Entries ready for upload, the HTTP JSON Endpoint will always deliver uploads in this format.

{% highlight json %}
{
    "entries": [
        {...entry_1...},
        {...entry_2...},
        ...
    ]
}
{% endhighlight %}


{% endcase %}
