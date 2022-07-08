---
layout: page
title: Kiteboarding kites
permalink: /kiteboarding/
---

<table>
<tr>
  <th>Make</th>
  <th>Model</th>
  <th>Size</th>
  <th>Obtained</th>
  <th>Description</th>
  <th>Photos</th>
</tr>
{% for kite in site.kiteboarding %}
<tr>
  <td>{{ kite.make }}</td>
  <td>{{ kite.model }}</td>
  <td>{{ kite.size }}</td>
  <td>{{ kite.obtained }}</td>
  <td>{{ kite.content | markdownify }}</td>
  <td>TODO photos</td>
</tr>
{% endfor %}
</table>
