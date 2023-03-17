# DELETE User's Folder

Delete a user's folder in drive

**URL**: ```https://www.googleapis.com/drive/v3/files/fileId```

**URL Parameter**: ```fileId``` which can be obtained from GET API Response.

**Method**: ```DELETE```

**Auth required**: YES. OAuth 2.0

**Permissions required**: YES

**Request Body** : NO. This method does not need a request Body.

-----------

## Success response

A successfully response will return a status code. 

**Code**: ```204 No Content```

**Content examples**

*JSON response received*
```json
{}
```

-----------

## Error Response

**Condition**: The file that is going to be deleted does not exist.

**Code**: ```404 Not Found```

**Content example**:

```json
{
    "error": {
        "code": 404,
        "message": "File not found: 1KZMsO7xpNobfW6MYfu8_iVwVKCXL8ycD.",
        "errors": [
            {
                "message": "File not found: 1KZMsO7xpNobfW6MYfu8_iVwVKCXL8ycD.",
                "domain": "global",
                "reason": "notFound",
                "location": "fileId",
                "locationType": "parameter"
            }
        ]
    }
}
```

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

-----------

## Parameters
|Parameter Name|Value|Description|
|--------------|-----|-----------|
|fileId|string|The ID of the file.|

*Optional query parameters*
|Parameter Name|Value|Description|
|--------------|-----|-----------|
|enforceSingleParent|	boolean	| Warning: This item is deprecated. Deprecated. If an item is not in a shared drive and its last parent is deleted but the item itself is not, the item will be placed under its owner's root. (Default: false)|
|supportsAllDrives|	boolean|	Whether the requesting application supports both My Drives and shared drives. (Default: false)|
|supportsTeamDrives	|boolean| Warning: This item is deprecated. Deprecated use supportsAllDrives instead. (Default: false)|

-----------

**_For further references go to_**
https://developers.google.com/drive/api/v3/reference/files/delete