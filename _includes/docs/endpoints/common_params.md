{% case include.family %}

{% when 1.0 %}

{% when 2.0 %}`minimumPriorityLevel` | _Type:_ `LXPriorityLevel` <br> _Default:_ `.All` | The minimum [Priority Level][levels] a [Log Entry][entries] must meet to be accepted by this [Endpoint][endpoints]
{% unless include.excludeFormatters == true %}`dateFormatter` | _Type:_ `LXDateFormatter` <br> _Default:_ `.standardFormatter()` | The formatter used by this Endpoint to serialize a [Log Entry's][entries] `dateTime` property to a string
`entryFormatter` | _Type:_ `LXEntryFormatter` <br> _Default:_ `.standardFormatter()` | The formatter used by this Endpoint to serialize each [Log Entry][entries] to a string{% endunless %}

{% endcase %}
