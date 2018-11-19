# Authentication

Authentication module will be used by [Connection](./connection).
This module allow we authenticate with kintone app by password authenticator or API token authenticator. This module is also support basic authenticator.

!!! warning

    - If both the Token and Password Authentication are specified, the Token Authentication will be ignored and the Password authentication will be used.

## Constructor

**Parameter**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Init authentication module</Summary>

** Source code **

```Swift
let kintoneAuth = Auth()
```

</details>

## Methods

### setPasswordAuth(username, password)

> Set password authentication for Authentication module.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| username | String | yes | The username that is able to authenticate on kintone app
| password | String | yes | The password that is able to authenticate on kintone app

**Return**

[Auth](./authentication)

**Sample code**

<details class="tab-container" open>
<Summary>Set password authentication</Summary>

** Source code **

```Swift
let username: String = {your_user_name}
let password: String = {your_user_password}
kintoneAuth.setPasswordAuth(username, password)
```

</details>


### setApiToken(apiTokenString)

> Set Api Token for Authentication module.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| apiToken | String | yes | The apiToken that is able to authenticate on kintone app

**Return**

[Auth](./authentication)


<details class="tab-container" open>
<Summary>Set APIToken authentication</Summary>

** Source code **

```Swift
let apiToken: String = "123456789abcdefghijklmnopqrstuvwxyz"
kintoneAuth.setApiToken(apiToken)
```

</details>


### setBasicAuth(username, password)

> Set Basic authentication for Authentication module.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| username | String | yes | The username that is able to authenticate on kintone app
| password | String | yes | The password that is able to authenticate on kintone app

**Return**

[Auth](./authentication)

**Sample code**

<details class="tab-container" open>
<Summary>Set basic authentication</Summary>

** Source code **

```Swift
let username: String = {your_user_name}
let password: String = {your_user_password}
kintoneAuth.setBasicAuth(username, password)
```

</details>


### createHeaderCredentials()

> Provide the list of HTTP Headers which use to authentication in.

**Parameter**

(none)

**Return**

[HTTPHeader?]

**Sample code**

<details class="tab-container" open>
<Summary>Provide the list of HTTP Headers which use to authentication in</Summary>

** Source code **

```Swift
let headers: [HTTPHeader?] = kintoneAuth.createHeaderCredentials()
var count = 0
for header in headers {
    print("Key[" + count.description + "]: " + (header?.getKey())!)
    print("Value[" + count.description + "]: " + (header?.getValue())!)
    count += 1
}
```

</details>