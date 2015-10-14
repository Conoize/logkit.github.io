{% case include.family %}

{% else %}


If the included Endpoint types do not meet your needs, LogKit makes it easy to create a custom Endpoint for use within your application. Simply define an object that conforms to LogKit's Endpoint protocol, and include it when initializing your [Logger][loggers]. The protocol defines a few properties that control which [Log Entries][entries] an Endpoint will accept and how the Entries will be [formatted][formatting], as well as a method for writing Log Entries to the destination the Endpoint represents.


{% endcase %}
