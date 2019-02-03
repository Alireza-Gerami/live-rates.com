# Live-Rates.com

[**Live-Rates.com**](https://www.live-rates.com/) is a real-time JSON / XML Webservice & Rest API for forex, commodities and indexes. There is also a [Streaming API](#streaming-api) available for subscribers, starting in 2019.

The rates are updated **every second**.

# Usage

## Web-Service

Get the latest foreign exchange reference rates in JSON format.

```http
GET /rates
Host: live-rates.com
```

Get the latest foreign exchange reference rates in XML format.

```http
GET /rates?rate_format=xml
Host: live-rates.com
```

## API 
(requires authentication)

Get the available currency pairs, commodities & indexes and also when they were last updated

```http
GET /api/rates
Host: live-rates.com
```

Get the latest foreign exchange reference rates for the requested params, in JSON format.

```http
GET /api/price?rate=EUR_USD,EUR_GBP
Host: live-rates.com
```

## Streaming API
(requires authentication)

With streaming API, it's no longer necessary to request for fresh data every second. 
When updated data is retrieved by the main server, it's automatically pushed to client via Web-socket technology (socket.io).

Check the Streaming API [Client Example](https://github.com/Live-Rates/live-rates.com/blob/master/examples/streaming_client.js) to understand how you can use it.

![streaming_api](https://thumbs.gfycat.com/MeatyThatApatosaur-small.gif)


# Cross-Rates

For obvious reasons, Live-Rates don't provide all the thousands of possible cross-rate's combinations directly. All our available rates come directly from providers with real liquidity. If you need to get/calculate a rate not available directly, you can convert it, changing the base currency.

## Example:
MYR/CNY, MYR/GBP or any other cross-rates with base currency MYR are not provided. However that doesn't mean you can't get them. In this case/example, you can directly use the USD/MYR, and then the USD/XXX you want.

{"currency":"USD/MYR","rate":”4.14611}
{"currency":"USD/CNY","rate":”6.8421"}

6.84/4.15 = 1.65 MYR/CNY


## Authentication

We allow up to 3 hits/hour/ip for un-authententicated requests, if you need to make API requests or get live rates updated every second you'll need to [subscribe a licence](https://www.live-rates.com/checkout) and include on your requests the following param:


```http
GET /rates?key=Your key
Host: live-rates.com
```
