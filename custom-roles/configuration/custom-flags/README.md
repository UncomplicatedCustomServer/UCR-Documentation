---
icon: tags
---

# Custom Flags

**Custom Flags** are the easiest and most user-friendly way to add more complex custom behaviors to a Custom Role.

Since `v6.0.0` Custom Flags became a more powerful tool as they started supporting **arguments** and developers could finally create their own.

The **Custom Flag** configuration param is a **List** of Custom Abilities.\
Elements inside this List might also require some arguments that can be added like they were an object.

Here's an example of a Custom Flag configuration:

```yaml
custom_flags: 
- CustomScpAnnouncer:
    name: '250'
- DoNotTriggerTeslaGates
```

As you can see the Custom Flag **CustomScpAnnouncer** does require an argument and it's given like it was an object, while the **DoNotTriggerTeslaGates** can work without any argument(s).

Developers can read the development page related to Custom Flags (or Modules) in order to create their one that **can be also used in the YAML configurations!**
