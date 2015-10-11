Every `LXLogEntry` contains the following properties:

Property          | Type       | Description
----------------- | ---------- | ------------------------------------------------------------------------------
`logKitVersion`   | `String`   | The version of the LogKit framework that generated the entry
`message`         | `String`   | The log message
`userInfo`        | `[String:AnyObject]` | Additional values to be provided to the entry formatter; always present but may be empty; see [here][user-info] for using userInfo
`level`           | `String`   | The name of the log entry's [Priority Level][levels]
`timestamp`       | `Double`   | The number of seconds since the [Unix epoch][epoch]
`dateTime`        | `String`   | The timestamp formatted by an Endpoint's `dateFormatter`
`functionName`    | `String`   | The name of the function from which the log entry was created
`fileName`        | `String`   | The name of the source file from which the log entry was created
`filePath`        | `String`   | The absolute path of the source file from which the log entry was created
`lineNumber`      | `Int`      | The line number within the source file from which the log entry was created
`columnNumber`    | `Int`      | The column number within the source file from which the log entry was created
`threadID`        | `String`   | The ID of the thread from which the log entry was created
`threadName`      | `String`   | The name of the thread from which the log entry was created
`isMainThread`    | `Bool`     | An indicator of whether the log entry was created on the main thread
{% if include.family >= 2.0 %}`osVersionString` | `String`   | A description of the operating system, including its name and version
`osMajorVersion`  | `Int`      | The major version number of the operating system
`osMinorVersion`  | `Int`      | The minor version number of the operating system
`osPatchVersion`  | `Int`      | The patch version number of the operating system
`osBuildVersion`  | `String`   | The build version string of the operating system
`bundleID`        | `String`   | The bundle ID of the host application
`deviceModel`     | `String`   | The model of the device running the application
`deviceType`      | `String`   | The type of the device running the application
`deviceVendorID`  | `String`   | The vendor ID of the device running the application (if available)
`deviceAdvertisingID` | `String` | The advertising ID of the device running the application (if available)
{% endif %}

Each of these properties will be available in every `LXLogEntry` that is passed to an [Endpoint's][endpoints] `entryFormatter`. The developer may choose to use or ignore each property when crafting a [custom Entry formatter][custom-entry-formatting].
