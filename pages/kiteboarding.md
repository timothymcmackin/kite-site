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

<table>
<tr>
  <th>Details</th>
  <th>Description</th>
  <th>Photos</th>
</tr>
{% assign imageCounter = 0 %}
{% for kite in site.kiteboarding %}
<tr>
  <td>
    <ul>
      <li>Make: {{ kite.make }}</li>
      <li>Model: {{ kite.model }}</li>
      <li>Size: {{ kite.size }}</li>
      <li>Obtained: {{ kite.obtained }}</li>
    </ul>
  </td>
  <td>{{ kite.content | markdownify }}</td>
  <td>
    {% for image in kite.images %}
      <div onClick="window.showKites({{ imageCounter }})">
        <img src="{{ site.baseurl }}/assets/images/{{ image }}">
        <div id="description_{{ imageCounter}}" style="display:none;">{{ kite.content | markdownify }}"</div>
      </div>
      {% assign imageCounter = imageCounter | plus: 1 %}
    {% endfor %}
  </td>
</tr>
{% endfor %}
</table>
