---
layout: default
title: Quad-line kites
permalink: /quad/
---

<script>
const gallery = [
{% for kite in site.quad %}
{% for image in kite.images %}
  {
    src: "{{ site.baseurl }}/assets/images/{{ image }}",
    title: "loading description...",
  },
{% endfor %}
{% endfor %}
];

window.showKites = function(idx) {
  Spotlight.show(gallery, {
    index: idx,
    onchange: (index, options) => {
      // https://github.com/nextapps-de/spotlight/issues/53
      // Decode HTML entities in title and description
      const titleElement = document.querySelector('#spotlight .spl-title');
      // const descriptionElement = document.querySelector('#spotlight .spl-description');
      // titleElement.innerHTML = decodeURIComponent(titleElement.innerText);

      let html = document.querySelector('#description_' + (index)).innerHTML;
      // Remove trailing "
      html = html.substr(0, html.length - 1);
      // both lines needed - can't figure out why
      titleElement.innerHTML = decodeURIComponent(html);
      titleElement.innerHTML = decodeURIComponent(html);


    },
  });
}
</script>

{% assign imageCounter = 0 %}
<div class="kite-detail-container">
  {% for kite in site.quad %}
  <div class="kiteRow">
    <div>
      <div class="kiteName">
        {% if kite.name %}
          {{ kite.name }}
        {% else %}
          {{ kite.make }} {{ kite.model }} {{ kite.trim }}
        {% endif %}
      </div>
      <ul class="kite-detail-list">
        <li>Make: {{ kite.make }}</li>
        <li>Model: {{ kite.model }}</li>
        <li>Trim: {{ kite.trim }}</li>
        <li>Obtained: {{ kite.obtained }}</li>
      </ul>
    </div>
    <div class="kiteContent">
      {{ kite.content | markdownify }}
    </div>
    <div class="kiteImages">
      {% for image in kite.images %}
        {% assign imageCounter = imageCounter | plus: 1 %}
        <div onClick="window.showKites({{ imageCounter }})">
          <img src="{{ site.baseurl }}/assets/images/{{ image }}" class="kiteThumb">
          <div id="description_{{ imageCounter}}" style="display:none;">{{ kite.content | markdownify }}"</div>
        </div>
      {% endfor %}
    </div>
  </div>
  {% endfor %}
</div>
