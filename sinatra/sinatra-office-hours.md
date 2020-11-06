# Sinatra Office Hours

> **Howard DeVennish**  
> Email: [howard@flatironschool.com](mailto:howard@flatironschool.com)  
> GitHub: [https://github.com/howardbdev](https://github.com/howardbdev)

## General

* erb interpolation is `<%= %>`
  * Use the ternary operator

## Application Controllers

* Each controller action block is a method
* Everytime we fire a redirect, a brand new instance of our controller class will be created and initialized
  * Only when we render, do instance variables make it from the controller to the view page

## Sessions

* Does the user exist and have the correct credentials?
  * `||=` means “if what’s on the left side doesn’t already exist, do what’s on the right side”
* Take the current user and turn it into a boolean by adding `!!` in front of it
* Recommend using a sessions controller → contains the operations of logging in and out

## Helper Methods

* If used by one controller, put them in that controller
* If used by multiple controllers or views, write them into the application controller
* **Separation of concerns**

## Flash Messages

* Use `gem 'sinatra-flash'`
* Shows the user when something worked or didn’t work
* Only works when the controller action ends in a redirect and only survives one HTTP request

## Models vs. Classes

* Models are used to represent data from a database
* In Ruby, a class is a specific data structure
* **Ruby is a class-based language**
* “Model” is more of a generic term

## **Sinatra Project Example**

{% embed url="https://github.com/howardbdev/sinatra-journal-app" %}

