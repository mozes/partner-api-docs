# Project

## Get Projects

`POST /v1/project/get_all` - Gets all projects under accounts that are available to the current API key.

An optional account ID may be passed, to restrict projects to a certain account. This is useful if your API key has access to multiple accounts and you only want to see a certain account's projects.

### Request Parameters

`account_id` *Optional.* Only return projects under the provided account ID.

### Response Data

`projects` The list of projects available to the current API key.

### Example Request

```json
{
    "account_id": "123456"
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

`none`



## Add Subscriber

`POST /v1/project/subscribe` - Subscribes a user to the given project.

If the user is under the age of 13, then, under COPPA guidelines, the user's phone number is flagged, and an error is returned. Otherwise, the user is subscribed to the mobile list and an SMS is sent to the user's mobile phone confirming the subscription.

### Request Parameters

`mozes_id` The Mozes ID of the user to be subscribed.

`project_id` The project to be modified.

`dob` The date of birth of the user. Though this information isn't saved, it must be passed to check the participant's age as part of COPPA compliance. (YYYYMMDD)

### Response Data

`none`

### Example Request

```json
{
    "mozes_id": "455327",
    "project_id": "123456",
    "dob": "19801123"
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
    "response": []
}
```

### Return Codes

`11002 : USER_UNDERAGE`
* The user is under the age of 13. Under COPPA guidelines, we cannot subscribe users who are underage.

`11003 : USER_BLOCKED`
* The user has been blocked. Usually this status is passed on from the wireless carrier as a result of disconnected service or a transferred number.

`13000 : PROJECT_ALREADY_SUBSCRIBED`
* An attempt was made to subscribe a user who is already in the project.




## Remove Subscriber

`POST /v1/project/unsubscribe` - Unsubscribes a user from the given project.

### Request Parameters

`mozes_id` The Mozes ID of the user to be subscribed.

`project_id` The project to be modified.

### Response Data

`none`

### Example Request

```json
{
    "mozes_id": "455327",
    "project_id": "123456"
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
    "response": []
}
```

### Return Codes

`none`



## Get Subscription Changes

`POST /v1/project/get_subscriber_updates` - Gets list subscription changes for a project since a given date

### Request Parameters

`project_id` The project to be checked.

`start_date` Results will be returned for all users who subscribed/unsubscribed since start_date (YYYY-MM-DDThh:mm:ssZ)

### Response Data

`Array` of modifications:

`mozes_id` User's Mozes ID

`phone` User's phone

`subscription_status`
* 0 - Unsubscribed
* 1 - Subscribed

`modified_date` Date user changed their subscription status

### Example Request

```json
{
    "project_id": "455327",
    "start_date": "2012-03-04T00:00:00Z"
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
    "response": [
        {
            "mozes_id": "123456",
            "phone": "16505551234",
            "subscription_status": 0,
            "modified_date": "2012-03-27T02:10:01Z"
        },
        {
            "mozes_id": "234567",
            "phone": "14085556677",
            "subscription_status": 0,
            "modified_date": "2012-05-09T02:59:30Z"
        },
        {
            "mozes_id": "345678",
            "phone": "16305557683",
            "subscription_status": 1,
            "modified_date": "2012-04-04T18:21:00Z"
        }
    ]
}
```

### Return Codes

`none`

