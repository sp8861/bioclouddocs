

***URI :*** `/palm/vis/register`

***Method*** : `POST`

***Request param*** : `templateId`

This endpoint is specifically used to register an image for visible palm detection. The client must upload an image containing a palm in a supported format such as JPEG and PNG.

***Request body :***
`The body must include the image to be uploaded in binary format, such as through multipart/form-data.`

***Note:***

Ensure the image file you are uploading contains a visible palm and follows the supported formats (JPEG and PNG) to avoid errors.

**Success Response**

***Condition*** : If the provided data is valid, the API key and signature are authenticated successfully, and the image is registered correctly.

**Id** : Id is the template ID, a unique identifier for the image that was registered successfully. It is used to reference this specific image in future operations.

```json
{
    "code": "ABSI0000",
    "message": "Success",
    "data": {
        "id": "c734d5bd36554045a03844d0f96922cb",
        "templateLength": 544,
        "object": {
            "class_id": 0,
            "x": 1884,
            "y": 747,
            "w": 1765,
            "h": 2358,
            "point": [
                1859.0398,
                1655.4126,
                1862.1228,...
            ],
            "pitch": -14.018374,
            "roll": -0.38649264,
            "yaw": 6.447996,
            "score": 0.84122145,
            "track_id": 0,
            "state": -1
        }
    }
}
```

***URI :*** `/palm/vis/identification`

***Method*** : `POST`

This endpoint is specifically used to identify an image for visible palm detection. The client must upload an image containing a palm in a supported format such as JPEG and PNG.

***Request body :***
`The body must include the image to be uploaded in binary format, such as through multipart/form-data.`

***Note:***

Ensure the image file you are uploading contains a visible palm and follows the supported formats (JPEG and PNG) to avoid errors.

**Success Response**

***Condition*** : If the provided data is valid, the API key and signature are authenticated successfully, and the image is registered correctly.

**Id** : Id is the template ID, a unique identifier for the image that was registered successfully. It is used to reference this specific image in future operations.

```json
{
    "code": "ABSI0000",
    "message": "Success",
    "data": {
        "id": "c734d5bd36554045a03844d0f96922cb",
        "templateLength": 544,
        "object": {
            "class_id": 0,
            "x": 1884,
            "y": 747,
            "w": 1765,
            "h": 2358,
            "point": [
                1859.0398,
                1655.4126,
                1862.1228,...
            ],
            "pitch": -14.018374,
            "roll": -0.38649264,
            "yaw": 6.447996,
            "score": 0.84122145,
            "track_id": 0,
            "state": -1
        }
    }
}
```

***URI :*** `/palm/vis/liveness`

***Method*** : `POST`

This endpoint is used to check if an uploaded image contains a live palm for visible palm detection. The client must upload an image that clearly shows a palm in a supported format, such as JPEG and PNG.

***Request body :***
`The body must include the image to be uploaded in binary format, such as through multipart/form-data.`

***Note:***

Ensure the image file you are uploading contains a visible palm and follows the supported formats (JPEG and PNG) to avoid errors.

**Success Response**

***Condition*** : If the provided data is valid, the API key and signature are authenticated successfully, and the image is registered correctly.

**Id** : Id is the template ID, a unique identifier for the image that was registered successfully. It is used to reference this specific image in future operations.

```json
{
    "code": "ABSI0000",
    "message": "Success",
    "data": {
        "id": "c734d5bd36554045a03844d0f96922cb",
        "templateLength": 544,
        "object": {
            "class_id": 0,
            "x": 1884,
            "y": 747,
            "w": 1765,
            "h": 2358,
            "point": [
                1859.0398,
                1655.4126,
                1862.1228,...
            ],
            "pitch": -14.018374,
            "roll": -0.38649264,
            "yaw": 6.447996,
            "score": 0.84122145,
            "track_id": 0,
            "state": -1
        }
    }
}
```

***URI :*** `/palm/ir/register`

***Method*** : `POST`

***Request param*** : `templateId`

This endpoint is used to register an image for infrared palm detection. The client must upload an image that clearly shows a palm in a supported format, such as JPEG and PNG.

***Request body :***
`The body must include the image to be uploaded in binary format, such as through multipart/form-data.`

***Note:***

Ensure the image file you are uploading contains a palm and follows the supported formats (JPEG and PNG) to avoid errors.

**Success Response**

***Condition*** : If the provided data is valid, the API key and signature are authenticated successfully, and the image is registered correctly.

**Id** : Id is the template ID, a unique identifier for the image that was registered successfully. It is used to reference this specific image in future operations.

