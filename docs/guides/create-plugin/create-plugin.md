---
sidebar_position: 1
title: Create a Plugin
slug: /plugins/create
---

# Create a Plugin

:::info
You should use **Node.js 16.x** to build plugins for TagoCore.
:::

Plugins for TagoCore are built using Node.js. To start building, run this command in an empty folder:

```shell
tagocore plugin-init <name>
```

This command you walk you through creating and building a plugin. It will ask you things such as **name** and **version** of the plugin to build the manifest object inside of package.json.

```js
Name: my-first-plugin
Version: 1.0.0
Author: John Doe
License: MIT
```

Once you set the manifest information of your plugin, the command will create the package.json file, and create a sample application for you to use.
The sample application will contain an index.js file which will look something like this:

```js
// Welcome to Building TagoCore plugins!
// This is a sample application to help you understand how a plugin works.

// This application logs "Hello World!" when the plugin gets loaded,
// and logs "Goodbye World!" when the plugin gets destroyed.

// Feel free to use another Plugin Class, or override the code for this one.

const { ServicePlugin } = require("@tago-io/tagocore-sdk");

const myService = new ServicePlugin({
  id: "hello-world-service",
  name: "Hello World service",
});

myService.onStart = async () => {
  console.log("Hello World!");
};

myService.onDestroy = async () => {
  console.log("Goodbye World!");
};
```

<!-- To understand more about how to customize your plugin, check out [Plugin Classes](/docs/guides/create-plugin). -->
