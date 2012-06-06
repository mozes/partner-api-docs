Authentication
================

Headers
----------------
API requests must include two headers, `X-API-Key` and `X-API-Shared-Secret`, which can be requested by contacting support@mozes.com or speaking to your client services representative. Because the API key and shared secret are sent in plain text, requests must be made over SSL.

Request Generation
----------------
Requests are sent using HTTP POST. The "Content-Type" header of the request must be "application/json." In addition, the request must include the "X-API-Key" and "X-API-Shared-Secret" headers. The request data itself is sent as JSON formatted POST data. An example of a HTTP request is as follows:

```
User-Agent: curl/7.12.1 (i686-redhat-linux-gnu) libcurl/7.12.1 OpenSSL/0.9.7a zlib/1.2.1.2 libidn/0.5.6
Host: api.mozes.com
Pragma: no-cache
Accept: */*
Content-Type: application/json
X-API-Key: xxxxxx
X-API-Shared-Secret: XXXXXXXXXXX
Content-Length: 61

{"mozes_id":"nnnnnnnnn","project_id":nnnnn,"dob":"19750312"}
```