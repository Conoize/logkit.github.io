{% case include.family %}

{% else %}


Each logging method above has an optional `userInfo` parameter. `userInfo` provides the application developer with an opportunity to customize their logging calls. Any `userInfo` included in a logging call is captured as part of the [Log Entry][entries] and made available to each of the Logger's [Endpoints][endpoints], specifically during [Entry formatting][formatting].

[Endpoints][endpoints] may use `userInfo` in a variety of ways. In one example, a developer could provide one or more additional objects in `userInfo` that an Endpoint can later include in its [Entry Formatter][formatting] for output as part of a serialized [Log Entry][entries]. In another example, additional state could be included in `userInfo` that affects control flow during Entry formatting.

See [Customizing Entry Properties][user-info] for examples of using `userInfo` in logging calls.


{% endcase %}
