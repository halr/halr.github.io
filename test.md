---
title: "Tests & Debugging"
---
This page should not be linked from anywhere.
* W1. Experience concept based on intro song — [Music Fits Room]({% post_url 2021-02-06-music-fits-room %})

## Posts
[Displaying an index of postsPermalink](https://jekyllrb.com/docs/posts/)

### All
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}

## Liquid Filters
Let's test out some [Liquid Filters](https://jekyllrb.com/docs/liquid/filters/)!
