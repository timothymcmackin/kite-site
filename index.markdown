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
{% for kite in site.power %}
  {% if kite.givenAway %}
    {% assign givenAway = givenAway | plus: 1 %}
  {% else %}
    {% assign kiteTotal = kiteTotal | plus: 1 %}
  {% endif %}
{% endfor %}

This is a catalog of the {{ kiteTotal }} kites that are in my collection and a few ({{ givenAway }}) of the kites that I've given away.

<style type="text/css">
a div {
}

a img {
  max-height: 200px
}
</style>

<div class="container">
  <div class="row">
    <div class="col" align="center">
      <a href="./dual">
        <div>Dual-line kites</div><br/>
        <img src="{{ site.baseurl }}/assets/images/dual/talonv3.jpg">
      </a>
    </div>
    <div class="col" align="center">
      <a href="./single">
        <div>Single-line kites</div><br/>
        <img src="{{ site.baseurl }}/assets/images/single/skysong_1_sm.jpg">
      </a>
    </div>
    <div class="col" align="center">
      <a href="./kiteboarding">
        <div>Kiteboarding kites</div><br/>
        <img src="{{ site.baseurl }}/assets/images/kiteboarding/12switch12_2_sm.jpg">
      </a>
    </div>
    <div class="col" align="center">
      <a href="./power">
        <div>Power kites</div><br/>
        <img src="{{ site.baseurl }}/assets/images/power/hornet5_stock_1_sm.jpg">
      </a>
    </div>
  </div>
</div>