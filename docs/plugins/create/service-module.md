---
sidebar_position: 3
title: ServiceModule
slug: /plugins/create/service
---

# ServiceModule

The Service module allows you to run any kind of code once your plugin is loaded.

## How it works

As soon the Plugin is loaded, the `onLoad` function of the module will be invoked. You can override this function to execute your code, such as to start an http server or to run analytics on some data you have stored.

Just like all other modules, the `onDestroy` function will be invoked just before the module is stopped. You can override this function if you wish to clean up your code before the module is destroyed.

## Service status

Besides the default invocations of these functions, they may also be invoked when the user **starts** or **stops** the service in the Plugin Configuration screen via the **Service status** buttons.

The service status will always reflect the current execution status of your service.

<img className="big-image" src="/docs/img/service-status.png" height="50px" />

:::info
The service status is not saved as a setting. If an user stops your service and restarts TagoCore, your module's `onLoad` function will be called normally once your plugin starts.
:::

:::tip Good to know
The `onDestroy` function will never be invoked before the `onLoad`. You can be confident that the code in the `onLoad` function will always be executed first.
:::

## Setup

Setup is the name of object passed to the constructor of the ServiceModule.

Like all other modules, the setup object **must have** an `id` and a `name` property. The setup object may also contain a `configs` property to request configuration parameters to the user. [Learn more about this property](https://npmjs.com/package/express).

## Sample code

This sample starts an http server with [express](https://npmjs.com/package/express). When a `GET /` request is made to the server, the string `Hello World` will be sent back.

```js
const { ServiceModule } = require("@tago-io/tcore-sdk");
const express = require('express');
const app = express();
let server = null;

const myService = new ServiceModule({
  id: "hello-world-service",
  name: "Hello World service",
});

// `onLoad` is used to run your code.
// This function will be called once when your plugin gets loaded.
myService.onLoad = async () => {
  app.get('/', function (req, res) {
    res.send('Hello World');
  });
  server = app.listen(3000);
};

// `onDestroy` is used to clean up your code.
// This function will never be called before `onLoad`.
myService.onDestroy = async () => {
  server.close();
};
```

