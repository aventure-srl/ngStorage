# webStorage
angular module for simply save data (single values, object, array) into browser local storage for web and mobile app.

Local storage allow to store only string data type. This module allow you to store JSON objects and Array also using serialization. You can store any type of structured data with a single method.

### Add module on your angular app
```javascript
var app = angular.module('myAppName', ['webStorage']);
```

### Using prefix
You can set prefix that will be added before each variable name to distinguish same variable name between more apps.

```javascript
app.config(['$localStorageProvider', function($localStorageProvider){

	/*
	 * Set local storage Namespace
	 */
  $localStorageProvider.setPrefix('myAppName_');

}]);
```
Add prefix is similar to create a "namespace" for your app. If you set prefix, it will be added automatically in all subsequent calls to manage only local storage params in your namespace.

# Get & Set
Inject service in controller and use it.

### Single value
```javascript
app.controller('ExampleCtrl', ['$localStorage', function($localStorage){

  $localStorage.set('key1', 'Hello');
  console.log($localStorage.get('key1'));

}]);
```

### JSON Object
```javascript
app.controller('ExampleCtrl', ['$localStorage', function($localStorage){

  // JSON Object
  $localStorage.set('key2', {title: 'Hello'});
  console.log($localStorage.get('key2'));
  
}
```

### Array 
```javascript
app.controller('ExampleCtrl', ['$localStorage', function($localStorage){

  // Array of Objects
  $localStorage.set('key3', [{title: 'Hello'}, {title: 'World'}]);
  console.log($localStorage.get('key3'));
  
}
```

# Remove
```javascript
app.controller('ExampleCtrl', ['$localStorage', function($localStorage){

  // Remove single key
  $localStorage.remove('key1');
  
  // Remove multiple keys at the same time
  $localStorage.remove(['key2', 'key3']);
  
  // Remove all keys in your "prefix namespace"
  //if you don't declare your personal "prefix" this call will delete all local storage
  $localStorage.clear();
}
```
Attention when using clear() without set prefix namespace. It is very likely that you will lose the data of other applications.