```json
{
    "code": "ABSI0000",
    "message": "Success",
    "data": {
        "id": "c734d5bd36554045a03844d0f96922cb",
        "templateLength": 544,
        "object": {
            "class_id": 0,
            "x": 1884,
            "y": 747,
            "w": 1765,
            "h": 2358,
            "point": [
                1859.0398,
                1655.4126,
                1862.1228,...
            ],
            "pitch": -14.018374,
            "roll": -0.38649264,
            "yaw": 6.447996,
            "score": 0.84122145,
            "track_id": 0,
            "state": -1
        }
    }
}
```

***URI :*** `/palm/ir/identification`

***Method*** : `POST`

This endpoint is used to identify an image for infrared palm detection. The client must upload an image that clearly shows a palm in a supported format, such as JPEG and PNG.

***Request body :***
`The body must include the image to be uploaded in binary format, such as through multipart/form-data.`

***Note:***

Ensure the image file you are uploading contains a palm and follows the supported formats (JPEG and PNG) to avoid errors.

**Success Response**

***Condition*** : If the provided data is valid, the API key and signature are authenticated successfully, and the image is registered correctly.

**Id** : Id is the template ID, a unique identifier for the image that was registered successfully. It is used to reference this specific image in future operations.

```json
{
    "code": "ABSI0000",
    "message": "Success",
    "data": {
        "id": "c734d5bd36554045a03844d0f96922cb",
        "templateLength": 544,
        "object": {
            "class_id": 0,
            "x": 1884,
            "y": 747,
            "w": 1765,
            "h": 2358,
            "point": [
                1859.0398,
                1655.4126,
                1862.1228,...
            ],
            "pitch": -14.018374,
            "roll": -0.38649264,
            "yaw": 6.447996,
            "score": 0.84122145,
            "track_id": 0,
            "state": -1
        }
    }
}
```

***URI :*** `/palm/ir/liveness`

***Method*** : `POST`

This endpoint is used to identify an image for infrared palm detection. The client must upload an image that clearly shows a palm in a supported format, such as JPEG and PNG.

***Request body :***
`The body must include the image to be uploaded in binary format, such as through multipart/form-data.`

***Note:***

Ensure the image file you are uploading contains a palm and follows the supported formats (JPEG and PNG) to avoid errors.

**Success Response**

***Condition*** : If the provided data is valid, the API key and signature are authenticated successfully, and the image is registered correctly.

**Id** : Id is the template ID, a unique identifier for the image that was registered successfully. It is used to reference this specific image in future operations.

```json
{
    "code": "ABSI0000",
    "message": "Success",
    "data": {
        "id": "c734d5bd36554045a03844d0f96922cb",
        "templateLength": 544,
        "object": {
            "class_id": 0,
            "x": 1884,
            "y": 747,
            "w": 1765,
            "h": 2358,
            "point": [
                1859.0398,
                1655.4126,
                1862.1228,...
            ],
            "pitch": -14.018374,
            "roll": -0.38649264,
            "yaw": 6.447996,
            "score": 0.84122145,
            "track_id": 0,
            "state": -1
        }
    }
}
```

***URI :*** `/palm/vis/{id}`

***Method*** : `DELETE`

This endpoint allows the deletion of a registered VIS palm image by its unique identifier (id). It is primarily used for removing previously uploaded palm data from the system, which may have been used for liveness detection or other palm recognition purposes.

***Request Param :***
`Replace {id} with the template ID, which is the unique identifier of the palm data that needs to be deleted.`

***Note:***

Ensure that the {id} in the URI corresponds to a valid palm identifier that was previously registered.

**Success Response**

***Condition*** : If the provided palm ID is valid, and the API key and signature are authenticated successfully, the palm data will be deleted.

```json
{
    "message": "Success",
    "code": "ABSI0000"
}
```

***URI :*** `/palm/ir/{id}`

***Method*** : `DELETE`

This endpoint allows the deletion of a registered IR palm image by its unique identifier (id). It is primarily used for removing previously uploaded palm data from the system, which may have been used for liveness detection or other palm recognition purposes.

***Request Param :***
`Replace {id} with the template ID, which is the unique identifier of the palm data that needs to be deleted.`

***Note:***

Ensure that the {id} in the URI corresponds to a valid palm identifier that was previously registered.

**Success Response**

***Condition*** : If the provided palm ID is valid, and the API key and signature are authenticated successfully, the palm data will be deleted.

```json
{
    "message": "Success",
    "code": "ABSI0000"
}
```