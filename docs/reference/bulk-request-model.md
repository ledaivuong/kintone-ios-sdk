# Bulk Request Model

Store a list of requests and responses for a bulk request.

## BulkRequestModel

### Constructor

**Parameter**

(none)

### Methods

#### addRequest(bulkRequestItem)

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| bulkRequestItem | [BulkRequestItem](#bulkrequestitem) | The BulkRequest Item.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>add Request</Summary>

** Source code **

```swift
BulkRequestModel bulkRequestModel = new BulkRequestModel();

Integer appID = 1;

HashMap<String, FieldValue> record = new HashMap<String, FieldValue>();
FieldValue fv = new FieldValue();
fv.setType("SINGLE_LINE_TEXT");
fv.setValue("test_value");
record.put("sample_FieldCode", fv);

AddRecordRequest addRecordRequest = new AddRecordRequest(appID, record);
BulkRequestItem bulkRequestItem = new BulkRequestItem("POST", "/k/v1/record.json", addRecordRequest);

bulkRequestModel.addRequest(bulkRequestItem);
```

</details>

##BulkRequestItem

### Constructor

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| method | String | The API method name.
| api | String | The path of the API.
| payload | Any | The parameters to be passed onto the API.Contents and formats will change depending on the API.

**Sample code**

<details class="tab-container" open>
<Summary>Init Bulk Request Item</Summary>

** Source code **

```swift

Integer appID = 1;

HashMap<String, FieldValue> record = new HashMap<String, FieldValue>();
FieldValue fv = new FieldValue();
fv.setType("SINGLE_LINE_TEXT");
fv.setValue("test_value");
record.put("sample_FieldCode", fv);

AddRecordRequest addRecordRequest = new AddRecordRequest(appID, record);
BulkRequestItem bulkRequestItem = new BulkRequestItem("POST", "/k/v1/record.json", addRecordRequest);
```

</details>

##BulkRequestResponse

### Constructor

**Parameter**

(none)

### Methods

#### getResults()

**Parameter**

(none)

**Return**

Array<Any\>?

**Sample code**

<details class="tab-container" open>
<Summary>get Results</Summary>

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
    let results = response.getResults()
} catch  {
    // Handle error
}
```

</details>

