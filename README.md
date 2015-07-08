# Configify
Browserify transform for [node-config](https://github.com/lorenwest/node-config) library

### Install
```
npm install config-browserify
```

### Example
### Setup (via Grunt OR package.json)
**Gruntfile.js**
```js
var configify = require('config-browserify');
// ...
{
    // ...
	browserify: {
		options: {
			transform: [configify]
		}
	}
	// ...
}
```
**package.json**
```js
{
  "name": "mymodule",
  "browserify": {
    "transform": "config-browserify"
  }
}
```

### Usage
**ClientSide.js** (which will be bundled by browserify)
```js
var config = require('config');
global.window && console.log(config.get('Client.testProperty')); // prints `hello!`
```

**config/default.json**
```js
{
  "Client": {
  	"testProperty": "hello!"
  }
}
```

#### Important 
- For security purposes, only the `Client` level config properties can be accessible from client-side code (which is bundled by browserify)
- For support for server-side rendering frameworks, there is no support for `watchify` at the moment. The entire app must be restarted in order to get config properties which were modified since the server started.