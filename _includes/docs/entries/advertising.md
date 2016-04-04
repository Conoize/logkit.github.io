{% case include.family %}


{% when 1.0 or 1.1 or 2.0 or 2.1 or 2.2 %}


{% else %}


The `deviceAdvertisingID` Log Entry property is only available on iOS and tvOS devices. However, even on those platforms, the ID is disabled by default to prevent triggering unnecessary [IDFA reviews][IDFA] when submitting applications to the App Store. The ID is managed by a compiler flag -- thus ensuring applications that do not use the ID will have no code related to the ID in their binaries.

In all cases, LogKit honors the `ASIdentifierManager.advertisingTrackingEnabled` flag. If an end user has disabled advertising tracking on their device, LogKit will substitute an empty string for the `deviceAdvertisingID`.

### Enabling

Enabling the `deviceAdvertisingID` for an app that requires this ID is easy; a compiler flag must simply be removed. The flag is found in the **LogKit Project's** build settings, in the _Swift Compiler - Custom Flags_ section. Remove the `-DLogKitAdvertisingIDDisabled` flag from the _Other Swift Flags_ line. The exact process varies a little depending on the installation method used.

> Updating to a new version of LogKit may reset the `-DLogKitAdvertisingIDDisabled` compiler flag, because LogKit includes this flag be default. Be sure to check after updating!

#### Embedded

Select `LogKit.xcodeproj` from the Project Navigator, and select the LogKit project item. In the **Build Settings** tab, find the **Swift Compiler - Custom Flags** section. Remove `-DLogKitAdvertisingIDDisabled` from the **Other Swift Flags** line. You may have to show "All" settings to find the Swift Compiler - Custom Flags section.

![Embedded Enabling Advertising ID][img-ad-id-enable-embedded]

#### CocoaPods

Select `Pods` from the Project Navigator, and select the LogKit target item. In the **Build Settings** tab, find the **Swift Compiler - Custom Flags** section. Remove `-DLogKitAdvertisingIDDisabled` from the **Other Swift Flags** line. You may have to show "All" settings to find the Swift Compiler - Custom Flags section.

![CocoaPods Enabling Advertising ID][img-ad-id-enable-cocoapods]

#### Carthage

Because Carthage integrates an already built framework into your project, removing the `-DLogKitAdvertisingIDDisabled` is just a little bit trickier.

1. Run `carthage checkout logkit`.
2. Open the LogKit project in `Carthage/Checkouts/logkit` and modify the compiler flag as desired. The process is identical to the "Embedded" section above.
3. Close Xcode.
4. Run `carthage build logkit`. You may have to add the `--configuration Debug` option depending on your project's code signing setup.
5. If you have not already, you may continue to set up Carthage as you normally would.

#### Source

If you simply copied all of LogKit's `.swift` source files into your project, the compiler flag should be added to _your project_ (because there is no LogKit project in this case). Otherwise, the instructions are the same as the "Embedded" section above.


{% endcase %}
