---
layout: home
title: Home
---

<section class="hero-intro">
  <img src="{{ '/assets/images/index/profile.jpg' | relative_url }}" alt="Portrait of Michael Ngo" class="hero-intro__image">

  <div class="hero-intro__content">
    <div class="hero-intro__title-row">
      <h1 class="hero-intro__title">Michael Ngo</h1>
      <button type="button" class="hero-intro__audio-button" aria-label="Play pronunciation of Michael Ngo" onclick="toggleIntroAudio()">
        <img src="{{ '/assets/images/index/speaker.png' | relative_url }}" alt="" class="hero-intro__audio-icon">
      </button>
      <audio id="intro-audio" preload="none" class="hero-intro__audio">
        <source src="{{ '/assets/audio/index/michael_ngo.m4a' | relative_url }}" type="audio/mp4">
        Your browser does not support the audio element.
      </audio>
    </div>
    <div class="hero-intro__line">Incoming Computer Science PhD Candidate @ MIT</div>
    <div class="hero-intro__line">
      mn542@cornell.edu
    </div>
    <div class="hero-intro__tagline">Exploring Crypto+ML;<br>Championing community, growth, and authenticity.</div>
    <div class="hero-intro__line"> Links:
      <a href="{{ '/assets/documents/index/CV.pdf' | relative_url }}">CV</a>
      |
      <a href="#">Google Scholar</a>
      |
      <a href="https://www.youtube.com/@mikono04">YouTube</a>
    </div>
  </div>
</section>

<script>
  function toggleIntroAudio() {
    const audio = document.getElementById('intro-audio');
    if (!audio) {
      return;
    }

    if (audio.paused) {
      audio.play();
      return;
    }

    audio.pause();
    audio.currentTime = 0;
  }
</script>

### About Me

I'm fourth-year undergraduate studying computer science at Cornell University.

I'm interested in theoretical computer science (cryptography, learning theory, proof systems).

I'm a peer mentor for the Cornell Engineering Leadership Certification Program. I have been a TA for algorithms and discrete math. I led new member onboarding for the Cornell Data Science project team. I facilitated mastermind circles for goal-oriented Cornellians.

I post a few math videos on [YouTube](https://www.youtube.com/@mikono04). I enjoy anime and connecting with people. 

Hit me up for a chat anytime!



### Selected Publications 

See a selection of cool publiciations below. [[All Publications]({% link blog.md %})]

<div class="gallery-wrapper">
<div class="card-gallery">
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
</div>

### Leadership & Outreach

Here are a few pieces about teaching, mentoring, and making ideas more accessible.

<div class="gallery-wrapper">
<div class="card-gallery">
  {% for item in site.data.leadership_outreach %}
    {% include linked-card.html
      title=item.title
      position=item.position
      description=item.description
      image=item.image
      image_alt=item.image_alt
      url=item.url
    %}
  {% endfor %}
</div>
</div>

### Blog

Some writing highlights from across the site.

<div class="gallery-wrapper">
<div class="card-gallery">
  {% for item in site.data.blog_highlights %}
    {% include linked-card.html
      title=item.title
      date=item.date
      category=item.category
      description=item.description
      image=item.image
      image_alt=item.image_alt
      url=item.url
    %}
  {% endfor %}
</div>
</div>
