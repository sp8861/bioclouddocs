<!-- ## Document: -->
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


