# Record

Provide manipulate functions on records: get, update, delete, update the record status & assignees in the kintone app

## Constructor

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| connection | [Connection](./connection) | yes | The connection module of this SDK.

**Sample code**

<details class="tab-container" open>
<Summary>Init record module</Summary>

** Source code **

```swift
// Define Authentication object
let username: String = {your_user_name}
let password: String = {your_user_password}
let kintoneAuth = Auth()
kintoneAuth.setPasswordAuth(username, password)

let myDomainName: String = "sample.cybozu.com"
let connection = Connection(myDomainName, kintoneAuth)

// Init Record Module
let kintoneRecordManager = Record(connection);
```

</details>

## Methods

### getRecord(app, id)

> Retrieves details of 1 record from an app.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| id | Int | yes | The record ID in kintone app


**Return**

[GetRecordResponse](./record-model/#getrecordresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Get record</Summary>

** Source code **

```swift
// Define Authentication object
let username: String = {your_user_name}
let password: String = {your_user_password}
let auth = Auth()
auth.setPasswordAuth(username, password)

let myDomainName: String = {your_domain}
let connection = Connection(myDomainName, auth)

// Init Record Module
let recordManagement = Record(connection)
         
// execute get record API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetRecordResponse? = nil
do {
    response = try recordManagement.getRecord(appID, recordID)
             
    let resultData = response!.getRecord()!
    print(resultData["$id"]?.getValue())
             
    for (code, value) in resultData {
        print(value.getType()!)
        print(value.getValue())
    }
} catch {
    // error handle
}
```

</details>

### getRecords(app, query, fields, totalCount)

> Retrieves details of multiple records from an app using a query string.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| query | String | (optional) | [The query string](https://developer.kintone.io/hc/en-us/articles/213149287#getrecords) that will specify what records will be responded.
| fields | ArrayList<String\>| (optional) | List of field codes you want in the response.
| totalCount | Boolean | (optional) | If "true", the request will retrieve total count of records match with query conditions.

**Return**

[GetRecordsResponse](./record-model/#getrecordsresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Get records</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
         
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
         
// Init Record Module
let recordManagement = Record(connection)
         
// execute get records API
let appID: Int = {your_app_id}
let query: String? = "レコード番号 >= 2 order by レコード番号 asc"
var response: GetRecordsResponse? = nil
do {
    response = try recordManagement.getRecords(appID, query, nil, true)
    let records = response?.getRecords()
             
    for (i, dval) in (records?.enumerated())! {
        for (code, value) in dval {
            print(value.getType())
            print(value.getValue())
        }
    }
} catch {
    // error handle
}
```

</details>

### addRecord(app, record)

>Add one record to an app.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| record | Dictionary<String, [FieldValue](./record-field-model#fieldvalue)\> | (optional) | The record data to be add to kintone app. About the format, please look the sample below or [reference](#reference) at the end of this page

**Return**

[AddRecordResponse](./record-model/#addrecordresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Add record</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
         
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
         
// Init Record Module
let recordManagement = Record(connection)
         
// create add data
var addData: Dictionary<String, FieldValue> = [:]
var field = FieldValue()
field.setType(FieldType.SINGLE_LINE_TEXT)
field.setValue("Test Value")
addData[{your_field_code}] = field
         
// execute add record API
let appID: Int = {your_app_id}
var response: AddRecordResponse? = nil
do {
    response = try recordManagement.addRecord(appID, addData)
    print(response?.getId())
    print(response?.getRevision())
} catch {
    // error handle
}
```

</details>

### addRecords(app, records)

>Add multiple records to an app.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| records | Array<Dictionary<String, [FieldValue](./record-field-model#fieldvalue)\>\> | yes | List of records data to be add to kintone app. About the format, please look the sample below or [reference](#reference) at the end of this page.

**Return**

[AddRecordsResponse](./record-model/#addrecordsresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Add multi records</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
         
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
         
// Init Record Module
let recordManagement = Record(connection)
         
// create add data
var addData1: Dictionary<String, FieldValue> = [:]
var addData2: Dictionary<String, FieldValue> = [:]
var field1 = FieldValue()
var field2 = FieldValue()
field1.setType(FieldType.SINGLE_LINE_TEXT)
field1.setValue("Test Value1")
field2.setType(FieldType.SINGLE_LINE_TEXT)
field2.setValue("Test Value2")
addData1[{your_field_code}] = field1
addData2[{your_field_code}] = field2
var addDataList = [addData1, addData2]
 
// execute add records API
let appID: Int = 311
var response: AddRecordsResponse? = nil
do {
    response = try recordManagement.addRecords(appID, addDataList)
    print(response!.getIDs())
    print(response!.getRevisions())
} catch {
    // error handle
}
```

</details>

### updateRecordByID(app, id, record, revision)

> Updates details of 1 record in an app by specifying its record number.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| id | Int | yes | The record ID on kintone app
| record | Dictionary<String, [FieldValue](./record-field-model#fieldvalue)\> | yes | The record data to be update in  kintone app. About the format, please look the sample below or [reference](#reference) at the end of this page.
| revision | Int | (optional) | The revision number of record

**Return**

[UpdateRecordResponse](./record-model/#updaterecordresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Update record by ID</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
         
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
         
// Init Record Module
let recordManagement = Record(connection)
         
// create add data
var updateData:Dictionary<String, FieldValue> = [:]
var field = FieldValue()
field.setType(FieldType.SINGLE_LINE_TEXT)
field.setValue("Test Value Update")
updateData[{your_field_code}] = field
         
// execute update record API
let appID: Int = {your_app_id}
let updRecID: Int = {your_record_id}
var response: UpdateRecordResponse? = nil
do {
    response = try recordManagement.updateRecordByID(appID, updRecID, updateData , nil)
    print(response?.getRevision())
} catch {
    // error handle
}
```

</details>

### updateRecordByUpdateKey(app, updateKey, record, revision)

Updates details of 1 record in an app by unique key.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| updateKey | [RecordUpdateKey](./record-model/#recordupdatekey) | yes | The unique key of the record to be updated. About the format, please look the sample below or [reference](#reference) at the end of this page.
| record | Dictionary<String, [FieldValue](./record-field-model#fieldvalue)\>  | yes | The record data will be added to kintone app. About the format, please look the sample below or [reference](#reference) at the end of this page.
| revision | Int | (optional) | The revision number of record

**Return**

[UpdateRecordResponse](./record-model/#updaterecordresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Update record by UpdateKey</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
         
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
         
// Init Record Module
let recordManagement = Record(connection)
         
// create update data
var updateData: Dictionary<String, FieldValue> = [:]
var field = FieldValue()
field.setType(FieldType.SINGLE_LINE_TEXT)
field.setValue("Test Value Update For Key")
updateData[{your_field_code}] = field
         
// create update key
let updKey = RecordUpdateKey("{your_field_code}", "update key value")
         
// execute update record API
let appID: Int = {your_app_id}
var response: UpdateRecordResponse? = nil
do {
    response = try recordManagement.updateRecordByUpdateKey(appID, updKey, updateData, nil)
    print(response?.getRevision())
} catch {
    // error handle
}
```

</details>

### updateRecords(app, records)

> Updates details of multiple records in an app, by specifying their record number, or a different unique key.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| records | Array<[RecordUpdateItem](./record-model/#recordupdateitem)\> | yes | The record data will be added to kintone app. About the format, please look the sample below or [reference](#reference) at the end of this page.

**Return**

[UpdateRecordsResponse](./record-model/#updaterecordsresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Update multi records</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
         
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
         
// Init Record Module
let recordManagement = Record(connection)
         
// create update data
var recId1: Int = {your_record_id}
var recId2: Int = {your_record_id}
var updateData1: Dictionary<String, FieldValue> = [:]
var updateData2: Dictionary<String, FieldValue> = [:]
var field1 = FieldValue()
var field2 = FieldValue()
field1.setType(FieldType.SINGLE_LINE_TEXT)
field1.setValue("Test Update Value1 ")
field2.setType(FieldType.SINGLE_LINE_TEXT)
field2.setValue("Test Update Value2")
updateData1[{your_field_code}] = field1
updateData2[{your_field_code}] = field2
var updateDataItem1 = RecordUpdateItem(recId1, nil, nil, updateData1)
var updateDataItem2 = RecordUpdateItem(recId2, nil, nil, updateData2)
let updateItemList = [updateDataItem1 , updateDataItem2]
         
// execute update records API
let appID: Int = {your_app_id}
var response: UpdateRecordsResponse? = nil
do {
    response = try recordManagement.updateRecords(appID, updateItemList)
    for value in (response!.getRecords())! {
        print(value.getID())
        print(value.getRevision())
    }
} catch {
    // error handle
}
```

</details>

### deleteRecords(app, ids)

> Deletes multiple records in an app.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| ids | Array<Int\> | yes | The list ids of record will be delete.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Delete multi record</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
 
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
  
// Init Record Module
let recordManagement = Record(connection)
 
// execute delete record API
let appID: Int = {your_app_id}
let delRecordID1: Int = {your_record_id1}
let delRecordID2: Int = {your_record_id2}
let delIdList = [delRecordID1, delRecordID2]
 
do {
    try recordManagement.deleteRecords(appID, delIdList)
} catch {
    // error handle
}
```

</details>

### deleteRecordsWithRevision(app, idsWithRevision)

> Deletes multiple records in an app with revision.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| idsWithRevision | Dictionary<Int, Int\> | yes |  (**key**: `The Id of record`, **value**: `The Revision of record.`)

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Delete record with revision</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
         
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
         
// Init Record Module
let recordManagement = Record(connection)
         
// execute delete record API
let appID: Int = {your_app_id}
var delIdAndRevision: Dictionary<Int, Int> = [:]
delIdAndRevision[{your_record_id}] = {your_revision_id}
delIdAndRevision[{your_record_id}] = {your_revision_id}
         
do {
    try recordManagement.deleteRecordsWithRevision(appID, delIdAndRevision)
} catch {
   // error handle
}
```

</details>

### updateRecordAssignees(app, id, assignees, revision)

> Update assignees of a record.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app  | Int | yes | The kintone app ID
| id  | Int | yes | The record ID of kintone app
| assignees | ArrayList<String\> | yes | The user code(s) of the assignee(s)
| revision | Int | (option) | The revision number of record

**Return**

[UpdateRecordResponse](./record-model/#updaterecordresponse)

**Sample code**

<details class="tab-container" open>
<Summary>update record Assignees</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
 
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
  
// Init Record Module
let recordManagement = Record(connection)
 
// execute update assignees API
let appID: Int = {your_app_od}
let updRecID: Int = {your_record_id}
let assignees: [String] = ["{your_user_code}"]
var response: UpdateRecordResponse? = nil
do {
    response = try recordManagement.updateRecordAssignees(appID, updRecID, assignees, nil)
    print(response!.getRevision())
} catch {
    // error handle
}
```

</details>

### updateRecordStatus(app, id, action, assignee, revision)

> Updates the Status of a record of an app.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID.
| id | Int | yes | The record ID on kintone app.
| action | String | yes | The Action name will be run.
| assignee | String | (Conditionally required) | The next Assignee. Specify the Assignee's log in name.</br>Required, if the "Assignee List" of the current status is set to "User chooses one assignee from the list to take action", and a selectable assignee exists.
| revision | Int | (optional) | The revision of record

**Return**

[UpdateRecordResponse](./record-model/#updaterecordresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Update record status</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
 
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
  
// Init Record Module
let recordManagement = Record(connection)
 
// execute update status API
let appID: Int = {your_app_id}
let updRecID: Int = {your_record_id}
let assignee: String? = "{your_user_code}"
let status: String = "{your_status}"
var response: UpdateRecordResponse? = nil
do {
    response = try recordManagement.updateRecordStatus(appID, updRecID, status, assignee, nil)
    print(response?.getRevision())
} catch {
    // error handle
}
```

</details>

### updateRecordsStatus(app, records)

> Updates the Status of multiple records of an app.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| records | Array<[RecordUpdateStatusItem](./record-model/#recordupdatestatusitem)\> | yes | The recod status data. See belowsample codee or [reference](#reference) at the end of this page to know format.

**Return**

[UpdateRecordsResponse](./record-model/#updaterecordsresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Update multi record status</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
 
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
  
// Init Record Module
let recordManagement = Record(connection)
 
// execute update status API
let appID: Int = {your_app_id}
let updRecID1: Int = {your_record_id1}
let updRecID2: Int = {your_record_id2}
let assignees1: String? = {your_login_code1}
let assignees2: String? = {your_login_code2}
let status1: String? = {your_update_status1}
let status2: String? = {your_update_status2}
let item1 = RecordUpdateStatusItem(status1, assignees1, updRecID1, nil)
let item2 = RecordUpdateStatusItem(status2, assignees2, updRecID2, nil)
let itemList = [item1, item2]
         
var response: UpdateRecordsResponse? = nil
do {
    response = try recordManagement.updateRecordsStatus(appID, itemList)
    for value in (response!.getRecords())! {
        print(value.getID())
        print(value.getRevision())
    }
} catch {
    // error handle
}
```

</details>

### getComments(app, record, order, offset, limit)

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| record | Int | yes | The kintone app ID
| order | String | (optional) | The sort order of the Comment ID. Please select **asc** or **desc**
| offset | Int | (optional) | The number of first comments will be ignored.
| limit | Int | (optional) | The number of records to retrieve.

**Return**

[GetCommentsResponse](./record-comment-model/#getcommentsresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Get comments</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
 
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
  
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)
             
    // data Response of the get request
    for value in (response?.getComments())! {
        print(value.getId())
        print(value.getCreatedAt())
        print(value.getText())
        print(value.getCreator()?.code)
        print(value.getMentions())
    }
} catch {
    // error handle
}
```

</details>

### addComment(app, record, comment)

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID |
| record | Int | yes | The kintone app ID |
| comment | [CommentContent](./record-comment-model/#commentcontent) | yes | About the format, please look the sample below or [reference](#reference) at the end of this page.|

**Return**

[AddCommentResponse](./record-comment-model/#addcommentresponse)

**Sample code**

<details class="tab-container" open>
<Summary>Add comment</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
 
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
  
// Init Record Module
let recordManagement = Record(connection)
 
// create add comment data
let mention = CommentMention()
let comment = CommentContent()
mention.setCode("cybozu")
mention.setType("USER")
let mentionList = [mention]
comment.setText("add comment")
comment.setMentions(mentionList)
             
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: AddCommentResponse? = nil
do {
    response = try recordManagement.addComment(appID, recordID, comment)
                 
    // data Response of the get request
    print(response?.getId())
} catch {
    // error handle
}
```

</details>

### deleteComment(app, record, comment)

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Int | yes | The kintone app ID
| record | Int | yes | The record ID on kintone app
| comment | Int | yes | The comment ID on kintone record

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Delete comment</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let domain: String = {your_domain}
  
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
 
// Init Connection without "guest space ID"
let connection = Connection(domain, auth)
  
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appId: Int = {your_app_id}
let recordId: Int = {your_record_id}
let commentId: Int = {your_comment_Id}
 
do {
    try recordManagement.deleteComment(appId, recordId, commentId)
} catch {
    // error handle
}
```

</details>

## Reference

- [Get Record](https://developer.kintone.io/hc/en-us/articles/213149287/) `on developer network`
- [Add Record](https://developer.kintone.io/hc/en-us/articles/212494628/)`on developer network`
- [Update Record](https://developer.kintone.io/hc/en-us/articles/213149027/)`on developer network`
- [Delete Record](https://developer.kintone.io/hc/en-us/articles/212494558/)`on developer network`
- [Get Comments](https://developer.kintone.io/hc/en-us/articles/219105188)`on developer network`
- [Add Comment](https://developer.kintone.io/hc/en-us/articles/219501367)`on developer network`
- [Delete Comment](https://developer.kintone.io/hc/en-us/articles/219562607)`on developer network`
- [Update Record Status](https://developer.kintone.io/hc/en-us/articles/213149747)`on developer network`
- [Update Record Assignees](https://developer.kintone.io/hc/en-us/articles/219563427)`on developer network`