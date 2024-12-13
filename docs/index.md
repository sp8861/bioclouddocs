<!-- # SDK APIS DOCUMENTATION -->

The SDK APIS allows authenticated users to perform POST,DELETE requests to specific endpoints, such as for registering a visible face and palm image. Below is a detailed explanation of how to interact with this API:

**URL** : `https://api.minervaiotdev.com/biocloud/v1`

This is the base URL for all SDK API requests, and you will need to append specific endpoints to this base URL depending on the API action you are performing.

**Auth required** : `YES`

**Headers:**
The following headers are required for every RESTful API operation:

```
X-API-KEY
```

This is the API key used for authentication. It should be sent in the X-API-KEY header of the request.

**How API Signatures Work:**

***Generate a Signature:***

The signature is a security measure that verifies the authenticity and integrity of the request.

The client generates a signature using a combination of the  nonce, timestamp and a secret key. The secret key is usually only known to the client and server.

***secretKey***
A secret key is a unique, confidential piece of information used to authenticate a user or system securely. It's often used in encryption processes or API authentication to verify the identity of the requester and protect data exchanges. The secret key must be kept private and secure, as anyone with access to it could potentially misuse it to access sensitive data or perform unauthorized actions.
When creating user credentials, the secret key is sent to the user's email.

***nonce:***
In cryptography and web security, a nonce (short for "number used once") is a random or pseudo-random value that is used only once in a specific context, usually to prevent replay attacks or ensure the uniqueness of certain requests.

***timestamp (UNIX) :***
Timestamps are crucial in generating signatures for secure communication because they ensure the request is time-bound and can't be reused (preventing replay attacks). A server can check if the timestamp is within an acceptable time window (e.g., within 5 minutes) to validate the request.

***HMAC-SHA256***
To generate a signature using HMAC-SHA256, you would combine the nonce, timestamp, and secret key, and then hash them together using the HMAC-SHA256 algorithm.

***Steps:***

1. Open Postman and select your request.
2. Navigate to the Pre-request Script tab.
3. Add the following JavaScript code to the Pre-request Script:

```
const nonce = Math.random().toString(36).substring(2);

const timestamp = Math.floor(Date.now() / 1000);

const secretKey = "d6101cc49ed2c2984e060e2f5985b50aa0c9a79cb582d441c1c29e30d9cdd15e";

const elements = [nonce, timestamp, secretKey];
elements.sort();
const rawSign = elements.join('');
const signature = CryptoJS.HmacSHA256(rawSign,secretKey).toString(CryptoJS.enc.Hex);

pm.environment.set("nonce", nonce);
pm.environment.set("timestamp", timestamp);
pm.environment.set("signature", signature);
```

**note:**

Replace "your_secret_key" with your actual secret key when using this script.

***How to Use:***
You can now use the generated nonce, timestamp, and signature values in your request params:

nonce: {{nonce}}

timestamp: {{timestamp}}

signature: {{signature}}

***Send Signature with Request:***

This signature is sent along with the API request, as a request param (e.g., signature).

***Server Verification:***

The server receives the request, extracts the signature, and uses its own copy of the secret key to recalculate the signature based on the received data.
If the recalculated signature matches the signature sent with the request, the server processes the request, as this confirms the request's authenticity and integrity.
If the signatures don’t match, the server rejects the request.

**Face API requests**

***URI :*** `/face/vis/register`

***Method*** : `POST`

***Request param*** : `templateId`

This endpoint is specifically used to register an image with a face for visible face detection. The client needs to upload an image containing a face in a supported format such as JPEG and PNG.

***Request body :***
`The body must include the image to be uploaded in binary format, such as through multipart/form-data.`

***Note:***

Ensure the image file you are uploading contains a visible face and follows the supported formats (JPEG and PNG) to avoid errors.

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

***URI :*** `/face/vis/identification`

***Method*** : `POST`

This endpoint is specifically used to identify an image with a face for visible face detection. The client needs to upload an image containing a face in a supported format such as JPEG and PNG.

***Request body :***
`The body must include the image to be uploaded in binary format, such as through multipart/form-data.`

***Note:***

Ensure the image file you are uploading contains a visible face and follows the supported formats (JPEG and PNG) to avoid errors.

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

***URI :*** `/face/vis/liveness`

***Method*** : `POST`

This endpoint is used to identify whether an uploaded image contains a live face for visible face detection. This is useful in scenarios where you want to verify that the face in the image belongs to a live person rather than a static image.

***Request body :***
`The body must include the image to be uploaded in binary format, such as through multipart/form-data.`

***Note:***

Ensure the image file you are uploading contains a visible face and follows the supported formats (JPEG and PNG) to avoid errors.

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

***URI :*** `/face/ir/liveness`

***Method*** : `POST`

This endpoint is used to verify if an uploaded image contains a live face using infrared (IR) face detection. It's especially helpful for detecting liveness of the image.

***Request body :***
`The body must include the image to be uploaded in binary format, such as through multipart/form-data.`

***Note:***

Ensure the image file you are uploading contains a face and follows the supported formats (JPEG and PNG) to avoid errors.

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

***URI :*** `/face/{id}`

***Method*** : `DELETE`

This endpoint allows the deletion of a registered face by its unique identifier (id). It is primarily used for removing previously uploaded face data from the system, which may have been used for liveness detection or other facial recognition purposes.

***Request Param :***
`Replace {id} with the template ID, which is the unique identifier of the face data that needs to be deleted.`

***Note:***

Ensure that the {id} in the URI corresponds to a valid face identifier that was previously registered.

**Success Response**

***Condition*** : If the provided face ID is valid, the API key and signature are authenticated successfully, and the face data is deleted.

```json
{
    "message": "Success",
    "code": "ABSI0000"
}
```

**Palm API requests**

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
