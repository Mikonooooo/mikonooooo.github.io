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
    <div class="hero-intro__line">Senior in Computer Science @ Cornell</div>
    <div class="hero-intro__line">
      mn542@cornell.edu
    </div>
    <div class="hero-intro__tagline">Exploring Crypto+ML;<br>Championing community, growth, and authenticity.</div>
    <div class="hero-intro__line"> Links:
      <a href="{{ '/assets/documents/index/CV.pdf' | relative_url }}">CV</a>
      |
      <a href="#">Google Scholar</a>
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
{: #about-me .home-section}

Hi! I'm currently a senior studying Computer Science at Cornell University, advised by [Michael P. Kim](https://www.cs.cornell.edu/~mpkim/). My research interests comprise of the intersection of cryptography and machine learning theory (which is sometimes called crypto+ML). In the summers of 2024 and 2025, I explored research via the [Bowers Undergraduate Research Experience](https://bowers.cornell.edu/research/undergraduate-research/bowers-undergraduate-research-experience). In the summer of 2024, I was fortunate to be co-advised by Michael P. Kim and [Noah Stephens-Davidowitz](https://www.noahsd.com/).

I co-founded and am currently organizing an [undergraduate theory club](https://theoryclub.cs.cornell.edu/) at Cornell. I am also a peer mentor for the [Engineering Leadership Certification Program](https://www.duffield.cornell.edu/selander-center-engineering-leadership/engineering-leadership-certification/), of which I completed the certification the year prior. Finally, I have served as a teaching assistant for 5 semesters for the Mathematical Foundations of Computer Science (CS 2800) and Introduction to the Analysis of Algorithms (CS 4820). 

I occasionally craft videos on [YouTube](https://www.youtube.com/@mikono04) and write things on my [blog]({% link blog.md %}). I'm also interested in piano, One Piece, and variety gaming culture. **Please hit me up for a chat anytime!**


### Selected Publications 
{: #selected-publications .home-section}

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
{: #leadership-outreach .home-section}

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

### Blog Highlights
{: #blog-highlights .home-section}

Some writing highlights from across the site. [[All Blog Posts]({% link blog.md %})]

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
