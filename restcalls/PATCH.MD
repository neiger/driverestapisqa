# UPDATE a file in Drive

UPDATE a file from the user's drive

**URL**: ```https://www.googleapis.com/drive/v3/files/fileId```

**Method**: ```PATCH```

**Auth required**: YES

**Permissions required**: YES

## Success response

The user is able to update a file to its Drive

**Code**: ```200 OK```

**Content examples**

*JSON request send*
```json
{
  "name": "myFile.pdf",
  "description":""
}
```

*JSON response received*
```json
{
    "kind": "drive#file",
    "id": "1jo-WXufcUXieR-GVJXzBU1qV5shaXCJR",
    "name": "myFile.pdf",
    "mimeType": "application/pdf"
}
```

## Error Response

**Condition**: User did not authenticate it previously or does not use the generated auth token

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