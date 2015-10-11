{% if include.doc_version %}
    {% assign family = include.doc_version %}
{% else %}
    {% assign family = site.releases.last.family %}
{% endif %}
{% capture doc_path %}/docs/{{ family }}/{% endcapture %}
{% assign static_images_path = '/static/images/' %}

{% capture installation %}          {{ doc_path }}installation/                                     {% endcapture %}
{% capture migration %}             {{ doc_path }}migration/                                        {% endcapture %}
{% capture usage %}                 {{ doc_path }}usage/                                            {% endcapture %}
{% capture loggers %}               {{ doc_path }}loggers/                                          {% endcapture %}
{% capture endpoints %}             {{ doc_path }}endpoints/                                        {% endcapture %}
{% capture ep_console %}            {{ doc_path }}endpoints/console/                                {% endcapture %}
{% capture ep_serial_console %}     {{ doc_path }}endpoints/serial-console/                         {% endcapture %}
{% capture ep_file %}               {{ doc_path }}endpoints/file/                                   {% endcapture %}
{% capture ep_rotating_file %}      {{ doc_path }}endpoints/rotating-file/                          {% endcapture %}
{% capture ep_dated_file %}         {{ doc_path }}endpoints/dated-file/                             {% endcapture %}
{% capture ep_http %}               {{ doc_path }}endpoints/http/                                   {% endcapture %}
{% capture ep_http_json %}          {{ doc_path }}endpoints/http-json/                              {% endcapture %}
{% capture entries %}               {{ doc_path }}entries/                                          {% endcapture %}
{% capture levels %}                {{ doc_path }}priority-levels/                                  {% endcapture %}
{% capture formatting %}            {{ doc_path }}formatting/                                       {% endcapture %}

{% comment %} === Versioned Documentation Links === {% endcomment %}
[installation]:             {{ installation }}                              "Installation Reference"
[migration]:                {{ migration }}                                 "Migration Reference"
[usage]:                    {{ usage }}                                     "Usage Reference"
[loggers]:                  {{ loggers }}                                   "Logger Reference"
[endpoints]:                {{ endpoints }}                                 "Endpoint Reference"
[ep-console]:               {{ ep_console }}                                "Console Endpoint Reference"
[ep-serial-console]:        {{ ep_serial_console }}                         "Serial Console Reference"
[ep-file]:                  {{ ep_file }}                                   "File Endpoint Reference"
[ep-rotating-file]:         {{ ep_rotating_file }}                          "Rotating File Endpoint Reference"
[ep-dated-file]:            {{ ep_dated_file }}                             "Dated File Endpoint Reference"
[ep-http]:                  {{ ep_http }}                                   "HTTP Endpoint Reference"
[ep-http-json]:             {{ ep_http_json }}                              "HTTP JSON Endpoint Reference"
[entries]:                  {{ entries }}                                   "Log Entry Reference"
[levels]:                   {{ levels }}                                    "Priority Level Reference"
[formatting]:               {{ formatting }}                                "Formatting Reference"

{% comment %} === Documentation Anchor Links === {% endcomment %}
[log-methods]:              {{ loggers | remove:' ' }}#logging-methods                  "Logger Methods"
[json-formatting]:          {{ ep_http_json | remove:' ' }}#entry-formatting            "HTTP JSON Entry Formatting"
[date-formatting]:          {{ formatting | remove:' ' }}#date-formatters               "Date Formatting"
[entry-formatting]:         {{ formatting | remove:' ' }}#entry-formatters              "Entry Formatting"
[default-formatting]:       {{ formatting | remove:' ' }}#default-formatters            "Default Formatters"
[default-date-formatting]:  {{ formatting | remove:' ' }}#default-date-formatter        "Default Date Formatters"
[default-entry-formatting]: {{ formatting | remove:' ' }}#default-entry-formatter       "Default Entry Formatters"
[custom-formatting]:        {{ formatting | remove:' ' }}#writing-formatters            "Writing Custom Formatters"
[custom-date-formatting]:   {{ formatting | remove:' ' }}#custom-date-formatters        "Custom Date Formatters"
[custom-entry-formatting]:  {{ formatting | remove:' ' }}#custom-entry-formatters       "Custom Entry Formatters"
[user-info]:                {{ formatting | remove:' ' }}#customizing-entry-properties  "Customizing with userInfo"

{% comment %} === Main Page Links === {% endcomment %}
[about]:                    /about/                                         "About LogKit"
[releases]:                 /releases/                                      "Releases"
[docs]:                     {{ doc_path }}                                  "Documentation"


{% comment %} === Dynamic Internal Links === {% endcomment %}
{% for release in site.releases %}
[docs-{{ release.family | replace:".","_" }}]: {{ release.docs_path }}      "LogKit {{ release.family }} Documentation"
{% endfor %}


{% comment %} === Static Files === {% endcomment %}
[img-installation1]:        {{ static_images_path }}installation1.png
[img-installation2]:        {{ static_images_path }}installation2.png
[img-installation3]:        {{ static_images_path }}installation3.png
[img-installation3v2]:      {{ static_images_path }}installation3v2.png
[img-installation3v3]:      {{ static_images_path }}installation3v3.png


{% comment %} === Dynamic External Links === {% endcomment %}
[gh-release]:               {{ site.releases | where:'family',family | map:'download_link' }}   "LogKit {{ family }} Release"
[changelog]:                {{ site.releases | where:'family',family | map:'changelog_link' }}  "LogKit {{ family }} ChangeLog"
[cocoadocs]:                {{ site.releases | where:'family',family | map:'cocoadocs_link' }}  "LogKit at CocoaDocs"


{% comment %} === Static External Links === {% endcomment %}
[install-cocoapods]: https://guides.cocoapods.org/using/getting-started.html "Getting Started with CocoaPods"
[cocoapods]: https://guides.cocoapods.org/using/using-cocoapods.html "Using CocoaPods"
[carthage]: https://github.com/Carthage/Carthage "Carthage Project"
[utc]: https://en.wikipedia.org/wiki/Coordinated_Universal_Time "Coordinated Universal Time"
[iso8601]: https://en.wikipedia.org/wiki/ISO_8601 "ISO 8601"
[epoch]: https://en.wikipedia.org/wiki/Unix_time "Unix Time"
[statusCodes]: https://en.wikipedia.org/wiki/List_of_HTTP_status_codes "HTTP Status Codes"
[nsDateFormatter]: https://developer.apple.com/library/ios/documentation/Cocoa/Reference/Foundation/Classes/NSDateFormatter_Class/index.html "NSDateFormatter Reference"
[nsURLRequest]: https://developer.apple.com/library/ios/documentation/Cocoa/Reference/Foundation/Classes/NSURLRequest_Class/index.html "NSURLRequest Reference"
[nsURLSessionConfig]: https://developer.apple.com/library/ios/documentation/Foundation/Reference/NSURLSessionConfiguration_class/index.html#//apple_ref/occ/cl/NSURLSessionConfiguration "NSURLSessionConfiguration Reference"
[autoclosures]: https://developer.apple.com/swift/blog/?id=4 "Swift Autoclosures"
[swift-specials]: https://developer.apple.com/swift/blog/?id=15 "Swift Special Keywords"
[json]: https://en.wikipedia.org/wiki/JSON "JSON"
[cocoadocs-latest]: http://cocoadocs.org/docsets/LogKit "LogKit Reference"
