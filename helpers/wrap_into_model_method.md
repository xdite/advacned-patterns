# Wrap into model method

Sometimes, we will write this kind of code:

``` ruby
def render_comment_author(comment)
  if comment.user.present?
    comment.user.name
  else
    comment.custom_name
  end
end
```

The issues here are:

* Ask, Not Tell
* this is Model's responsibility


## Refactor

(Helper)

``` ruby
def render_comment_author(comment)
  comment.author_name
end
```

(Model)

``` ruby
class Comment < ActiveRecord::Base
  def author_name
    if user.present?
      user.name
    else
      custom_name
    end
  end
end
```
