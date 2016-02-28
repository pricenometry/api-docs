# API V1

## Get Status

> Request example

```shell
curl "http://api.pricenometry.com/v1"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "status": {
    "active": true,
    "api_last_used": "2015-03-04",
    "available": {
      "amazon-offers": "15.7M",
      "walmart-offers": "11.2M",
      "bestbuy-offers": "919.4K",
      "target-offers": "581.4K",
      "costco-offers": "10.9K",
      "boxed-offers": "896"
    },
    "indexing": "10K",
    "processing": "11.3M",
    "pending": "1.5B"
  }
}
```

Check the status of your current api usage as well as available data sources to pull from. Default response is JSON, also available in XML using a *.xml extension.

### HTTP Request

`GET http://api.pricenometry.com/v1`

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





## Search Products

> Request example

```shell
curl "http://api.pricenometry.com/v1/amazon-offers/search/chromecast"
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

Search Products based on a query or key word. Default response is JSON, also available in XML using a *.xml extension.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/search/:QUERY`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container you are searching in
:QUERY | true | What you are searching for
results | false | Number of Results you want back (default: 10)
fetch | false | Automatically crawl new data (default: true)
social | false | Automatically fetch new social data (default: false)

<aside class="notice">
You must replace `:CONTAINER` with the available container you are searching in and `:QUERY` with what you are searching for.
</aside>





## Match Products

> Request example

```shell
curl "http://api.pricenometry.com/v1/walmart-offers/match?model=86002596-01"
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
      "id": "811571013579",
      "container": "walmart-offers"
      "name": "Google Chromecast HDMI Streaming Media Player",
      "social": {
        "facebook_shares": 42,
        "google_shares": 47,
        "twitter_shares": 12,
        "pinterest_shares": 10,
        "stumbleupon_shares": 1
      },
      "price": {
        "priceCurrency": "USD",
        "price": "30.07",
        "original_price": 35
      },
      "url": "http://www.walmart.com/ip/Google-Chromecast-HDMI-Streaming-Media-Player/33142918",
      "date": "2015-02-24",
      "open_graph": true,
      "type": "Offer",
      "image": "http://i5.walmartimages.com/dfw/dce07b8c-cc82/k2-_6f892d53-39df-4687-adae-fd16b2656547.v4.jpg",
      "site_name": "Walmart.com",
      "schema_org": true,
      "tags": [
        "Google",
        "Chromecast",
        "HDMI",
        "Streaming",
        "Media",
        "Player",
        "Wal-mart",
        "Walmart.com"
      ],
      "productID": "811571013579",
      "screenshot": "811571013579/2015-02-23.jpg",
      "availability": "InStock",
      "title": "Media Streaming Players",
      "sku": "811571013579",
      "mpn": "86002596-01",
      "brand": "Google",
      "model": "86002596-01"
    }
  ]
}
```

