---
title: "Big LEDs"
tag: bigleds
---
Big LEDs, Spring 2021
<ul>
{% for post in site.posts %}
{% for tag in post.tags %}
{% if tag == page.tag %}
    <li>
        {{ post.date | date_to_string: "ordinal", "US" }} — <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
{% endif %}
{% endfor %}
{% endfor %}
</ul>