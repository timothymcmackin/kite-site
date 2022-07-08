---
layout: page
title: Kiteboarding kites
permalink: /kiteboarding/
---

<table>
<tr>
  <th>Details</th>
  <th>Description</th>
  <th>Photos</th>
</tr>
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
    <img src="{{ site.baseurl}}/assets/images/{{ kite.images | first }}"/>
  </td>
</tr>
{% endfor %}
</table>
