# UPDATE a User's folder

UPDATE a user's folder in drive

**URL**: ```https://www.googleapis.com/drive/v3/files/fileId```

**URL Parameter**: ```fileId``` which can be obtained from GET API Response.

**Method**: ```PATCH```

**Auth required**: YES. OAuth 2.0

**Permissions required**: YES

**Request Body** : YES. Optional parameters.

**Content examples**

*JSON request Body send*
```json
{
    "name": "thisFolderHasBeenModifiedViaRestCall",
    "description":"Adding just a simple description"
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
    "id": "1MGj2lbxYCmKydUzAI8SKS3er4sYeaFXF",
    "name": "thisFolderHasBeenModifiedViaRestCall",
    "mimeType": "application/vnd.google-apps.folder"
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

-----------

## Parameters
|Parameter Name|Value|Description|
|--------------|-----|-----------|
|fileId|string|The ID of the file.|
|uploadType|string|The type of upload request to the /upload URI. If you are uploading data (using an /upload URI), this field is required. If you are creating a metadata-only file, this field is not required. Additionally, this field is not shown in the "Try this API" widget because the widget doesn't support data uploads. Acceptable values are: <li>media - Simple upload. Upload the media only, without any metadata.</li> <li>multipart - Multipart upload. Upload both the media and its metadata, in a single request.</li><li>resumable - Resumable upload. Upload the file in a resumable fashion, using a series of at least two requests where the first request includes the metadata.</li>|

*Optional query parameters*
|Parameter Name|Value|Description|
|--------------|-----|-----------|
|addParents|	string	|A comma-separated list of parent IDs to add.|
|enforceSingleParent	|boolean	| Warning: This item is deprecated. Deprecated. Adding files to multiple folders is no longer supported. Use shortcuts instead. (Default: false)|
|includeLabels|	string|	A comma-separated list of IDs of labels to include in the labelInfo part of the response.|
|includePermissionsForView	|string|	Specifies which additional view's permissions to include in the response. Only 'published' is supported.|
|keepRevisionForever	|boolean|	Whether to set the 'keepForever' field in the new head revision. This is only applicable to files with binary content in Google Drive. Only 200 revisions for the file can be kept forever. If the limit is reached, try deleting pinned revisions. (Default: false)|
|ocrLanguage|	string|	A language hint for OCR processing during image import (ISO 639-1 code).|
|removeParents	|string	|A comma-separated list of parent IDs to remove.|
|supportsAllDrives	|boolean|	Whether the requesting application supports both My Drives and shared drives. (Default: false)|
|supportsTeamDrives	|boolean	| Warning: This item is deprecated. Deprecated use supportsAllDrives instead. (Default: false)|
|useContentAsIndexableText	|boolean|	Whether to use the uploaded content as indexable text. (Default: false)|

-----------
**_For further references go to_**
https://developers.google.com/drive/api/v3/reference/files/update