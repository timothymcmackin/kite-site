---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: default
author_profile: false
---

{% assign kiteTotal = 0 %}
{% assign givenAway = 0 %}
{% for kite in site.dual %}
  {% if kite.givenAway %}
    {% assign givenAway = givenAway | plus: 1 %}
  {% else %}
    {% assign kiteTotal = kiteTotal | plus: 1 %}
  {% endif %}
{% endfor %}
{% for kite in site.single %}
  {% if kite.givenAway %}
    {% assign givenAway = givenAway | plus: 1 %}
  {% else %}
    {% assign kiteTotal = kiteTotal | plus: 1 %}
  {% endif %}
{% endfor %}
{% for kite in site.kiteboarding %}
  {% if kite.givenAway %}
    {% assign givenAway = givenAway | plus: 1 %}
  {% else %}
    {% assign kiteTotal = kiteTotal | plus: 1 %}
  {% endif %}
{% endfor %}
{% for kite in site.power %}
  {% if kite.givenAway %}
    {% assign givenAway = givenAway | plus: 1 %}
  {% else %}
    {% assign kiteTotal = kiteTotal | plus: 1 %}
  {% endif %}
{% endfor %}
{% for kite in site.quad %}
  {% if kite.givenAway %}
    {% assign givenAway = givenAway | plus: 1 %}
  {% else %}
    {% assign kiteTotal = kiteTotal | plus: 1 %}
  {% endif %}
{% endfor %}

This is a catalog of the {{ kiteTotal }} kites that are in my collection and a few ({{ givenAway }}) of the kites that I've given away.

{% assign kite_types = site.collections | where: "collection_type", "kite" %}

<div class="kite-type-container">
{% for type in kite_types %}
  <div class="type">
    <a href="{{ type.href }}">
      <img src="{{ type.photo }}">
    </a>
    <div class="label">
      {{ type.name }}
    </div>
  </div>
{% endfor %}
</div>
