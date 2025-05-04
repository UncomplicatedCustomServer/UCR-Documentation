---
icon: person-to-portal
---

# Escape Logic

Customizing the **Escape Logic** of a Custom Role is a very important way to make the users experience even more beautiful.

UCR does provide a powerful tool to decide almost everything about the escape.

## Escape Object

The **Escape** object is a simple Dictionary (object) with a key and a value.\
It should look like this:

```yaml
role_after_escape:
  default: InternalRole Spectator
  cuffed by InternalTeam ChaosInsurgency: InternalRole ClassD
```

## Escape Syntax

The syntax for handling the escape logic is quite complicated but when you'll learn how to use it you'll see that it's very powerful.

As you can see from the example of the YAML every key-value pair represents a different scenario.

### Key

The key represents the condition that you want to handle.\
If the condition is not present the `default` one will be used.

In the condition there are two variable elements: `InternalTeam` and `ChaosInsurgency`.\
The plain syntax is:

```
cuffed by <Group> <Subject>
```

There are two available Groups: `InternalTeam` and `CustomRole`.\
If you put `InternalTeam` you then have to put as the Subject a value of the [Team](../../syntax-notions/enums.md#roletypeid-and-team) [enum](../../syntax-notions/enums.md).\
If you instead put `CustomRole` you then have to put as the Subject the Custom Role Id.

Let's see some examples:

```
cuffed by InternalTeam Scientists
cuffed by CustomRole 2
```

### Value

The value represents the action that the plugin will do to the player.\
The syntax is really clear:

```
<Group> <Target>
```

There are two available groups: `InternalRole` and `CustomRole`.\
If you put `InternalRole` you then have to put as the Target a value of the [RoleTypeId](../../syntax-notions/enums.md#roletypeid-and-team) [enum](../../syntax-notions/enums.md).\
If you instead put `CustomRole` you then have to put as the Target the Custom Role Id.

For example, if we put `CustomRole 2` and the associated condition is true the player will be spawned as the Custom Role with Id=2 when they escape.

Let's see some examples:

```
CustomRole 5
InternalRole ClassD
```

### Logic

Now that we have both the **key** and the **value** if we put them together we have a condition=>action group.

For example, if we have this configuration:

```yaml
role_after_escape:
  default: InternalRole Spectator
  cuffed by CustomRole 5: CustomRole 10
  cuffed by InternalTeam Scientists: CustomRole 9
  cuffed by CustomRole 1: InternalRole ClassD
```

* If we escape **not cuffed** then we will become spectators
* If we escape **cuffed by Custom Role 5** we'll become Custom Role 10
* If we escape cuffed by a member of the **Scientists** team we'll become Custom Role 9
* If we escaped **cuffed by Custom Role 1** we'll become Class-Ds
