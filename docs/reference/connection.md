# Connection

[Connection](#) module will used as a connector to connect to kintone Rest API

## Constructor

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| domain | String | yes | The Domain name or FQDN
| auth | [Auth](./authentication) | yes | The authentication object
| guestSpaceID | Int | (optional) | The guest space id. Use this parameter to connect to kintone guest space.

**Sample code**

<details class="tab-container" open>
<Summary>Init Connection module</Summary>

** Source code **

```Swift
// Define Authentication object
let username: String = {your_user_name}
let password: String = {your_user_password}
let kintoneAuth = Auth()
kintoneAuth.setPasswordAuth(username, password)

let myDomainName: String = {your_domain}
let connection = Connection(myDomainName, kintoneAuth)


// Define connection that included guest space
let guestSpaceID: Int = 1
let connection = Connection(myDomainName, kintoneAuth, guestSpaceID)

```

</details>

## Methods

### setHeader(key, value)

> Set new header of the [Connection](./connection)

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| key | String | yes | The header's `key` name
| value | String | yes | The header's value of `key`

**Return**

[Connection](./connection)

**Sample code**

<details class="tab-container" open>
<Summary>Set header of the Connection</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let key: String = "X-HTTP-Method-Override"
let value: String = "GET"

// Init authenticationAuth
let kintoneAuth = Auth()
kintoneAuth.setPasswordAuth(username, password)

let myDomainName: String = {your_domain}
let connection = Connection(myDomainName, kintoneAuth)
connection.setHeader(key, value);
```

</details>

### setProxy(proxyHost, proxyPort)

> Set the proxy of the request

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| proxyHost | String | yes | The proxy host name
| proxyPort | Int | yes | The proxy port number

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Set the proxy of the request</Summary>

** Source code **

```swift
let username: String = {your_user_name}
let password: String = {your_user_password}
let proxyHost: String = "xxxx"
let proxyPort: Int = 1234
  
// Init authenticationAuth
let kintoneAuth = Auth()
kintoneAuth.setPasswordAuth(username, password)

let myDomainName: String = {your_domain}
let connection = Connection(myDomainName, kintoneAuth)
connection.setProxy(proxyHost, proxyPort)
```

</details>
