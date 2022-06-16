# Programming in JavaScript

## Functions

Functions in JavaScript are declared with the `function` keyword. They can accept any number of argument and any type. They can also return a value for further use. Anything the function does on its own is called a **side-effect**. This is an action that doesn't process information or contribute to the return value. For exampe, `console.log` prints something out as a side-effect. It doesn't actually return anything back to the program that executed it.

## Operators

There are 2 main types of operator, **unary** and **terenary**. Some unary operators are `+`, `-`, `++`, `*`, and `=`. These all modify the value of an expression. Just like in math, you can use parenthesis to specify which operation occurs first. The main terenary operator is a basically a condensed if-else statement. It's considered bad practice to use these, because it makes code hard to read and debug. For example:

```js
if (thing === that) {
    console.log("Thing is equal to that");
} else {
    console.log ("Thing is not equal to that");
}
```

Now in terenary:

```js
thing === that ? console.log("Thing is equal to that"); : console.log("Thing is not equal to that");
```

Both are functionally the same, but the first one is easier to understand.
