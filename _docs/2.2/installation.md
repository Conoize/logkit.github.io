---
layout: docpage
title: Installation
family: 2.2
---

{% assign supported =        'OS X 10.9+, iOS 8+, watchOS 2+, tvOS 9+' %}
{% assign supported_source = 'OS X 10.9+, iOS 7+, watchOS 2+, tvOS 9+' %}

{% include docs/installation/requirements.md family=page.family %}

There are a few ways to install LogKit. You may choose any one method from those below. After completing installation, visit the [usage guide][usage] to get started.

### CocoaPods

> Supports {{ supported }}

{% include docs/installation/cocoapods.md family=page.family %}

### Carthage

> Supports {{ supported }}

{% include docs/installation/carthage.md family=page.family %}

### Embedded Framework

> Supports {{ supported }}

{% include docs/installation/embedded.md family=page.family %}

### Source

> Supports {{ supported_source }}

{% include docs/installation/source.md family=page.family %}


{% include links.md doc_version=page.family %}
