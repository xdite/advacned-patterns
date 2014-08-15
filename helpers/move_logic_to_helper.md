# Move Logic to Helper

``` rhtml
  <% if current_user && (post.user == current_user || current.user.is_forum_admin? || current.user_is_admin? ) %>
  <%= link_to("Edit", edit_post_path(post) ) %>
  <% end %>
```

## Principles

* If only have "one" condition in view, like `current_user`, just go for it, use in View.
* If you have 2+ conditions in view, extract to customer_helper

### Example

``` rhtml
  <% if can_edit_by?(post, current_user) %>
     <%= link_to("Edit", edit_post_path(post) ) %>
  <% end %>
```
