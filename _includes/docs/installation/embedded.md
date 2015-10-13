{% case include.family %}

{% when 1.0 %}


[Download LogKit][gh-release]. Include `LogKit.xcodeproj` within your project (second level, below your project root, as a sub-project). The LogKit project icon should be indented slightly to the right relative to your main project's icon.

![Embedded Installation Image 1][img-installation1]

Select your main project's target, and add LogKit as an Embedded Binary in the General tab.

![Embedded Installation Image 2][img-installation2]

Add the top LogKit for an iOS target, or the bottom LogKit for OS X. You may choose from either grouping.

![Embedded Installation Image 3][img-installation3]


{% when 1.1 %}


[Download LogKit][gh-release]. Include `LogKit.xcodeproj` within your project (second level, below your project root, as a sub-project). The LogKit project icon should be indented slightly to the right relative to your main project's icon.

![Embedded Installation Image 1][img-installation1]

Select your main project's target, and add LogKit as an Embedded Binary in the General tab.

![Embedded Installation Image 2][img-installation2]

Add the top LogKit for an OS X target, or the bottom LogKit for iOS. You may choose from either grouping.

![Embedded Installation Image 3][img-installation3v2]


{% else %}


[Download LogKit][gh-release]. Include `LogKit.xcodeproj` within your project (second level, below your project root, as a sub-project). The LogKit project icon should be indented slightly to the right relative to your main project's icon.

![Embedded Installation Image 1][img-installation1]

Select your main project's target, and add LogKit as an Embedded Binary in the General tab.

![Embedded Installation Image 2][img-installation2]

Add the top LogKit for an OS X target, the middle LogKit for iOS, or the bottom for watchOS. You may choose from either grouping.

![Embedded Installation Image 3][img-installation3v3]


{% endcase %}
