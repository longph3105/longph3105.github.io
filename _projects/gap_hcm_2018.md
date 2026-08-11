---
layout: page
title: GAP-HMC-2018
description: Development of A Smartphone‑based Laser Measurement System for Assessment of Gap, Flush, and Curvature in Car Body
img: assets/img/publication_preview/2021_07_tie.gif
importance: 1
category: Work
related_publications: true
images:
  compare: true
  slider: true
---

<style>
  .post-title, .post-description {
    text-align: center;
  }
</style>


<h2 align='center'>Overview</h2>

Accurate measurement of **Gap** (horizontal distance) and **Flush** (vertical displacement) between vehicle body panels is a critical quality control metric in automotive manufacturing. Traditional inspection relies either on expensive, rigid inline robotic arms or high-error manual tools (e.g., taper and dial gauges).

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_gap_flush.gif" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
            Gap and Flush definition.
        </div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_02.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
            Conventional manual inspection using a taper and dial gauge.
        </div>
    </div>
</div>

Developed in collaboration with **Hyundai Motor Company (Advanced Manufacturing CAE Team)**, this project engineered a handheld, low-cost **Smartphone-based Laser Measurement (SLM)** device {% cite Pham2021Smartphone %}. By combining a custom 3D-printed triangulation mount, a violet-blue line laser, and real-time mobile computer vision algorithms, the system replaces manual inspection tools directly on the assembly line.

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_01.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
            Left: 3D CAD model of the reverse triangulation frame. Right: Operational handheld prototype with integrated violet-blue laser and iPhone X sensor.
        </div>
    </div>
</div>

---

## Key Hardware & Optical Innovations

* **Reverse Triangulation Geometry:** Designed a reverse optical setup where the smartphone camera is perpendicular to the car body panel while the laser is offset at $45^\circ$. This converts vertical surface shifts ($\partial Z$) directly into horizontal pixel displacements ($\partial y = \partial Z \tan 45^\circ = \partial Z$), maximizing height sensing resolution.
* **Violet-Blue Laser Technology:** Replaced standard red lasers with a 405 nm violet-blue line laser (20 mW) to eliminate light absorption and diffusion across dynamic car body paint colors (e.g., white, metallic silver, deep red, black).
* **Ambient Light Rejection via Shutter Bias:** Adapted a temporal exposure filtering technique, locking camera ISO/sensitivity ($S=22$) and forcing ultra-fast shutter speeds ($t = 1/306\text{ s}$ to $1/12000\text{ s}$) to completely suppress bright factory ambient lighting, isolating a single sharp laser profile.

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_laser_filtering_compare.gif" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
            Left: Default camera capture with ambient light interference. Right: Filtered laser profile with ambient light suppressed.
        </div>
    </div>
</div>

---

## Methodology

The real-time computer vision pipeline runs directly on the mobile device, executing six sequential stages:

1. **Ambient Light Rejection:** Captures high-contrast laser frames using negative exposure bias to reject background illumination {% cite Pham2021Analysis %}.
2. **Sub-Pixel Profile Extraction:** Applies median spatial filtering followed by a **Center-of-Mass-Peak (CoMP)** algorithm to locate sub-pixel laser center coordinates along image columns {% cite Pham2021Improved %}.
3. **Extreme Points Extraction:** Isolates dominant left and right laser contours and fits bounding circles to curved edge gaps to track true panel boundary coordinates {% cite Pham2021Developing %}.
4. **Direct Polynomial Calibration:** Maps extracted pixel gaps and flushes to physical millimeter dimensions via weighted polynomial regression derived from a precision calibration board {% cite Pham2021Smartphone %}.
5. **Real-Time Metric Computation:** Computes final real-world gap and flush parameters using the geometric triangulation {% cite Pham2021Smartphone %}.
6. **Visualization:** Overlays live measurement HUD graphics on screen and transmits inspection logs via Bluetooth/Wi-Fi to central factory databases.

---

Full presentation slides are available below for download: [ppt](https://docs.google.com/presentation/d/1H0pXIbIgaJg7n6uhVvQMmOCNUl5nYpxi/edit?usp=drive_link&ouid=115104576605687193169&rtpof=true&sd=true)

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
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
    </div>
</div>
---

## Performance & Industrial Impact

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_processing_speed.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="caption">
        Real-time measurement visualization on smartphone screen displaying calculated Gap and Flush values.
    </div>
</div>

* **High Measurement Accuracy:** Evaluated under GUM (Guide to the Expression of Uncertainty in Measurement) and AIAG MSA standards. Achieved an expanded measurement uncertainty of **$\pm$ 0.201 mm for Gap** and **$\pm$ 0.154 mm for Flush** on real vehicle bodies, well within the strict automotive tolerance threshold of $\pm$ 0.200 mm$.
* **Real-Time Execution:** Operates at **60 FPS at Full-HD** resolution using lightweight CPU-based mobile processing.
* **Significant Productivity Gain:** Reduced inspection cycle time from **218.26$ man-seconds/car** (manual two-operator method) to **11.01 man-seconds/car**, saving **1.38 man-hours/car** on the production line.
