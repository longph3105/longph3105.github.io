---
layout: page
title: GAP-FLUSH-HMC-2018
description: Development of A Smartphone‑based Laser Measurement System for Assessment of Gap, Flush, and Curvature in Car Body
img: assets/img/publication_preview/2021_07_tie.gif
importance: 2
category: Work
related_publications: true
images:
  compare: true
  slider: true
---

## Overview

Accurate measurement of **Gap** (horizontal distance) and **Flush** (vertical displacement) between vehicle body panels is a critical quality control metric in automotive manufacturing. Traditional inspection relies either on expensive, rigid inline robotic arms or high-error manual tools (e.g., taper and dial gauges).

<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_gap_flush.gif" title="Gap and Flush Definition" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-3 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_taper_gauge.jpg" title="Using the Taper Gauge" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-3 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_dial_gauge.jpg" title="Using the Dial Gauge" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Gap and Flush definition. Middle: Using the Taper Gauge to measure gap. Right: Using the Dial Gauge to measure flush.
</div>

Developed in collaboration with **Hyundai Motor Company (Advanced Manufacturing CAE Team)**, this project engineered a handheld, low-cost **Smartphone-based Laser Measurement (SLM)** device {% cite Pham2021Smartphone %}. By combining a custom 3D-printed triangulation mount, a violet-blue line laser, and real-time mobile computer vision algorithms, the system replaces manual inspection tools directly on the assembly line.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_slm_device.jpg" title="SLM 3D CAD & Physical Prototype" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_using_slm_device.jpg" title="Using the SLM Device" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: 3D CAD model of the reverse triangulation frame. Right: Operational handheld prototype with integrated violet-blue laser and iPhone X sensor.
</div>

---

## Key Hardware & Optical Innovations

* **Reverse Triangulation Geometry:** Designed a reverse optical setup where the smartphone camera is perpendicular to the car body panel while the laser is offset at $45^\circ$. This converts vertical surface shifts ($\partial Z$) directly into horizontal pixel displacements ($\partial y = \partial Z \tan 45^\circ = \partial Z$), maximizing height sensing resolution.
* **Violet-Blue Laser Technology:** Replaced standard red lasers with a 405 nm violet-blue line laser (20 mW) to eliminate light absorption and diffusion across dynamic car body paint colors (e.g., white, metallic silver, deep red, black).
* **Ambient Light Rejection via Shutter Bias:** Adapted a temporal exposure filtering technique, locking camera ISO/sensitivity ($S=22$) and forcing ultra-fast shutter speeds ($t = 1/306\text{ s}$ to $1/12000\text{ s}$) to completely suppress bright factory ambient lighting, isolating a single sharp laser profile.

---

## Methodology

<swiper-container keyboard="true" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" rewind="true">
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_17.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_18.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_19.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_20.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_21.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_22.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_23.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_24.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_25.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_26.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_27.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slide_28.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
</swiper-container>

The real-time computer vision pipeline runs directly on the mobile device, executing six sequential stages:

1. **Ambient Light Rejection:** Captures high-contrast laser frames using negative exposure bias to reject background illumination {% cite Pham2021Analysis %}.
2. **Sub-Pixel Profile Extraction:** Applies median spatial filtering followed by a **Center-of-Mass-Peak (CoMP)** algorithm to locate sub-pixel laser center coordinates along image columns {% cite Pham2021Improved %}.
3. **Extreme Points Extraction:** Isolates dominant left and right laser contours and fits bounding circles to curved edge gaps to track true panel boundary coordinates {% cite Pham2021Developing %}.
4. **Direct Polynomial Calibration:** Maps extracted pixel gaps and flushes to physical millimeter dimensions via weighted polynomial regression derived from a precision calibration board.
5. **Real-Time Metric Computation:** Computes final real-world gap and flush parameters using the geometric triangulation relation.
6. **Visualization:** Overlays live measurement HUD graphics on screen and transmits inspection logs via Bluetooth/Wi-Fi to central factory databases.

---

## Performance & Industrial Impact

<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_slm_measurement_ui.jpg" title="Live SLM UI Output" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_processing_speed.jpg" title="Processing Speed" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Real-time measurement visualization on smartphone screen displaying calculated Gap and Flush values.
</div>

* **High Measurement Accuracy:** Evaluated under GUM (Guide to the Expression of Uncertainty in Measurement) and AIAG MSA standards. Achieved an expanded measurement uncertainty of **$\pm 0.201\text{ mm}$ for Gap** and **$\pm 0.154\text{ mm}$ for Flush** on real vehicle bodies, well within the strict automotive tolerance threshold of $\pm 0.200\text{ mm}$.
* **Real-Time Execution:** Operates at **60 FPS at Full-HD** resolution using lightweight CPU-based mobile processing.
* **Significant Productivity Gain:** Reduced inspection cycle time from **218.26$ man-seconds/car$** (manual two-operator method) to **11.01 man-seconds/car**, saving **1.38 man-hours/car** on the production line.
