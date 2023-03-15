# READ the Drive files

List all the files and folders from the user's drive

**URL**: ```https://www.googleapis.com/drive/v3/files/```

**Method**: ```GET```

**Auth required**: YES

**Permissions required**: YES

**Request Body** : NO. This method does not need a request Body.

-----------

## Success response

A successfully response will return a status code and a json, even if there are no files/folders in Drive. 

**Code**: ```200 OK```

**Content examples**

*No files in Drive*
```json
{
    "kind": "drive#fileList",
    "incompleteSearch": false,
    "files": []
}
```
*With a file in Drive*
```json
{
    "kind": "drive#fileList",
    "incompleteSearch": false,
    "files": [
        {
            "kind": "drive#file",
            "mimeType": "application/json",
            "id": "1xMCycKx5Jyrp6zWlK5byMzKaVav3dtDc",
            "name": "justInfo.pdf"
        }
    ]
}
```
-----------

## Error Response

**Condition**: User did not authenticate it previously or does not use the generated auth token

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

-----------