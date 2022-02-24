---
title: Wikipedia's API, and Using 'wikipedia-query' to Fetch Articles
description: This is a post on getting started with the Wikipedia API.
date: 2022-02-24
tags: wikipedia
layout: layouts/post.njk
---

Let's say you want to display information about a company, city, or your favorite food on your website. Of course you could just write it out yourself, but what if something changes or gets updated with better information? You can use Wikipedia's API to find an article from their website using regular search terms. In this blog, we will find out how to do this, but first we will talk about the `fetch()` JavaScript function. I will use my project [here](https://github.com/erikgraybill/ip-project) as an example.

`fetch()` is an asynchronous function, meaning it can execute as other code is running at the same time; it will return whatever data is gathered whenever it can and the rest of the code continues on. It is used for HTTP requests and responses. You can learn more about the function [here](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch). In my example, the fetch function is used to return a JSON response with information about the user's location from [https://freegeoip.app/json/](https://freegeoip.app/json/). Once the function receives the information, it returns it and the code within `.then` executes.
_Example JSON retrieved from fetch()_
```
{
"ip": "192.0.2.1",
"country_code": "US",
"country_name": "United States",
"region_code": "PA",
"region_name": "Pennsylvania",
"city": "State College",
"zip_code": "16803",
"time_zone": "America/New_York",
"latitude": 40,
"longitude": -77,
"metro_code": 574
}
```
From here, my code takes the information from the JSON response and stores it for later use in the Wikipedia query, as seen in this screenshot. _I specifically use city and state for the query._
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dn4bw5lff4kl6rxnhxm9.png)

## MediaWiki API ##
We will begin with looking at the API itself. This API can perform many different actions and be utilized in very specified ways dependent on the use case, but we will focus on the action, origin, and format parameters here. Full documentation of the API can be found [here](https://en.wikipedia.org/w/api.php).

- **origin** sets the originating domain of the information being queried. In my instance, this is set to '*' to signify a non-authenticated request which still works, but some user-specific functions are disabled.
- **action** specifies which action is to be performed. In our case, we will set this to 'query'.
- **format** is self explanatory, and specifies what format the information will be returned as. In my case, it is set to return JSON.

When performing `action=query`, some more parameters can be specified. In my case, I use **prop** and set it to 'extracts' in order to get the plain text of the given page being fetched, as well as **titles** which specifies what the title of the page to be returned. This is set to be the term being queried in `wikipedia-query`.

## wikipedia-query ##
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/na9lsrk4gy8ff6hj8tbz.png) Now it's time to implement the MediaWiki API. The code pictured above is the block within the `wikipedia-query` tag that uses the MediaWiki API. It uses `fetch()` to send a query via the API, and the query has the titles parameter set to a variable. I use three `wikipedia-query` tags to display the city and state, just the city, and just the state of the user using the data that was stored earlier from [https://freegeoip.app/json/](https://freegeoip.app/json/). In the picture below, you can see how the search term is constructed in my code.
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yrfflah5q1fhpxksvhbr.png) So, in this example, three queries are sent to the MediaWiki API: one with title set to State College, Pennsylvania, one set to State College, and one set to Pennsylvania. The following picture shows a portion of what is returned from the MediaWiki API, what isn't shown is just the rest of the article.
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/59j14w9imh9jtjs780x4.png)
_You can see the that 'title' is the search term, and extract is the HTML version of the Wikipedia article for State College, Pennsylvania. The page id is also given._

In summary, my example fetches a JSON response with the user's location information and stores it. The `wikipedia-query` tag invokes the MediaWiki API, takes the search term (in my case, city and state, city, and state in three separate queries), and sets the API 'titles' parameter to that term. The MediaWiki API then sends the query and retrieves the Wikipedia article for the given title (aka search term) in JSON format.

