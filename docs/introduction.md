---
sidebar_position: 1
title: Introduction
slug: /
---

# Introduction

Welcome to TagoCore's Documentation!

## Fast Track

We know your time is valuable, so we'll help you understand TagoCore in 5 minutes! ⏰

### TagoCore

TagoCore is a **free**, **fast**, and **open-source** IoT platform for edge computing that you can use to parse, and analyze the data from your devices!

TagoCore supports all major operating systems, and can be downloaded from our [Downloads page](https://tagocore.com/download).

Once you have [downloaded and decompressed](/download) TagoCore, you can run it by opening a terminal in the folder where `tagocore` is located and typing the following command:

```shell
./tagocore
```

That's it! TagoCore is up and running. ⚡

### Devices

Devices are the link between the data in your TagoCore and your devices in the real world. For a physical device to send data to TagoCore, you must create a new Device in the application. [Learn more about Devices](/device).

### Buckets

Buckets are where the data from your Devices are stored. You may create as many buckets as you wish. [Learn more about Buckets](/bucket).

:::tip
When a Device is created, TagoCore automatically creates a bucket for it with the same name.
:::



### Analyses

Analyses allow you to implement scripts to analyze and manipulate data from any device in real-time. You can combine Analyses with [Actions](/action) to execute an Analysis as soon as an event defined by you happens.

Check out our [Analysis Overview](/analysis) to learn more.

### Plugins

Missing something? Don't worry! With TagoCore you can install plugins from developers directly inside of the application. Our plugins range from **Raspberry Pi GPIO integrations** all the way to **MQTT connections**.

<!-- And if you didn't find what you were looking for in the Plugin Store, you can [create your very own Plugin](/plugins/create) by using our powerful TagoCore SDK. -->
