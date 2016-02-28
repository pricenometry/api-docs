---
title: Pricenometry API Documentation


toc_footers:
  - <a href='http://about.pricenometry.com/'>Blog</a>
  - <a href='http://about.pricenometry.com/what-we-do/'>What We Do?</a>
  - <a href='http://about.pricenometry.com/get-access/'>Get API Access</a>
  - <a href='http://about.pricenometry.com/get-access/'>Get Customer Support</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>
  - <p>&#169; 2015 Pricenometry, Inc. San Diego, CA</p>

includes:
  - apiv1
  - changelog
  - errors
  - terms

search: true
---

# Introduction

Welcome to the Pricenometry API documentation! We provide real time data to our customers. Through our system, you will be able to receive daily updates on any price changes or product promotions for your product, a competitor’s product or a product you are interested in as a consumer across hundreds of websites. Our entire system is automated so there is no waiting or combing through raw data to find the pricing information you need. We've scaled our technology to provide you with up to the minute real time intelligence as well as trends and forecasts that you can use from real daily available data, not guess work. We will change the way you research product pricing.

The API is RESTful and enables gathering pricing data on [Pricenometry.com](http://pricenometry.com) and it’s properties. The API also allows you to check the status of a product and map your pricing data to our database as well as retrieve all your pricing data within our system.

Sample code is currently available as cURL in the menu to the right. Requests and responses are all in JSON.

The API base url is: **https://api.pricenometry.com/v1/**

The API is versioned, the current version is 1. This is designated in the url path with /v1

If you have any question please visit [our support pages](http://pricenometry.com).


# Authentication

> To set authorization, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl http://api.pricenometry.com
  -H "Authorization: Token token=YOUR-ACCESS-TOKEN"
```

> Make sure to replace `YOUR-ACCESS-TOKEN` with your API access key.

We use API keys to allow access to the API. You can get an account by contacting us.

The API expects for the API key to be included in all API requests to the server. The API key can be passed either as a parameter like the following:

`access_token=YOUR-ACCESS-TOKEN`

Or in a header that looks like the following:

`Authorization: Token token=YOUR-ACCESS-TOKEN`

<aside class="notice">
You must replace `YOUR-ACCESS-TOKEN` with your API key.
</aside>

# Product Data Types

> Sample JSON Payload:

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

Pricing data is made up of different pieces of data. These are the excepted base record data for a product. These should be sent in the JSON payload. These are all optional except where requests require a particular parameter. You may also add in any data that is not included specifically here, label the data type appropriatly, we will accept any data you would like to send.

### Data Types

Data Type | Description
--------- | -----------
url | Unique URL for product
date | When data was last gathered
id | Unique ID for product
tags | Tags associated with product
name | Unique name of product
description | Given description for product
type | Product Type
image | Unique product image
sku | Unique product sku
mpn | Unique product manufacturer part number
model | Unique product model number
screenshot | Screenshot taken at the time data was collected
price | Price of product at time of sale
original_price | Original retail price of the product
facebook_shares | Number of times product has been shared on Facebook
google_shares | Number of times product has been shared on Google Plus
twitter_shares | Number of times product has been shared on Twitter
reddit_shares | Number of times product has been shared on Reddit
linkedin_shares | Number of times product has been shared on LinkedIn
pinterest_shares | Number of times product has been shared on Pinterest
stumbleupon_shares | Number of times product has been shared on StumbleUpon
