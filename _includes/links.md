{% capture doc_path %}/docs/{% if include.doc_version %}{{ include.doc_version }}{% else %}{{ site.releases.last.family }}{% endif %}/{% endcapture %}
{% capture static_images_path %}/static/images/{% endcapture %}

{% capture installation %}          {{ doc_path }}installation/                                     {% endcapture %}
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
{% capture levels %}                {{ doc_path }}priority-levels/                                  {% endcapture %}
{% capture formatting %}            {{ doc_path }}formatting/                                       {% endcapture %}

[installation]:             {{ installation }}                              "Installation Reference"
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
[levels]:                   {{ levels }}                                    "Priority Level Reference"
[formatting]:               {{ formatting }}                                "Formatting Reference"

[log-methods]:              {{ loggers | remove:' ' }}#logging-methods                   "Logger Methods"
[json-formatting]:          {{ ep_http_json | remove:' ' }}#entry-formatting             "HTTP JSON Entry Formatting"
[default-formatting]:       {{ formatting | remove:' ' }}#default-formatters             "Default Formatters"
[entries]:                  {{ formatting | remove:' ' }}#log-entries                    "Log Entry Reference"
[custom-formatting]:        {{ formatting | remove:' ' }}#writing-formatters             "Writing Formatters"
[user-info]:                {{ formatting | remove:' ' }}#customizing-entry-properties   "Customizing with userInfo"

[about]:                    /about/                                         "About LogKit"
[docs]:                     {{ doc_path }}                                  "Documentation"
[releases]:                 /releases/                                      "Releases"

[img-embedded1]:            {{ static_images_path }}embedded1.png
[img-embedded2]:            {{ static_images_path }}embedded2.png
[img-embedded3]:            {{ static_images_path }}embedded3.png
[img-embedded3_1]:          {{ static_images_path }}embedded3_1.png


[install-cocoapods]: https://guides.cocoapods.org/using/getting-started.html "Getting Started with CocoaPods"
[cocoapods]: https://guides.cocoapods.org/using/using-cocoapods.html "Using CocoaPods"
[carthage]: https://github.com/Carthage/Carthage "Carthage Project"
[utc]: https://en.wikipedia.org/wiki/Coordinated_Universal_Time "Coordinated Universal Time"
[epoch]: https://en.wikipedia.org/wiki/Unix_time "Unix Time"
[statusCodes]: https://en.wikipedia.org/wiki/List_of_HTTP_status_codes "HTTP Status Codes"
[nsDateFormatter]: https://developer.apple.com/library/ios/documentation/Cocoa/Reference/Foundation/Classes/NSDateFormatter_Class/index.html "NSDateFormatter Reference"
[nsURLSessionConfig]: https://developer.apple.com/library/ios/documentation/Foundation/Reference/NSURLSessionConfiguration_class/index.html#//apple_ref/occ/cl/NSURLSessionConfiguration "NSURLSessionConfiguration Reference"
[autoclosures]: https://developer.apple.com/swift/blog/?id=4 "Swift Autoclosures"
[swift-specials]: https://developer.apple.com/swift/blog/?id=15 "Swift Special Keywords"
[json]: https://en.wikipedia.org/wiki/JSON "JSON"
[cocoadocs_1_0]: http://cocoadocs.org/docsets/LogKit/1.0.4/ "LogKit Reference"
[cocoadocs_1_1]: http://cocoadocs.org/docsets/LogKit/1.1.0/ "LogKit Reference"
[cocoadocs_2_0]: http://cocoadocs.org/docsets/LogKit/2.0.0/ "LogKit Reference"
