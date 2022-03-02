---
sidebar_position: 1
title: Overview
slug: /plugins/create/overview
---

# Creating Plugin

:::info
You should use **Node.js version 14.x** or greater to build plugins for TagoCore.
:::

TagoCore Plugins are built using Node.js and the TagoCore Plugin SDK. The easiest way to start creating your plugin is to run `npm init --yes` in your plugin's folder project.

After creating your package.json, you should install the [TagoCore Plugin SDK](https://npmjs.com/package/@tago-io/tcore-sdk) library:

```bash
npm install @tago-io/tcore-sdk
```

After installing the SDK, you are free to start playing around with your Plugin! If you want a quick start, here is a sample plugin that creates a Service Module that logs `Hello World!` when the plugin gets loaded and logs `Goodbye World!` when the plugin gets destroyed:

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


## Package attributes

After generating your package.json, you must add a `tagocore` property to it, this is a sample JSON showing all attributes of the object:

```json
{
  "tagocore": {
    "name": "My Plugin Name",
    "short_description": "Explain what your Plugin does in a few words",
    "full_description": "./README.md",
    "icon": "./assets/icon.png",
    "types": [
      "service",
      "action-type",
      "action-trigger"
    ],
    "permissions": [
      "device",
      "device-data"
    ]
  },
}
```

### name
This property must contain the name of your Plugin. This is the same name that will appear in the Plugin Store when you publish your plugin.

### short_description
Explain in up to 100 characters what your Plugin does.

### full_description
This property should contain a markdown file that will be rendered in the body of your Plugin Configuration. In the markdown file you explain your Plugin and its API in-depth. Developers usually use the `README.md` file in the root of the project.

:::info Good to know
TagoCore doesn't support html in the `full_description` file.
:::

### icon
Set the path of an image file to act as your Plugin's main icon. We recommend you use a `PNG` image for the icon.

### types
This is an array that should contain all [module](#Modules) types used by your Plugin. For instance, if you are using a [Service Module](/plugins/create/service) and a [Payload Encoder Module](/plugins/create/encoder) in your code, you should have an array like this:

```json
["service", "encoder"]
```

Here are all the types of modules:

- Payload Encoder Module: `encoder`
- Service Module: `service`

### permissions
This array specifies which API calls you will be able to make to TagoCore's API via the [core](plugins/create/core) object. For instance, if you wish to create a new [Device](/device) via the `core.createDevice` function, you have need to add the `device` property to this permissions array.

These are all the possibilities for this array:

```json
["action", "analysis", "device", "device-data"]
```

## Modules

In TagoCore Plugins, all functionalities can be added via Modules. We currently offer these modules for you to use in your Plugin:

- [Payload Encoder Module](/plugins/create/encoder);
- [Service Module](/plugins/create/service);

## Using a Module

Once you have defined which modules you are going to use, it's time to actually use them. To create a new module you must require the appropriate module from the `@tago-io/tcore-sdk` package and instantiate them in your code.

After you have instantiated your Module, you can override its functions in order to capture or to react to certain events in the Plugins lifecycle.
