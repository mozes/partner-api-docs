# Broadcast List

## Create

`/v1/broadcast_list/create` - Create a subset of a project’s mobile list. The list appears as narrowcast criteria in Mozes Connect’s project broadcast page.

An optional account ID may be passed, to restrict projects to a certain account. This is useful if your API key has access to multiple accounts and you only want to see a certain account's projects.

### Request Parameters

`project_id` The project's ID to associate the new broadcast list with

`name` The name for this broadcast list

*NOTE: broadcast list names must be unique within a project. Attempting to create a list with a name that already exists will result in an error*

### Response Data

`projects` The list of projects available to the current API key.

### Example Request

```json
{
    "project_id": "123456",
    "name": "my list"
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
        "broadcast_list_id": 132141
    }
}
```

### Return Codes

`12000 : BROADCAST_LIST_DUPLICATE_LIST`
* An attempt was made to create a list that already exists.





## Delete

`/v1/broadcast_list/delete` - Deletes a project’s subset list when it is no longer needed.

### Request Parameters

`broadcast_list_id` The id of the broadcast list to be deleted

`project_id` The containing project id.

### Response Data

`none`

### Example Request

```json
{
    "broadcast_list_id": 455327,
    "project_id": 123456
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

`12002 : BROADCAST_LIST_INVALID_LIST_PROJECT`
* The list ID does not correspond to the provided project ID.




## Truncate

`/v1/broadcast_list/truncate` - Removes all users from a broadcast list.

### Request Parameters

`broadcast_list_id` The id of the broadcast list to be deleted

`project_id` The containing project id.

### Response Data

`none`

### Example Request

```json
{
    "broadcast_list_id": 455327,
    "project_id": 123456
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

`12002 : BROADCAST_LIST_INVALID_LIST_PROJECT`
* The list ID does not correspond to the provided project ID.






## Insert Users

`/v1/broadcast_list/insert_users` - Inserts a list of users into a broadcast list that you have created.

### Request Parameters

`broadcast_list_id` The id of the broadcast list to be deleted.

`project_id` The containing project id.

`mozes_ids` *list* An array of Mozes IDs representing the users to be inserted into the broadcast list

### Response Data

`none`

### Example Request

```json
{
    "broadcast_list_id": 455327,
    "project_id": 123456,
    "mozes_ids": [461274,47238,4738,4738,473827,4732]
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

`12001 : BROADCAST_LIST_LIST_NOT_FOUND`
* Could not find list for the provided list ID.
