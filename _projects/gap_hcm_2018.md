---
layout: page
title: GAP-FLUSH-HMC-2018
description: Development of A Smartphone‑based Laser Measurement System for Assessment of Gap, Flush, and Curvature in Car Body
img: assets/img/publication_preview/2021_07_tie.gif
importance: 2
category: Work
related_publications: true
---

## Overview

Accurate measurement of **Gap** (horizontal distance) and **Flush** (vertical displacement) between vehicle body panels is a critical quality control metric in automotive manufacturing. Traditional inspection relies either on expensive, rigid inline robotic arms or high-error manual tools (e.g., taper and dial gauges).

Developed in collaboration with **Hyundai Motor Company (Advanced Manufacturing CAE Team)**, this project engineered a handheld, low-cost **Smartphone-based Laser Measurement (SLM)** device {% cite Pham2021Smartphone %}. By combining a custom 3D-printed triangulation mount, a violet-blue line laser, and real-time mobile computer vision algorithms, the system replaces manual inspection tools directly on the assembly line.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_slm_device.jpg" title="SLM 3D CAD & Physical Prototype" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: 3D CAD model of the reverse triangulation frame ($\alpha=45^\circ$). Right: Operational handheld prototype with integrated violet-blue laser and smartphone sensor.
</div>

---

## Key Hardware & Optical Innovations

* **Reverse Triangulation Geometry ($\alpha = 45^\circ$):** Designed a reverse optical setup where the smartphone camera is perpendicular to the car body panel while the laser is offset at $45^\circ$. This converts vertical surface shifts ($\partial Z$) directly into horizontal pixel displacements ($\partial y = \partial Z \tan 45^\circ = \partial Z$), maximizing height sensing resolution.
* **Violet-Blue Laser Technology ($\lambda = 405\text{ nm}$):** Replaced standard red lasers with a $405\text{ nm}$ violet-blue line laser ($20\text{ mW}$) to eliminate light absorption and diffusion across dynamic car body paint colors (e.g., white, metallic silver, deep red, black).
* **Ambient Light Rejection via Shutter Bias:** Adapted a temporal exposure filtering technique, locking camera ISO/sensitivity ($S=22$) and forcing ultra-fast shutter speeds ($t = 1/306\text{ s}$ to $1/12000\text{ s}$) to completely suppress bright factory ambient lighting, isolating a single sharp laser profile.

---

## Methodology

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/figure_workflow.jpg" title="Workflow" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Workflow of the real-time Gap and Flush measurement.
</div>

The real-time computer vision pipeline runs directly on the mobile device, executing six sequential stages:

1. **Ambient Light Rejection:** Captures high-contrast laser frames using negative exposure bias to reject background illumination {% cite Pham2021Analysis %}.
2. **Sub-Pixel Profile Extraction:** Applies median spatial filtering followed by a **Center-of-Mass-Peak (CoMP)** algorithm to locate sub-pixel laser center coordinates along image columns {% cite Pham2021Improved %}.
3. **Extreme Points Extraction:** Isolates dominant left ($L$) and right ($R$) laser contours and fits bounding circles to curved edge gaps to track true panel boundary coordinates {% cite Pham2021Developing %}.
4. **Direct Polynomial Calibration:** Maps extracted pixel gaps ($\partial x$) and flushes ($\partial y$) to physical millimeter dimensions via weighted polynomial regression derived from a precision calibration board.
5. **Real-Time Metric Computation:** Computes final real-world gap ($B_g$) and flush ($B_f$) parameters using the geometric triangulation relation:
$$\begin{bmatrix} \partial X \\ \partial Z \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 0 & 1/\tan\alpha \end{bmatrix} \begin{bmatrix} \partial x \\ \partial y \end{bmatrix} \begin{bmatrix} B_g \\ B_f \end{bmatrix}$$
6. **Visualization:** Overlays live measurement HUD graphics on screen and transmits inspection logs via Bluetooth/Wi-Fi to central factory databases.

---

## Performance & Industrial Impact

* **High Measurement Accuracy:** Evaluated under GUM (Guide to the Expression of Uncertainty in Measurement) and AIAG MSA standards. Achieved an expanded measurement uncertainty of **$\pm 0.201\text{ mm}$ for Gap** and **$\pm 0.154\text{ mm}$ for Flush** on real vehicle bodies, well within the strict automotive tolerance threshold of $\pm 0.200\text{ mm}$.
* **Real-Time Execution:** Operates at **$60\text{ FPS}$ at Full HD ($1920\times 1080$)** resolution using lightweight CPU-based mobile processing.
* **Significant Productivity Gain:** Reduced inspection cycle time from **$218.26\text{ man-seconds/car}$** (manual two-operator method) to **$11.01\text{ man-seconds/car}$**, saving **$1.38\text{ man-hours per car}$** on the production line.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/gap_hcm_2018/slm_measurement_ui.jpg" title="Live SLM UI Output" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Real-time measurement visualization on smartphone screen displaying calculated Gap ($W: 3.32\text{ mm}$) and Flush ($F: 0.06\text{ mm}$) values.
</div>
