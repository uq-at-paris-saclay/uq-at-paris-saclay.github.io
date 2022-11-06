---
layout: default
permalink: /jobs/
---

_Pour proposer une offre de stage : envoyer un email décrivant
votre offre à [comite-scientifique.uq@paris-saclay.fr](mailto:comite-scientifique.uq@paris-saclay.fr)_

<div class="posts">

  {% for category in site.categories %}

    {% if category[0] == "jobs" %}

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
