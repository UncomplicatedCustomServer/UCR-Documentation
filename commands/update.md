---
icon: page-caret-up
---

# Update

Since `v7.0.0` and the [Compatibility](../custom-roles/compatibility.md) update UCR does support also roles from the previous versions (starting from `v6.0.0`).

These roles are loaded by the plugin with some limitations as they are not updated and some new configuration parameters might not be included in the previous versions.

UCR does load them **without editing the file**: if you want your roles to get updated you can use this command - the file will be modified but every old value will be still here.\
You'll just have to configure the new ones and nothing more.

### Syntax

```
ucr update <Custom Role Id / all>
```

### Permission

```
ucr update
```

### Description

Updates a Custom Role configuration file with the newest version of the role, keeping every configuration parameter as-it-is.
