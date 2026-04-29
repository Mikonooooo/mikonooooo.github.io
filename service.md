---
layout: page
title: Service
permalink: /service/
---

I really value engaging with the community, to create communities via clubs, raise the next generations of leaders, and help others achieve their goals.

<div class="gallery-wrapper">
<div class="card-gallery card-gallery--stacked">
  {% for item in site.data.leadership %}
    {% include linked-card.html
      title=item.title
      position=item.position
      description=item.description
      image=item.image
      image_alt=item.image_alt
      url=item.url
      external_url=item.external_url
      external_label=item.external_label
    %}
  {% endfor %}
</div>
</div>
