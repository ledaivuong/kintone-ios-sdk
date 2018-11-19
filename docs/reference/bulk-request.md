# BulkRequest

The Bulk Request API allows multiple API requests to run on multiple kintone apps. The below API can be used with the Bulk Request API:

- Add Record
- Add Records
- Update Record
- Update Records
- Delete Records
- Update Status
- Update Statuses
- Update Assignees

## Constructor

### **Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| connection | [Connection](./connection) | yes | The connection module of this SDK.

### **Sample code**

<details class="tab-container" open>
<Summary>Init bulk request module</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let myDomainName: String = {your_domain}
let appId = 1
 
// Init authenticationAuth
let auth = Auth()
auth.setPasswordAuth(username, password)
 
// Init Connection without "guest space ID"
let connection = Connection(myDomainName, auth)
 
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);
```

</details>

## Methods

> All below methods (excluded `execute()` method) will add request to queue, you must execute the `execute()` function to get result of BulkRequest.

### addRecord(app, record)

**Parameter**

See at [Record - addRecord](./record#addrecordappid-recorddata)

**Return**

[BulkRequest](#bulkrequest)

### **Sample code**

<details class="tab-container" open>
<Summary>add Record</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);

// create add data
var record: [String: FieldValue] = [:]
let fv = FieldValue()
fv.setType(FieldType.SINGLE_LINE_TEXT)
fv.setValue("test")
record["FieldCode1"] = fv

// execute add record API
let appID: Int = {your_app_id}
var response: BulkRequestResponse? = nil
do {
    bulkRequestManager = try bulkRequestManager.addRecord(appId, nil)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

### addRecords(app, records)

**Parameter**

See at [Record - addRecords](./record#addrecordsappid-recordsdata)

**Return**

[BulkRequest](#bulkrequest)

### **Sample code**

<details class="tab-container" open>
<Summary>add multiple Records</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);

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
var response: BulkRequestResponse? = nil
 
do {
    bulkRequestManager = try bulkRequestManager.addRecords(appId, addData)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

### updateRecordByID(app, id, record, revision)

**Parameter**

See at [Record - updateRecordByID](./record#updaterecordbyidappid-recordid-recorddata-revision)

**Return**

[BulkRequest](#bulkrequest)

### **Sample code**

<details class="tab-container" open>
<Summary>update Record By ID</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);
 
// create update data
var updateData:Dictionary<String, FieldValue> = [:]
var field = FieldValue()
field.setType(FieldType.SINGLE_LINE_TEXT)
field.setValue("Test Value Update")
updateData[{your_field_code}] = field

// execute update record API
let appID: Int = {your_app_id}
let updRecID: Int = {your_record_id}
var response: BulkRequestResponse? = nil
do {
    bulkRequestManager = try bulkRequestManager.updateRecordByID(appID, updRecID, updateData , nil)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

### updateRecordByUpdateKey(app, updateKey, record, revision)

**Parameter**

See at [Record - updateRecordByUpdateKey](./record#updaterecordbyupdatekeyappid-updatekey-recorddata-revision)

**Return**

[BulkRequest](#bulkrequest)

### **Sample code**

<details class="tab-container" open>
<Summary>update Record By UpdateKey</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);
 
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
var response: BulkRequestResponse? = nil
 
do {
    bulkRequestManager = try bulkRequestManager.updateRecordByUpdateKey(appID, updKey, updateData, nil)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

### updateRecords(app, records)

**Parameter**

See at [Record - updateRecords](./record#updaterecordsappid-recordsdata)

**Return**

[BulkRequest](#bulkrequest)

### **Sample code**

<details class="tab-container" open>
<Summary>update multiple Records</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);
 
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
var response: BulkRequestResponse? = nil
 
do {
    bulkRequestManager = try bulkRequestManager.updateRecords(appID, updateItemList)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

### deleteRecords(app, ids)

**Parameter**

See at [Record - deleteRecords](./record#deleterecordsappid-recordids)

**Return**

[BulkRequest](#bulkrequest)

### **Sample code**

<details class="tab-container" open>
<Summary>Bulk Delete Records</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);

// execute delete record API
let appID: Int = {your_app_id}
let delRecordID1: Int = {your_record_id1}
let delRecordID2: Int = {your_record_id2}
let delIdList = [delRecordID1, delRecordID2]

var response: BulkRequestResponse? = nil
 
do {
    bulkRequestManager = try bulkRequestManager.deleteRecords(appID, delIdList)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

### deleteRecordsWithRevision(app, idsWithRevision)

**Parameter**

See at [Record - deleteRecordsWithRevision](./record#deleterecordswithrevisionappid-idswithrevision)

**Return**

[BulkRequest](#bulkrequest)

### **Sample code**

<details class="tab-container" open>
<Summary>delete Records With Revision</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);

// execute delete record API
let appID: Int = {your_app_id}
var delIdAndRevision: Dictionary<Int, Int> = [:]
delIdAndRevision[{your_record_id}] = {your_revision_id}
delIdAndRevision[{your_record_id}] = {your_revision_id}

var response: BulkRequestResponse? = nil
 
do {
    bulkRequestManager = try bulkRequestManager.deleteRecordsWithRevision(appID, delIdAndRevision)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

### updateRecordAssignees(app, record, assignees, revision)

**Parameter**

See at [Record - updateRecordAssignees](./record#updaterecordassigneesappid-recordid-assignees-revision)

**Return**

[BulkRequest](#bulkrequest)

### **Sample code**

<details class="tab-container" open>
<Summary>Update the Assignees for the record</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);

// execute update assignees API
let appID: Int = {your_app_od}
let updRecID: Int = {your_record_id}
let assignees: [String] = ["{your_user_code}"]

var response: BulkRequestResponse? = nil
 
do {
    bulkRequestManager = try bulkRequestManager.updateRecordAssignees(appID, updRecID, assignees, nil)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

### updateRecordStatus(app, id, action, assignee, revision)

**Parameter**

See at [Record - updateRecordStatus](./record#updaterecordstatusappid-recordid-actionname-assignee-revision)

**Return**

[BulkRequest](#bulkrequest)

### **Sample code**

<details class="tab-container" open>
<Summary>Update the status of a single record</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);

// execute update status API
let appID: Int = {your_app_id}
let updRecID: Int = {your_record_id}
let assignee: String? = "{your_user_code}"
let status: String = "{your_status}"

var response: BulkRequestResponse? = nil
 
do {
    bulkRequestManager = try bulkRequestManager.updateRecordStatus(appID, updRecID, status, assignee, nil)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

### updateRecordsStatus(app, records)

**Parameter**

See at [Record - updateRecordsStatus](./record#updaterecordsstatusappid-recordsstatusupdate)

**Return**

[BulkRequest](#bulkrequest)

### **Sample code**

<details class="tab-container" open>
<Summary>Update the status of multiple records in bulk</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);

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

var response: BulkRequestResponse? = nil
 
do {
    bulkRequestManager = try bulkRequestManager.updateRecordsStatus(appID, itemList)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

### execute()

> Execute the bulk request and get data response

**Parameter**

(none)

**Return**

[BulkRequestResponse](./bulk-request-model#bulkrequestresponse)

### **Sample code**

<details class="tab-container" open>
<Summary>Execute bulk request</Summary>

** Source code **

```swift
// Init Bulk request
var bulkRequestManager = BulkRequest(connection);

do {
    bulkRequestManager = try bulkRequestManager.addRecord(/*[Args]*/)
    bulkRequestManager = try bulkRequestManager.addRecords(/*[Args]*/)
    bulkRequestManager = try bulkRequestManager.updateRecords(/*[Args]*/)
    bulkRequestManager = try bulkRequestManager.deleteRecords(/*[Args]*/)
    response = try bulkRequestManager.execute()
} catch  {
    // Handle error
}
```

</details>

## Reference

- [Get Record](https://developer.kintone.io/hc/en-us/articles/213149287/) `on developer network`