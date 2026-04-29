---
layout: blog
title: Publications
permalink: /research/
include_categories:
  - Research
---

Research posts, paper writeups, and publication pages.

<div class="gallery-wrapper">
<div class="card-gallery">
  {% for publication in site.data.publications %}
    {% include publication-card.html
      title=publication.title
      authors=publication.authors
      venue=publication.venue
      link=publication.link
      paper_url=publication.paper_url
      icon=publication.icon
      icon_alt=publication.icon_alt
      image=publication.image
      image_alt=publication.image_alt
      description=publication.description
    %}
  {% endfor %}
</div>
</div>
