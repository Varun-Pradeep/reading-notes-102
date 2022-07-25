# Intro to React

React is a component based UI library. When used in conjunction with `react-dom`, it can be used to create UI for web apps.

## What is a component?

A component represents a *seperation of concern*, or a logical piece of an application. A component can contain HTML as JSX, CSS, and JavaScript. For example, instead of one massive CSS file, you can have multiple files for each piece of the application. This allowes for easier debugging and the ability to swap and replace components easily. It also allows you to use prebuilt components from elsewhere.

## What are props?

"Props", or properties, are a way to pass data from a parent to a child component. In React, data only flows **one** way, from top to bottom. Props can be used to pass auth status to children, or trigger re-renders when data is changed.
