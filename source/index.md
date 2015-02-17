---
title: Pricels.com API Documentation


toc_footers:
  - <a href='http://pricels.com'>Get a Access</a>
  - <a href='http://pricels.com'>Get some help</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>
  - <p>&#169; 2015 Pricels.com, Inc. San Diego, CA</p>

includes:
  - apiv1
  - changelog
  - errors
  - terms

search: true
---

# Introduction

Welcome to the Pricels.com API documentation! Pricels (pronounced Price-Less) is by providing real time data to our customers, through our system you will be able to receive daily updates on any price changes, product promotions and updates for you or your competitor’s products across hundreds of websites. Our entire system is automated so there is no waiting or combing through raw data to find the nuggets of information needed. We’ve scaled our technology to provide you with up to the minute real time intelligence as well as trends and forecasts that you can use from real daily available data, not guess work. Pricels.com will change the way you research.

The API is RESTful and enables getting pricing data on [Pricels.com](http://pricels.com) and it's properties. The API also allows you to check the status and map your pricing data to our database as well as retrieve all your pricing data within our system.

Sample code is currently available as cURL in the dark area to the right. Requests and responses are all in JSON.

The API base url is: **https://api.pricels.com/v1/**

The API is versioned, the current version is 1. This is designated in the url path with /v1

If you have any question please visit [our support pages](http://pricels.com).


# Authentication

> To set authorization, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl http://api.pricels.com
  -H "Authorization: Token token='YOUR-ACCESS-TOKEN'"
```

> Make sure to replace `YOUR-ACCESS-TOKEN` with your API access key.

Pricels uses API keys to allow access to the API. You can get an account by contacting us.

The Pricels API expects for the API key to be included in all API requests to the server. The API key can be passed either as a parameter like the following:

`access_token=YOUR-ACCESS-TOKEN`

Or in a header that looks like the following:

`Authorization: Token token="YOUR-ACCESS-TOKEN"`

<aside class="notice">
You must replace `YOUR-ACCESS-TOKEN` with your API key.
</aside>

# Product Data Types

> Sample JSON Payload:

```json
{
  "url": "http://www.amazon.com/Google-Chromecast-Streaming-Media-Player/dp/B00DR0PDNE",
  "date": "2015-02-10",
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
  "screenshot": "B00DR0PDNE/2015-02-10.jpg",
  "price": "31.78",
  "original_price": "35.00",
  "facebook_shares": 48466,
  "google_shares": 5803,
  "twitter_shares": 174,
  "reddit_shares": 144,
  "linkedin_shares": 358,
  "pinterest_shares": 106,
  "stumbleupon_shares": 23,
  "total_shares": 55074
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
total_shares | Number of times product has been shared on Social Media
