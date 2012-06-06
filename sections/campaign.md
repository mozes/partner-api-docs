# Campaign

## Start SMS flow

`POST /v1/campaign/start_sms_flow` - Gets list subscription changes for a project since a given date

### Request Parameters

`campaign_id` The ID of the campaign that you wish to invoke.

`mozes_id` The ID of the user to whom you wish to begin the campaign flow.

### Response Data

`none`

### Example Request

```json
{
    "campaign_id": "97483",
    "mozes_id": "123456"
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

`10004 : INVALID_MOZES_ID`
* Mozes ID could not be found in our system.

