# Configify
Browserify transform for node-config (aka. config) library

### Example
**Gruntfile.js** (alternatively, you can put the transform into your `package.json` file)
```js
var configify = require('node-configify');
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
For security purposes, only the `Client` level config properties can be accessible from client-side code (which is bundled by browserify)
