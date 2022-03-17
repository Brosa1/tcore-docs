
## Modules

Modules are JavaScript classes that allow you to add a specific functionality for your Plugin. Your Plugin should contain at least
one module.

We currently offer these modules for you to use in your Plugin:

- [Payload Encoder Module](/plugins/create/encoder);
- [Service Module](/plugins/create/service);
- [Action Trigger Module](/plugins/create/action-trigger);
- [Action Type Module](/plugins/create/action-type);
- [Database Module](/plugins/create/database);

## Core

The `core` object allows your plugin to interact with data in TagoCore. By using the functions provided by this object
your plugin can create [Devices](/device), update [Actions](/action), delete [Analyses](/analysis), and much more.

To learn more about the `core` object, click [here](/plugins/create/core).

## Plugin Storage

Your plugin has the ability to save data in a key-value database via the `pluginStorage` object. You can use this object
to save information for future use.

To learn more about the `pluginStorage` object, click [here](/plugins/create/core).

## Plugin Storage

Your plugin has the ability to save data in a key-value database via the `pluginStorage` object. You can use this object
to save information for future use.

To learn more about the `pluginStorage` object, click [here](/plugins/create/core).

## Helpers

You plugin has access to helper functions via the `helpers` object. Click [here](/plugins/create/helpers) to understand
more about this object. 
