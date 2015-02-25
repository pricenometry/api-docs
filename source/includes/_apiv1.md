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

Search Products based on a query or key word.

### HTTP Request

`GET http://api.pricels.com/v1/:CONTAINER/search/:QUERY`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container you are searching in
:QUERY | true | What you are searching for
fetch | false | Automatically crawl new data (default: true)
social | false | Automatically fetch new social data (default: false)

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

Search Products based on a query or key word.

### HTTP Request

`GET http://api.pricels.com/v1/:CONTAINER/search/:QUERY.xml`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container you are searching in
:QUERY | true | What you are searching for
fetch | false | Automatically crawl new data (default: true)
social | false | Automatically fetch new social data (default: false)

<aside class="notice">
You must replace `:CONTAINER` with the available container you are searching in and `:QUERY` with what you are searching for.
</aside>



## Get Product in JSON

> Request example

```shell
curl "http://api.pricels.com/v1/amazon-offers/B00DR0PDNE"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "url": "http://www.amazon.com/Google-Chromecast-Streaming-Media-Player/dp/B00DR0PDNE",
  "date": "2015-02-24",
  "id": "B00DR0PDNE",
  "tags": [
    "Google",
    "Chromecast",
    "HDMI",
    "Streaming",
    "Media",
    "Player",
    "Inc.",
    "H2G2-42",
    "86002596-01"
  ],
  "name": "Google Chromecast HDMI Streaming Media Player",
  "description": "Amazon.com: Google Chromecast HDMI Streaming Media Player: Electronics",
  "type": "Offer",
  "image": "http://ecx.images-amazon.com/images/I/811nvG%2BLgML._SL1500_.jpg",
  "sku": "B00DR0PDNE",
  "screenshot": "B00DR0PDNE/2015-02-24.jpg",
  "price": "30.07",
  "original_price": "35.00",
  "facebook_shares": 48466,
  "google_shares": 5776,
  "twitter_shares": 177,
  "reddit_shares": 149,
  "linkedin_shares": 364,
  "pinterest_shares": 106,
  "stumbleupon_shares": 23,
  "total_shares": 55061
}
```

Get most up to date Product information by Product id.

### HTTP Request

`GET http://api.pricels.com/v1/:CONTAINER/:ID`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container
:ID | true | Product ID
fetch | false | Automatically crawl new data (default: true)
social | false | Automatically fetch new social data (default: false)

<aside class="notice">
You must replace `:CONTAINER` with the available container and `:ID` with the Product ID.
</aside>




## Get Product in XML

> Request example

```shell
curl "http://api.pricels.com/v1/amazon-offers/B00DR0PDNE.xml"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns XML structured like this:

```xml
<hash>
  <response>
    <status type="integer">200</status>
  </response>
  <url>
  http://www.amazon.com/Google-Chromecast-Streaming-Media-Player/dp/B00DR0PDNE
  </url>
  <date>2015-02-24</date>
  <id>B00DR0PDNE</id>
  <tags type="array">
    <tag>Google</tag>
    <tag>Chromecast</tag>
    <tag>HDMI</tag>
    <tag>Streaming</tag>
    <tag>Media</tag>
    <tag>Player</tag>
    <tag>Inc.</tag>
    <tag>H2G2-42</tag>
    <tag>86002596-01</tag>
  </tags>
  <name>Google Chromecast HDMI Streaming Media Player</name>
  <description>
  Amazon.com: Google Chromecast HDMI Streaming Media Player: Electronics
  </description>
  <type>Offer</type>
  <image>
  http://ecx.images-amazon.com/images/I/811nvG%2BLgML._SL1500_.jpg
  </image>
  <sku>B00DR0PDNE</sku>
  <screenshot>B00DR0PDNE/2015-02-24.jpg</screenshot>
  <price>30.07</price>
  <original-price>35.00</original-price>
  <facebook-shares type="integer">48466</facebook-shares>
  <google-shares type="integer">5776</google-shares>
  <twitter-shares type="integer">177</twitter-shares>
  <reddit-shares type="integer">149</reddit-shares>
  <linkedin-shares type="integer">364</linkedin-shares>
  <pinterest-shares type="integer">106</pinterest-shares>
  <stumbleupon-shares type="integer">23</stumbleupon-shares>
  <total-shares type="integer">55061</total-shares>
</hash>
```

Get most up to date Product information by Product id.

### HTTP Request

`GET http://api.pricels.com/v1/:CONTAINER/:ID.xml`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container
:ID | true | Product ID
fetch | false | Automatically crawl new data (default: true)
social | false | Automatically fetch new social data (default: false)

