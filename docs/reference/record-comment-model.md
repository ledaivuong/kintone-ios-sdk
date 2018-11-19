# Comment Model

General comment structure of the record on kintone restAPI

## Comment

### Constructor

**Parameter**

(none)

### Methods

#### getId()

> get the Comment ID.

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get the Comment ID.</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)

    let resultComments: [Comment]? = response!.getComments()
    let comment: Comment = resultComments![0]
    let commentID: Int? = comment.getId()
} catch {
    // error handle
}
```

</details>

#### getText()

> get the comment including the line feed codes.

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get the comment including the line feed codes.</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)

    let resultComments: [Comment]? = response!.getComments()
    let comment: Comment = resultComments![0]
    let commentText: String? = comment.getText()
} catch {
    // error handle
}
```

</details>

#### getCreatedAt()

> get the created date and time of the comment.

**Parameter**

(none)

**Return**

Date?

**Sample code**

<details class="tab-container" open>
<Summary>get the created date and time of the comment.</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)

    let resultComments: [Comment]? = response!.getComments()
    let comment: Comment = resultComments![0]
    let commentCreateAt: Date? = comment.getCreatedAt()
} catch {
    // error handle
}
```

</details>

#### getCreator()

> get an object including information of the comment creator.

**Parameter**

(none)

**Return**

[Member](./member/#member)?

**Sample code**

<details class="tab-container" open>
<Summary>get an object including information of the comment creator.</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)

    let resultComments: [Comment]? = response!.getComments()
    let comment: Comment = resultComments![0]
    let commentCreateAt: Member? = comment.getCreator()
} catch {
    // error handle
}
```

</details>

#### getMentions()

> get an array including information of mentioned users.

**Parameter**

(none)

**Return**

Array<[CommentMention](#commentmention)\>?

**Sample code**

<details class="tab-container" open>
<Summary>get an array including information of mentioned users.</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)

    let resultComments: [Comment]? = response!.getComments()
    let comment: Comment = resultComments![0]
    let commentMentions: [CommentMention]? = comment.getMentions()
} catch {
    // error handle
}
```

</details>

## CommentContent

### Constructor

**Parameter**

(none)

### Methods

#### setText(String text)

> set the comment including the line feed codes.

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| text | String  | The comment including the line feed codes.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the comment including the line feed codes.</Summary>

** Source code **

```swift
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
} catch {
    // error handle
}
```

</details>

#### setMentions(List<[CommentMention](#commentmention)\> mentions)

> get an array including information of mentioned users.

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| mentions | List<[CommentMention](#commentmention)\>  | An array including information of mentioned users.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>get an array including information of mentioned users.</Summary>

** Source code **

```swift
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
} catch {
    // error handle
}
```

</details>

## CommentMention

### Constructor

**Parameter**

(none)

### Methods

#### getCode()

> get the code of the mentioned user, group or organization.

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get the code of the mentioned user, group or organization.</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)

    let resultComments: [Comment]? = response!.getComments()
    let comment: Comment = resultComments![0]
    let commentMentions: [CommentMention]? = comment.getMentions()
    let mention: CommentMention = commentMentions![0]
    let mentionUserCode: String? = mention.getCode()
} catch {
    // error handle
}
```

</details>

#### setCode(String code)

> set the comment including the line feed codes.

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| code | String  | The code of the mentioned user, group or organization.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the comment including the line feed codes.</Summary>

** Source code **

```swift
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
} catch {
    // error handle
}
```

</details>

#### getType()

> get the type of the mentioned user, group or organization.

**Parameter**

(none)

**Return**

String?

**Sample code**

<details class="tab-container" open>
<Summary>get the type of the mentioned user, group or organization.</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)

    let resultComments: [Comment]? = response!.getComments()
    let comment: Comment = resultComments![0]
    let commentMentions: [CommentMention]? = comment.getMentions()
    let mention: CommentMention = commentMentions![0]
    let mentionUserType: String? = mention.getType()
} catch {
    // error handle
}
```

</details>

#### setType(String type)

> get an array including information of mentioned users.

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| type | String  | The type of the mentioned user, group or organization.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>get an array including information of mentioned users.</Summary>

** Source code **

```swift
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
} catch {
    // error handle
}
```

</details>

## GetCommentsResponse

### Constructor

**Parameter**

(none)

### Methods

#### getComments()

> get the comments List on a record.

**Parameter**

(none)

**Return**

Array<[Comment](#comment)\>?

**Sample code**

<details class="tab-container" open>
<Summary>get the comments List on a record.</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)

    let resultComments: [Comment]? = response!.getComments()
} catch {
    // error handle
}
```

</details>

#### getOlder()

> get information of older comments.

**Parameter**

(none)

**Return**

Boolean

**Sample code**

<details class="tab-container" open>
<Summary>get information of older comments.</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)

    let resultOlderFlg: Boolean = response!.getOlder()
} catch {
    // error handle
}
```

</details>

#### getNewer()

> get information of newer comments.

**Parameter**

(none)

**Return**

Boolean

**Sample code**

<details class="tab-container" open>
<Summary>get information of newer comments.</Summary>

** Source code **

```swift
// Init Record Module
let recordManagement = Record(connection)
 
// execute get comments API
let appID: Int = {your_app_id}
let recordID: Int = {your_record_id}
var response: GetCommentsResponse? = nil
do {
    response = try recordManagement.getComments(appID, recordID, nil, nil, nil)

    let resultNewerFlg: Boolean = response!.getNewer()
} catch {
    // error handle
}
```

</details>

## AddCommentResponse

### Constructor

**Parameter**

(none)

### Methods

#### getId()

> get the ID of comment which have just created.

**Parameter**

(none)

**Return**

Int?

**Sample code**

<details class="tab-container" open>
<Summary>get the ID of comment which have just created.</Summary>

** Source code **

```swift
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
                 
    let resultID: Int? = response!.getId()
} catch {
    // error handle
}
```

</details>