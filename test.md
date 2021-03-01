---
title: "Tests & Debugging"
tag: intangible
published: true
---
This page should not be linked from anywhere.

## Link Tests
* W1. Experience concept based on intro song — [Music Fits Room]({% post_url 2021-02-06-music-fits-room %})

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