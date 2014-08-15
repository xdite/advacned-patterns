# Select Helper in View

Generally, we don't encoruge `query` or `ruby condition` in View. you should put logic in `helper` or `controller`.

However, there's a exception.

``` ruby
<%= select_tag :dispatch_zone_select, options_for_select(Zone.active_zones_for_select) %>

```

you can query `Zone.active_zones_for_select` in View. instead of puting in Controller.

### Reasons to do

Because if you put `Zone.active_zones_for_select` in controller, sometimes you need to contaminate many action/controllers to decrease maintainability.
