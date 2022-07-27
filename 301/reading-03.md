# React, the Spread Operator, and Functions

## React List and Keys

1. .map() returns a new array that has been passed through the callback function specified.
2. To loop through an array and display each value in JSX, simply map every value in the array to a new JSX element with the value inside. For example:

```js

let arrayOfValues = [1, 2, 3];

let arrayOfElements = arrayOfValues.map((value) => <p>{value}</p>);

// arrayOfElements now contains JSX paragraph elements with the original values inside.

```

3. Each list item needs a unique key.
4. The purpose of a key is to help React keep track of when elements are created, updated, or deleted.

## The Spread Operator

1. The spread operator is represented by an ellipsis(...). It can be used for many things, including destructuring objects, making copies of arrays, and much more.
2. The spread operator can convert array-like objects to arrays, combine properties between objects, adding to state in react, and adding an item to a list.
3. Example of using the spread operator to combine arrays:

```js
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];

let arr3 = [...arr1, ...arr2];

console.log(arr3) // [1, 2, 3, 4, 5, 6]
```

4. Example of adding an item to an array:

```js
let arr1 = [1, 2, 3];

let arr2 = [...arr1, 4];

console.log(arr2); // [1, 2, 3, 4]
```

5. Example of combining two objects using the spread operator:

```js
let object1 = {foo: true};
let object2 = {bar: false};

let object3 = {...object1, ...object2, fuzz: 0};

console.log(object3); // {foo: true, bar: false, fuzz: 0}
```

## Passing Functions Between Components

1. Writes the function in the parent
2. The increment function allows a `Person` component to increment the counter in the parent's state
3. You can pass the method as props.
4. The child can invoke the method through the props object.
