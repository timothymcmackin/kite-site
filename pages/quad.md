---
layout: page
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
<div class="container">
  {% assign imageCounter = 0 %}
  {% for kite in site.quad %}
  <div class="row kiteRow">
    <div class="col">
      <ul>
        <li>Make: {{ kite.make }}</li>
        <li>Model: {{ kite.model }}</li>
        <li>Model: {{ kite.trim }}</li>
        <li>Obtained: {{ kite.obtained }}</li>
      </ul>
    </div>
    <div class="col">
      {{ kite.content | markdownify }}
    </div>
    <div class="col">
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
