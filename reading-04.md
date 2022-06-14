# Reviewing HTML

## Basics

HTML, or HyperText Markup Language, is an XML-like language used to define the content and structure of a web page. It consists of *tags* that represent pieces of content. For example, this code would represent the title of the web page.
```
<title>My Website</title>
```

An HTML file usually has two sections, the `head` and the `body`. The head represents information not directly intended for humans, but helps search engines and the browser understand what the website is about. The body contains the main content of the page.

## Semantic tags

In HTML, there's a cool tag called `<div>`. It doesn't do anything on its own, but represents its children. Technically, you can use div for basically everything, but it makes it easier to understand and edit a website if you use **semantic tags**. These tags help comunicate what the developer intended that ssection to represent to the browser and other developers. A list, by no means exhaustive, is provided below.

* `<article>`
* `<aside>`
* `<details>`
* `<figcaption>`
* `<figure>`
* `<footer>`
* `<header>`
* `<main>`
* `<mark>`
* `<nav>`
* `<section>`
* `<summary>`
* `<time>`

All of these *could* be replaced by `<div>`, but it makes more sense to use these more specific tags. Also, you may have to mess around with css to get it to behave like some of these semantic tags.
