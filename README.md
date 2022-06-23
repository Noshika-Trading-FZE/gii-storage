# Media Server

## Upload media file

### New file

To upload a media file and create the media object at the same time, use your access token `JWT` to request:

```
POST pix-media-server:5001/upload/0/${JWT}
```

The media file is to be passed to the request with the key `uploaded_file` (body/form-data). The name of the media object is taken from the file name and the mimetype is set as the content type of the uploaded file.

If nothing is specified, media objects are created using the default media object schema provisioned in the platform.
But you can pass json parameters to the request to use a specific schema by either id or tags (with id taking precedence if the two are provided):

```json
{
    "schemaid": ${uuid},
    "schematags": [${tag1}, ${tag2}, ...]
}
```

If the upload is successful the POST request returns the uuid of the media object that was created.

### Existing file

To upload a new media file to an existing media object with id `UUID`, use your access token `JWT` to request:

```
POST pix-media-server:5001/upload/${UUID}/${JWT}
```

The media file is to be passed to the request with the key `uploaded_file` (body/form-data). The name of the media object is taken from the file name and the mimetype is set as the content type of the uploaded file.

## Download media file

To download a media file with id `UUID` you need to provide your access token `JWT` and request: 

```
GET pix-media-server:5001/download/${UUID}/${JWT}
```

