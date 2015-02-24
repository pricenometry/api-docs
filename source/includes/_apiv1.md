# API V1

## Get Status in JSON

> Request example

```shell
curl "http://api.pricels.com/v1"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
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





## Get Status in XML

> Request example

```shell
curl "http://api.pricels.com/v1.xml"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns XML structured like this:

```xml
<hash>
  <response>
    <status type="integer">200</status>
  </response>
  <active type="boolean">true</active>
  <api-usage-cap type="integer">1000</api-usage-cap>
  <api-last-used>2015-02-24</api-last-used>
  <api-daily-usage type="integer">38</api-daily-usage>
  <available>
    <amazon-offers>2.9M</amazon-offers>
    <walmart-offers>135.9K</walmart-offers>
    <costco-offers>83K</costco-offers>
    <target-offers>38.4K</target-offers>
  </available>
  <indexing>63</indexing>
  <processing>453.3K</processing>
  <pending>947.2M</pending>
</hash>
```

Check the status of your current api usage as well as available data sources to pull from.

### HTTP Request

`GET http://api.pricels.com/v1.xml`

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




## Search Products in JSON

> Request example

```shell
curl "http://api.pricels.com/v1/amazon-offers/search/chromecast"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "results": [
    {
      "id": "B00DR0PDNE",
      "name": "Google Chromecast HDMI Streaming Media Player",
      "container": "amazon-offers"
    }
  ]
}
```

Search products based on a query or key word.

### HTTP Request

`GET http://api.pricels.com/v1/:CONTAINER/search/:QUERY`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container you are searching in
:QUERY | true | What you are searching for

<aside class="notice">
You must replace `:CONTAINER` with the available container you are searching in and `:QUERY` with what you are searching for.
</aside>




## Search Products in XML

> Request example

```shell
curl "http://api.pricels.com/v1/amazon-offers/search/chromecast.xml"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns XML structured like this:

```xml
<hash>
  <response>
    <status type="integer">200</status>
  </response>
  <results type="array">
    <result>
      <id>B00DR0PDNE</id>
      <name>Google Chromecast HDMI Streaming Media Player</name>
      <container>amazon-offers</container>
    </result>
  </results>
</hash>
```

Search products based on a query or key word.

### HTTP Request

`GET http://api.pricels.com/v1/:CONTAINER/search/:QUERY.xml`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container you are searching in
:QUERY | true | What you are searching for

<aside class="notice">
You must replace `:CONTAINER` with the available container you are searching in and `:QUERY` with what you are searching for.
</aside>




























## Search All Products in JSON

> Request example

```shell
curl "http://api.pricels.com/v1/search/chromecast"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "results": [
    {
      "id": "B00DR0PDNE",
      "name": "Google Chromecast HDMI Streaming Media Player",
      "container": "amazon-offers"
    },
    {
      "id": "811571013579",
      "name": "Google Chromecast HDMI Streaming Media Player",
      "container": "walmart-offers"
    },
    {
      "name": "Google Chromecast HDMI Streaming Media Player",
      "id": "15460778",
      "container": "target-offers"
    },
    {
      "id": "945132",
      "name": "Google Chromecast HDMI Streaming Media Player with $10 Google Play Credit",
      "container": "costco-offers"
    }
  ]
}
```

Search all availble products based on a query or key word.

### HTTP Request

`GET http://api.pricels.com/v1/search/:QUERY`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:QUERY | true | What you are searching for

<aside class="notice">
You must replace `:QUERY` with what you are searching for.
</aside>




## Search All Products in XML

> Request example

```shell
curl "http://api.pricels.com/v1/search/chromecast.xml"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns XML structured like this:

```xml
<hash>
  <response>
    <status type="integer">200</status>
  </response>
  <results type="array">
    <result>
      <id>B00DR0PDNE</id>
      <name>Google Chromecast HDMI Streaming Media Player</name>
      <container>amazon-offers</container>
    </result>
    <result>
      <id>811571013579</id>
      <name>Google Chromecast HDMI Streaming Media Player</name>
      <container>walmart-offers</container>
    </result>
    <result>
      <name>Google Chromecast HDMI Streaming Media Player</name>
      <id>15460778</id>
      <container>target-offers</container>
    </result>
    <result>
      <id>945132</id>
      <name>Google Chromecast HDMI Streaming Media Player with $10 Google Play Credit</name>
      <container>costco-offers</container>
    </result>
  </results>
</hash>
```

Search all availble products based on a query or key word

### HTTP Request

`GET http://api.pricels.com/v1/search/:QUERY.xml`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:QUERY | true | What you are searching for

<aside class="notice">
You must replace `:QUERY` with what you are searching for.
</aside>
