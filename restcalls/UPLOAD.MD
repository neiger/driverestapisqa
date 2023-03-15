# UPLOAD a file in Drive

UPLOAD a file from the user's drive

**URL**: ```https://www.googleapis.com/upload/drive/v3/files/```

**Method**: ```POST```

**Auth required**: YES

**Permissions required**: YES

## Success response

The user is able to upload a file to its Drive

**Code**: ```200 OK```

**Content examples**

*JSON request send*
```json
{}
```

*JSON response received*
```json
{
    "kind": "drive#file",
    "id": "1DsmCD0Cv-FJ9MxAUn9QwWyqyimotjgLB",
    "name": "Untitled",
    "mimeType": "image/png"
}
```

## Error Response

**Condition**: Upload was not successful due a bad request

**Code**: ```400 Bad Request```

**Content example**:

```json
{
    "error": {
        "code": 400,
        "message": "Not an upload request. Re-send request to: https://www.googleapis.com/drive/v3/files?access_token=ya29.a0AVvZVspkCapAHZVM5KTkt2Ry2sMFDS107L_vmSTbSoz_W4gQxPUpPvhXR7nRYnR0JuzjHXDn7FjqrV3vtesj79eTCt0VJib0-IwcK9ZWbQiJOI1gPXO7M1imFTCkrDkt9l7iriTinrTY8ykuBWJlhi-op3zQTAaCgYKAcMSARMSFQGbdwaI3enHpwJtTP79F_mgNMh4SQ0165",
        "errors": [
            {
                "message": "Not an upload request. Re-send request to: https://www.googleapis.com/drive/v3/files?access_token=ya29.a0AVvZVspkCapAHZVM5KTkt2Ry2sMFDS107L_vmSTbSoz_W4gQxPUpPvhXR7nRYnR0JuzjHXDn7FjqrV3vtesj79eTCt0VJib0-IwcK9ZWbQiJOI1gPXO7M1imFTCkrDkt9l7iriTinrTY8ykuBWJlhi-op3zQTAaCgYKAcMSARMSFQGbdwaI3enHpwJtTP79F_mgNMh4SQ0165",
                "domain": "global",
                "reason": "notUpload"
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