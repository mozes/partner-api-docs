# Authentication

## Basics

Partner API requests can be made via HTTP calls to `https://partnerapi.mozes.com/{version}/{endpoint}`. The current Partner API version is `v1`.

Example: `https://partnerapi.mozes.com/v1/user/lookup`

## Headers

API requests must include two headers, `X-API-Key` and `X-API-Shared-Secret`, which can be requested by contacting support@mozes.com or speaking to your client services representative. Because the API key and shared secret are sent in plain text, requests must be made over SSL.

## Request Generation

Requests are sent using the HTTP `POST` method. The `Content-Type` header of `POST` requests must be `application/json` as the request data itself is sent as JSON formatted string. An example of a HTTP request is as follows:

```
User-Agent: curl/7.12.1 (i686-redhat-linux-gnu) libcurl/7.12.1 OpenSSL/0.9.7a zlib/1.2.1.2 libidn/0.5.6
Host: partnerapi.mozes.com
Pragma: no-cache
Accept: */*
Content-Type: application/json
X-API-Key: xxxxxx
X-API-Shared-Secret: XXXXXXXXXXX
Content-Length: 61

{"mozes_id":"#######","project_id":######,"dob":"########"}
```

*Note: Read-only requests may be made via `GET` requests with request parameters sent via the query string.*

## Response Format

JSON responses from the API follow a standard structure:
```json
{
    "status": {
        "code": 0,
        "name": "SHORT_NAME",
        "description": "Human readable description."
    },
    "response": {
        "arbitrary": "data",
        "integer": 184732,
        "string": "value"
    }
}
```
The "status" block contains a numeric return code, an alphanumeric code name, and longer description. The "response" block contains arbitrary data returned by the Web service called.