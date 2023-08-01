# node-osc

A very basic [Open Sound Control](http://opensoundcontrol.org/introduction-osc) client. Heavily inspired by [pyOSC](https://trac.v2.nl/wiki/pyOSC).

Install using npm

```
npm install node-osc
```

## ⚠️ Experimental ⚠️

This is an experimental ESM version of node-osc make sure to run node with the `--experimental-modules` flag. This version require at minimum Node.js 13.2.0

## Example

### Sending OSC messages:

```js
import { Client } from 'node-osc';

const client = new Client('127.0.0.1', 3333);
client.send('/oscAddress', 200, () => {
  client.close();
});
```
  
### Listening for OSC messages:

```js
import { Server } from 'node-osc';

var oscServer = new Server(3333, '0.0.0.0');

oscServer.on('message', function (msg) {
  console.log(`Message: ${msg}`);
  oscServer.close();
});
```

### Legacy API

This just works due to conditional exports, isn't that cool!

```js
const { Client, Server } = require('node-osc');

const client = new Client('127.0.0.1', 3333);
var server = new Server(3333, '0.0.0.0');

server.on('message', function (msg) {
  console.log(`Message: ${msg}`);
  server.close();
});

client.send('/hello', 'world', (err) => {
  if (err) console.error(err);
  client.close();
});
```

## License

LGPL.  Please see the file lesser.txt for details.
