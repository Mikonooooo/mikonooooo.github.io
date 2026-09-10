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
    <div class="hero-intro__line"><b>Incoming PhD Student at MIT</b><br>
    Cryptography & ML</div>
    <div class="hero-intro__email" aria-label="email address">
      <span aria-hidden="true">mi</span><span aria-hidden="true">ngo</span><span aria-hidden="true">&#64;</span><span aria-hidden="true">mit</span><span aria-hidden="true">&#46;</span><span aria-hidden="true">edu</span>
    </div>
    <div class="hero-links">
      <a href="{{ '/assets/documents/index/CV.pdf' | relative_url }}" class="hero-link-icon" aria-label="CV">
        <img src="{{ '/assets/images/index/cv-icon.svg' | relative_url }}" alt="" aria-hidden="true" class="hero-link-icon--cv">
        <span class="hero-link-label">CV</span>
      </a>
      <a href="#" class="hero-link-icon" aria-label="Google Scholar">
        <img src="{{ '/assets/images/index/icons8-google-scholar.svg' | relative_url }}" alt="" aria-hidden="true">
        <span class="hero-link-label">Google Scholar</span>
      </a>
      <a href="https://www.linkedin.com/in/mic-ngo/" class="hero-link-icon" aria-label="LinkedIn">
        <img src="{{ '/assets/images/index/icons8-linkedin.svg' | relative_url }}" alt="" aria-hidden="true">
        <span class="hero-link-label">LinkedIn</span>
      </a>
      <a href="https://www.youtube.com/@mikono04" class="hero-link-icon" aria-label="YouTube">
        <img src="{{ '/assets/images/index/icons8-youtube.svg' | relative_url }}" alt="" aria-hidden="true">
        <span class="hero-link-label">YouTube</span>
      </a>
    </div>
  </div>
</section>

<section class="recent-news">
  <div class="recent-news__box">
    <div class="recent-news__title"><b>Recent News</b><br>
    <span>
    Starting my PhD at MIT in the fall! 
    <br>Awarded the 2026 NSF GRFP!
    </span>
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

Hi! I'm a 1st-year PhD student at **MIT EECS**. Previously, I was an undergraduate at **Cornell University**, advised by [**Michael P. Kim**](https://www.cs.cornell.edu/~mpkim/). My research interests lie in **trustworthy machine learning**, specifically the intersection of **cryptography** and **machine learning theory**. I am honored to be an **NSF Graduate Research Fellow**.

During my time at Cornell, I founded the [**CS theory club**](https://theoryclub.cs.cornell.edu/), was a **peer mentor** and **participant** of the [**Engineering Leadership Certification Program**](https://www.duffield.cornell.edu/selander-center-engineering-leadership/engineering-leadership-certification/), and served as a **teaching assistant** for 5 semesters for the **Mathematical Foundations of Computer Science** (CS 2800) and **Introduction to the Analysis of Algorithms** (CS 4820). 

On the personal side, I occasionally craft [**YouTube videos**](https://www.youtube.com/@mikono04) and write things on my [**blog**]({% link tidbits.md %}). I'm also interested in piano, One Piece, variety gaming culture, musicals, movies, and books (from time to time). **Ask me for a chat via email!**


### Selected Research
{: #selected-publications .home-section}

My research interests intersect cryptography, proof systems, and machine learning. [[All]({% link publications.md %})] [[Scholar](#)]


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
