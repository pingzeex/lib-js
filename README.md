# pingzeex: a Node.js javascript library

pingzeex is a simple to use, blazing fast, and thoroughly tested integration platform which helps users to connect and integrate apps , hardware , databases , servers , mircoservices


**Note**: This module does work in the browser. The client in the docs is a
reference to both front end and  back end with the role of a client 
communication.

## Table of Contents

* [Protocol support](#protocol-support)
* [Installing](#installing)
* [API docs](#api-docs)
* [Usage examples](#usage-examples)
  + [Sending and receiving text data](#sending-and-receiving-text-data)
  + [Finding the connection name and rx uid](#finding-the-connection-name-and-rx-uid)
* [Changelog](#changelog)
* [License](#license)

## Protocol support

* **HyBi drafts 07-12** (Use the option `protocolVersion: 8`)
* **HyBi drafts 13-17** (Current default, alternatively option `protocolVersion: 13`)
* **MQTT v3.1.1** (Current default, alternatively option `MQTT v5`)

## Installing

```
npm install --save pingzeex
```

## API docs

## Usage examples

### Sending and receiving text data

```js
const PingzeeX = require('pingzeex');

const app = PingzeeX.connect('123456870'); /* unique configuration key */

app.on("data", function (data) {
  if (data.type === 0) {
    /* 0 = handshake done */
      
   app.send("Hello World !", "echo");

  }
  if (data.type !== 0 ) {
    /* 1 = incoming message */
    console.log(data);
  }
});

/* Error handling */
app.on("error",function(err){

    throw(err)
})

```

### Finding the connection name and rx uid

```js
const PingzeeX = require('pingzeex');

const app = PingzeeX.connect('123456870');

app.on("data", function (data) {
  if (data.type === 0) {
    console.log(this.con_name,this.rx_uid);
  }
});

app.on("error",function(err){

    throw(err)
})

```

## Changelog

We're using the GitHub [releases][changelog] for changelog entries.

## License

[MIT](LICENSE)
