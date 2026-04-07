---
layout: home
title: Home
---

I'm fourth-year undergraduate studying computer science at Cornell University.

I'm interested in theoretical computer science (cryptography, learning theory, proof systems).

I'm a peer mentor for the Cornell Engineering Leadership Certification Program. I have been a TA for algorithms and discrete math. I led new member onboarding for the Cornell Data Science project team. I facilitated mastermind circles for goal-oriented Cornellians.

I post a few math videos on [YouTube](https://www.youtube.com/@mikono04). I enjoy anime and connecting with people. 

Hit me up for a chat anytime!

### Selected Publications 

See a selection of cool publiciations below. [[All Publications]({% link blog.md %})]

<div class="gallery-wrapper">
<div class="card-gallery" id="gallery">
  {% for publication in site.data.publications %}
    {% include publication-card.html
      title=publication.title
      authors=publication.authors
      link=publication.link
      icon=publication.icon
      icon_alt=publication.icon_alt
      video=publication.video
      description=publication.description
    %}
  {% endfor %}
</div>
<div class="gallery-dots">
  <span class="dot" onclick="scrollGallery(0)"></span>
  <span class="dot" onclick="scrollGallery(1)"></span>
</div>
</div>
