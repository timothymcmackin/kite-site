---
layout: page
title: Single-line kites
permalink: /single/
---

<table>
<tr>
  <th>Details</th>
  <th>Description</th>
  <th>Photos</th>
</tr>
{% for kite in site.single %}
<tr>
  <td>
    {% if kite.name %}
      <div class="kiteName">{{ kite.name }}</div>
    {% endif %}
    <ul>
      <li>Make: {{ kite.make }}</li>
      <li>Model: {{ kite.model }}</li>
      <li>Obtained: {{ kite.obtained }}</li>
    </ul>
  </td>
  <td>{{ kite.content | markdownify }}</td>
  <td>
    {% for image in kite.images %}
      <a class="spotlight"
        href="{{ site.baseurl }}/assets/images/{{ image }}"
        title="{{ kite.content | markdownify }}">
        <img src="{{ site.baseurl }}/assets/images/{{ image }}">
      </a>
    {% endfor %}
  </td>
</tr>
{% endfor %}
</table>
