# View

> View settings of an App

## ViewModel

### Constants

#### BuiltinType

| Name| Type| Value| Description |
| --- | --- | --- | --- |
| ASSIGNEE | String | ASSIGNEE | The "Assigned to me" View.<br>(This list is automatically created if the Process Management settings have been enabled in the app.)

#### ViewType

| Name| Type| Value| Description |
| --- | --- | --- | --- |
| LIST | String | LIST | List View
| CALENDAR | String | CALENDAR | Custom View
| CUSTOM | String | CUSTOM | Custom View

### Methods

#### getBuiltinType()

> Get the BuiltinType of the built-in View.

**Parameter**

(none)

**Return**

[BuiltinType](./app-view/#builtintype)?

**Sample code**

<details class="tab-container" open>
<Summary>get the BuiltinType of the built-in View</Summary>

** Source code **

```java
let type = viewModel.getBuiltinType()
```

</details>

#### setName(name)

> Set the BuiltinType of the built-in View.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| name | [BuiltinType](./app-view/#builtintype)? | The BuiltinType of the built-in View.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the BuiltinType of the built-in View.</Summary>

** Source code **

```java
let viewModel = ViewModel()
viewModel.setBuiltinType(ViewModel.BuiltinType.ASSIGNEE)
```

</details>

#### getDate()

> Get the field code set for the Date Field.

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get the field code for the Date Field</Summary>

** Source code **

```java
let date = viewModel.getDate()
```

</details>

#### setDate(date)

> Set the field code set for the Date Field.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| date | String? |  The field code set for the Date Field.<br>Responded for Calendar Views.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the field code set for the Date Field</Summary>

** Source code **

```java
let viewModel = ViewModel()
viewModel.setDate("field_code")
```

</details>


#### getFields()

> Get the list of field codes for the fields displayed in the View.

**Parameter**

(none)

**Return**

Array<String>?

**Sample code**

<details class="tab-container" open>
<Summary>get the list of field codes for the fields displayed in the View</Summary>

** Source code **

```java
let fields = viewModel.getFields()
```

</details>

#### setFields(fields)

> Set the list of field codes for the fields displayed in the View.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| fields | Array<String>? | The list of field codes for the fields displayed in the View.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the field code set for the Date Field</Summary>

** Source code **

```java
let viewModel = ViewModel()
viewModel.setFields(["field_code1", "field_code2"])
```

</details>

#### getFilterCond()

> Get the filter condition as a query.

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get the filter condition as a query.</Summary>

** Source code **

```java
let query = viewModel.getFilterCond()
```

</details>

#### setFilterCond(filterCond)

> Set the filter condition as a query.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| filterCond | String? | The filter condition as a query.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the filter condition as a query</Summary>

** Source code **

```java
let viewModel = ViewModel()
viewModel.setFilterCond("query_text")
```

</details>

#### getHtml()

> Get the HTML code set for the custom View.

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get the HTML code set for the custom View</Summary>

** Source code **

```java
let html = viewModel.getHtml()
```

</details>

#### setHtml(html)

> Set the HTML code set for the custom View.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| html | String? | The HTML code set for the custom View

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the HTML code set for the custom View</Summary>

** Source code **

```java
let viewModel = ViewModel()
viewModel.setHtml("html")
```

</details>


#### getId()

> Get the View ID.

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get the View ID</Summary>

** Source code **

```java
let viewId = viewModel.getId()
```

</details>

#### setId(id)

> Set the View ID.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| id | Int? | The View ID

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the View ID</Summary>

** Source code **

```java
let viewModel = ViewModel()
let viewId: Int? = {view_id}
viewModel.setId(viewId)
```

</details>

#### getIndex()

> Get the display order (ascending) of the View.

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get the display order (ascending) of the View</Summary>

** Source code **

```java
let index = viewModel.getIndex()
```

</details>

#### setIndex(index)

> Set the display order (ascending) of the View.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| index | Int? | The display order (ascending) of the View

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the display order (ascending) of the View</Summary>

** Source code **

```java
let viewModel = ViewModel()
let index: Int? = {index_number}
viewModel.setIndex(index)
```

</details>

#### getName()

> Get the name of the View.

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get the name of the View</Summary>

** Source code **

```java
let viewName = viewModel.getName()
```

</details>

#### setName(name)

> Set the name of the View.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| name | String? | The name of the View

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the name of the View</Summary>

** Source code **

```java
let viewModel = ViewModel()
viewModel.setName("view_name")
```

</details>

#### getPager()

> Get the pagination settings that corresponded for Custom Views.

**Parameter**

(none)

**Return**

Bool?

**Sample code**

<details class="tab-container" open>
<Summary>get the pagination settings that corresponded for Custom Views</Summary>

** Source code **

```java
let viewPager = viewModel.getPager()
```

</details>

#### setPager(pager)

> Set the pagination settings that corresponded for Custom Views.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| pager | Bool? | The pagination settings that corresponded for Custom Views

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the pagination settings that corresponded for Custom Views</Summary>

** Source code **

```java
let viewModel = ViewModel()
viewModel.setPager(false)
```

#### getSort()

> Get the sort order as a query.

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get the sort order as a query</Summary>

** Source code **

```java
let sortOrder = viewModel.getSort()
```

</details>

#### setSort(sort)

> Set the sort order as a query.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| sort | String? | The sort order as a query

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the sort order as a query</Summary>

** Source code **

```java
let viewModel = ViewModel()
viewModel.setSort("field_code asc")
```
#### getTitle()

> Get the field code set for the Title Field that corresponded for Calendar Views.

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get the field code set for the Title Field that corresponded for Calendar Views</Summary>

** Source code **

```java
let viewTitleField = viewModel.getTitle()
```

</details>

#### setTitle(title)

> Set the field code set for the Title Field that corresponded for Calendar Views.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| title | String? | The field code set for the Title Field that corresponded for Calendar Views

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the field code set for the Title Field that corresponded for Calendar Views</Summary>

** Source code **

```java
let viewModel = ViewModel()
viewModel.setTitle("field_code")
```
#### getType()

> Get the type of View in type.

**Parameter**

(none)

**Return**

[type](./app-view/#viewtype)? 

**Sample code**

<details class="tab-container" open>
<Summary>get the type of View in type</Summary>

** Source code **

```java
let viewType = viewModel.getType()
```

</details>

#### setType(type)

> Set the type of View in type.

**Parameter**

| Name| Type| Description |
| --- | --- | --- |
| title | [type](./app-view/#viewtype)? | The type of View in type

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the type of View in type</Summary>

** Source code **

```java
let viewModel = ViewModel()
viewModel.setType(ViewModel.ViewType.CUSTOM)
```
