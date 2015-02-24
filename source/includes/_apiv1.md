# API V1

## Get Status

> Request example

```shell
curl "http://api.pricels.com/v1"
  -H "Authorization: Token token="YOUR-ACCESS-TOKEN""
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "active": true,
  "api_usage_cap": 100000000,
  "api_last_used": "2015-02-24",
  "api_daily_usage": 17,
  "available": {
    "amazon-offers": "2.9M",
    "walmart-offers": "134.4K",
    "costco-offers": "83K",
    "target-offers": "38.4K"
    },
  "indexing": "180",
  "processing": "453.6K",
  "pending": "947.2M"
}
```

Check the status of your current api usage as well as available data sources to pull from.

### HTTP Request

`GET http://api.pricels.com/v1`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate

### Status Types

Status Type | Description
--------- | -----------
active | Api Key is still active
api_usage_cap | Max number of allowed api calls per day (can be unlimited)
api_last_used | Date of the last call your key made to our api
api_daily_usage | Total number of api calls made on api_last_used date
available | Name and total number of data containers available for you to research
indexing | Collected data being added to search
processing | Data still waiting to be processed
pending | Data still waiting to be added to processing
