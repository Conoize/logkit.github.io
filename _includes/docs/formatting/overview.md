In LogKit, [Log Entries][entries] go from `LXLogEntry` to string by using each target Endpoint's formatters. Every [Endpoint][endpoints] has its own formatters, so different Endpoints can output Entries in different formats. For example, an application using both a [Console Endpoint][ep-console] and a [File Endpoint][ep-file] could choose concise formatters for the console, and more detailed formatters for the file.

An Endpoint requires two formatters to convert each [Log Entry][entries] to a string. The Endpoint's `dateFormatter` describes how an Entry's `dateTime` property will be converted. Its `entryFormatter` describes how the Entry itself will be converted. Using the [Endpoint's][endpoints] formatters, each `LXLogEntry` is converted to a string before the Endpoint writes it to its final destination.


{% case include.family %}

{% when 1.0 or 1.1 %}


Although the formatters of each Endpoint may be customized, all Endpoints include sensible defaults that will suit most developer's needs. If desired, however, a developer can create and use their own.


{% else %}


Although the formatters of each Endpoint may be customized, all Endpoints include sensible defaults that will suit most developer's needs. If desired, however, a developer can choose to use another of the variety of date and Entry formatters included with LogKit, or even create and use their own.


{% endcase %}
