---
sidebar_position: 3
title: Service
---

# ServicePlugin

This Plugin class allows you to run any kind of code while your plugin is loaded.

Once the Plugin starts, you can override the `onLoad` function of the class in order to perform any type of operation you desire, such as starting a server or running Analytics on data.

To clean up your code, you should override the `onDestroy` function of the class.

## Sample code

```js
const { ServicePlugin } = require("@tago-io/tagocore-sdk");
const express = require('express');
const app = express();
let server = null;

const myService = new ServicePlugin({
  id: "hello-world-service",
  name: "Hello World service",
});

// `onDestroy` is used to run your code.
// This function will be called once when your plugin gets loaded.
myService.onStart = async () => {
  app.get('/', function (req, res) {
    res.send('Hello World');
  });
  server = app.listen(3000);
};

// `onDestroy` is used to clean up your code.
// This function will never be called before `onStart`.
myService.onDestroy = async () => {
  server.close();
};
```

