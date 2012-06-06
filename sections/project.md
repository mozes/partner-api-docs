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

`None`

