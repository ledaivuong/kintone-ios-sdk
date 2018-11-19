# Response

General record response, using for data response from the kintone app


## BasicResponse

### Methods

#### getRevision()

> Get a revision number

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get a revision number</Summary>

** Source code **

```swift
let revision: Int? = basicResponse.getRevision()
```

</details>

## AddPreviewAppResponse

### Methods

#### getApp()

> Get the App ID of the created preview App

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>Get the App ID</Summary>

** Source code **

```swift
let appID: Int? = addPreviewAppResponse.getApp()
```

</details>

#### getRevision()

> Get a revision number

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get a revision number</Summary>

** Source code **

```swift
let revision: Int? = addPreviewAppResponse.getRevision()
```

</details>

## GetViewsResponse

### Methods

#### getViews()

> Get the View information

**Parameter**

(none)

**Return**

Dictionary< String, [ViewModel](./app-viewmodel)>?

**Sample code**

<details class="tab-container" open>
<Summary>get the View information</Summary>

** Source code **

```swift
let views: [String: ViewModel]? = getViewResponse.getViews()
```
</details>

#### getRevision()

> Get a revision number

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get a revision number</Summary>

** Source code **

```swift
let revision: Int? = getViewsResponse.getRevision()
```
</details>

## UpdateViewsResponse

### Methods

#### getViews()

> Get the View information

**Parameter**

(none)

**Return**

Dictionary< String, [ViewModel](./app-viewmodel)>?

**Sample code**

<details class="tab-container" open>
<Summary>get the View information</Summary>

** Source code **

```swift
let views: [String: ViewModel]? = updateViewsResponse.getViews()
```
</details>

#### getRevision()

> Get a revision number

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get a revision number</Summary>

** Source code **

```swift
let revision: Int? = updateViewsResponse.getRevision()
```
</details>

## GetAppDeployStatusResponse

### Methods

#### getApps()

> Get the list of objects with data of deploy statuses.

**Parameter**

(none)

**Return**

Array<[AppModel](./app-model/#appmodel)>?

**Sample code**

<details class="tab-container" open>
<Summary>get the list of objects with data of deploy statuses</Summary>

** Source code **

```swift
let apps: [AppDeployStatus]? = getAppDeployStatusResponse.getApps()
```
</details>

## GetAppsResponse

### Methods

#### getApps()

> Get the list of App Info.

**Parameter**

(none)

**Return**

Array<[AppDeployStatus](./app-model/#appdeploystatus)>?

**Sample code**

<details class="tab-container" open>
<Summary>get the list of App Info</Summary>

** Source code **

```swift
let apps: [AppModel]? = getAppsResponse.getApps()
```
</details>
