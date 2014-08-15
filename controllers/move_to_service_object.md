# Move to Service Object

* if you need to do mutiple things in a controller, the best way is wrap to a service object like a vending machine.

(before)

``` ruby
  def create
    @order = current_user.orders.build(order_params)

    if @order.save
      @order.build_item_cache_from_cart(current_cart)
      @order.calculate_total!(current_cart)
      current_cart.clear!
      OrderMailer.notify_order_placed(@order).deliver

      redirect_to order_path(@order.token)
    else
      render "carts/checkout"
    end
  end
```


(after)

```
  def create
    @order = current_user.orders.build(order_params)

    if @order.save

      OrderPlacingService.new(current_cart, order).place_order!

      redirect_to order_path(@order.token)
    else
      render "carts/checkout"
    end
  end
  ```

``` ruby
class OrderPlacingService
  def initialize(cart,order)
    @order = order
    @cart = cart
  end

  def place_order!
    @order.build_item_cache_from_cart(@cart)
    @order.calculate_total!(@cart)
    @cart.clear!
    OrderMailer.notify_order_placed(@order).deliver
  end
end
```
