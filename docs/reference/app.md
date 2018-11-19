# App

Gets general information of an App, including the name, description, related Space, creator and updater information.

>
- Permissions to view the App is needed.
- API Tokens cannot be used with this API.

## Constructor

### **Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| connection | [Connection](./connection) | yes | The connection module of this SDK.

### **Sample code**

<details class="tab-container" open>
<Summary>Init app module</Summary>

** Source code **

```java
// Define Authentication object
let username: String = {your_user_name}
let password: String = {your_user_password}
let kintoneAuth = Auth()
kintoneAuth.setPasswordAuth(username, password)

let myDomainName: String = "sample.cybozu.com"
let connection = Connection(myDomainName, kintoneAuth)

// Init App Module
let app = App(connection)
```

</details>

## Methods

### getApp(appId)

> Get single app

#### **Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| appId | Int? | yes | The kintone app ID

**Return**

[AppModel](./app-model#appmodel)

**Sample code**

<details class="tab-container" open>
<Summary>get App</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let appId: Int = {your_app_id}
do {
    let response = try app.getApp(appId)
    print("appId : \(response.getAppId()!)")
    print("spaceId : \(response.getSpaceId())" )
    print("threadId : \(response.getThreadId())" )
    print("name : \(response.getName()!)")
    print("description : \(response.getDescription()!)")
    print("----------------")
} catch let error as KintoneAPIException {
    print(error.getErrorResponse()!.getMessage()!)
} catch {
    // Handle another error
}
```

</details>

### getApps(offset, limit)

> Get multiple apps

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| offset | Int? | (optional) | The offset off data result
| limit | Int? | (optional) | The limit number of result

**Return**

Array<[AppModel](./app-model#appmodel)>

**Sample code**

<details class="tab-container" open>
<Summary>Get Apps</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

do {
    let apps = try app.getApps()
    var count = 1
    for appInfo in apps {
        print("App[\(count)] : ");
        print("appId : \(appInfo.getAppId()!)")
        print("spaceId : \(appInfo.getSpaceId())" )
        print("threadId : \(appInfo.getThreadId())" )
        print("name : \(appInfo.getName()!)")
        print("description : \(appInfo.getDescription()!)")
        print("----------------")
        count = count + 1
    }
} catch let error as KintoneAPIException {
    print(error.getErrorResponse()!.getMessage()!)
} catch {
    // Handle another error
}
```

</details>

### getAppsByIDs(ids, offset, limit)

> Get multiple apps by list of ids

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| ids | Array<Int\>? | yes | The array of app ids
| offset | Int? | (optional) | The offset off data result
| limit | Int? | (optional) | The limit number of result

**Return**

Array<[AppModel](./app-model#appmodel)>

**Sample code**

<details class="tab-container" open>
<Summary>get Apps By IDs</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

var appIds: [Int] = [{your_app_id}, {your_app_id}]
let limit: Int = {your_limit}
let offset : Int = {your_offset}
  
do {
   let apps = try app.getAppsByIDs(appIds, offset, limit)
   var count = 1
   for appInfo in apps {
      print("App[\(count)] : ");
      print("appId : \(appInfo.getAppId()!)")
      print("spaceId : \(appInfo.getSpaceId())" )
      print("threadId : \(appInfo.getThreadId())" )
      print("name : \(appInfo.getName()!)")
      print("description : \(appInfo.getDescription()!)")
      print("----------------")
      count = count + 1
   }
} catch let error as KintoneAPIException {
   print(error.getErrorResponse()!.getMessage()!)
} catch {
    // Handle another error 
}
```

</details>

### getAppsByCodes(codes, offset, limit)

> Get multiple apps by a list of codes

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| codes | Array<String\>? | yes | The array of app codes
| offset | Int? | (optional) | The offset off data result
| limit | Int? | (optional) | The limit number of result

**Return**

Array<[AppModel](./app-model#appmodel)>

**Sample code**

<details class="tab-container" open>
<Summary>get Apps By Codes</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

var appCode: [String] = [{your_app_code}, {your_app_code}]
let limit: Int = {your_limit}
let offset: Int = {your_offset}
 
do {
   let apps = try app.getAppsByCodes(appCode, offset, limit)
   var count = 1
   for appInfo in apps {
      print("App[\(count)] : ");
      print("appId : \(appInfo.getAppId()!)")
      print("appCode : \(appInfo.getCode()!)")
      print("spaceId : \(appInfo.getSpaceId())" )
      print("threadId : \(appInfo.getThreadId())" )
      print("name : \(appInfo.getName()!)")
      print("description : \(appInfo.getDescription()!)")
      print("----------------")
      count = count + 1
   }
} catch let error as KintoneAPIException {
   print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error         
}
```

</details>

### getAppsByName(name, offset, limit)

> Get multiple apps by name

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| name | String | yes | The app name
| offset | Int | (optional) | The offset off data result
| limit | Int | (optional) | The limit number of result

**Return**

Array<[AppModel](./app-model#appmodel)>

**Sample code**

<details class="tab-container" open>
<Summary>get Apps By Name</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let appName: String = {your_app_name}
let limit: Int = {your_limit}
let offset: Int = {your_offset}
  
do {
   let apps = try app.getAppsByName(appName, offset, limit)
   var count = 1
   for appInfo in apps {
      print("App[\(count)] : ");
      print("appId : \(appInfo.getAppId()!)")
      print("appCode : \(appInfo.getCode()!)")
      print("spaceId : \(appInfo.getSpaceId())" )
      print("threadId : \(appInfo.getThreadId())" )
      print("name : \(appInfo.getName()!)")
      print("description : \(appInfo.getDescription()!)")
      print("----------------")
      count = count + 1
   }
} catch let error as KintoneAPIException {
   print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error          
}
```

</details>

### getAppsBySpaceIDs(spaceIds, offset, limit)

> Get multiple apps by list of space's ids

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| spaceIds | Array<Int\>? | yes | The array of space ids
| offset | Int | (optional) | The offset off data result
| limit | Int | (optional) | The limit number of result

**Return**

Array<[AppModel](./app-model#appmodel)>

**Sample code**

<details class="tab-container" open>
<Summary>get Apps By Space IDs</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let spaceIds: [Int] = [{your_space_id}, {your_space_id}]
let limit = {your_litmit}
let offset = {your_offset}
  
do {
   let apps = try app.getAppsBySpaceIDs(spaceIds, offset, limit)
   var count = 1
   for appInfo in apps {
      print("App[\(count)] : ");
      print("appId : \(appInfo.getAppId()!)")
      print("spaceId : \(appInfo.getSpaceId())" )
      print("threadId : \(appInfo.getThreadId())" )
      print("name : \(appInfo.getName()!)")
      print("description : \(appInfo.getDescription()!)")
      print("----------------")
      count = count + 1
   }
} catch let error as KintoneAPIException {
   print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```

</details>

### addPreviewApp(name, space, thread)

> Creates a preview App. 

#### **Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| name | String? | yes | The App name. The maximum length is 64 characters.
| space | Int? | (optional) | The Space ID of where the App will be created.
| thread | Int? | (optional) | The Thread ID of the thread in the Space where the App will be created.

**Return**

[AddPreviewAppResponse](./app-model/#AddPreviewAppResponse)

**Sample code**

<details class="tab-container" open>
<Summary>Creates a preview App.</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let appName: String = {your_app_name}
let spaceId = {your_space_id} // Space will add this app
let threadId = {your_thread_id} // Thread will add this app
  
do {
   var addPreviewRespones: AddPreviewAppResponse? = nil
   addPreviewRespones = try app.addPreviewApp(appName, spaceId, threadId)
   print(addPreviewRespones?.getApp())
   print(addPreviewRespones?.getRevision())
} catch let error as KintoneAPIException {
   print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```
</details>

### deployAppSettings(name, space, thread)

> Updates the settings of a pre-live App to the live App. 

#### **Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| apps | Array<[AddPreviewAppResponse](./app-model/#AddPreviewAppResponse)>? | yes | The list of Apps to deploy the pre-live settings to the live Apps.
| revert | Bool? | (optional) | The flag that indicate whether to cancel all changes made to the pre-live settings. 

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Updates the settings of a pre-live App to the live App.</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let appId: Int = {your_app_id}
let revision: Int = {your_revision} // Revision of application to deploy
let appPreview: AddPreviewAppResponse? = AddPreviewAppResponse(appId, revision)
  
do {
   try app.deployAppSettings([appPreview!], false)
} catch let error as KintoneAPIException {
   print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```

</details>

### getAppDeployStatus(apps)

> Gets the deployment status of the App settings for multiple Apps.

#### **Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| apps | Array<Int>? | yes | The list of Apps to check the deploy statuses of. The Maximum limit is 300.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Gets the deployment status of the App settings for multiple Apps.</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let appIds: [Int] = [{your_app_id}, {your_app_id}]
do {
    var deployStatusReponse: GetAppDeployStatusResponse? = nil
    deployStatusReponse = try app.getAppDeployStatus(appIds)
    let listAppsDeployStatus = deployStatusReponse?.getApps()
    for appDeployStatus in listAppsDeployStatus! {
        print(appDeployStatus.getApp())
        print(appDeployStatus.getStatus())
    }
} catch let error as KintoneAPIException {
    print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```

</details>

### getFormFields(appId, lang, isPreview)

> Get field of form in kintone app

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| appId | Int | yes | The app ID
| lang | LanguageSetting | (optional) | The language code. Support: <ul><li>DEFAULT: Default language setting of system </li><li>JA: Japanese language setting</li><li>ZH: Chinese language setting</li><li>EN: English language setting</li> |
| isPreview | Bool? | (optional) | Get the app form fields with a [pre-live settings](https://developer.kintone.io/hc/en-us/articles/115005509288).

**Return**

[FormFields](./form-fields/#formfields)

**Sample code**

<details class="tab-container" open>
<Summary>get FormFields</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let appId: Int = {your_app_id} // Integer
let lang: LanguageSetting = {language_code} // LanguageSetting .Ex: LanguageSetting.JA
  
do {
    let resp = try app.getFormFields(appId, lang)
    print(resp) // FormFields Object
} catch let error as KintoneAPIException {
    print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
  
// Get a pre-live (preview) form fields
let appId: Int = {your_app_id} // Integer
let lang: LanguageSetting = {language_code} // LanguageSetting .Ex: LanguageSetting.JA
let isPreview: Bool = true
  
do {
    let resp = try app.getFormFields(appId, lang, isPreview)
    print(resp) // FormFields Object
} catch let error as KintoneAPIException {
    print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```

</details>

### addFormFields(app, fields, revision)

> Adds fields to a form of an App. 

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int? | yes | The app ID
| fields | Dictionary<String, [Field](./form-fields/#field)\>? | yes | The formFields which will add to form of kintone app |
| revision | Int? | (optional) | revision number of the settings that will be deployed.
**Return**

[BasicResponse](./app-model/#basicresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Adds fields to a form of an App. </Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let appId: Int = {your_app_id} // App Id
let fieldCode: String = {field_code_string} // Field code of new Field. It must be not as same as any fields in Pre-Live App Setttings
let revision: Int = {latest_revision_of_the_settings} // Integer
  
// Create Radio field instance and set properties
let addNewField = RadioButtonField(fieldCode)
var optionArray = [String: OptionData]()
optionArray["1"] = OptionData("1","1")
optionArray["2"] = OptionData("2","2")
optionArray["3"] = OptionData("3","3")
addNewField.setOptions(optionArray)
addNewField.setNoLabel(false)
addNewField.setRequired(true)
addNewField.setLabel("Label Radio")
addNewField.setAlign(AlignLayout.VERTICAL)
  
// Add Field object into dictionary with key is Field Code
var properties = [String: Field]()
properties[fieldCode] = addNewField
// Another add field here
  
do {
    let response_add = try app.addFormFields(appId, properties, revision)
    print(response_add) // BasicResponse { revision : <String> }
} catch let error as KintoneAPIException {
    print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```

</details>

### updateFormFields(app, fields, revision)

> Updates the field settings of fields in a form of an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int? | yes | The app ID
| fields | Dictionary<String, [Field](./form-fields/#field)\>? | yes | The formFields which will update |
| revision | Int? | (optional) | revision number of the settings that will be deployed.
**Return**

[BasicResponse](./app-model/#basicresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Updates the field settings of fields in a form of an App.</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let appId: Int = {your_app_id} // Integer
let fieldCode: String = {field_code_string} // String | fieldCode of exist fields in Pre-Live App Setttings
let revision: Int = {latest_revision_of_the_settings} // Integer
  
// Create Field Object to Update
let updateField = SingleLineTextField(fieldCode)
updateField.setDefaultValue("Hello Kintone")
updateField.setRequired(true)
  
// Add Update Field object into dictionary with key is Field Code
var properties = [String: Field]()
properties[fieldCode] = updateField
  
do {
    let response_update = try app?.updateFormFields(appId, properties, revision)
    print(response_update) // BasicResponse { revision : <String> }
} catch let error as KintoneAPIException {
    print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```

</details>


### deleteFormFields(app, fields, revision)

> Deletes fields from a form of an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int? | yes | The app ID
| fields | Array<String>? | yes | The list of field codes of the fields to delete. Up to 100 field codes can be specified. |
| revision | Int? | (optional) | revision number of the settings that will be deployed.

**Return**

[BasicResponse](./app-model/#basicresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Deletes fields from a form of an App.</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let appId: Int = {your_app_id} // Integer
let fieldCodeArray: [String] = [{field_code_string}] // Array<String> | Array of fieldCodes of exist fields in Pre-Live App Setttings
let revision: Int = {latest_revision_of_the_settings} // Integer
  
do {
    let response_delete = try app.deleteFormFields(appId, fieldCodeArray, revision)
    print(response_delete) // BasicResponse { revision : <String> }
} catch let error as KintoneAPIException {
    print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```

</details>


### getFormLayout(appId, isPreview)

> Get layout of form in kintone app

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| appId | Int? | yes | The kintone app id
| isPreview | Bool? | (optional) | Get the app form layout with a [pre-live settings](https://developer.kintone.io/hc/en-us/articles/115005509288).

**Return**

[FormLayout](./form-layout#formlayout)

**Sample code**

<details class="tab-container" open>
<Summary>get FormLayout</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)
  
// Get a pre-live (preview) form fields
let appId: Int = {your_app_id}
let isPreview: Bool = true
  
do {
   // Get form layout by app id
   let response_layout = try app.getFormLayout(appId, isPreview)
   print(response_layout.getLayout()!)
} catch let error as KintoneAPIException {
   print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error 
}
```

</details>

### updateFormLayout(app, layout, revision)

> Updates the field layout info of a form in an App. 

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int? | yes | The kintone app id
| layout | Array<[ItemLayout](./form-layout/#itemlayout)> | yes | A list of field layouts for each row.
| revision | Int? | (optional) | revision number of the settings that will be deployed.

**Return**

[BasicResponse](./app-model/#basicresponse)

**Sample code**

<details class="tab-container" open>
<Summary>get FormLayout</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)
  
let appId: Int = {your_app_id} // Integer
do {
  let response = try app.getFormLayout(appId)
  let response_layout = response.getLayout()!
  let update_itemlayout = response_layout[0]
  if update_itemlayout.getType() == LayoutType.ROW {
    let rowLayout = update_itemlayout as! RowLayout
    let firstFields = rowLayout.getFields()![0]
    firstFields.getSize()!.setWidth("90")
  }
  let response_update_layout = try app.updateFormLayout(appId, response_layout)
  print(response_update_layout)
} catch let error as KintoneAPIException {
    print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```

</details>

### getGeneralSettings(app, lang, isPreview)

> Gets the description, name, icon, revision and color theme of an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int? | yes | The app ID
| lang | LanguageSetting | (optional) | The language code. Support: <ul><li>DEFAULT: Default language setting of system </li><li>JA: Japanese language setting</li><li>ZH: Chinese language setting</li><li>EN: English language setting</li> |
| isPreview | Bool? | (optional) | Get the app form fields with a [pre-live settings](https://developer.kintone.io/hc/en-us/articles/115005509288).

**Return**

[GeneralSettings](./app-model/#GeneralSettings)

**Sample code**

<details class="tab-container" open>
<Summary>Deletes fields from a form of an App.</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)

let appId = {your_app_id}
 
do {
   let response = try app.getGeneralSettings(appId)
   print(response)
} catch let error as KintoneAPIException {
   print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
  
// Get a pre-live (preview) general settings
let appId = {your_app_id}
let lang = {your_language_code} // LanguageSetting( EN | JA | ZH ). Ex: LanguageSetting.JA
let isPreview = true
do {
   let response = try app.getGeneralSettings(appId, lang, isPreview)
   print(response)
} catch let error as KintoneAPIException {
   print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```

</details>

### updateGeneralSettings(app, GeneralSettings, revision)

> Updates the field layout info of a form in an App. 

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int? | yes | The kintone app id
| generalSettings | [GeneralSettings](./app-model/#generalsetting) | (Conditional) | The description, name, icon, revision and color theme of an App.
| revision | Int? | (optional) | revision number of the settings that will be deployed.

**Return**

[BasicResponse](./app-model/#basicresponse)

**Sample code**

<details class="tab-container" open>
<Summary>get FormLayout</Summary>

** Source code **

```java
// Init App Module
let app = App(connection)
  
let appId: Int = {your_app_id}
let revision: Int = {latest_revision_id} // default: -1
do {
   let generalSetting = try app.getGeneralSettings(appId)
   generalSetting.setDescription("Test preview app description")
  
// Update current general settings
   let response = try app.updateGeneralSettings(appId, generalSetting, revision)
   print(response)
   // After using this API, use the Deploy App Settings API to deploy the settings to the live App.
} catch let error as KintoneAPIException {
   print(error.getErrorResponse()!.getMessage()!)
} catch {
   // Handle another error
}
```
</details>


## Reference

- [Get App](https://developer.kintone.io/hc/en-us/articles/212494888)`on developer network`
- [Get Apps](https://developer.kintone.io/hc/en-us/articles/115005336727)`on developer network`
- [Get Form fields](https://developer.kintone.io/hc/en-us/articles/115005509288)`on developer network`
- [Get Form Layout](https://developer.kintone.io/hc/en-us/articles/115005509068)`on developer network`