---
layout: page
title: Kiteboarding kites
permalink: /kiteboarding/
---

<script>
const gallery = [
{% for kite in site.kiteboarding %}
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

      let html = document.querySelector('#description_' + (index - 1)).innerHTML;
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
  {% for kite in site.kiteboarding %}
  <div class="row kiteRow">
    <div class="col">
      {% if kite.name %}
        <div class="kiteName">{{ kite.name }}</div>
      {% endif %}
      <ul>
        <li>Make: {{ kite.make }}</li>
        <li>Model: {{ kite.model }}</li>
        <li>Size: {{ kite.size }}</li>
        <li>Obtained: {{ kite.obtained }}</li>
      </ul>
    </div>
    <div class="col">
      {{ kite.content | markdownify }}
    </div>
    <div class="col">
      {% for image in kite.images %}
        <div onClick="window.showKites({{ imageCounter }})">
          <img src="{{ site.baseurl }}/assets/images/{{ image }}" class="kiteThumb">
          <div id="description_{{ imageCounter}}" style="display:none;">{{ kite.content | markdownify }}"</div>
        </div>
        {% assign imageCounter = imageCounter | plus: 1 %}
      {% endfor %}
    </div>
  </div>
  {% endfor %}
</div>