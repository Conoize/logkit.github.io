---
layout: docpage
title: Usage
family: 2.3
---

## Quick Start

LogKit makes it easy to get started logging!

1. [Install LogKit][installation]
2. `import LogKit`
3. Create a [Logger][loggers]

> Note: If you installed LogKit by including its source directly within your project, there is no need to `import LogKit` (in fact, you will not be able to). Skip that step and just create a Logger.

To get started right away, install LogKit and follow the Simple Example code below. Later, it's easy to add more [Endpoints][endpoints] by just modifying the [Logger's][loggers] initialization. All logging calls will begin outputting to the new Endpoints the next time your application is run.

### Simple Example (in iOS)

{% include docs/usage/ex_simple.md family=page.family %}


## Advanced Usage

The basics of LogKit don't change, but its real power comes from using [Endpoints][endpoints] other than the console. LogKit allows you to write [Log Entries][entries] to as many Endpoints as desired. Each of these Endpoints can be customized to log in different [formats][formatting], or set to accept different [Priority Levels][levels].

### Complex Example (in OS X) with Multiple Endpoints

{% include docs/usage/ex_complex.md family=page.family %}


{% include links.md doc_version=page.family %}
