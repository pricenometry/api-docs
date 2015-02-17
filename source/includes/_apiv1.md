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
  "active": true,
  "name" : "YOUR COMPANY NAME"
  "api_usage_cap": 1000,
  "api_last_used": "2015-02-17",
  "api_daily_usage": 2,
  "available": [
    "amazon-offers",
    "walmart-offers",
    "bestbuy-offers",
    "rakuten-offers",
    "ebay-offers",
    "costco-offers",
    "target-offers"
  ]
}
```

Check the status of your current api usage as well as available data sources to pull from.

### HTTP Request

`GET http://api.pricels.com/v1`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
