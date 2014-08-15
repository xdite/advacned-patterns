# Move to model

* if you need to modify objects in controller, if actions is longer than > 5 lines, and clear can't see it's purpose. you should wrap into model as a method.



( Before )

``` ruby
def create
  @order = current_user.orders.build(order_params)

  if @order.save
    current_cart.items.each do |cart_item|
      item = items.build
      item.product_name = cart_item.title
      item.quantity = 1
      item.price = cart_item.price
      item.save
    end

    @order.total = current_cart.total_price
    @order.save

    redirect_to account_path
  else
    render :new
  end
end

```

( After )

``` ruby

class Order < ActiveRecord::Base

  has_many :items, :class_name => "OrderItem", :dependent => :destroy

  def build_item_cache_from_cart(cart)
    cart.items.each do |cart_item|
      item = items.build
      item.product_name = cart_item.title
      item.quantity = 1
      item.price = cart_item.price
      item.save
    end
  end

  def calculate_total!(cart)
    self.total = cart.total_price
    self.save
  end
end

```


``` ruby
def create
  @order = current_user.orders.build(order_params)

  if @order.save
    @order.build_item_cache_from_cart(current_cart)
    @order.alculate_total!(current_cart)
    redirect_to account_path
  else
    render :new
  end
end

```
