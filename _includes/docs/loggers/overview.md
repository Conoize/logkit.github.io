{% case include.family %}

{% else %}


A Logger instance is the primary way in which an application developer interacts with LogKit. This object is responsible for receiving [Log Entries][entries] and distributing them to its [Endpoints][endpoints]. Generally, a Logger instance is created once, at application load time, and used throughout the life of the application. LogKit includes the `LXLogger` class which fulfills this function, and is not meant to be subclassed.


{% endcase %}
