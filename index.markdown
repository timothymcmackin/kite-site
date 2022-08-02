---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
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

This is a catalog of the {{ kiteTotal }} kites that are in my collection and the {{ givenAway }} kites that I've given away.
