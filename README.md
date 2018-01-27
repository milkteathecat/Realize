# Realize

A full stack Java web service for users to view nearby events/restaurants, add to favorites and view recommendations.

Using TicketMaster API to find all the event data. (Yelp API implementation to be done.)

Using MySQL/MongoDB to store following data:
* User information: user_id, password, user's favorite items (register/login to be done)
* Event item information: event_id, address, categories, rating, images, url, etc.

Handle three kinds of requests by utilizing RESTful APIs

1. /search?user_id=1234&lat=37.5&lon=-120.5

Search nearby events:
* Create url with lat and lon offered by user and send request to TicketMaster server
* Parse the JSON arrays in response to Java class Item objects, save the item lists to db with user information

2. /history?user_id=1234

View user's favorite events:
* Search user_id from db (search history table if MySQL/search favorite key if MongoDB)
* Get a lists of Item objects, transfer to JSON objects and return

3. /recommendation?user_id=1234&lat=37.5&lon=-120.5

View recommended events:
* Use content-based recommendation 
* Search user_id from db, check categories of user's favorite items
* Create url with lat and lon offered by user as well as favorite categories and send request to TicketMaster server
* Get a lists of events, filter those user saved in history, and rank by distance, then return

The web page designed for the search and recommendation service:
![alt text](https://github.com/milkteathecat/Realize/blob/master/capture.jpg)
