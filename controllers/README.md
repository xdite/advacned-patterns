# Controllers

## General Principles

* method shouldn't longer than 15 - 20 lines
* if you plan to do create / save a record, consider move to model method.
* if you plan to do mulitple things, consider move to a Service Object


## If...

* multiple action have the same code, move to before_action
* multiple controllers have the same before_action, use inheritance.
* multiple controller have the same "method", use Controller Concern


