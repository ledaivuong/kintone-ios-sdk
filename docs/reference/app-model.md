# AppModel


## AppModel

Gets the basic information about the app.

>
- Permissions to view the App is needed.
- API Tokens cannot be used with this API.

### Constructor

#### **Parameter**

(none)

#### **Sample code**

<details class="tab-container" open>
<Summary>Init App Model</Summary>

** Source code **

```swift
let appModel = AppModel()
```

</details>

### Methods

#### getAppId()

> Get the appId

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get App Id</Summary>

** Source code **

```swift
let appId = appModel.getAppId()
```

</details>

#### getCode()

> Get the code

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get Code</Summary>

** Source code **

```swift
let code = appModel.getCode()
```

</details>

#### getName()

> Get the name

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get Name</Summary>

** Source code **

```swift
let name = appModel.getName()
```

</details>

#### getDescription()

> Get the description

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get Description</Summary>

** Source code **

```swift
let description = appModel.getDescription()
```

</details>

#### getSpaceId()

> Get the spaceId

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get Space Id</Summary>

** Source code **

```swift
let spaceId = appModel.getSpaceId()
```

</details>

#### getThreadId()

> Get the threadId

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get Thread Id</Summary>

** Source code **

```swift
let threadId = appModel.getThreadId()
```

</details>

#### getCreator()

> Get the creator

**Parameter**

(none)

**Return**

[Member](./member)?

**Sample code**

<details class="tab-container" open>
<Summary>get Creator</Summary>

** Source code **

```swift
let member = appModel.getCreator()
```

</details>

#### getModifier()

> Get the modifier

**Parameter**

(none)

**Return**

[Member](./member)?

**Sample code**

<details class="tab-container" open>
<Summary>get Modifier</Summary>

** Source code **

```swift
let member = appModel.getModifier()
```

</details>

#### getCreatedAt()

> Get the createdAt

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get Create Date</Summary>

** Source code **

```swift
let date = appModel.getCreatedAt()
```

</details>

#### getModifiedAt()

> Get the modifiedAt

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get Modified Date</Summary>

** Source code **

```swift
let date = appModel.getModifiedAt()
```

</details>

## AppDeployStatus

Gets the basic information about the app.

>
- The status of the deployment of App settings.

### Constants

#### Status

| Name| Type| value| Description |
| --- | --- | --- | --- |
| PROCESSING | String | PROCESSING | The App settings are being deployed.
| SUCCESS | String | SUCCESS | The App settings have been deployed.
| FAIL | String | FAIL | An error occurred, and the deployment of App settings failed.
| CANCEL | String | CANCEL | The deployment of App settings was canceled, due to the deployment of other App settings failing.

### Methods

#### getApp()

> Get the appId

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get App Id</Summary>

** Source code **

```swift
let appId: Int? = appDeployStatus.getApp()
```

</details>

#### setApp(app)

> Set the appId

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| app | Int? | The kintone app ID

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set App Id</Summary>

** Source code **

```swift
appDeployStatus.setApp({app_id})
```

</details>

#### getStatus()

>  Get the status of the deployment of App settings.

**Parameter**

(none)

**Return**

[AppDeployStatus.Status](./app-model/#status)?

**Sample code**

<details class="tab-container" open>
<Summary>get status</Summary>

** Source code **

```swift
let status = appDeployStatus.getStatus()
```

</details>

#### setStatus(status)

> Set the status of the deployment of App settings.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| status | [AppDeployStatus.Status](./app-model/#status) |  The kintone app ID

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the status</Summary>

** Source code **

```swift
appDeployStatus.setStatus(AppDeployStatus.Status.FAIL)
```

</details>

