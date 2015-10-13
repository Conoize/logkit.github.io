{% case include.family %}

{% when 1.0 or 1.1 %}

{% else %}

`LXDateFormatter` comes with the following built-in presets:

----------------------------- | ------------------------------------
`.standardFormatter()`        | Converts `NSDate` objects into a datetime string, using the [UTC timezone][utc] <br> _Format String:_ `yyyy-MM-dd HH:mm:ss.SSS`
`.timeOnlyFormatter()`        | Converts `NSDate` objects into a time-only string, using the [UTC timezone][utc] <br> _Format String:_ `HH:mm:ss.SSS`
`.dateOnlyFormatter()`        | Converts `NSDate` objects into a date-only string, using the [UTC timezone][utc] <br> _Format String:_ `yyyy-MM-dd`
`.ISO8601DateTimeFormatter()` | Converts `NSDate` objects into strings following the [ISO 8601 combined datetime format][iso8601], using the [UTC timezone][utc] <br> _Format String:_ `yyyy-MM-dd'T'HH:mm:ss.SSSSSSZZZZZ`

{% endcase %}
