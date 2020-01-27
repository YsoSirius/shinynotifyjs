# Bringing `notifyjs` in Shiny 

## About 

`notifyjs` is an open source JavaScript library designed to create custom notification boxes, released under the MIT License. 

> Notify.js is a jQuery plugin to provide simple yet fully customisable notifications. 

<https://notifyjs.jpillora.com/>

## Our goal for today 

Bring `notifyjs` to Shiny

## Step by step

### Create a `{golem}` app

### Download `notifyjs` in the app

+ Should go into `app/inst/www`

### Add to your app 

+ Link the script to the app in `R/app_ui.R`, in the `golem_add_external_resources`

> Use a `tags$script` or create an `htmlDependency`

### Try it by adding an `onclick` alert on a button
 
### Create a custom handler that takes a text as input and show a success alert with the text in it

### Create a function that can call this custom handler 

### Create more custom alerts using the `notifyjs` options 

> See "Custom Styling Guide" at https://notifyjs.jpillora.com/
