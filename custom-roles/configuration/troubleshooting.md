---
icon: bullseye-arrow
---

# Troubleshooting

**UncomplicatedCustomRoles** is both a simple and a complex product and errors can happen.\
Here you'll be guided on how you should find, handle and fix problems with this powerful product.

## YAML Error

It's really easy to do something wrong in a file configuration and the plugin will make sure you'll see it by throwing in the console a **YAML Error** that should look something like this:

```
[2025-01-17 18:23:07.434 +01:00] [ERROR] [UncomplicatedCustomRoles] Failed to parse C:\Users\piwnica\AppData\Roaming\EXILED\Configs\UncomplicatedCustomRoles\7777\dfds.yml. YAML Exception: (Line: 48, Col: 7, Idx: 989) - (Line: 48, Col: 8, Idx: 990): Exception during deserialization.
```

These errors **are not a plugin bug** but they are caused by an **error in the YAML syntax of one or more of your Custom Roles**!

Remember always to double-check the syntax before and after asking for support on our Official Discord server!

**Note:** online YAML validators MIGHT NOT WORK because they check only for the syntax and not for the type consistency!

## Generic Error

Sometimes you can encounter a "generic error": it's an error thrown by UCR who's **NOT** a YAML error.\
In this case you can consider the error a bug and you **must report it** on our official Discord server in order to allow us to patch it.

Remember that **after you encounter the error you should do the command** `ucrlogs` **and send the Id with the bug report in order to allow us to work even faster!**
