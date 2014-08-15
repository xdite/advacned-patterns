# Model Concern

if you have the same code in different Model, you can consider use model concern.

For example:



```
class Order

  before_create :generate_token


  def generate_token
    self.token = SecureRandom.uuid
  end
end

```

```
class Recipe

  before_create :generate_token


  def generate_token
    self.token = SecureRandom.uuid
  end
end

```


### Refactor

You can refactor with model concern

``` ruby
module Tokenable
  extend ActiveSupport::Concern

  included do
    before_create :generate_token
  end

  def generate_token
    self.token = SecureRandom.uuid
  end
end

```


```
class Order
  include Tokenable
end

```

```
class Order
  include Tokenable
end

```