Match Products in a container based on a specific set of known parameters and values. Default response is JSON, also available in XML using a *.xml extension.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/match`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container you are searching in
:QUERY | true | What you are searching for
results | false | Number of Results you want back (default: 10)
fetch | false | Automatically crawl new data (default: true)
social | false | Automatically fetch new social data (default: false)
url | false | Unique URL for product
date | false | When data was last gathered
id | false | Unique ID for product
tags | false | Tags associated with product
name | false | Unique name of product
description | false | Given description for product
type | false | Product Type
image | false | Unique product image
sku | false | Unique product sku
mpn | false | Unique product manufacturer part number
model | false | Unique product model number
price | false | Price of product at time of sale
original_price | false | Original retail price of the product
facebook_shares | false | Number of times product has been shared on Facebook
google_shares | false | Number of times product has been shared on Google Plus
twitter_shares | false | Number of times product has been shared on Twitter
reddit_shares | false | Number of times product has been shared on Reddit
linkedin_shares | false | Number of times product has been shared on LinkedIn
pinterest_shares | false | Number of times product has been shared on Pinterest
stumbleupon_shares | false | Number of times product has been shared on StumbleUpon
total_shares | false | Number of times product has been shared on Social Media

<aside class="notice">
You must replace `:CONTAINER` with the available container you are matching against.
</aside>





## Top Products

> Request example

```shell
curl "http://api.pricenometry.com/v1/amazon-offers/top/price"
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
      "id": "B011390PHY",
      "container": "amazon-offers",
      "price": {
        "price": 850000
      },
      "availability": "Only 1 left in stock.",
      "name": "FREAKS 1932 * TOD BROWNING * COMPLETE LOBBY CARD SET * MINT * SUPER RARE!!",
      "url": "http://www.amazon.com/FREAKS-BROWNING-COMPLETE-LOBBY-SUPER/dp/B011390PHY?tag=pricelscom-20"
    },
    {
      "id": "B00EN5R088",
      "container": "amazon-offers",
      "price": {
        "instant_rebate_price": 43838.9,
        "original_price": 219194.48,
        "price": 175355.58
      },
      "name": "1139461 Trimode 9/6/4Monitors Expanded Ea Soma Technology -GEOEC9600",
      "url": "http://www.amazon.com/4Monitors-Expanded-Soma-Technology-GEOEC9600/dp/B00EN5R088?tag=pricelscom-20"
    }
  ]
}
```

Top Products in a container based on a specific set of known parameters and values. Default response is JSON, also available in XML using a *.xml extension.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/top/:TYPE`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container you are searching in
:TYPE | true | The Top Type you want to retrieve (example: price, facebook_shares, etc)
results | false | Number of Results you want back (default: 10)
fetch | false | Automatically crawl new data (default: true)
social | false | Automatically fetch new social data (default: false)

<aside class="notice">
You must replace `:CONTAINER` with the available container you are searching in and `:TYPE` with what you are comparing.
</aside>





## Get Product

> Request example

```shell
curl "http://api.pricenometry.com/v1/bestbuy-offers/9071056"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "result": {
    "id": 9071056,
    "container": "bestbuy-offers",
    "name": "Google - Chromecast - Black",
    "social": {
      "facebook_shares": 81,
      "google_shares": 110,
      "twitter_shares": 3,
      "pinterest_shares": 1
    },
    "price": {
      "priceCurrency": "USD",
      "price": 35,
      "original_price": 35,
      "instant_rebate_price": 10.01
    },
    "url": "http://www.bestbuy.com/site/google-chromecast-black/9071056.p?id=1219013308425&skuId=9071056",
    "date": "2016-02-24",
    "open_graph": true,
    "type": "Offer",
    "description": "Google Chromecast: Easily stream your favorite apps and media to your TV via Wi-Fi with Chromecast. Use the included USB cable to plug the Chromecast into your TV, and control streaming content using your compatible smartphone, tablet or computer.",
    "image": "http://pisces.bbystatic.com/image2/BestBuy_US/images/products/9071/9071056_sa.jpg;canvasHeight=210;canvasWidth=210",
    "site_name": "Best buy",
    "schema_org": true,
    "tags": [
      "GOOGLE",
      "Chromecast",
      "H2G2-42",
      "Wireless",
      "Multimedia",
      "Networking"
    ],
    "categories": [
      "TV & Home Theater",
      "TV & Home Theater Accessories",
      "Home Theater Networking"
    ],
    "availability": "InStock",
    "itemCondition": "NewCondition",
    "model": "H2G2-42",
    "sku": 9071056
  }
}
```

