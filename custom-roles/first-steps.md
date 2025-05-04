---
icon: hand-holding-skull
---

# First steps

With UCR you can create **Custom Roles** for your EXILED server.\
But what's a Custom Role?

## What's a Custom Role?

A Custom Role is a base role with a different behavior and different stats.\
For example a Custom Role can be a Facility Guard with 250HP (instead of the default 100HP) and with 2 First-Aid Kits in the inventory (instead of the default 1).

Custom Roles can also have different stamina, different escaping rules, different AHP (Artificial Health), different item group limitations, different name, different custom info, different spawn point and so on.

With UCR you can customize almost every aspect of a Custom Role through a simple YAML configuration and through simple RA commands.

## Where are the Custom Roles?

Each Custom Role has its personal `.yml` configuration file.\
These files are inside the `.config/EXILED/Configs/UncomplicatedCustomRoles` folder.

**Note:** Every role outside that folder **won't be loaded** as it won't be recognized by the plugin!

### Folder structure

From `v6.0.0` you _can_ create custom folders inside the `UncomplicatedCustomRoles` main folder and they will be loaded.

UCR since `v3.2.0` as a thing called **port-based loading** that loads certain Custom Roles only if the current port of the server is equal to the given value.\
These roles have a custom folder inside the main folder and it's name is equal to the name of the server port.\
For example the roles inside the folder `UncomplicatedCustomRoles/7778` will be loaded **ONLY** if the server is running on the `7778` port and so on.

Because of that **every folder that has as a name an&#x20;**<kbd>**int32**</kbd>**&#x20;WONT BE EVALUATED** as these folders are reserved for the **port-based** loading.

Let's imagine that we start the server on the `8888` port:

```
UncomplicatedCustomRoles/
- custom_role.yml                 // WILL BE LOADED
- MyBeautifulRoles/
  - another_custom_role.yml       // WILL BE LOADED
- 8888/
  - yey_custom_role.yml           // WILL BE LOADED (name of the folder == port)
- 6969/
  - homely_owo.yml                // WONT BE LAODED (name of the folder != port)
- AWA/
  - myRole.yml                    // WILL BE LOADED
  - no_u/
    - anotherRole.yml             // WONT BE LOADED (sub-sub folders are not evaluated)
```

## Where can I take a base Custom Role in order to customize it?

When the plugin starts for the first time it autogenerates two example Custom Role configuration files.\
You can tho generate more example Custom Role configuration files via the `ucr generate` command, but we'll talk about it later!
