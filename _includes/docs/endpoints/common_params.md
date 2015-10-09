{% case include.family %}

{% when 1.0 %}

{% when 2.0 %}`minimumPriorityLevel` | `LXPriorityLevel` | The minimum Priority Level an Entry must be to be accepted by this Endpoint | `All`
`dateFormatter` | `LXDateFormatter` | The formatter to be used to convert an Entry's `dateTime` to a string | `.standardFormatter()`
{% unless include.excludeEntry == true %}`entryFormatter` | `LXEntryFormatter` | The formatter to be used to convert each Entry to a string | `.standardFormatter()`{% endunless %}

{% endcase %}
