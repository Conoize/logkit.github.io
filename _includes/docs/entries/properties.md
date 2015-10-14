Every `LXLogEntry` contains the following properties:

{% for prop in site.data.entry_props %}{% if forloop.first %}
Property          | Type              | Description
----------------- | ----------------- | ---------------{% endif %}{% if include.family >= prop.avail and (include.family < prop.deprc or prop.deprc == null) %}
`{{ prop.name }}` | `{{ prop.type }}` | {{ prop.desc }}{% endif %}{% endfor %}
