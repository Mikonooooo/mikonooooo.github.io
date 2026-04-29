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
    <div class="hero-intro__line">Incoming PhD Student at MIT EECS<br>
    Cryptography & ML</div>
    <div class="hero-intro__email">
      mingo@mit.edu
    </div> <br>
    <div class="hero-intro__line">
    <i>
    Growth<br>
    Authenticity<br>
    Helping Others<br>
    Belonging</i>
    </div>
    <br>
    <!-- <div class="hero-intro__tagline">Research in Cryptography & Machine Learning</div> -->
    <!-- <div class="hero-intro__tagline"><i>growth<br>authenticity<br>helping others<br>belonging</i></div> -->
  </div>
</section>

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

Hi! I'm currently a senior studying Computer Science at Cornell University, advised by [Michael P. Kim](https://www.cs.cornell.edu/~mpkim/). My research interests comprise of the intersection of cryptography and machine learning theory (which is sometimes called crypto+ML). In the summers of 2024 and 2025, I explored research via the [Bowers Undergraduate Research Experience](https://bowers.cornell.edu/research/undergraduate-research/bowers-undergraduate-research-experience). In the summer of 2024, I was fortunate to be co-advised by Michael P. Kim and [Noah Stephens-Davidowitz](https://www.noahsd.com/).

I co-founded and am currently organizing an [undergraduate theory club](https://theoryclub.cs.cornell.edu/) at Cornell. I am also a peer mentor for the [Engineering Leadership Certification Program](https://www.duffield.cornell.edu/selander-center-engineering-leadership/engineering-leadership-certification/), of which I completed the certification the year prior. Finally, I have served as a teaching assistant for 5 semesters for the Mathematical Foundations of Computer Science (CS 2800) and Introduction to the Analysis of Algorithms (CS 4820). 

I occasionally craft videos on [YouTube](https://www.youtube.com/@mikono04) and write things on my [blog]({% link tidbits.md %}). I'm also interested in piano, One Piece, and variety gaming culture. **Please hit me up for a chat!**


### Selected Publications

My research interests intersect cryptography, proof systems, and machine learning. [[Publications]({% link publications.md %})] [[Scholar](#)]


<div class="publication-list">
  {% for publication in site.data.publications %}
    <div class="publication-item">
      <a href="{{ publication.paper_url }}" target="_blank" rel="noopener noreferrer"><b>{{ publication.title }}</b></a><br>
      <span>{{ publication.authors }}</span><br>
      <i>{{ publication.venue }}</i>
    </div>
  {% endfor %}
</div>
