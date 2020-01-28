# Bringing `notifyjs` in your golem app 

## Notes 

### Creating a custom JavaScript handler

``` r
golem::add_js_handler("name")
```

or add 

```
$( document ).ready(function() {
  Shiny.addCustomMessageHandler('fun', function(arg) {
    
  })
});
```

In `inst/app/www/handler.js`

### Link in your app 

In `R/app_ui.R` : 

```
golem_add_external_resources <- function(){
  
  addResourcePath(
    'www', system.file('app/www', package = 'nineties')
  )
  
  tags$head(
    golem::activate_js(),
    golem::favicon(), 
    tags$script(src="www/handlers.js")
  )
}
```

### Calling custom handler

From the server side: 

```r
session$sendCustomMessage("fun", arg)
```

__Good practice__

```
$( document ).ready(function() {
  Shiny.addCustomMessageHandler('fun', function(arg) {
    arg.this + arg.that
  })
});
```

Call them with 

```{r, eval = FALSE}
session$sendCustomMessage(
  "fun", 
  list(
    this = 40, 
    that = 42
  )
)
```

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

+ `pop_succes(text)`
+ `pop_error(text)`
+ `pop_info(text)`
+ `pop_warn(text)`
+ `pop_succes(text, position)`
+ `pop_error(text, position)`
+ `pop_info(text, position)`
+ `pop_warn(text, position)`
+ `pop_succes(text, autoHide)`
+ `pop_error(text, duration)`
+ `pop_info(text, clickToHide)`
