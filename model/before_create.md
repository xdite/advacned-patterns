# before_create

ActiveRecord has `before_create`, `before_update`, `before_save`, `before_xxxx`, and also have `after_create`, `after_xxxx` ....

But this is ONLY suit for `modifying it self`-like behavior.

Fore example:

( OK )

```
class Order

  before_create :generate_token


  def generate_token
    self.token = SecureRandom.uuid
  end
end

```

( !!! DONT do this !!!)

```
class Order

  after_create :send_place_order_email


  def send_place_order_email
    OrderMailer.send_place_order_message(order).deliver
  end
end

```

