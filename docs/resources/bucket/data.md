---
sidebar_position: 2
title: Data
slug: /bucket/data
---

# Bucket Data

[Buckets](/bucket) are resources that store data points, and these data points have a specific JSON structure. Every time new data points are sent to the Bucket, TagoCore validates the data point to make sure it has the correct JSON structure.

The JSON of a data point has the same structure as defined in our [TagoIO Cloud](https://api.docs.tago.io/#41e953a9-8b0c-4166-aa0f-1db3596b02f7) platform, which is as follows:

```json
{
  "origin": "61be276db205c10019e6a218",
  "variable": "temperature",
  "value": 100,
  "time": "2022-01-01T12:00:00Z",
  "unit": "F",
  "serie": "123456",
  "metadata": {},
}
```

For more information on other common specifications, check out [API Overview](https://help.tago.io/portal/en/kb/articles/31-api-overview#Security).
