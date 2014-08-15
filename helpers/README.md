# Helpers / Partials


## General Priciciples for Helpers

* DO NOT mix Ruby with HTML
* DO NOT mix HTML in Helper
* avoid using `html_safe`
* it's OK to mix with partials



## General Priciciples for Partials

* using partials to describe a `HTML BLOCK`
* break View Logic with partials for better maintainbility
* avoid query in View
* there's a excetion for `avoid query in View`, if you need to design `select box`, it's better to put condition is partial but not controller
*

