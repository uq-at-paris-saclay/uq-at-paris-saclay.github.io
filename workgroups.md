---
layout: default
permalink: /workgroups/
---

## Objectif des Groupes de Travail (GTs)

Les GTs sont des groupes informels de chercheurs autour de thèmes
particuliers. Les GTs proposent des actions (stages en commun,
thèses, etc.). Ils intéragissent avec le Comité Scientifique du GIS
pour soutenir la réalisation des projets et rechercher les
financements.

## Qui peut participer ?

Tous les chercheurs du GIS, issus du monde académique ou des
entreprises et EPICs. Il faut envoyer un email aux porteurs des GTs,
en mettant le
[comite-scientifique.uq@paris-saclay.fr](mailto:comite-scientifique.uq@paris-saclay.fr)
en copie.

## Comment proposer un GT ?

_Pour proposer un groupe de travail : envoyer un email décrivant
votre projet à [comite-scientifique.uq@paris-saclay.fr](mailto:comite-scientifique.uq@paris-saclay.fr)_


## Liste des GTs proposés

<div class="posts">

  {% for category in site.categories %}

    {% if category[0] == "wgs" %}

      {% for post in category[1] %}
        <article class="post">

          <h3><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>

          <div class="entry">
            {{ post.excerpt }}
          </div>

        <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
        </article>

      {% endfor %}

    {% endif %}

  {% endfor %}

</div>
