---
title: Projects
tags:
  - projects
---

A collection of things I've built. Each card links to a full write-up with the motivation, tech stack, and what I learned along the way.

<!--
  To add a project: copy one <a class="project-card"> block below.
  - href      -> the GitHub repo URL for the project
  - cover     -> put an emoji inside the cover div, OR drop an <img> in it.
                 Write the image src as a bare filename ("foo.png"), never
                 "/foo.png": the site is served from the /n1mk1/ subpath, so a
                 leading slash 404s in deployment. Quartz rewrites the bare
                 filename to the right path at build time.
  - title / desc / tags -> whatever you want shown on the card
  Keep target/rel so the repo opens in a new tab.
-->

<div class="projects-grid">
  <a class="project-card" href="https://github.com/n1mk1/Bodybuilding-Judge" target="_blank" rel="noopener noreferrer">
    <div class="project-card__cover project-card__cover--image">
      <img class="project-card__img" src="body-statue.png" alt="" loading="lazy" />
    </div>
    <div class="project-card__body">
      <div class="project-card__title">Computer Vision Physique Analysis</div>
      <p class="project-card__desc">Automated bodybuilding physique assessment using pose estimation and landmark geometry.</p>
      <div class="project-card__tags"><span>Python</span><span>OpenCV</span><span>MediaPipe</span></div>
    </div>
  </a>
  <a class="project-card" href="https://github.com/n1mk1/terracomrad" target="_blank" rel="noopener noreferrer">
    <div class="project-card__cover project-card__cover--image">
      <img class="project-card__img" src="mammogram.png" alt="" loading="lazy" />
    </div>
    <div class="project-card__body">
      <div class="project-card__title">TerraComrad</div>
      <p class="project-card__desc">AI-assisted mammogram diagnostics — a DICOM viewer with deterministic mass segmentation and clinician-directed AI insights.</p>
      <div class="project-card__tags"><span>Python</span><span>FastAPI</span><span>DICOM</span><span>Gemini</span></div>
    </div>
  </a>
</div>

More projects coming soon as I write them up.
