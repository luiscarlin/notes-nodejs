## Promises

```javascript
// create a defered object
// the deferred object has a promise in it
// you can "resolve" and "reject" the deferred object
var deferred = Promise.defer()

// get the promise from the deferred object
// you can use "then" and "catch" on a promise.
// They will be executed once the deferred object is resolved/ rejected
// this is a callback
var promise = deferred.promise

// this is not triggered until the promise is resolved
// then listener will be executed when deferred obj status is resolved
promise.then((resolvedValue) => { console.log(resolvedVavlue * 10) })

// catch listener will be executed when deferred obj status is rejected
promise.catch((error) => { console.log(`PROMISE CAUGHT AND ERROR: ${error.message}`) })


// now resolve the deferred object
deferred.resolve(17)


// this triggers the promise.then() and runs the callback
// outputs 170


// you can have multiple promises listening for the same deferred object

// instead you could have rejected it (note that once deferred obj status is set, it cannot be changed)
// deferred.reject(new Error("Something went wrong"))
// this will trigger the catch listener and run its callback


// will not be executed until all deferred objects for all promises are resolved/ rejected
Promise.all([promise1, promise2, promise3]).then((valuesArray) => { console.log(valuesArray.reduce((memo, i) => { resturn memo + i}))})
deferred1.resolve(10)
deferred2.resolve(15)
deferred3.resolve(25)

// finally the Promise.all is run by passing the returned values in an array
50

/////////////////////////////////////////////
domainlogic.js

var APIService = require("./APIService")
var loadData = function(endpoint) {
  promise.all([APIService.getData(endpoint1),
               APIService.getData(endpoint2),
               APIService.getData(endpoint3)])
  .then((values) => {

    // do something with values array
  })
  .catch(error) => {
    // handle the error
  }
}

loadData("...")


///////////////////////////////////////////////


class APIService {
  getData(endpoint) {
    var deferred = Promise.defer()
    fetch(endpoint, fetchConfig)
    .then((data) => {
      deferred.resolve(data)
    })
    return deferred.promise
  }
}

module.exports = new APIService


///////////////////////////////////////////////
```
