---
layout: page
title: Publications
permalink: /publications/
---

Coming soon...

# Manuscripts

<div class="publication-list">
  {% for publication in site.data.publications %}
    <div class="publication-item">
      <a href="{{ publication.paper_url }}" target="_blank" rel="noopener noreferrer"><b>{{ publication.title }}</b></a><br>
      <span>{{ publication.authors }}</span><br>
      <i>{{ publication.venue }}</i>
    </div>
  {% endfor %}
</div>
