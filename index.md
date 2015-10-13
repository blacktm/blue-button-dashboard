---
title: Blue Button Dashboard
edit_page: false
---

**{{ site.data.organizations | size }}** Organizations in the [Connector](http://bluebuttonconnector.healthit.gov).

<div>
  <div class="status green"></div> = Available
  <br>
  <div class="status red"></div> = Unavailable
</div>

# View

<div class="status-boxes">
  {% for org in site.data.organizations %}
  <div class="status {% if org.view %}green{% else %}red{% endif %}" data-tooltip="{{ org.organization }}"></div>
  
  {% endfor %}
</div>

# Download

<div class="status-boxes">
  {% for org in site.data.organizations %}
  <div class="status {% if org.download %}green{% else %}red{% endif %}" data-tooltip="{{ org.organization }}"></div>
  {% endfor %}
</div>

# Transmit

<div class="status-boxes">
  {% for org in site.data.organizations %}
  <div class="status {% if org.transmit %}green{% else %}red{% endif %}" data-tooltip="{{ org.organization }}"></div>
  {% endfor %}
</div>

# All Data

<table>

  <thead>
    <tr>
      <th>Organization</th>
      <th>Category</th>
      <!-- <th>Description</th> -->
      <!-- <th>Phone</th> -->
      <!-- <th>States</th> -->
      <!-- <th>URL</th> -->
      <th>View</th>
      <th>Download</th>
      <th>Transmit</th>
    </tr>
  </thead>
  
  {% for org in site.data.organizations %}
  <tr>
    <td>{{ org.organization }}</td>
    <td>{{ org.category }}</td>
    <!-- <td>{{ org.description }}</td> -->
    <!-- <td>{{ org.phone }}</td> -->
    <!-- <td>{{ org.states }}</td> -->
    <!-- <td>{{ org.url }}</td> -->
    <td>{% if org.view %}✅{% else %}❌{% endif %}</td>
    <td>{% if org.download %}✅{% else %}❌{% endif %}</td>
    <td>{% if org.transmit %}✅{% else %}❌{% endif %}</td>
  </tr>
  {% endfor %}
  
</table>