Get most up to date Product information by Product id. Default response is JSON, also available in XML using a *.xml extension.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/:ID`

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






## Get Product History

> Request example

```shell
curl "http://api.pricenometry.com/v1/bestbuy-offers/9071056/history"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "result": {
    "id": "9071056",
    "container": "bestbuy-offers",
    "name": "Google - Chromecast - Black",
    "history": {
      "price": {
        "2015-07-26": 29.99,
        "2015-08-02": 35.00,
        "2015-08-16": 29.99,
        "2015-09-27": 27.99,
        "2015-11-01": 29.99,
        "2015-11-15": 24.99,
        "2016-02-21": 35.00
      },
      "facebook_shares": {
        "2015-09-13": 39,
        "2015-09-27": 43,
        "2015-10-04": 54,
        "2015-10-11": 64,
        "2015-11-01": 73,
        "2015-11-08": 74,
        "2015-11-22": 79,
        "2016-02-21": 81
      },
      "google_shares": {
        "2015-07-26": 105,
        "2015-08-02": 107,
        "2015-08-09": 106,
        "2015-08-30": 107,
        "2015-11-08": 108,
        "2015-11-15": 105,
        "2016-02-21": 110
      },
      "total_shares": {
        "2015-07-26": 105,
        "2015-08-02": 108,
        "2015-08-09": 107,
        "2015-08-30": 109,
        "2015-09-27": 110,
        "2015-10-04": 111,
        "2015-10-11": 153,
        "2015-11-01": 162,
        "2016-02-14": 164,
        "2016-02-21": 169
      },
      "twitter_shares": {
        "2015-08-02": 1,
        "2015-08-09": 2,
        "2015-09-13": 3
      }
    }
  }
}
```

Get most up to date Product history by Product id.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/:ID/history`

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




## Get Product News

> Request example

```shell
curl "http://api.pricenometry.com/v1/bestbuy-offers/9071056/news"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "result": {
    "id": "9071056",
    "container": "bestbuy-offers",
    "name": "Google - Chromecast - Black",
    "news": [
      {
        "title": "Black Friday Streaming Devices: Best Deals for Chromecast, Roku, Apple TV and More",
        "description": "Black Friday is nearly upon us, and this year, consumers around the country are once again looking for devices that help them to stream their favorite shows and movies from services like Netflix, Hulu and HBO Now. Whether it's to take a first step ...",
        "image": "http://t3.gstatic.com/images?q=tbn:ANd9GcQgA_iqMsC1sh9Ty4Tii4Qvt8OIhLLIx9MM1vOFdFzoF-Q9Lb3N2S7N1KI",
        "url": "http://variety.com/2015/digital/news/black-friday-roku-chromecast-appletv-firetv-deals-1201647930/",
        "publisher": "Variety",
        "published": "2015-11-25",
        "language": "en",
        "related": [
          {
            "title": "The Best Black Friday Deals on Streaming Devices",
            "url": "http://www.pcmag.com/article2/0,2817,2495664,00.asp",
            "publisher": "PC Magazine",
            "published": "2015-11-25",
            "language": "en"
          },
          {
            "title": "Black Friday guide to streaming media players: the best deals on Apple TV ...",
            "url": "http://qz.com/559344/black-friday-guide-to-streaming-media-players-the-best-deals-on-apple-tv-chromecast-fire-tv-and-roku/",
            "publisher": "Quartz",
            "published": "2015-11-26",
            "language": "en"
          }
        ]
      },
      {
        "title": "Buy Two Google Chromecast in Best Buy Black Friday Sale for $50",
        "description": "The Best Buy Black Friday 2015 Ad was already packed with deals in the initial release. Today Best Buy packed on another 300 Black Friday deals, almost doubling their Black Friday ad. A deal that jumped out already before the new 300 deals is a deal on ...",
        "image": "http://t2.gstatic.com/images?q=tbn:ANd9GcQ5rrhrzMghDz5Ar2p_uJltsNQxJDg0IASUItlHiQMrv3PnMZra9_Cnslg",
        "url": "http://www.i4u.com/2015/11/97969/buy-two-google-chromecast-best-buy-black-friday-sale-50",
        "publisher": "I4U News",
        "published": "2015-11-16",
        "language": "en",
        "related": []
      }
    ]
  }
}
```

