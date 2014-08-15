# Pre-decorate with Helper

When we design application, some columns are frequently used, and decoreated with styles. like `@topic.content`.

from

``` rhtml
   <%= @topic.content %>
```

to

``` rhtml
  <%= simple_format(@post.content) %> %>
```

then

``` rhtml
  <%= truncate(simple_format(@post.content), :lenth => 100) %>
```

then

``` rhtml
   <%= auto_link(truncate(simple_format(@post.content), :lenth => 100)) %>
```

## Principles

* If you know this column "might" be extend many times in future, you should pre-decorate this first by wraping it to helpers at `very first beginning`.

( When you need to use this 2nd time, it's might be a good timing to wrap it )



``` rhtml
   <%= render_topic_content(@topic) %>
```


Afterwards, you can extend it easily.

