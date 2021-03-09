---
title: "Tests & Debugging"
tag: mixd
published: true
---
This page should not be linked from anywhere.

## Link Tests
Here are some [link](https://jekyllrb.com/docs/liquid/tags/#link) examples:
* [Link to a document]({% link /intangible.md %})
* [Link to a post]({% post_url 2021-02-06-music-fits-room %})
* [Link to a page]({% link /intangible.html %})

## Class Posts with Excerpts Test
Written in [Liquid](https://shopify.github.io/liquid/) and [Liquid Filters](https://jekyllrb.com/docs/liquid/filters/) to [display an index of posts](https://jekyllrb.com/docs/posts/).
<ul>
{% for post in site.posts %}
{% for tag in post.tags %}
{% if tag == page.tag %}
  <li>
    {{ post.date | date_to_string: "ordinal", "US" }} — <a href="{{ post.url }}">{{ post.title }}</a>
    {{ post.excerpt }}
  </li>
{% endif %}
{% endfor %}
{% endfor %}
</ul>