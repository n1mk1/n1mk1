---
title: Computer Vision Bodybuilding Physique Analysis System
tags:
  - projects
  - computer-vision
  - python
---

An automated physique assessment system for bodybuilding image analysis, built with **Python, OpenCV, MediaPipe, Tkinter, and NumPy**.

## What it does

Takes an image of a physique and produces objective measurements of the proportions bodybuilders actually care about — the X-frame taper, shoulder-to-waist ratio, and muscle mass distribution.

## How it works

- **Pose estimation, segmentation, and visualization** pipeline built on MediaPipe, OpenCV, and NumPy, integrating everything into a single assessment flow.
- **Landmark geometry algorithms** compute X-Frame and mass ratios (shoulders, latissimus, waist, quadriceps) using center-out scans from pose landmarks.
- **Image processing** combines CLAHE enhancement, Canny edge detection, and morphological operations to find body contours reliably across lighting conditions.
- **Tkinter UI** with robust file handling, logging capabilities, and comprehensive error management, so it's usable by people who don't want to touch a terminal.

## Tech stack

`Python` `OpenCV` `MediaPipe` `Tkinter` `NumPy`

## What I learned

Pose landmarks give you *points*, not *edges* — the interesting work is in the geometry layer that turns landmark positions into body-contour measurements. Center-out scanning from the skeleton toward the silhouette edge turned out to be much more robust than trying to segment the body outline directly.

---

More projects at [[projects/index|Projects]].
