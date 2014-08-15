# Mix Helper with Partial

## Examples you shouln't use helper

``` ruby
def render_post_title(post)
  str = ""
  str += "<li>"
  str += link_to(post.title, post_path(post))
  str += "</li>"
  return raw(str)
end
```

The reason you shouln't do it because `raw` & `.html_safe` will bypass Rails anit-XSS protection. And cause biger problem


## Principles

If these appears in codebase, it means you're doing it wrong

* `raw` or `.html_safe`
* nested  `content_tag`
* pure `HTML` in helper


## Examples

you should refactor above code to this one

``` ruby
def render_post_title(post)
  render :partial => "posts/title_for_helper", :locals => { :title => post.title }
end
```

