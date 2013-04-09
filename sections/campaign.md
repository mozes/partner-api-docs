# Campaign

## Start SMS flow

`/v1/campaign/start_sms_flow` - Invokes a new SMS flow for a user with the desired campaign. To the user, it will be as if he had sent a text message himself to begin the flow.

The Campaign participation API allows a consumer to interact with specific campaigns that you've created in Mozes Connect.
For example: A consumer submits their mobile phone number on a web form. They can receive the text message flow that they would have received if they texted into the campaign keyword.

### Request Parameters

`campaign_id` The ID of the campaign that you wish to invoke.

`mozes_id` The ID of the user to whom you wish to begin the campaign flow.

`channel_id` _Optional._ The channel ID corresponds to a specific choice in a vote campaign.

### Response Data

`none`

### Example Request

```json
{
    "campaign_id": "97483",
    "mozes_id": "123456",
    "channel_id":"241512"
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

