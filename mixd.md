---
title: "MIxD"
tag: mixd
---
Musical Interaction Design, Spring 2021
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