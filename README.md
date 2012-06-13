# Mozes Partner API Documentation

Basics
--------

Partner API requests can be made via HTTP calls to `https://partnerapi.mozes.com/{version}/{endpoint}`. The current Partner API version is `v1`.

Example: `https://partnerapi.mozes.com/v1/user/lookup`

Authentication
--------

API requests must include two headers, `X-API-Key` and `X-API-Shared-Secret`, which can be requested by contacting support@mozes.com or speaking to your client services representative. Because the API key and shared secret are sent in plain text, requests must be made over SSL.

Requests
--------

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

Response Format
--------

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

Currently Documented APIs
--------

* [Broadcast](https://github.com/mozes/partner-api-docs/blob/master/sections/broadcasting.md#broadcasting "Broadcast")
* [Broadcast List](https://github.com/mozes/partner-api-docs/blob/master/sections/broadcast_list.md#broadcast-list "Broadcast List")
* [Campaign](https://github.com/mozes/partner-api-docs/blob/master/sections/campaign.md#campaign "Campaign")
* [Project](https://github.com/mozes/partner-api-docs/blob/master/sections/project.md#project "Project")
* [Reports](https://github.com/mozes/partner-api-docs/blob/master/sections/reports.md#reports "Reports")
* [User](https://github.com/mozes/partner-api-docs/blob/master/sections/user.md#mozes-user "User")

Under Development
--------
* Web hooks (callbacks) for data capture integration with CRM systems

Have questions or suggestions to improve the API?
--------
We're always open to feedback at Mozes. Open an issue in this repository and a member of the engineering team will get back to you.



