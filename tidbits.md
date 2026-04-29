---
layout: page
title: Tidbits
permalink: /tidbits/
---

I love to post mathy videos on my YouTube and post expositional pieces here.

<div class="gallery-wrapper">
<div class="card-gallery card-gallery--stacked">
  {% for item in site.data.explainers %}
    {% include linked-card.html
      title=item.title
      date=item.date
      category=item.category
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
