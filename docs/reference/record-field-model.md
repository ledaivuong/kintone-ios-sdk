# Field Model

## FieldValue

General Field's value of the kintone app

### Constructor

**Parameter**

(none)

### Methods

#### getType()

> get the type of field.

**Parameter**

(none)

**Return**

FieldType?

**Sample code**

<details class="tab-container" open>
<Summary>get the type of field.</Summary>

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
             
    let resultData = response!.getRecord()!
    print(resultData["$id"]?.getValue())
             
    for (code, value) in resultData {
        let ft: FieldType? = value.getType()
    }
} catch {
    // error handle
}
```

</details>

#### setType(type)

> set the type of field.

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| type | FieldType  | The type of field - kintone-sdk FieldType constants.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the type of field.</Summary>

** Source code **

```swift
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
} catch {
    // error handle
}
```

</details>

#### getValue()

> get the value of field in the record.

**Parameter**

(none)

**Return**

Any?

**Sample code**

<details class="tab-container" open>
<Summary>get the value of field in the record.</Summary>

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
             
    let resultData = response!.getRecord()!
    print(resultData["$id"]?.getValue())
             
    for (code, value) in resultData {
        let fv: Any? = value.getValue()
    }
} catch {
    // error handle
}
```

</details>

#### setValue(value)

> set the value of field in the record.

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| value | Any?  | The value of field in the record, read more at [Field Type here](https://developer.kintone.io/hc/en-us/articles/212494818/#responses).


**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the value of field in the record.</Summary>

** Source code **

```swift
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
} catch {
    // error handle
}
```

</details>

##SubTableValueItem

### Constructor

**Parameter**

(none)

### Methods

#### getID()

> get the ID of item in table.

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get the ID of item in table.</Summary>

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
             
    let resultData = response!.getRecord()!
    let fv = resultData["SubTable field"]
    let subTable: [SubTableValueItem] = fv.getValue() as! [SubTableValueItem]
    let subTableItem: SubTableValueItem = subTable[0]
    let itemID: Int = subTableItem.getID()
} catch {
    // error handle
}
```

</details>


#### setID(id)

> set the ID of table.

**Parameter**

| Name| type | Description |
| --- | ---  | --- |
| id | Int | The ID of table .

**Return**

(none)


**Sample code**

<details class="tab-container" open>
<Summary>set the ID of item in table.</Summary>

** Source code **

```swift
let subtableValue = SubTableValueItem()
let item = Dictionary<String, FieldValue>()
let itemID = 1
subtableValue.setID(itemID)
subtableValue.setValue(item)
```

</details>

#### getValue()

> get the value of field in the record.

**Parameter**

(none)

**Return**

Dictionary<String, [FieldValue](#fieldvalue)\>?

**Sample code**

<details class="tab-container" open>
<Summary>get the ID of item in table.</Summary>

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
             
    let resultData = response!.getRecord()!
    let fv = resultData["SubTable field"]
    let subTable: [SubTableValueItem] = fv.getValue() as! [SubTableValueItem]
    let item: Dictionary<String, FieldValue>? = subTable[0].getValue()
} catch {
    // error handle
}
```

</details>

#### setValue(value) 

> set the value of field in the record.

**Parameter**

| Name| type | Description |
| --- | ---  | --- |
| value | Dictionary<String, [FieldValue](#fieldvalue)\>  | The row data of table.


**Return**

(none)


**Sample code**

<details class="tab-container" open>
<Summary>get the ID of item in table.</Summary>

** Source code **

```swift
let subtableValue = SubTableValueItem()
let item = Dictionary<String, FieldValue>()
let itemID = 1
subtableValue.setID(itemID)
subtableValue.setValue(item)
```

</details>


