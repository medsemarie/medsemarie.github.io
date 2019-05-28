---
layout: default
---

<div style="margin-bottom: 30px;">
<a href="http://bit.ly/medsemarie" style="text-decoration: none; background-color:#de2d26; padding:8px"><span style="color:white; text-decoration: none"> <i class="fas fa-arrow-circle-right"></i> <i class="fas fa-arrow-circle-right"></i> <i class="fas fa-arrow-circle-right"></i> Cliquez ici pour répondre à l'invitation <i class="fas fa-arrow-circle-left"></i> <i class="fas fa-arrow-circle-left"></i> <i class="fas fa-arrow-circle-left"></i> </span></a>
</div>

<!-- Load the squares -->
<div class="thumbnails-content row">
{% for node in site.documentation %}
{% if node.thumbnail == true %}
<div class="col-sm-5 thumbnail">{{ node.content }} </div>
{% endif %}
{% endfor %}
</div>

<!-- Load the content -->
{% assign sorted = site.documentation | sort: 'order' %}
{% for node in sorted %}
  {% if node.front == true %}
  {{ node.content }}
  {% for subpage in site.documentation %}
  {% if subpage.front == false and subpage.permalink contains node.permalink and subpage.thumbnail != true %}
  {{ subpage.content }}
  {% endif %}
  {% endfor %}
  {% endif %}
{% endfor %}
