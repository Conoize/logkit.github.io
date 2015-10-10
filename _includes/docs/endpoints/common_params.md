{% case include.family %}

{% when 1.0 %}

{% when 2.0 %}`minimumPriorityLevel` | _Type:_ `LXPriorityLevel` <br> _Default:_ `.All` | The minimum [Priority Level][levels] an [Entry][entries] must be to be accepted by this [Endpoint][endpoints]
{% unless include.excludeFormatters == true %}`dateFormatter` | _Type:_ `LXDateFormatter` <br> _Default:_ `.standardFormatter()` | The formatter to be used to convert an [Entry][entries]'s `dateTime` to a string
`entryFormatter` | _Type:_ `LXEntryFormatter` <br> _Default:_ `.standardFormatter()` | The formatter to be used to convert each [Entry][entries] to a string{% endunless %}

{% endcase %}
