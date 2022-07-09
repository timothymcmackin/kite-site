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
    <ul>
      <li>Make: {{ kite.make }}</li>
      <li>Model: {{ kite.model }}</li>
      <li>Obtained: {{ kite.obtained }}</li>
      {% if kite.name %}
        <li>Name: {{ kite.name }}</li>
      {% endif %}
    </ul>
  </td>
  <td>{{ kite.content | markdownify }}</td>
  <td>
    <img src="{{ site.baseurl }}/assets/images/{{ kite.images | first }}"/>
  </td>
</tr>
{% endfor %}
</table>
