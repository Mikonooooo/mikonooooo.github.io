---
layout: page
title: Tidbits
permalink: /tidbits/
---

{% assign featured_item = site.data.explainers | first %}
{% assign featured_url = featured_item.url | default: featured_item.link %}
{% include linked-card.html
  shell_class="featured-video-card"
  title=featured_item.title
  date=featured_item.date
  category=featured_item.category
  description=featured_item.description
  image=featured_item.image
  image_alt=featured_item.image_alt
  embed_url=featured_item.embed_url
  url=featured_url
  external_url=featured_item.external_url
  external_label=featured_item.external_label
%}

<div class="gallery-wrapper">
<div class="card-gallery card-gallery--stacked">
  {% for item in site.data.explainers offset:1 %}
    {% assign item_url = item.url | default: item.link %}
    {% include linked-card.html
      title=item.title
      date=item.date
      category=item.category
      description=item.description
      image=item.image
      image_alt=item.image_alt
      url=item_url
      external_url=item.external_url
      external_label=item.external_label
    %}
  {% endfor %}
</div>
</div>
