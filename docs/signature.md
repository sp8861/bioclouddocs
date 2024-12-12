
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


