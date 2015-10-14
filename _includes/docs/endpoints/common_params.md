{% case include.family %}

{% when 1.0 or 1.1 %}`minimumLogLevel` | _Type:_ `LXLogLevel` <br> _Default:_ `.All` | The minimum [Priority Level][levels] a [Log Entry][entries] must meet to be accepted by this [Endpoint][endpoints]
`dateFormatter` | _Type:_ `NSDateFormatter` <br> _Default:_ [default date formatter][default-date-formatting] | The formatter used by this Endpoint to serialize a [Log Entry's][entries] `dateTime` property to a string
{% unless include.excludeFormatters == true %}`entryFormatter` | _Type:_ `LXLogEntryFormatter` <br> _Default:_ [default Entry formatter][default-entry-formatting] | The formatter used by this Endpoint to serialize each [Log Entry][entries] to a string{% endunless %}


{% else %}`minimumPriorityLevel` | _Type:_ `LXPriorityLevel` <br> _Default:_ `.All` | The minimum [Priority Level][levels] a [Log Entry][entries] must meet to be accepted by this [Endpoint][endpoints]
{% unless include.excludeFormatters == true %}`dateFormatter` | _Type:_ `LXDateFormatter` <br> _Default:_ `.standardFormatter()` | The formatter used by this Endpoint to serialize a [Log Entry's][entries] `dateTime` property to a string
`entryFormatter` | _Type:_ `LXEntryFormatter` <br> _Default:_ `.standardFormatter()` | The formatter used by this Endpoint to serialize each [Log Entry][entries] to a string{% endunless %}


{% endcase %}
