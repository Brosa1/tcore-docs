---
sidebar_position: 1
title: PayloadEncoder
---

# PayloadEncoderPlugin

This Plugin class allows you to encode data before it reaches a bucket.

The flow works as follows:

```shell
Device sends data -----> PayloadEncoderPlugin ----> Payload Parser ---> Bucket
```

Once the device sends data, the data is immediately forwarded to the first `PayloadEncoderPlugin` found, which is defined through the `priority` field in the Plugin Settings.

After the first `PayloadEncoderPlugin` resolves a value, the value passes sequentially through all the remaining `PayloadEncoderPlugin` classes.

:::info
The value received in your `PayloadEncoderPlugin` class may have already been parsed by another `PayloadEncoderPlugin` from a different publisher.
:::

## Sample code

```js
const { PayloadEncoderPlugin } = require("@tago-io/tagocore-sdk");

const myEncoderPlugin = new PayloadEncoderPlugin({
  id: "number-to-hex-encoder",
  name: "Number to Hex encoder",
});

// You should encode your data here.
// This example encodes number values into a hex format.
myEncoderPlugin.onCall = async (data) => {
  if (data) {
    const isNumber = !isNaN(data.value);
    if (isNumber) {
      // encodes data.value to a hex format
      data.value = data.value.toString(16);
    }
  }
};
```
