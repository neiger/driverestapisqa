# DELETE a file in Drive

DELETE a file from the user's drive

**URL**: ```https://www.googleapis.com/drive/v3/files/fileId```

**Method**: ```DELETE```

**Auth required**: YES

**Permissions required**: YES

## Success response

The user is able to update a file to its Drive

**Code**: ```204 No Content```

**Content examples**

*JSON response received*
```json
{}
```

## Error Response

**Condition**: The file that is going to be deleted does not exist

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