---
layout: docpage
title: Entry Formatting
family: 1.0
---

{% include docs/formatting/overview.md family=page.family %}


## Date Formatters

Date formatting is handled by the `NSDateFormatter` class.

### Default Date Formatter

{% include docs/formatting/dates/default.md family=page.family %}

### Custom Date Formatters

{% include docs/formatting/dates/custom.md family=page.family %}

### Using a Date Formatter

{% include docs/formatting/dates/usage.md family=page.family %}


## Entry Formatters

[Log Entry][entries] formatting is handled by the `LXLogEntryFormatter` closure.

### Default Entry Formatter

{% include docs/formatting/entries/default.md family=page.family %}

### Custom Entry Formatters

{% include docs/formatting/entries/custom.md family=page.family %}

### Using an Entry Formatter

{% include docs/formatting/entries/usage.md family=page.family %}

### Customizing Entry Properties

{% include docs/formatting/entries/userInfo.md family=page.family %}


{% include links.md doc_version=page.family %}
