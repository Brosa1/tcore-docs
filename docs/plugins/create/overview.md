---
sidebar_position: 1
title: Introduction
slug: /plugins/create
---

# Creating Plugins

Plugins are programs or applications created by the community and TagoIO that extend the functionality of TagoCore.

Like TagoCore itself, Plugins are built using Node.js. You’ll need an understanding of **JavaScript** and Node.js to
develop plugins. You should take a look at our [Prerequisites](/plugins/create/prerequisites) before starting.

The easiest way to start creating your plugin is by running the following commands in an empty folder:

```bash
npm init --yes
npm install @tago-io/tcore-sdk
```

By running those commands, a new project will be created and the [TagoCore Plugin SDK](https://npmjs.com/package/@tago-io/tcore-sdk) will be installed.

Now you are free to start playing around with your Plugin! If you want a quick start, here is a sample file that creates a Service Module logging `Hello World!` when the plugin gets loaded and logging `Goodbye World!` when the plugin gets destroyed:

```js
// Welcome to Building TagoCore plugins!
// This is a sample application to help you understand how a plugin works.

// This application logs "Hello World!" when the plugin gets loaded,
// and logs "Goodbye World!" when the plugin gets destroyed.

// Feel free to use another Plugin Class, or override the code for this one.

const { ServiceModule } = require("@tago-io/tcore-sdk");

const service = new ServiceModule({
  id: "hello-world-service",
  name: "Hello World service",
});

service.onStart = async () => {
  console.log("Hello World!");
};

service.onDestroy = async () => {
  console.log("Goodbye World!");
};
```

## Manifest

After generating your package.json, you must add a `tagocore` property to it to declare the manifest of the Plugin.
Read more about it [here](/plugins/create/manifest).

## Modules

In TagoCore Plugins, all functionalities can be added via Modules.

We currently offer these types of Modules for you to use in your Plugin:

- [Payload Encoder Module](/plugins/create/encoder) - To encode data before reaching a Bucket;
- [Service Module](/plugins/create/service) - To create a service that runs code;
- [Action Trigger Module](/plugins/create/action-trigger) - To create a new trigger for Actions;
- Action Type Module - To create a new type for Actions;
- Database Module - To create a database that will save TagoCore data.

## Using a Module

Once you have defined which modules you are going to use, it's time to actually use them.
To create a new module you must require the appropriate module from the `@tago-io/tcore-sdk`package and instantiate
them in your code.

After you have instantiated your Module, you can override its functions in order to capture or to react to certain
events in the Plugins lifecycle.
