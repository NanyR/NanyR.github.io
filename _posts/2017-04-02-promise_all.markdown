---
layout: post
title:  "PROMISE ALL"
date:   2017-04-02 15:48:19 -0400
---



Ever since we started learning Javascript and AJAX we have been hearing more and more about the promise object which
"represents a value which may be available now, or in the future, or never" (Mozilla Developer Network). Promises are good when dealing with asynchronous functionalities. jQuery AJAX requests and fetch requests always return a promise, or a 'thenable' object which essentially passes on the data returned from the request as an argument to a resolve function, unless some error occured in which case a reject function is called instead. 
For our API JS app, my group and I were working with google maps to render some results from an API call on a map based on current user location. Basically we had a function to get the geolocation of the user which needed to be called before the map was rendered on the page. At the same time, we had an API call running to get some data to be rendered on the map. We kept getting error messages on page load about undefined variables since in order to render our map we needed a "center location" which was the return value from our geolocation function. All of these functions were being called on document ready.
The solution was to make these functions return a promise and that way have better control of the order in which each one executes. Here is an example of how we created a promise out of our function to get the location of the user:


```
let currentLocationPromise = getLocation()

function getLocation(){
    return new Promise(function(resolve, reject) {
        navigator.geolocation.getCurrentPosition(function(position){
          let uluru = {lat:position.coords.latitude , lng:position.coords.longitude}
					//fulfill the promise
          resolve(uluru)
        })
  }
```

getLocation() returns a new promise object so now currentLocationPromise is a 'thenable' object. This led us to Promise.all(). The promise object has built-in properties and methods ( .all() being one of them). Promise.all takes an array of promises and it returns a single promise (in the form of an array) once all promises are resolved. This promise array consist of the return values of each promise. We basically passed all of the promises we needed to work with ( current location, google map, and our API call) to Promise.all, ensuring that we would have all 3 of these ready so that the map could render with its current location and then, that we would have the map ready to render the data from our API call :

```
Promise.all([mapPromise, fluPromise, currentLocationPromise])
  .then(([map, fluData, currentLocation]) => {
    let $tweets = $('#tweets')
    let $map = map
    let fluController = new FluController(fluData, $map, $tweets, currentLocation)
  })
```

The biggest take away from this learning experience was that you can create promises out of functions that do not involve AJAX calls, this is useful especially when dealing with asynchronous operations to coordinate flow of the program since it essentially promises some outcome that you can count on to say: this is what happens after this step is done. 
