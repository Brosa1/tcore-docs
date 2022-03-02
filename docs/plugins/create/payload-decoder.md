---
sidebar_position: 2
title: PayloadDecoder
slug: /plugins/create/payload-decoder
---

# PayloadDecoderModule

This Plugin class allows you to decode data after it is retrieved from a bucket.

The flow works as follows:

```shell
Device requests data -------------> PayloadDecoderModule -------------> Bucket
```

Once the device sends data, the data is immediately forwarded to the first `PayloadDecoderModule` found, which is defined through the `priority` field in the Plugin Settings.

After the first `PayloadDecoderModule` resolves a value, the value passes sequentially through all the remaining `PayloadDecoderModule` classes.

:::info
The value received in your `PayloadDecoderModule` class may have already been parsed by another `PayloadDecoderModule` from a different publisher.
:::

## Sample code

```js
const { PayloadDecoderModule } = require("@tago-io/tcore-sdk");

const myDecoderPlugin = new PayloadDecoderModule({
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
