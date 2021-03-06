{% case include.family %}

{% when 1.0 or 1.1 %}


LogKit supports a variety of [Log Entry][entries] Priority Levels, as defined in the `LXLogLevel` enumeration. The supported Levels are:


{% else %}


LogKit supports a variety of [Log Entry][entries] Priority Levels, as defined in the `LXPriorityLevel` enumeration. The supported Levels are:


{% endcase %}


Level      | Priority | Suggested Use
---------- | -------- | ------------------------------------------------------------------------
`All`      |          | Special value that includes all Levels
`Debug`    | Low      | Programmer debugging
`Info`     |          | Programmer informational
`Notice`   |          | General notice
`Warning`  |          | An event that may affect user experience, if not corrected, has occurred
`Error`    |          | An event that will definitely affect user experience has occurred
`Critical` | High     | An event that may crash the application has occurred
`None`     |          | Special value that excludes all Levels

When using a [Logger][loggers], the Priority Level for each [Log Entry][entries] will be determined by the [Logger method][log-methods] called to create the Entry. Each of a Logger's [Endpoints][endpoints] may individually define a minimum accepted Priority Level, and thus some Log Entries may be excluded from reaching specific Endpoints.

> The Levels `All` and `None` are special values for including and excluding all other Levels, respectively. `All` and `None` are not available as [Logger methods][log-methods].
