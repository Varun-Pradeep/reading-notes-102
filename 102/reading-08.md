# Assignment vs Equality and Loops

## Assignment vs Equality

In math, the = sign means that both sides of the equation will always be equal. It's a given. Unfortunately, in programming languages the = sign means something comepletely different. Consider the following code:

```js
let foo = 4;
```

In english, instinctively we would say it as "Foo equals 4". However, it really is "Set foo to 4" or "Foo is 4". Foo is **not** equal to 4, because foo in the future might be something else. All we are doing is setting foo to 4 right now. There is no guarantee that foo will always be 4. This comes into play when we write an if-statement:

```js
if (foo = 4) {
    console.log("Foo is equal to 4.");
}
```

At first glance, it seems ok, but what the if statement is really doing is setting foo to 4, even if it wasn't 4 before. An assignment expression always returns true, so the if statement will still run even if foo is not 4. What we should do then is **check for equality**, not assign a value. We can do this with the `==` or `===` operator. `==` checks for equality while preforming type coercion, while `===` checks if the variable is the value, **and** the type of the value.
