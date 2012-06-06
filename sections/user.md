# User

## Lookup

`/v1/user/lookup` - Creates a new Mozes ID or retrieves an existing mozes\_id for a user based on the given mobile number. 

### Request Parameters

`phone` Eleven-digit (starting with 1) numeric string of the participating user's phone number (e.g., 14155551234)

### Response Data

`mozes_id` The unique ID of the participating user as used by the Mozes Connect platform.

### Example Request

```json
{
    "phone": "14155551234"
}
```

### Example Response

```json
{
    "status": {
        "code": 0,
        "message": "OK",
        "description": "OK"
    },
    "response": {
        "mozes_id": "123456"
    }
}
```

### Return Codes

`11001 : USER_INVALID_PHONE_FORMAT`
* The phone number should be a numeric string representing the phone number. The first digit should be '1'.

`11002 : USER_UNDERAGE`
* The user is under the age of 13. Under COPPA guidelines, we cannot subscribe users who are underage.

`11003 : USER_BLOCKED`
* The user has been blocked. Usually this status is passed on from the wireless carrier as a result of disconnected service or a transferred number.

`11004 : USER_LANDLINE`
* The phone number is for a landline. Mozes only handles mobile numbers.



## Get Subscribed Projects

`/v1/user/get_subscribed_projects` - Get array of projects/lists that the given user is subscribed to. 

### Request Parameters

`mozes_id` The unique ID of the participating user as used by the Mozes Connect platform.

### Response Data

`projects` The array of projects the given user is subscribed to.

### Example Request

```json
{
    "mozes_id": "1239876454"
}
```

### Example Response

```json
{
    "status": {
        "code": 0,
        "name": "OK",
        "description": "OK"
    },
    "response": {
        "projects": [
            [
                {
                    "id": "74905",
                    "name": "My cool project",
                    "account_id": "12345"
                }
            ],
            [
                {
                    "id": "78008",
                    "name": "The other cool project",
                    "account_id": "12345"
                }
            ]
        ]
    }
}
```

### Return Codes

`10004 : INVALID_MOZES_ID`
* Mozes ID could not be found in our system.
