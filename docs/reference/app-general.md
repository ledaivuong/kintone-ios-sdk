# General

>The description, name, icon, revision and color theme of an App


## GeneralSettings

The description, name, icon, revision and color theme of an App.

### Constants

#### IconTheme
| Name| Type| value|
| --- | --- | --- |
| WHITE | String | WHITE |
| RED | String | RED |
| BLUE | String | BLUE |
| GREEN | String | GREEN |
| YELLOW | String | YELLOW |
| BLACK | String | BLACK |

### Methods

#### getName()

> Get the app name

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get app name</Summary>

** Source code **

```swift
let app = generalSettings.getName()
```

</details>

#### setName(name)

> Set the app name

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| name | String? | The kintone app name. The maximum character limit is 64.

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get app name</Summary>

** Source code **

```swift
let generalSettings = GeneralSettings()
let appName: String =  {app_name}
generalSettings.setName(appName)
```

</details>


#### getDescription()

> Get the app description

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get app description</Summary>

** Source code **

```swift
let description = generalSettings.getDescription()
```

</details>

#### setDescription()

> Set the app description

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| description | String? | The App description. The maximum character limit is 10,000. HTML tags can be used.

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>set app description</Summary>

** Source code **

```swift
let generalSettings = GeneralSettings()
generalSettings.setDescription("description")

```

</details>

#### getIcon()

> Get the App icon.

**Parameter**

(none)

**Return**

[Icon](./app-general/#icon)?

**Sample code**

<details class="tab-container" open>
<Summary>get the App icon</Summary>

** Source code **

```swift
let appIcon = generalSettings.getIcon()
```

</details>

#### setIcon(icon)

> Set the App icon

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| icon | [Icon](./app-general/#icon) | An Icon containing information of the App icon.

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>set the app icon</Summary>

** Source code **

```swift
let generalSettings = GeneralSettings()
let icon = Icon("icon_key", Icon.IconType.PRESET, nil)
generalSettings.setIcon(icon)
```

</details>

#### getTheme()

> Get the Color theme.

**Parameter**

(none)

**Return**

[GeneralSettings.IconTheme](./app-general/#icontheme)?

**Sample code**

<details class="tab-container" open>
<Summary>get the Color theme</Summary>

** Source code **

```swift
let appIconTheme = generalSettings.getTheme()
```

</details>

#### setTheme(theme)

> Set the App icon

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| theme | [GeneralSettings.IconTheme](./app-general/#icontheme) | An Icon containing information of the App icon.

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>set the app icon</Summary>

** Source code **

```swift
let generalSettings = GeneralSettings()
generalSettings.setTheme(GeneralSettings.IconTheme.WHITE)
```

</details>

## Icon

The App icon.

### Constants

#### IconType
| Name| Type| value| Description
| --- | --- | --- | --- |
| FILE | String | FILE | An uploaded image. |
| PRESET | String | PRESET | A preset icon within kintone. |

### Constructor

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| icontype | [Icon.IconType](./app-general/#icontype) | The icon Type.
| File | [File](./file-model)? | A File containing information of uploaded icon files <br>Required, if the "icon.type" parameter is set as "FILE".|
| key | String? | The key identifier of the icon.<br>Required, if the "icon.type" parameter is set as "PRESET".<br>(Preset icons have key identifiers that can be obtained using theGet General Settings API.)|

**Sample code**

<details class="tab-container" open>
<Summary>Init Icon class</Summary>

** Source code **

```swift
let icon = Icon("icon_key", Icon.IconType.PRESET, nil)
```

</details>

### Methods

#### getIcontype()

> Get icon Type.

**Parameter**

(none)

**Return**

[Icon.IconType](./app-general/#icontype)?

**Sample code**

<details class="tab-container" open>
<Summary>get icon Type.</Summary>

** Source code **

```swift
let file = icon.getIcontype()
```

</details>

#### setIcontype()

> Set icon Type

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| icontype | [Icon.IconType](./app-general/#icontype) | The icon Type.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set icon Type</Summary>

** Source code **

```swift
let icon = Icon(nil, Icon.IconType.FILE, nil)
icon.setIcontype(Icon.IconType.PRESET)
```

</details>

#### getFile()

> Get file data

**Parameter**

(none)

**Return**

[File](./file-model)?

**Sample code**

<details class="tab-container" open>
<Summary>get file data</Summary>

** Source code **

```swift
let file = icon.getFile()
```

</details>

#### setFile()

> Set file data

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| File | [File](./file-model)? | A File containing information of uploaded icon files <br>Required, if the "icon.type" parameter is set as "FILE".|

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set file data</Summary>

** Source code **

```swift

// Init File Module
let fileManager = File(connection)
let recordManager = Record(connection)
let icon = Icon(nil, Icon.IconType.FILE, nil)

do {
    // execute upload file API
    let bundle = Bundle(for: type(of: self))
    let upload_file_path = bundle.url(forResource: "test", withExtension: "txt")
    let fileModel = try fileManager.upload(upload_file_path!.absoluteString)
    icon.setFile(fileModel)
}
```

</details>

#### getKey()

> Get the key identifier of the icon.

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get the key identifier of the icon</Summary>

** Source code **

```swift
let iconKey = icon.getKey()
```

</details>

#### setKey()

> Set the key identifier of the icon

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| key | String? | The key identifier of the icon.<br>Required, if the "icon.type" parameter is set as "PRESET".<br>(Preset icons have key identifiers that can be obtained using theGet General Settings API.)|

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the key identifier of the icon</Summary>

** Source code **

```swift
let icon = Icon(nil, Icon.IconType.FILE, nil)
let iconKey: String = {app_icon_key}
icon.setKey(iconKey)
```

</details>
