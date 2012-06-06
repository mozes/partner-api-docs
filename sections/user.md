# User


## User Lookup

`GET /v1/user/lookup` - Creates a new Mozes ID or retrieves an existing mozes\_id for a user based on the given mobile number. 

### Request Paramters

`phone` **numeric string** Eleven-digit (starting with 1) numeric string of the participating user's phone number (e.g., 14155551234)

### Response Data

`mozes_id` **numeric string** The unique ID of the participating user as used by the Mozes Connect platform.

### Return Codes

`11001` **USER\_INVALID\_PHONE\_FORMAT**
The phone number should be a numeric string representing the phone number. The first digit should be '1'.

`11002` **USER\_UNDERAGE**
The user is under the age of 13. Under COPPA guidelines, we cannot subscribe users who are underage.

`11003` **USER\_BLOCKED**
The user has been blocked. Usually this status is passed on from the wireless carrier as a result of disconnected service or a transferred number.

`11004` **USER\_LANDLINE**
The phone number is for a landline. Mozes only handles mobile numbers.