<aside class="notice">
You must replace `:CONTAINER` with the available container and `:ID` with the Product ID.
</aside>




## Get Product History in JSON

> Request example

```shell
curl "http://api.pricels.com/v1/amazon-offers/B00DR0PDNE/history"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "id": "B00DR0PDNE",
  "name": "Google Chromecast HDMI Streaming Media Player",
  "sku": {
    "2015-02-09": "B00DR0PDNE"
  },
  "screenshot": {
    "2015-02-09": "B00DR0PDNE/2015-02-09.jpg",
    "2015-02-10": "B00DR0PDNE/2015-02-10.jpg",
    "2015-02-21": "B00DR0PDNE/2015-02-21.jpg",
    "2015-02-24": "B00DR0PDNE/2015-02-24.jpg"
  },
  "price": {
    "2015-02-09": "32.49",
    "2015-02-10": "31.78",
    "2015-02-21": "30.07"
  },
  "original_price": {
    "2015-02-09": "35.00"
  }
}
```

Get most up to date Product history by Product id.

### HTTP Request

`GET http://api.pricels.com/v1/:CONTAINER/:ID/history`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container
:ID | true | Product ID
fetch | false | Automatically crawl new data (default: true)
social | false | Automatically fetch new social data (default: false)

<aside class="notice">
You must replace `:CONTAINER` with the available container and `:ID` with the Product ID.
</aside>




## Get Product Screenshot Image

> Request example

```shell
curl "http://api.pricels.com/v1/amazon-offers/B00DR0PDNE/2015-02-24.jpg"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command redirects to a URL like the one below:

```html
  <html>
    <body>
    You are being
    <a href="https://amazon-screenshots.pricels.com/B00DR0PDNE/2015-02-24.jpg?AWSAccessKeyId=AUTO-GENERATED&Signature=AUTO-GENERATED&Expires=24-HOURS">redirected</a>.
    </body>
  </html>
```

Get Product redirect to screenshot image.

### HTTP Request

`GET http://api.pricels.com/v1/:CONTAINER/:ID/:SCREENSHOT_DATE.jpg`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container
:ID | true | Product ID
:SCREENSHOT_DATE | true | Date screenshot was captured

<aside class="notice">
You must replace `:CONTAINER` with the available container, `:ID` with the Product ID and `:SCREENSHOT_DATE` with date screenshot was taken.
</aside>




## Get Product Screenshot in JSON

> Request example

```shell
curl "http://api.pricels.com/v1/amazon-offers/B00DR0PDNE/2015-02-24"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "id": "B00DR0PDNE",
  "redirect_url": "https://amazon-screenshots.pricels.com/B00DR0PDNE/2015-02-24.jpg?AWSAccessKeyId=AUTO-GENERATED&Signature=AUTO-GENERATED&Expires=24-HOURS"
}
```

Get Product screenshot in JSON form.

### HTTP Request

`GET http://api.pricels.com/v1/:CONTAINER/:ID/:SCREENSHOT_DATE`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container
:ID | true | Product ID
:SCREENSHOT_DATE | true | Date screenshot was captured

<aside class="notice">
You must replace `:CONTAINER` with the available container, `:ID` with the Product ID and `:SCREENSHOT_DATE` with date screenshot was taken.
</aside>



## Get Product Screenshot in XML

> Request example

```shell
curl "http://api.pricels.com/v1/amazon-offers/B00DR0PDNE/2015-02-24.xml"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns XML structured like this:

```xml
<hash>
  <response>
    <status type="integer">200</status>
  </response>
  <id>B00DR0PDNE</id>
  <redirect-url>
  https://amazon-screenshots.pricels.com/B00DR0PDNE/2015-02-24.jpg?AWSAccessKeyId=AUTO-GENERATED&Signature=AUTO-GENERATED&Expires=24-HOURS
  </redirect-url>
</hash>
```

Get Product screenshot in XML form.

### HTTP Request

`GET http://api.pricels.com/v1/:CONTAINER/:ID/:SCREENSHOT_DATE.xml`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container
:ID | true | Product ID
:SCREENSHOT_DATE | true | Date screenshot was captured

<aside class="notice">
You must replace `:CONTAINER` with the available container, `:ID` with the Product ID and `:SCREENSHOT_DATE` with date screenshot was taken.
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

Search all availble Products based on a query or key word.

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

Search all availble Products based on a query or key word

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
