---
layout: page
title: Leadership
permalink: /leadership/
---

I really value engaging with the community, to create communities via clubs, raise the next generations of leaders, and help others achieve their goals.

### Core Values
Core values are the guiding principles I use, both as a leader, researcher, and in my day-to-day life.
<section class="core-values" aria-labelledby="core-values-title">
  <div class="core-values__grid">
    <button
      class="core-value-card"
      type="button"
      aria-haspopup="dialog"
      data-core-value-title="Authenticity"
      data-core-value-image="{{ '/assets/images/core_values/Authenticity.png' | relative_url }}"
      data-core-value-image-alt="Authenticity core value illustration"
      data-core-value-description="I value authenticity. Authenticity is about staying true to myself, keeping my values and goals in mind, enjoying the present moment and doing what I most love to do.">
      <img src="{{ '/assets/images/core_values/Authenticity.png' | relative_url }}" alt="Authenticity core value illustration" class="core-value-card__image">
      <span class="core-value-card__overlay">Authenticity</span>
    </button>
    <button
      class="core-value-card"
      type="button"
      aria-haspopup="dialog"
      data-core-value-title="Helping Others"
      data-core-value-image="{{ '/assets/images/core_values/Helping Others.png' | relative_url }}"
      data-core-value-image-alt="Helping Others core value illustration"
      data-core-value-description="I value helping others. Helping others is about helping others find satisfaction and happiness, whether by teaching, creating equal opportunities, or by being a good friend.">
      <img src="{{ '/assets/images/core_values/Helping Others.png' | relative_url }}" alt="Helping Others core value illustration" class="core-value-card__image">
      <span class="core-value-card__overlay">Helping Others</span>
    </button>
    <button
      class="core-value-card"
      type="button"
      aria-haspopup="dialog"
      data-core-value-title="Belonging"
      data-core-value-image="{{ '/assets/images/core_values/Belonging.png' | relative_url }}"
      data-core-value-image-alt="Belonging core value illustration"
      data-core-value-description="I value Belonging. Belonging is about finding and creating places where myself and others are valued and able to contribute value. A place where everyone can be authentic, grow and help each other.">
      <img src="{{ '/assets/images/core_values/Belonging.png' | relative_url }}" alt="Belonging core value illustration" class="core-value-card__image">
      <span class="core-value-card__overlay">Belonging</span>
    </button>
    <button
      class="core-value-card"
      type="button"
      aria-haspopup="dialog"
      data-core-value-title="Grit"
      data-core-value-image="{{ '/assets/images/core_values/Grit.png' | relative_url }}"
      data-core-value-image-alt="Grit core value illustration"
      data-core-value-description="I value grit. Grit is always believing in myself, being okay with failure, doing what I can to make amends and push outside my comfort zone. Focusing on what is in my control; adjusting, growing and mastering.">
      <img src="{{ '/assets/images/core_values/Grit.png' | relative_url }}" alt="Grit core value illustration" class="core-value-card__image">
      <span class="core-value-card__overlay">Grit</span>
    </button>
  </div>
</section>

<dialog class="core-value-dialog" aria-labelledby="core-value-dialog-title">
  <button class="core-value-dialog__close" type="button" aria-label="Close core value popup">&times;</button>
  <img src="" alt="" class="core-value-dialog__image" id="core-value-dialog-image">
  <h2 id="core-value-dialog-title"></h2>
  <p id="core-value-dialog-description"></p>
</dialog>


### Experience 
I put effort into helping the community in small and large ways.

<section class="leadership-experience" aria-labelledby="leadership-experience-title">
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
</section>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    const dialog = document.querySelector(".core-value-dialog");
    const image = document.getElementById("core-value-dialog-image");
    const title = document.getElementById("core-value-dialog-title");
    const description = document.getElementById("core-value-dialog-description");
    const closeButton = document.querySelector(".core-value-dialog__close");

    if (!dialog || !image || !title || !description || !closeButton) return;

    document.querySelectorAll(".core-value-card").forEach(function (card) {
      card.addEventListener("click", function () {
        image.src = card.dataset.coreValueImage || "";
        image.alt = card.dataset.coreValueImageAlt || "";
        title.textContent = card.dataset.coreValueTitle || "";
        description.textContent = card.dataset.coreValueDescription || "";

        if (typeof dialog.showModal === "function") {
          dialog.showModal();
        } else {
          dialog.setAttribute("open", "open");
        }
      });
    });

    function closeDialog() {
      if (typeof dialog.close === "function") {
        dialog.close();
      } else {
        dialog.removeAttribute("open");
      }
    }

    closeButton.addEventListener("click", closeDialog);

    dialog.addEventListener("click", function (event) {
      if (event.target === dialog) {
        closeDialog();
      }
    });
  });
</script>
