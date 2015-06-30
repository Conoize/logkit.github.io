{% for each in site.data.links.internal %}
[{{ each[0] }}]: {{ each[1].path }}{% if each[1].caption %} "{{ each[1].caption }}"{% endif %}
{% endfor %}

{% for each in site.data.links.external %}
[{{ each[0] }}]: {{ each[1].path }}{% if each[1].caption %} "{{ each[1].caption }}"{% endif %}
{% endfor %}
