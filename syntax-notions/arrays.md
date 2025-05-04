---
icon: brackets-square
---

# Arrays

Almost every programming language does support **Arrays**: they are a **List** of elements.\
C# does have both **Arrays** and **Lists**: for developers they are NOT the same but for users with YAML they work the same way.\
From now on we'll call them **Lists**.

C# is a **strongly typed language** and because of this every List **must contain only a single, specified type**.

For example, if we create a `List<string>` it can contains only strings, while a `List<int>` can contain only `int32`.

In a list a value can be repeated as much times as you want.

YAML does support two different notation for Lists:

```yaml
list1: [a, b, c]
list2:
- a
- b
- c
```

They are almost the same: the only difference is that the second one does support also objects while the first one doesn't.

If you want to give to YAML a **empty List** then do the following thing: `list3: []`