Get most up to date Product News by Product id.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/:ID/news`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container
:ID | true | Product ID

<aside class="notice">
You must replace `:CONTAINER` with the available container and `:ID` with the Product ID.
</aside>




## Get Product Videos

> Request example

```shell
curl "http://api.pricenometry.com/v1/bestbuy-offers/9071056/videos"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "result": {
    "id": "9071056",
    "container": "bestbuy-offers",
    "name": "Google - Chromecast - Black",
    "videos": [
      {
        "title": "Google Chromecast HDMI Streaming Media Player ...",
        "description": "http://www.shorti.me/Black-Friday-Deals ◅ check the best deals Google  Chromecast HDMI ...",
        "image": "https://img.youtube.com/vi/OIVcP780JV4/default.jpg?h=90&w=120&sigh=__bm2WSBbFoR43kQp58pd7Miz3sdU=",
        "url": "https://www.youtube.com/watch?v=OIVcP780JV4",
        "length": "1 minute",
        "published": "2015-04-23"
      }
    ]
  }
}
```

Get most up to date Product Videos by Product id.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/:ID/videos`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container
:ID | true | Product ID

<aside class="notice">
You must replace `:CONTAINER` with the available container and `:ID` with the Product ID.
</aside>





## Get Product References

> Request example

```shell
curl "http://api.pricenometry.com/v1/bestbuy-offers/9071056/references"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "result": {
    "id": "9071056",
    "container": "bestbuy-offers",
    "name": "Google - Chromecast - Black",
    "references": [
      {
        "title": "Unlock the Power of Your Chromecast",
        "description": "by Aaron Halbert ISBN: ISBN1494976765",
        "image": null,
        "url": "http://books.google.com/books?id=NyQ_ngEACAAJ&dq=Google+-+Chromecast+-+Black&client=internal-uds&num=8&cd=1&source=uds",
        "length": "44 pages",
        "published": "2013"
      }
    ]
  }
}
```

Get most up to date Product Books or other Reference manuals by Product id.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/:ID/references`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container
:ID | true | Product ID

<aside class="notice">
You must replace `:CONTAINER` with the available container and `:ID` with the Product ID.
</aside>




## Get Product Links

> Request example

```shell
curl "http://api.pricenometry.com/v1/bestbuy-offers/9071056/links"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "result": {
    "id": "9071056",
    "container": "bestbuy-offers",
    "name": "Google - Chromecast - Black",
    "links": [
      {
        "title": "Google Chromecast (2015) review - CNET",
        "description": "Oct 3, 2015 ... The innovative Chromecast might be the ultimate living-room accessory for your \nphone or tablet, but more ... Google Chromecast 2015 (Black).",
        "url": "http://www.cnet.com/products/google-chromecast-2015/"
      }
    ]
  }
}
```

Get most up to date Product Links by Product id.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/:ID/links`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:CONTAINER | true| The available container
:ID | true | Product ID

<aside class="notice">
You must replace `:CONTAINER` with the available container and `:ID` with the Product ID.
</aside>




## Get Product Screenshot Image

> Request example

```shell
curl "http://api.pricenometry.com/v1/amazon-offers/B00DR0PDNE/2015-02-24.jpg"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command redirects to a URL like the one below:

```html
  <html>
    <body>
    You are being
    <a href="https://amazon-screenshots.pricenometry.com/B00DR0PDNE/2015-02-24.jpg?AWSAccessKeyId=AUTO-GENERATED&Signature=AUTO-GENERATED&Expires=24-HOURS">redirected</a>.
    </body>
  </html>
```

Get Product redirect to screenshot image.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/:ID/:SCREENSHOT_DATE.jpg`

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




## Get Product Screenshot

> Request example

```shell
curl "http://api.pricenometry.com/v1/amazon-offers/B00DR0PDNE/2015-02-24"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "response": {
    "status": 200
  },
  "id": "B00DR0PDNE",
  "redirect_url": "https://amazon-screenshots.pricenometry.com/B00DR0PDNE/2015-02-24.jpg?AWSAccessKeyId=AUTO-GENERATED&Signature=AUTO-GENERATED&Expires=24-HOURS"
}
```

Get Product screenshot data. Default response is JSON, also available in XML using a *.xml extension.

### HTTP Request

