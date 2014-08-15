# Inheritance


``` ruby

class Admin::ProductsController < ApplicationController
  layout 'admin'
  before_filter :login_required
  before_filter :admin_required
end

```


``` ruby

class Admin::OrdersController < ApplicationController
  layout 'admin'
  before_filter :login_required
  before_filter :admin_required
end

```

## Refactor

can be refactor to

``` ruby

class AdminController < ApplicationController
  layout 'admin'
  before_filter :login_required
  before_filter :admin_required
end

```


``` ruby

class Admin::ProductsController < AdminController
end

```


``` ruby

class Admin::OrdersController < AdminController
end

```
