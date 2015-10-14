---
title: Blue Button Dashboard
edit_page: false
---

Data on **{{ site.data.organizations | size }}** organizations compiled from the [Blue Button Connector](http://bluebuttonconnector.healthit.gov) detailing progress toward allowing patients and consumers to view, download, and transmit their health data, defined in [Meaningful Use Stage 2](http://www.healthit.gov/buzz-blog/meaningful-use/view-download-transmit-facts/). Hover or tap on a square to view the organization name.

Jump to: [View](#view), [Download](#download), [Transmit](#transmit), [Composite](#composite), [All Data](#all-data)

<div class="legend">
  <div class="status green"></div> = Available
  <br>
  <div class="status red"></div> = Unavailable
</div>

<a name="view"></a>
# View

{% assign num_orgs = 0 %}
{% for org in site.data.organizations %}
  {% if org.view == true %}
    {% assign num_orgs = num_orgs | plus: 1 %}
  {% endif %}
{% endfor %}

**{{ num_orgs }}** organizations allow viewing of health data online.

<div class="status-boxes">
  {% for org in site.data.organizations %}
  <div class="status {% if org.view %}green{% else %}red{% endif %}" data-tooltip="{{ org.organization }}" onclick=""></div>
  
  {% endfor %}
</div>

<a name="download"></a>
# Download

{% assign num_orgs = 0 %}
{% for org in site.data.organizations %}
  {% if org.download == true %}
    {% assign num_orgs = num_orgs | plus: 1 %}
  {% endif %}
{% endfor %}

**{{ num_orgs }}** organizations allow downloading of health data.

<div class="status-boxes">
  {% for org in site.data.organizations %}
  <div class="status {% if org.download %}green{% else %}red{% endif %}" data-tooltip="{{ org.organization }}" onclick=""></div>
  {% endfor %}
</div>

<a name="transmit"></a>
# Transmit

{% assign num_orgs = 0 %}
{% for org in site.data.organizations %}
  {% if org.transmit == true %}
    {% assign num_orgs = num_orgs | plus: 1 %}
  {% endif %}
{% endfor %}

**{{ num_orgs }}** organizations allow transmission of health data.

<div class="status-boxes">
  {% for org in site.data.organizations %}
  <div class="status {% if org.transmit %}green{% else %}red{% endif %}" data-tooltip="{{ org.organization }}" onclick=""></div>
  {% endfor %}
</div>

<a name="composite"></a>
# Composite

<div class="legend">
  <div class="status gray"></div> = None
  <br>
  <div class="status light"></div> = View
  <br>
  <div class="status medium"></div> = View, Download
  <br>
  <div class="status dark"></div> = View, Download, and Transmit
</div>

<div class="status-boxes">
  {% for org in site.data.organizations %}
  
  <div class="status {% if org.transmit %}dark{% elsif org.download %}medium{% elsif org.view %}light{% else %}gray{% endif %}" data-tooltip="{{ org.organization }}" onclick=""></div>
  
  {% endfor %}
</div>

<a name="all-data"></a>
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
