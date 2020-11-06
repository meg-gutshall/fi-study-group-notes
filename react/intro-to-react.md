# Intro to React

> **Z on 10/06/20**

## About React

React is a framework or a JavaScript library, it's **not** a language.

Framework — have very specific ways of coding, have set conventions, upgrades on libraries \(more powerful\), built on unchangeable patterns

Library — have a lot more leeway and options, many ways to do something \(which makes it difficult to learn\), built on patterns that are changeable

### What Is React and Why?

Makes the code repeatable, better organized, and dynamic.

Logic is handled differently. We have components and containers. Components are like partials in Rails — reusable, powerful, etc. but they can re-render themselves, unlike in Rails.

React is great with the single responsibility principle!

React has the concept of a virtual DOM in which it stashes a copy of your DOM tree. It compares the user's actions against the copy in the virtual DOM and then reacts accordingly.

Functionality is no different than in Vanilla JavaScript, it's just _much_ faster.

### Babel and Webpack

#### Webpack

Bundles scripts and minifies them in output. Like our executable file in Ruby. Must use Webpack for React to work --&gt; it allows the import/export function.

#### Babel

A JavaScript compiler that ensures your code is backwards compatible with browsers.

### Other Front End Frameworks

* Angular
* Vue
* Backbone
* Ember
* Svelte
* Express

### Documentation

Source of truth:

{% embed url="https://reactjs.org/" %}

## Starting a React Project

### Creating a React App

Type `npx create-react-app <your-app-name>` in the terminal

**Or** you can type `react.new` in your browser's URL and it will automatically redirect you to a Codesandbox with a React app up and ready to go.

### Walkthrough of a File Structure

React apps are SPAs.

`index.html` is located in the `public` directory.

Imports are relative.

`import React from 'react';` should always be your first line of code.

Every file needs to have _at least one_ export.

