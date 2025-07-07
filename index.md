---
layout: homepage
---

<h1 id="about-me"></h1>

<h2 style="margin: 80px 0px 10px;"></h2>

I am a second year PhD in Computer Science student at [Stony Brook University](https://www.stonybrook.edu/), where I am fortunate to be advised by [Prof. Omar Chowdhury](https://www.cs.stonybrook.edu/people/faculty/omarchowdhury).

My research lies at the intersection of **privacy compliance** and **formal verification** -- with a special focus on building privacy-secured systems that satisfies system specification requirement. My research interests include **privacy compliance**, **formal verification**, **security**, and **large language models**.
<!-- , **3D geometry models**, and **medical imaging**. -->

Previously, I successfully completed my graduate studies in Computer Science at the [University of New Brunswick](https://unb.ca/), Canada. During my time pursuing my graduate studies, I served as a Graduate Research Assistant at the [Canadian Institute of Cybersecurity](https://www.unb.ca/cic/). My research interests spanned the Internet of Things (IoT), Anomaly Detection, and Security under the supevision of Professor [Ali Ghorbani](https://www.cs.unb.ca/people/ghorbani). My biography is [here](./biography/).


<!-- <strong style="color:#e74d3c; font-weight:600"><strong style="color:#e74d3c; font-weight:600">I am currently looking for summer 2025 internship positions which I hope will help hone my skills and attain industry experience. You can find my resume  [here](./assets/resume_summarized_2025.pdf).</strong> -->


<!-- <div class="call-to-action">
  <h2 style="color: #e74d3c; font-weight: 600; margin-bottom: 10px;">
    Looking for Summer 2025 Internship!
  </h2>
  <p style="font-size: 16px; color: #555; margin-bottom: 20px;">
    I am currently looking for summer 2025 internship positions which I hope will help hone my skills and attain industry experience.
  </p>
  <!-- <a href="./assets/resume_summarized_2025.pdf" download class="resume-button">
    Download My Resume
  </a> 
  <a href="./assets/cv.pdf" download class="resume-button">
    Download My Resume
  </a>
</div> -->

<!-- <div class="call-to-action">
  <h2 style="color: #e74d3c; font-weight: 600; margin-bottom: 10px;">
    Looking for Summer 2025 Internship!
  </h2>
  <p style="font-size: 16px; color: #555; margin-bottom: 20px;">
    I am currently looking for summer 2025 internship positions which I hope will help hone my skills and attain industry experience.
  </p>
    <div class="button-container">
    <a href="./assets/cv.pdf" target="_blank" class="resume-button">
      View My Resume
    </a>
    <a href="./assets/research_summary.pdf" target="_blank" class="resume-button">
      View Research Summary
    </a>
  </div>
</div> -->

{% include_relative _includes/news.md %}

{% include_relative _includes/contact.md %}

<style>
@keyframes blink {
  0% { opacity: 1; }
  50% { opacity: 0; }
  100% { opacity: 1; }
}

.blinking-text {
  animation: blink 1.5s infinite;
}

.resume-button {
  display: inline-block;
  padding: 10px 20px;
  font-size: 16px;
  font-weight: 600;
  color: #fff;
  background-color: #0b192f;
  border-radius: 5px;
  text-decoration: none;
  transition: background-color 0.3s ease;
}

.resume-button:hover {
  background-color: #64ffda;
}

.call-to-action {
  background-color: #f8f9fa;
  padding: 20px;
  text-align: center;
  border-radius: 10px;
  margin: 30px 0;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.call-to-action:hover {
  transform: scale(1.02);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}
</style>