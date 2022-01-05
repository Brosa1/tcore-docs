---
sidebar_position: 2
title: PayloadDecoder
---

# PayloadDecoderPlugin

This Plugin class allows you to decode data after it is retrieved from a bucket.

The flow works as follows:

```shell
Device requests data -------------> PayloadDecoderPlugin -------------> Bucket
```

Once the device sends data, the data is immediately forwarded to the first `PayloadDecoderPlugin` found, which is defined through the `priority` field in the Plugin Settings.

After the first `PayloadDecoderPlugin` resolves a value, the value passes sequentially through all the remaining `PayloadDecoderPlugin` classes.

:::info
The value received in your `PayloadDecoderPlugin` class may have already been parsed by another `PayloadDecoderPlugin` from a different publisher.
:::

## Sample code

```js
const { PayloadDecoderPlugin } = require("@tago-io/tagocore-sdk");

const myDecoderPlugin = new PayloadDecoderPlugin({
  id: "hex-to-number-decoder",
  name: "Hex to Number decoder",
});

// You should decode your data here.
// This example decodes hex values into a numbers.
myDecoderPlugin.onCall = async (data) => {
  if (data) {
    data.value = parseInt(data.value, 16);
  }
};
```
