---
layout: page
title: Releases
---

{% for release in site.releases reversed %}

**LogKit {{ release.family }}** -- Latest: {{ release.latest_version }} -- [Download]({{ release.download_link }}) -- [Documentation]({{ release.docs_path }})

{% if forloop.last != true %}
***
{% endif %}

{% endfor %}
