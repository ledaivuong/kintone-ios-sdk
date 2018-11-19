# Record Model

General record response, using for data response from the kintone app

## GetRecordResponse

### Methods

#### getRecord()

> get the Record data response.

**Parameter**

(none)

**Return**

Dictionary<String, [FieldValue](./record-field-model#fieldvalue)\>


**Sample code**

<details class="tab-container" open>
<Summary>get the Record data response.</Summary>

** Source code **


```swift
// Init Record Module
let recordManagement = Record(connection)
         
// execute get record API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetRecordResponse? = nil
do {
    response = try recordManagement.getRecord(appID, recordID)
             
    let resultData: Dictionary<String, FieldValue> = response!.getRecord()!
    }
} catch {
    // error handle
}
```

</details>

## GetRecordsResponse

### Methods

#### getRecords()

> get the Records data response.

**Parameter**

(none)

**Return**

Array<Dictionary<String, [FieldValue](./record-field-model#fieldvalue)\>\>

**Sample code**

<details class="tab-container" open>
<Summary>get the Records data response</Summary>

** Source code **
```swift
// Init Record Module
let recordManagement = Record(connection)
         
// execute get records API
let appID: Int = {your_app_id}
let query: String? = "レコード番号 >= 2 order by レコード番号 asc"
var response: GetRecordsResponse? = nil
do {
    response = try recordManagement.getRecords(appID, query, nil, true)
    let records: Array<Dictionary<String, FieldValue>>? = response?.getRecords()
} catch {
    // error handle
}
```

</details>

#### getTotalCount()

> get the number of records response.

**Parameter**

(none)

**Return**

Int

**Sample code**

<details class="tab-container" open>
<Summary>get the number of records response</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
         
// execute get records API
let appID: Int = {your_app_id}
let query: String? = "レコード番号 >= 2 order by レコード番号 asc"
var response: GetRecordsResponse? = nil
do {
    response = try recordManagement.getRecords(appID, query, nil, true)
    let count: Int? = response?.getTotalCount()
} catch {
    // error handle
}
```
</details>

## AddRecordResponse

### Methods

#### getId()

> get the the ID of record added.

**Parameter**

(none)

**Return**

Int

**Sample code**

<details class="tab-container" open>
<Summary>get the the ID of record added</Summary>

** Source code **

```swift
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
} catch {
    // error handle
}
```

</details>

#### getRevision()

> get the revision number of record added.

**Parameter**

(none)

**Return**

Int

**Sample code**

<details class="tab-container" open>
<Summary>get the revision number of record added</Summary>

** Source code **

```swift
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
    print(response?.getRevision())
} catch {
    // error handle
}
```

</details>

## AddRecordsResponse

### Methods

#### getIDs()

> get the array of added records ID.

**Parameter**

(none)

**Return**

Array<Int\>

**Sample code**

<details class="tab-container" open>
<Summary>get the array of added records ID</Summary>

** Source code **

```swift
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
} catch {
    // error handle
}
```

</details>

#### getRevisions()

> get the array of added records revision number.

**Parameter**

(none)

**Return**

Array<Int\>

**Sample code**

<details class="tab-container" open>
<Summary>get the array of added records revision number</Summary>

** Source code **

```swift
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
    print(response!.getRevisions())
} catch {
    // error handle
}
```

</details>

## UpdateRecordResponse

### Methods

#### getRevision()

> get the revision number of record updated.

**Parameter**

(none)

**Return**

Int

**Sample code**

<details class="tab-container" open>
<Summary>get the revision number of record updated</Summary>

** Source code **

```swift
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

## UpdateRecordsResponse

### Methods

#### getRecords()

> get the array of added records ID with revision.

**Parameter**

(none)

**Return**

Array<[RecordUpdateResponseItem](#recordupdateresponseitem)\>

**Sample code**

<details class="tab-container" open>
<Summary>get the array of added records ID with revision</Summary>

** Source code **

```swift
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
    let records: [RecordUpdateResponseItem] = response!.getRecords()!
} catch {
    // error handle
}
```

</details>

## RecordUpdateResponseItem

### Methods

#### getID()

> get the the ID of record updated.

**Parameter**

(none)

**Return**

Int

**Sample code**

<details class="tab-container" open>
<Summary>get the the ID of record updated</Summary>

** Source code **

```swift
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
    let resultRecords: [RecordUpdateResponseItem] = response!.getRecords()!
    let resultRecord = resultRecords[0]
    resultID: Int = resultRecord.getID()
} catch {
    // error handle
}
```

</details>

#### getRevision()

> get the revision number of record updated.

**Parameter**

(none)

**Return**

Int

**Sample code**

<details class="tab-container" open>
<Summary>get the revision number of record updated</Summary>

** Source code **

```swift
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
    let resultRecords: [RecordUpdateResponseItem] = response!.getRecords()!
    let resultRecord = resultRecords[0]
    resultRevision: Int = resultRecord.getRevision()
} catch {
    // error handle
}
```

</details>

## RecordUpdateItem

### Constructor

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| id | Int  | The ID of the record.
| revision | Int  | The revision number of the record.
| updateKey | [RecordUpdateKey](#recordupdatekey)  |  The unique key of the record to be updated. Required, if id will not be specified. To specify this field, the field must have the "Prohibit duplicate values" option turned on.
| record | Dictionary<String, [FieldValue](./record-field-model#fieldvalue)\>  | The data to update record.

**Sample code**

<details class="tab-container" open>
<Summary>init RecordUpdateItem class</Summary>

** Source code **

```swift
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
} catch {
    // error handle
}
```

</details>

### Methods

(none)

## RecordUpdateKey

### Constructor

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| field | String  | The field code of unique key in the kintone app.
| value | String  | The field value in the record.

**Sample code**

<details class="tab-container" open>
<Summary>init RecordUpdateKey class</Summary>

** Source code **

```swift
field: String = "{your_field_code}";
value: String = "update key value"
let updKey = RecordUpdateKey(field, value)
```

</details>

### Methods

(none)

## RecordUpdateStatusItem

### Constructor

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| action | String  | The Action name of the action you want.
| assignee | String  |  (Optional) The next Assignee. Specify the Assignee's log in name..
| id | Int  |   The record ID.
| revision | Int  |  (Optional) The revision number of the record before updating the status.If the specified revision is not the latest revision, the request will result in an error.

**Sample code**

<details class="tab-container" open>
<Summary>init RecordUpdateStatusItem class</Summary>

** Source code **

```swift
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
} catch {
    // error handle
}
```

</details>

### Methods

(none)