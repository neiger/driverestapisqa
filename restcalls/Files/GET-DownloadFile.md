# DOWNLOAD User's files

Download a User's file.

**URL**: ```https://www.googleapis.com/drive/v3/files/fileId?alt=media```

**URL Parameter**: 
```fileId``` To get the specific file.
```alt=media``` It tells the server that a download of content is being requested as an alternative response format.

**Method**: ```GET```

**Auth required**: YES. OAuth 2.0

**Permissions required**: YES

**Request Body** : NO. This method does not need a request Body.

-----------

## Success response

A successfully response will return a status code and a json with the files information. 

**Code**: ```200 OK```

**Content examples**

*With a file in Drive*
```json
{
  "kind": "drive#file",
  "id": "1d9RlJG3-M8P-QlgHYxlJ0-HGF4NYQXDd",
  "name": "useCases.jpg",
  "mimeType": "image/jpeg"
}

```
-----------

## Error Response

**Condition**: User did not authenticate it previously or does not use the generated auth token.

**Code**: ```401 Unauthenticated```

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
**Code**: ```403 Forbidden```

**Content example**:
```json
{
    "error": {
        "code": 403,
        "message": "The request is missing a valid API key.",
        "errors": [
            {
                "message": "The request is missing a valid API key.",
                "domain": "global",
                "reason": "forbidden"
            }
        ],
        "status": "PERMISSION_DENIED"
    }
}
```

### Optional Parameters that can be used

*Optional query parameters*
|Parameter Name|Value|Description|
|--------------|-----|-----------|
|acknowledgeAbuse|	boolean|	Whether the user is acknowledging the risk of downloading known malware or other abusive files. This is only applicable when alt=media. (Default: false)|
|fields|	string	|The paths of the fields you want included in the response. If not specified, the response includes a default set of fields specific to this method. For development you can use the special value * to return all fields, but you'll achieve greater performance by only selecting the fields you need. For more information, see Return specific fields for a file.|
|includeLabels|	string|	A comma-separated list of IDs of labels to include in the labelInfo part of the response.|
|includePermissionsForView|	string|	Specifies which additional view's permissions to include in the response. Only 'published' is supported.|
|supportsAllDrives|	boolean|	Whether the requesting application supports both My Drives and shared drives. (Default: false)|
|supportsTeamDrives	|boolean |	Warning: This item is deprecated. Deprecated use supportsAllDrives instead. (Default: false)|


-----------

**_For further references go to_**
https://developers.google.com/drive/api/guides/manage-downloads#node.js