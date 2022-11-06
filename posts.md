---
layout: default
permalink: /posts/
---

<div class="posts">

  {% for category in site.categories %}

    {% if category[0] == "news" %}

      {% for post in category[1] %}
        <article class="post">

          <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>

          <div class="entry">
            {{ post.excerpt }}
          </div>

        <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
        </article>

      {% endfor %}

    {% endif %}

  {% endfor %}

</div>
