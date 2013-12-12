AngularJS-Geolocation
=========

An angular.js wrapper around window.navigator.geolocation

Bower
--
This module is available as bower package, install it with this command:

```bash
bower install angularjs-geolocation
```
or

```bash
bower install git://github.com/arunisrael/angularjs-geolocation.git
```

Usage
--
- Add the geolocation module as dependency
- Inject the geolocation service (yes, it has the same name)
- Invoke the getLocation method on the geolocation service to retrieve a promise
- The promise will be resolved with the position returned by window.navigator.getCurrentPosition if the user allows the browser to access their location
- The promise will be rejected if the user rejects location access or the browser does not support it

Example
--
For AngularJS v1.2.4 use the following as an example:
```
angular.module('myApp',['geolocation'])
  .controller('mainCtrl', function ($scope,geolocation) {
    geolocation.getLocation().then(function(data){
      $scope.coords =  {lat:data.coords.latitude, long:data.coords.longitude};
    });
});
```


Error Handling
--
The geolocation module defines a geolocation-msgs constant holding error msgs that are broadcast if the user rejects location access:
```
$rootScope.$broadcast('error',CONSTANTS['errors.location.notFound']);
```

or if the browser does not support geolocation:
```
$rootScope.$broadcast('error',geolocation_msgs['errors.location.unsupportedBrowser']);
```

Testing
--
```
grunt test
```

License
--
MIT
