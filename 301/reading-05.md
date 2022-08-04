# Thinking in React

1. The single responsibilty principle means that each component in react should only manage one part of the UI, but it should do it completely.
2. It means that you build out the UI with plain HTML elements with no interactivity first, and then add the props and data to it.
3. You need to add interactivity and dynamic content.
4. State is managed within the component, and triggers re-renders when it changes. Props are passed down.
5. State should be owned by the highest common component of all the components that need the state in question.

## Higher Order Functions

1. Higher order functions are functions that modify or create other functions. (Inception time)
2. Line 2 is returning a new arrow function that compares the parameter n to the parameter to the new function.
3. Map and Reduce operate by taking in a callback and using it to modify the given array.
