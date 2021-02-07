---
title: "Tests & Debugging"
---
This page should not be linked from anywhere.
* W1. Experience concept based on intro song — [Music Fits Room]({% post_url 2021-02-06-music-fits-room %})


## Liquid Filters & Posts
Let's test out some [Liquid Filters](https://jekyllrb.com/docs/liquid/filters/) to [Display an index of posts](https://jekyllrb.com/docs/posts/)

'''
{{ site.posts | where_exp:"item", "item.tags contains 'mixd'" }}
'''

### MIxD
<ul>
  {% for post in { site.posts | where_exp:"item", "item.tags contains 'mixd'" } %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>