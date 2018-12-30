# wsproxy.js - A proxy for websockets 

This is a fork from the original repository [wsproxy]( https://github.com/sensepost/wsproxy); on top of the existing 
features, this fork will let you to edit outgoing requests "on the fly".  

## Install
You need to setup your Nodejs environment, in the project directory:
```
git clone https://github.com/tampe125/wsproxy.git
npm install
```

This will install all your dependencies etc.

## Usage
The tool should be easy enough to use,

```
nodejs wsproxy.js
```

## Editing requests
You will have to copy and rename the file `custom_scripts/outgoing.example.js`. You'll see that there are two different
functions being exported: `editTextData` and `editBinaryData`. In those functions you will have to perform your editing logic.

### A quick example
Change the `editTextData` function so it will be something like this:  
```js
exports.editTextData = function (data) {
  data += " edited";

  return data;
};
```

Now attach your proxy and visit the [WebSocket echo server](https://www.websocket.org/echo.html). In the console you'll 
see that every reply from the server has the string ` edited` appended. Since it's just an echo server, returning what you
sent to him, this means that the message you just sent has been modified by our proxy.

[images/websockets_test.png]

## License
WSProxy is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (http://creativecommons.org/licenses/by-nc-sa/4.0/)
