---
title: "Tests & Debugging"
tags: intangible
published: true
---
This page should not be linked from anywhere.

## Link Tests
* W1. Experience concept based on intro song — [Music Fits Room]({% post_url 2021-02-06-music-fits-room %})

## Liquid Filters & Posts
Let's test out some [Liquid Filters](https://jekyllrb.com/docs/liquid/filters/) to [Display an index of posts](https://jekyllrb.com/docs/posts/).

### Class Posts with Excerpts Test
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