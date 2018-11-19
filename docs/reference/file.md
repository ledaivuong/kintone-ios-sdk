# File

Provide manipulate functions on file: file download & file upload in the kintone app.


## Constructor

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| connection | [Connection](./connection) | yes | The connection module of this SDK.

**Sample code**

<details class="tab-container" open>
<Summary>Initial file class</Summary>

** Source code **

```swift
// Define Authentication object
let username: String = {your_user_name}
let password: String = {your_user_password}
let auth = Auth()
auth.setPasswordAuth(username, password)

let myDomainName: String = {your_domain}
let connection = Connection(myDomainName, auth)

let fileManagement = File(connection);
```

</details>

## Methods

### upload(filePath)

> Upload file kintone via Rest API

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| filePath | String | yes | The full path of file on your environment

**Return**

[FileModel](./file-model)

**Sample code**

<details class="tab-container" open>
<Summary>Get app sample</Summary>

** Source code **

```swift
// Define Authentication object
let username: String = {your_user_name}
let password: String = {your_user_password}
let auth = Auth()
auth.setPasswordAuth(username, password)

let myDomainName: String = {your_domain}
let connection = Connection(myDomainName, auth)

// Init File Module
let fileManager = File(connection)
let recordManager = Record(connection)
 
do {
    // execute upload file API
    let bundle = Bundle(for: type(of: self))
    let upload_file_path = bundle.url(forResource: "test", withExtension: "txt")
    let fileModel = try fileManager.upload(upload_file_path!.absoluteString)
    let fileKey = fileModel.getFileKey()
     
    // update record
    let fileParam = ["fileKey" : fileKey]
    let fkeyList = [fileParam]
    let fval = FieldValue()
    fval.setValue(fkeyList)
    let updateParam = ["attachment1" : fval]
    let updRes: UpdateRecordResponse  = try recordManager.updateRecordByID(APP_ID, 1, updateParam, nil)
} catch  {
    // Handle error
}
```

</details>

### download(fileKey, outPutFilePath)

> Download file kintone via Rest API

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| fileKey | String | yes | The file key of the uploaded file on kintone
| outPutFilePath | String | yes | The full path of output file on your environment

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Get apps sample</Summary>

** Source code **

```swift
// Define Authentication object
let username: String = {your_user_name}
let password: String = {your_user_password}
let auth = Auth()
auth.setPasswordAuth(username, password)

let myDomainName: String = {your_domain}
let connection = Connection(myDomainName, auth)

// Init File Module
let fileManager = File(connection)
let recordManager = Record(connection)
do {
    // get filekey
    let appID = 1
    let recordID = 1
    let getResponse: GetRecordResponse? = try recordManager.getRecord(appID, recordID)
    let recordVal = getResponse?.getRecord()
    let fileVal = recordVal?["TempFile"]
    let fileList = fileVal?.getValue() as! [FileModel]
     
    // execute download file API
    for fileResult in fileList {
        if let dowloadDir = FileManager.default.urls(for: .documentDirectory, in: .userDomainMask).first {
            let pathFileName = dowloadDir.absoluteString + fileResult.getName()!
            try fileManager.download(fileResult.getFileKey()!, pathFileName)
        }
    }
} catch {
    // Handle error
}
```

</details>
