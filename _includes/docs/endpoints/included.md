{% case include.family %}

{% when 1.0 or 1.1 %}


LogKit includes the following Endpoints ready for use:

* [Console Endpoint][ep-console]
* [Serial Console Endpoint][ep-serial-console]
* [File Endpoint][ep-file]
* [Dated File Endpoint][ep-dated-file]
* [HTTP Endpoint][ep-http]
* [HTTP JSON Endpoint][ep-http-json]

Each of these included Endpoint types has unique settings and characteristics. View each specific Endpoint's documentation to learn about initializing and using that Endpoint.


{% else %}


LogKit includes the following Endpoints ready for use:

* [Console Endpoint][ep-console]
* [File Endpoint][ep-file]
* [Rotating File Endpoint][ep-rotating-file]
* [Dated File Endpoint][ep-dated-file]
* [HTTP Endpoint][ep-http]
* [HTTP JSON Endpoint][ep-http-json]

Each of these included Endpoint types has unique settings and characteristics. View each specific Endpoint's documentation to learn about initializing and using that Endpoint.


{% endcase %}
