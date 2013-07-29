# Campaign

* [Cast Vote](#cast-vote)
* [Get Vote Config](#get-vote-config)
* [Start SMS Flow](#start-sms-flow)

## Cast Vote

`/v1/campaign/cast_vote` - Casts a vote on behalf of a user

### Request Parameters

`campaign_id` The ID of the campaign that you wish to get configuration info for.

`project_id` The ID of the project associated with this campaign.

`mozes_id` The ID of the user to whom you wish to cast the vote (use [user api](user.md) to lookup).

`vote_choice_id` The ID of the choice the user is going to vote for (use [get_vote_config](#get-vote-config) to lookup choice ids for a campaign)

### Response Data

`status_code` Can be one of the following values:

```
VOTE_STATUS_OK = 0;
VOTE_STATUS_INACTIVE = 100;
VOTE_STATUS_LIMIT_EXCEEDED = 200;
VOTE_STATUS_NOT_UNIQUE = 300;
```

### Example Request

```json
{
    "campaign_id": "97483",
    "project_id": "78945",
    "mozes_id": "12545135",
    "vote_choice_id": "1234"
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
    "status_code": 0
  }
}
```

### Return Codes


`10004 : INVALID_MOZES_ID`
* Mozes ID could not be found in our system.

`13003 : PROJECT_INVALID_CAMPAIGN_ID`
* The campaign ID passed is invalid.


## Get Vote Config

`/v1/campaign/get_vote_config` - Retrieves the question and vote chocies for a vote campaign.

### Request Parameters

`campaign_id` The ID of the campaign that you wish to get configuration info for.

`project_id` The ID of the project associated with this campaign.

### Response Data

`question` The question to be displayed to users.

`chocies` An set of responses to the question. Each has an id, description for display and position in the list.

### Example Request

```json
{
    "campaign_id": "97483",
    "project_id": "78945"
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
    "choices": {
      "7726": {
        "id": 7726,
        "description": "#mozes1",
        "position": 0,
        "avatar_id": 0
      },
      "7727": {
        "id": 7727,
        "description": "#mozes2",
        "position": 1,
        "avatar_id": 0
      },
      "7728": {
        "id": 7728,
        "description": "#mozes3",
        "position": 2,
        "avatar_id": 0
      }
    },
    "question": "What is your favorite?"
  }
}
```

### Return Codes

`13003 : PROJECT_INVALID_CAMPAIGN_ID`
* The campaign ID passed is invalid.


## Start SMS flow

`/v1/campaign/start_sms_flow` - Invokes a new SMS flow for a user with the desired campaign. To the user, it will be as if he had sent a text message himself to begin the flow.

The Campaign participation API allows a consumer to interact with specific campaigns that you've created in Mozes Connect.
For example: A consumer submits their mobile phone number on a web form. They can receive the text message flow that they would have received if they texted into the campaign keyword.

### Request Parameters

`campaign_id` The ID of the campaign that you wish to invoke.

`mozes_id` The ID of the user to whom you wish to begin the campaign flow.

`project_id` The ID of the project associated with this flow.

`channel_id` _Optional._ The channel ID corresponds to a specific choice in a vote campaign.

### Response Data

`none`

### Example Request

```json
{
    "campaign_id": "97483",
    "mozes_id": "123456",
    "project_id": "78945",
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

