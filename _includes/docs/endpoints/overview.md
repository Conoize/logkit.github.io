{% case include.family %}

{% else %}


Endpoints are responsible for processing and writing [Log Entries][entries] to the destinations they represent. LogKit includes several built-in Endpoints for various logging needs, but application developers can also create their own.

Endpoints are specified when a [Logger][loggers] instance is initialized. A [Logger][loggers] instance can include several Endpoints, and each Endpoint can be configured independently.


{% endcase %}
