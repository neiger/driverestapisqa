# CREATE a file in Drive

CREATE a new file in user's drive

**URL**: ```https://www.googleapis.com/drive/v3/files/```

**Method**: ```POST```

**Auth required**: YES. OAuth 2.0

**Permissions required**: YES

**Request Body** : YES. Optional parameters.

**Content examples**

*JSON request Body send*
```json
{
  "name": "myFile.pdf",
  "description":"This file is created via REST API"
}
```
-----------

## Success response

A successfully response will return a status code and a json.

**Code**: ```200 OK```

**Content examples**

*JSON response received*
```json
{
    "kind": "drive#file",
    "id": "1jo-WXufcUXieR-GVJXzBU1qV5shaXCJR",
    "name": "myFile.pdf",
    "mimeType": "application/pdf"
}
```
-----------

## Error Response


**Condition**: User did not authenticate it previously or does not use the generated auth token.

**Code**: ```401 Unauthorized```

**Content example**:

```json
{
    "error": {
        "code": 401,
        "message": "Request had invalid authentication credentials. Expected OAuth 2 access token, login cookie or other valid authentication credential. See https://developers.google.com/identity/sign-in/web/devconsole-project.",
        "errors": [
            {
                "message": "Invalid Credentials",
                "domain": "global",
                "reason": "authError",
                "location": "Authorization",
                "locationType": "header"
            }
        ],
        "status": "UNAUTHENTICATED"
    }
}
```

**Condition**: User includes body fields which are not directly writable.

**Code**: ```403 Forbidden```

**Content example**:
```json
{
    "error": {
        "code": 403,
        "message": "The resource body includes fields which are not directly writable.",
        "errors": [
            {
                "message": "The resource body includes fields which are not directly writable.",
                "domain": "global",
                "reason": "fieldNotWritable"
            }
        ]
    }
}
```

-----------
### Optional parameters that can be used in the Body Request

| Property name | Value | Description | Notes |
| ------------- | ----- | ----------- | ----- |
| appProperties | object | A collection of arbitrary key-value pairs which are private to the requesting app. Entries with null values are cleared in update and copy requests. These properties can only be retrieved using an authenticated request. An authenticated request uses an access token obtained with a OAuth 2 client ID. You cannot use an API key to retrieve private properties. | writable |
| contentHints.indexableText |	string |	Text to be indexed for the file to improve fullText queries. This is limited to 128 KB in length and may contain HTML elements. For more information, see Manage file metadata.| writable |
|contentHints.thumbnail.image |	bytes |	The thumbnail data encoded with URL-safe Base64 (RFC 4648 section 5). |	writable |
| contentHints.thumbnail.mimeType|	string | The MIME type of the thumbnail.	|writable|
|contentRestrictions[].readOnly	| boolean |	Whether the content of the file is read-only. If a file is read-only, a new revision of the file may not be added, comments may not be added or modified, and the title of the file may not be modified.|	writable|
|contentRestrictions[].reason|	string|	Reason for why the content of the file is restricted. This is only mutable on requests that also set readOnly=true.|	writable|
|copyRequiresWriterPermission|	boolean|	Whether the options to copy, print, or download this file, should be disabled for readers and commenters.	|writable|
|createdTime|	datetime|	The time at which the file was created (RFC 3339 date-time).|	writable|
|description|	string	|A short description of the file.	|writable|
|folderColorRgb|	string	|The color for a folder or shortcut to a folder as an RGB hex string. The supported colors are published in the folderColorPalette field of the About resource. If an unsupported color is specified, the closest color in the palette will be used instead.| writable|
|id	|string|	The ID of the file.	|writable|
|mimeType|	string	|The MIME type of the file. Google Drive will attempt to automatically detect an appropriate value from uploaded content if no value is provided. The value cannot be changed unless a new revision is uploaded. If a file is created with a Google Doc MIME type, the uploaded content will be imported if possible. The supported import formats are published in the About resource. |writable|
|modifiedTime	|datetime	|The last time the file was modified by anyone (RFC 3339 date-time). Note that setting modifiedTime will also update modifiedByMeTime for the user.| writable|
|name|	string|	The name of the file. This is not necessarily unique within a folder. Note that for immutable items such as the top level folders of shared drives, My Drive root folder, and Application Data folder the name is constant.	|writable|
| originalFilename|	string|	The original filename of the uploaded content if available, or else the original value of the name field. This is only available for files with binary content in Google Drive.	| writable |
| parents[]	| list	| The IDs of the parent folders which contain the file. If not specified as part of a create request, the file will be placed directly in the user's My Drive folder. If not specified as part of a copy request, the file will inherit any discoverable parents of the source file. Update requests must use the addParents and removeParents parameters to modify the parents list. | writable |
|properties|	object|	A collection of arbitrary key-value pairs which are visible to all apps. Entries with null values are cleared in update and copy requests. | writable |
|shortcutDetails.targetId	|string	|The ID of the file that this shortcut points to.	|writable|
|starred	|boolean	|Whether the user has starred the file.	|writable|
|viewedByMeTime	|datetime|	The last time the file was viewed by the user (RFC 3339 date-time).	|writable|
|writersCanShare|	boolean|Whether users with only writer permission can modify the file's permissions. Not populated for items in shared drives.|	writable|

-----------

**_For further references go to_**
https://developers.google.com/drive/api/v3/reference/files/create