`GET http://api.pricenometry.com/v1/:CONTAINER/:ID/:SCREENSHOT_DATE`

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





## Search All Products

> Request example

```shell
curl "http://api.pricenometry.com/v1/search/chromecast"
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

Search all availble Products based on a query or key word. Default response is JSON, also available in XML using a *.xml extension.

### HTTP Request

`GET http://api.pricenometry.com/v1/search/:QUERY`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:QUERY | true | What you are searching for

<aside class="notice">
You must replace `:QUERY` with what you are searching for.
</aside>




## Match All Products

> Request example

```shell
curl "http://api.pricenometry.com/v1/match?name=chromecast"
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

Match all Products based on a specific set of known parameters and values. Default response is JSON, also available in XML using a *.xml extension.

### HTTP Request

`GET http://api.pricenometry.com/v1/match`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
results | false | Number of Results you want back (default: 10)
fetch | false | Automatically crawl new data (default: true)
social | false | Automatically fetch new social data (default: false)
url | false | Unique URL for product
date | false | When data was last gathered
id | false | Unique ID for product
tags | false | Tags associated with product
name | false | Unique name of product
description | false | Given description for product
type | false | Product Type
image | false | Unique product image
sku | false | Unique product sku
mpn | false | Unique product manufacturer part number
model | false | Unique product model number
price | false | Price of product at time of sale
original_price | false | Original retail price of the product
facebook_shares | false | Number of times product has been shared on Facebook
google_shares | false | Number of times product has been shared on Google Plus
twitter_shares | false | Number of times product has been shared on Twitter
reddit_shares | false | Number of times product has been shared on Reddit
linkedin_shares | false | Number of times product has been shared on LinkedIn
pinterest_shares | false | Number of times product has been shared on Pinterest
stumbleupon_shares | false | Number of times product has been shared on StumbleUpon
total_shares | false | Number of times product has been shared on Social Media





## All Top Products

> Request example

```shell
curl "http://api.pricenometry.com/v1/top/price"
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
      "id": "B011390PHY",
      "container": "amazon-offers",
      "price": {
        "price": 850000
      },
      "availability": "Only 1 left in stock.",
      "name": "FREAKS 1932 * TOD BROWNING * COMPLETE LOBBY CARD SET * MINT * SUPER RARE!!",
      "url": "http://www.amazon.com/FREAKS-BROWNING-COMPLETE-LOBBY-SUPER/dp/B011390PHY?tag=pricelscom-20"
    },
    {
      "id": "36144922",
      "container": "walmart-offers",
      "price": {
        "maximum_price": 418348.46,
        "minimum_price": 19.99,
        "price": 202462.33,
        "priceCurrency": "USD"
      },
      "availability": "Out of stock",
      "name": "Surya Intersecting Lines Polyester Throw Pillow",
      "url": "http://www.walmart.com/ip/Surya-Intersecting-Lines-Pillow/36144922"
    }
  ]
}
```

Top Products in a container based on a specific set of known parameters and values. Default response is JSON, also available in XML using a *.xml extension.

### HTTP Request

`GET http://api.pricenometry.com/v1/top/:TYPE`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate
:TYPE | true | The Top Type you want to retrieve (example: price, facebook_shares, etc)
results | false | Number of Results you want back (default: 10)
fetch | false | Automatically crawl new data (default: true)
social | false | Automatically fetch new social data (default: false)

<aside class="notice">
You must replace `:TYPE` with what you want compared.
</aside>





## Batch Products

> Request example

```shell
curl "https://api.pricenometry.com/v1/batch"
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
  -H "Content-Type: application/json"
  -X POST -d '{"amazon-offers": ["B00DR0PDNE"], "walmart-offers": ["811571013579"]}'

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
    }
  ]
}
```

Batch Products from any container based on a specific set of known ID's from each seperate container, maximum of 50 ID's total per request. Default response is JSON.

### HTTP Request

`POST https://api.pricenometry.com/v1/batch`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | true | Access token used to authenticate.
