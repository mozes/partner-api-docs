# Broadcasting

## Send Broadcast to a Single User

`/v1/broadacst/send_sms_to_user` - Sends a broadcast to a single user. The message to be sent will have the project’s name as well as a Mozes TOS signature added to it. An error will be returned if the combined length exceeds 160 characters.

### Request Parameters

`project_id` The ID of the project the user will receive the message from.

`mozes_id` The ID of the user to whom you wish to broadcast.

`message` The message to be broadcasted. Should be short enough so that the combined length of the message, the project’s name and the Mozes signature does not exceed 160 characters.

### Response Data

`client_id` A unique identifier for referencing this broadcast for later queries.

### Example Request

```json
{
    "project_id": 12345,
    "mozes_id": 1283228,
    "message": "My message. Be careful about the length!"
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
        "client_id":"eb1ea30eaee7d0b37c04f56960f6c6bd"
    }
}
```

### Return Codes

`14000 : BROADCAST_MESSAGE_LENGTH_EXCEEDED`
* The message passed in exceeded the 160-character limit for text messages after the project's name and the Mozes signature were added.

`14001 : BROADCAST_USER_NOT_SUBSCRIBED`
* An attempt was made to send a message to a user that is not subscribed to the project. Users must already be subscribed to a project in order to receive a broadcast.





## Send Broadcast to Broadcast List

`/v1/broadcast/send_sms_to_broadcast_list` - Sends a broadcast to a [broadcast list](https://github.com/mozes/partner-api-docs/blob/master/sections/broadcast_list.md#broadcast-list "broadcast list") created with the [broadcast_list/create](https://github.com/mozes/partner-api-docs/blob/master/sections/broadcast_list.md#create "broadcast_list/create") service. This allows a message to be sent to multiple users that you define in the list. The message to be sent will have the project’s name as well as a Mozes signature added to it. An error will be returned if the combined length exceeds 160 characters.

### Request Parameters

`project_id` The ID of the project the user will receive the message from.

`broadcast_list_id` The ID of the [broadcast list](https://github.com/mozes/partner-api-docs/blob/master/sections/broadcast_list.md#broadcast-list "broadcast list") containing the users to whom you wish to broadcast.

`message` The message to be broadcasted. Should be short enough so that the combined length of the message, the project’s name and the Mozes signature does not exceed 160 characters.

### Response Data

`client_id` A unique identifier for referencing this broadcast for later queries.

### Example Request

```json
{
    "project_id": 456442,
    "broadcast_list_id": 1483228,
    "message": "My message. Be careful about the length!"
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
        "client_id":"eb1ea30eaee7d0b37c04f56960f6c6bd"
    }
}
```

### Return Codes

`12002 : BROADCAST_LIST_INVALID_LIST_PROJECT`
* The list ID does not correspond to the provided project ID.

`14000 : BROADCAST_MESSAGE_LENGTH_EXCEEDED`
* The message passed in exceeded the 160-character limit for text messages after the project's name and the Mozes signature were added.




## Send Broadcast to Users

`/v1/broadcast/send_sms_to_users` - Sends a broadcast to a set of users. This allows a message to be sent to multiple users that you define in the request. The message to be sent will have the project’s name as well as a Mozes signature added to it. An error will be returned if the combined length exceeds 160 characters.

### Request Parameters

`project_id` The ID of the project the user will receive the message from.

`mozes_ids` The list of Mozes IDs of users to whom you wish to broadcast.

`message` The message to be broadcasted. Should be short enough so that the combined length of the message, the project’s name and the Mozes signature does not exceed 160 characters.

### Response Data

`client_id` A unique identifier for referencing this broadcast for later queries.

### Example Request

```json
{
    "project_id": 456442,
    "mozes_ids": [1483228,3838234,2349059,589834],
    "message": "My message. Be careful about the length!"
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
        "client_id":"eb1ea30eaee7d0b37c04f56960f6c6bd"
    }
}
```

### Return Codes

`10004 : INVALID_MOZES_ID`
* Mozes ID could not be found in our system.

`14000 : BROADCAST_MESSAGE_LENGTH_EXCEEDED`
* The message passed in exceeded the 160-character limit for text messages after the project's name and the Mozes signature were added.




## Get Broadcast Status

`/v1/broadcast/get_broadcast_status` - Retrieves information about a broadcast.

### Request Parameters

`project_id` The ID of the project the broadcast was associated with.

`client_id` The ID of the broadcast to query. This is the `client_id` returned by message sending APIs.

### Response Data

`created_ts` Timestamp when the broadcast was started.

`delivered_ts` Timestamp when the broadcast completed.

`recipient_count` Number of users the broadcast was sent to.

`delivered` Delivery status. 1 if completed, 0 if incomplete.

### Example Request

```json
{
    "project_id": 456442,
    "client_id": "eb1ea30eaee7d0b37c04f56960f6c6bd"
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
        "created_ts": "2012-06-13T12:01:52Z"
        "delivered_ts": "2012-06-13T12:01:55Z",
        "recipient_count": "1",
        "delivered": 1
    }
}
```

### Return Codes

`14002 : BROADCAST_STATUS_NOT_FOUND`
* Could not find a broadcast with the provided client ID.





