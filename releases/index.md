---
layout: page
title: Releases
---

Below is a list of LogKit releases, complete with compatibility information and links for downloads and documentation.

{% for release in site.releases reversed %}{% if forloop.first %}
Release | Latest | Xcode | Swift | Download | Documentation
:------ | -----: | ----: | ----: | :------: | :-----------:{% endif %}
LogKit **{{ release.family }}** | {{ release.latest_version }} | {{ release.xcode_version }} | {{ release.swift_version }} | [GitHub]({{ release.release_link }}) | [{{ release.family }} Docs]({{ release.docs_path }}){% endfor %}
