# Member

General information of the member(user/group/organization) on the kintone application


## Constructor

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| code | String | The user/group/organization code.
| name | String | The user/group/organization name.

**Sample code**

<details class="tab-container" open>
<Summary>Initial member class</Summary>

** Source code **

```java
let code: String = "usercode"
let name: String = "username"

let member = Member(code, name)
```

</details>

## Methods

### getCode()

> Get the code of the user/group/organization

**Parameter**

(none)

**Return**

String

**Sample code**

<details class="tab-container" open>
<Summary>Get the code of the user/group/organization</Summary>

** Source code **

```java
// Init Record Module
let recordManagement = Record(connection)
         
// execute get record API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetRecordResponse? = nil
do {
    response = try recordManagement.getRecord(appID, recordID)
             
    let resultData = response!.getRecord()!
    let member = resultData["fieldCode"]?.getValue() as! Member
    let usercode = member.getCode()
    let userName = member.getName()
} catch {
    // error handle
}
```

</details>

### setCode()

> Set the code of the user/group/organization

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| code | String | The user/group/organization code.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Set the code of the user/group/organization</Summary>

** Source code **

```java
let member = new Member
member.setCode("usercode");
member.setName("username");

Record recordManagement = new Record(connection);

Integer appID = 1;
HashMap<String, FieldValue> addRecord = new HashMap<String, FieldValue>();
FieldValue fv = new FieldValue();
fv.setType(FieldType.USER_SELECT);
fv.setValue(member);
addRecord.put("user", fv);

AddRecordResponse response = recordManagerment.addRecord(appID, addRecord);
```

</details>


### getName()

> Get the name of the user/group/organization

**Parameter**

(none)

**Return**

String

**Sample code**

<details class="tab-container" open>
<Summary>Get the name of the user/group/organization</Summary>

** Source code **

```java
// Init Record Module
let recordManagement = Record(connection)
         
// execute get record API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetRecordResponse? = nil
do {
    response = try recordManagement.getRecord(appID, recordID)
             
    let resultData = response!.getRecord()!
    let member = resultData["fieldCode"]?.getValue() as! Member
    let usercode = member.getCode()
    let userName = member.getName()
} catch {
    // error handle
}
```

</details>

### setName()

> Set the name of the user/group/organization

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| name | String | The user/group/organization name.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Set the name of the user/group/organization</Summary>

** Source code **

```java
let code: String = "usercode"
let name: String = "username"

let member = Member(code, name)
member.setCode("newUsercode")
member.setName("newUserName")
```

</details>
