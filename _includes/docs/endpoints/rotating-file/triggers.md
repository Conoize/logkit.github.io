{% case include.family %}

{% when 1.0 or 1.1 or 2.0 or 2.1 or 2.2 %}


{% else %}


{% if include.family == 2.3 %}***New in 2.3***{% endif %}

`LXRotatingFileEndpoint` instances include a `rotate()` method that will cause the Endpoint to attempt to rotate to its next log file. If, for whatever reason, the Endpoint cannot open the next file in its rotation, it will continue to use the current log file.

Manual log file rotation will trigger the expected rotation notifications, identical to automatic rotation.

{% endcase %}
