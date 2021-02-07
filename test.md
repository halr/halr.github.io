---
title: "Tests & Debugging"
tag: mixd
---
This page should not be linked from anywhere.
* W1. Experience concept based on intro song — [Music Fits Room]({% post_url 2021-02-06-music-fits-room %})


## Liquid Filters & Posts
Let's test out some [Liquid Filters](https://jekyllrb.com/docs/liquid/filters/) to [Display an index of posts](https://jekyllrb.com/docs/posts/).

'''
{{ page.tags | array_to_sentence_string }}
'''

### MIxD
<ul>
  {% for post in { site.posts | where_exp:"item", "item.tags contains 'mixd'" } %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

### MIxD
<ul>
{% for post in site.posts %}
{% for tag in post.tags %}
{% if tag == page.tag %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
{% endif %}
{% endfor %}
{% endfor %}
</ul>