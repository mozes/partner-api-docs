# Reports

## Get Project Summary

`/v1/report/get_project_summary` - Returns a summary of a day's metrics for a project. If a date is not passed in, then it will return the most recent day's data. Data is usually collected around 3am Pacific for the previous day.

### Request Parameters

`project_id` The ID of the project from which to retrieve data.

`date` *Optional.* The date of the data to retrieve, in YYYY-MM-DD format (ISO 8601). If not passed, it will default to the last recorded date.

### Response Data

`date` The date for this set of data.

`mobile_connections` The total number of interactions with the project.

`mobile_connections_in` The number of inbound connections. Usually represents the text messages sent to this project.

`mobile_connections_out` The number of outbound connections. Usually represents the text messages sent back to a user.

`subscriptions` The number of users added to the project's mobile list.

`subscribers` The total number of users in the project.

### Example Request

```json
{
    "project_id": 456442,
    "date":"2012-05-30"
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
        "date":"2012-05-30",
        "mobile_connections": 775,
        "mobile_connections_in": 234,
        "subscriptions": 153,
        "mobile_connections_out": 541,
        "subscribers": 5614
    }
}
```

### Return Codes

`none`





## Get Campaign Summary

`/v1/report/get_campaign_summary` - Returns a summary of a day's metrics for a campaign. If a date is not passed in, then it will return the most recent day's data. Data is usually collected around 3am Pacific for the previous day.

### Request Parameters

`project_id` The ID of the project from which to retrieve data.

`campaign_id` The ID of the campaign from which to retrieve data.

`date` *Optional.* The date of the data to retrieve, in YYYY-MM-DD format (ISO 8601). If not passed, it will default to the last recorded date.

### Response Data

`date` The date for this set of data.

`mobile_connections` The total number of interactions with the project.

`mobile_connections_in` The number of inbound connections. Usually represents the text messages sent to this campaign.

`mobile_connections_out` The number of outbound connections. Usually represents the text messages sent back to a user.

`subscriptions` The number of users added to the project's mobile list.

`subscribers` The total number of users in the project.

### Example Request

```json
{
    "project_id": 456442,
    "campaign_id": 2334234,
    "date":"2012-05-30"
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
        "date":"2012-05-30",
        "mobile_connections": 775,
        "mobile_connections_in": 234,
        "subscriptions": 153,
        "mobile_connections_out": 541,
        "subscribers": 5614
    }
}
```

### Return Codes

`none`





