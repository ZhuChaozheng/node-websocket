# Node.js Websocket Server 

This Node application perioducally receives JSON data from another web application, and serves it to clients connected to it.

# Running Locally

Install ZMQ first

```bash
brew install zeromq
```
Alternatively: http://zeromq.org/intro:get-the-software

``` bash
sudo npm install
node --harmony server.js
```

Module versions might be old when you install this application, so especially if you get node-gyp compilation errors after installing modules, try updating module versions of related packages on package.json

## How it works

Please see [node-fetcher](https://github.com/denizozger/node-fetcher) and [node-dataprovider](https://github.com/denizozger/node-dataprovider) implementations too, all three applications work together - although not necessarily.

1. A client connects to the application. ie. ws://node-websocket/some-key
2. App checks if it has some-key's data on memory
3. If some-key's data is on memory already, it serves it to connected client
4. If some-key's data is not found, then requests it with via a socket from a specific server, ie. [node-fetcher](https://github.com/denizozger/node-fetcher)
5. Waits to receive data for some-key, over a socket. When data is received, transmits it to clients who are connected via some-key.

Go to [localhost:5000/?test1](localhost:5000/?test1) for a demo
  
When you have all three applications, you should start node-socketio as:

``` bash
PORT=5000 node --harmony server.js
```

[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/denizozger/node-websocket/trend.png)](https://bitdeli.com/free "Bitdeli Badge")
 
