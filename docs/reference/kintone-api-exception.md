# kintoneAPIException

Handle error responses from kintone Rest API

## Methods

### getHttpErrorCode()

**Parameter**

(none)

**Return**

int?

**Sample code**

<details class="tab-container" open>
<Summary>Get http error code</Summary>

** Source code **

```swift
let recordManagement: Record = Record(connection)
do {
    let response: GetRecordsResponse = (try recordManagement.getRecords(999999, nil nil))!
} catch let error as kintoneAPIException {
	let httpCode = error.getHttpErrorCode
}
```

</details>

### getErrorResponse()

**Parameter**

(none)

**Return**

[ErrorResponse](https://developer.kintone.io/hc/en-us/articles/212495188#responses)?

**Sample code**

<details class="tab-container" open>
<Summary>Get apps with error response</Summary>

** Source code **

```swift
let recordManagement: Record = Record(connection)
do {
    let response: GetRecordsResponse = (try recordManagement.getRecords(999999, nil nil))!
} catch let error as kintoneAPIException {
    let errorID = error.getErrorResponse().getId()
    let errorMsg = error.getErrorResponse().getMessage()
    let errorCode = error.getErrorResponse().getCode()
}

```

</details>

### getErrorResponses()

**Parameter**

(none)

**Return**

Array&lt;[ErrorResponse](https://developer.kintone.io/hc/en-us/articles/212495188#responses)&gt;?

**Sample code**

<details class="tab-container" open>
<Summary>Get apps with error responses</Summary>

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
} catch let error as kintoneAPIException {
	let errorResps = error.getErrorResponses()
	let errorMsg = errorResps[0].getMessage()
}
```

</details>