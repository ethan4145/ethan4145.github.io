---
layout: default
title: Autonomous Drone Racing Controller
---

<div class="project-page">

  <h1 class="project-page-title">
    Autonomous Drone Racing Controller
  </h1>

  <img
    class="aigp-banner"
    src="/ai_gp/ai_gp_logo.jpg"
    alt="AI Grand Prix">

  <!-- OVERVIEW -->

  <section class="project-section">

    <h2>Overview</h2>

    <p>
      I entered Anduril's AI Grand Prix competition and developed
      autonomy software capable of navigating a drone through a race
      course using only a single FPV camera and inertial measurement
      units. I participated in the qualifying rounds of the competition,
      which took place in a simulated environment.
    </p>

  </section>


  <!-- RESEARCH -->

  <section class="project-section">

    <h2>Research</h2>

    <p>
      I studied the technical specifications for the competition and
      familiarized myself with drone control systems and image processing
      techniques. I used the Mission Planner simulator to understand
      quadcopter mechanics and MAVLink communication protocol.
    </p>

    <figure class="project-figure">
      <img
        src="/ai_gp/mission_planner.jpg"
        alt="Mission Planner Simulator">

      <figcaption>Mission Planner simulator</figcaption>
    </figure>

  </section>


  <!-- CONTROL ARCHITECTURE -->

  <section class="project-section">

    <h2>Designing the Control Architecture</h2>

    <p>
      Before setting up the exact control pipeline, I laid out the
      essential components I would need for my autonomy stack.
    </p>

    <figure class="project-figure diagram-figure">
      <img
        src="/ai_gp/control_components.jpg"
        alt="Initial control architecture concepts">
    </figure>

    <p>
      One complication was that the camera frames and IMU (inertial measurement unit) information came in at different frequencies. In order to use every data point, I designed the program architecture to use less frequent camera frames to re-anchor the target, and more frequent IMU data to perform dead reckoning. I settled on this conceptual control pipeline.
    </p>

    <figure class="project-figure diagram-figure">
      <img
        src="/ai_gp/control_pipeline.jpg"
        alt="Drone control pipeline">
    </figure>

  </section>


  <!-- IMPLEMENTATION -->

  <section class="project-section">

    <h2>Implementation</h2>

    <p>
      I started with the image processor to accurately identify the drone’s target point for every frame. In the competition, the drone must pass through square, orange gates. I built the detector around an HSV mask, morphological operations, a quad fit, and logic to account for overlapped and cut off gates. I utilized AI coding agents to build me a program to hand tune gate detection variables.
    </p>

    <figure class="project-figure">
      <img
        src="/ai_gp/gate_detector_tuner.png"
        alt="Gate Detector Tuner">

      <figcaption>Gate detector hand tuner</figcaption>
    </figure>

    <div class="project-image-grid">

        <figure class="project-grid-image">
            <img
            src="/ai_gp/gate_detector_raw_image.png"
            alt="Raw gate frame">
            <figcaption>Raw Frame</figcaption>
        </figure>

        <figure class="project-grid-image">
            <img
            src="/ai_gp/gate_detector_image_mask.png"
            alt="HSV mask">
            <figcaption>HSV Mask</figcaption>
        </figure>

        <figure class="project-grid-image">
            <img
            src="/ai_gp/gate_detector_image_quad_fit.png"
            alt="Morphology and quad fit">
            <figcaption>Morphology + Quad Fit</figcaption>
        </figure>

        <figure class="project-grid-image">
            <img
            src="/ai_gp/gate_detector_image_final.png"
            alt="Final gate detection">
            <figcaption>Processed Frame</figcaption>
        </figure>

    </div>

    <p>
      I also used AI coding agents to transform my drone control architecture into Python code. I oversaw the implementation of my pipeline and leveraged AI to autonomously iterate through hundreds of test flights on the simulator, continuously tuning the flight controller and debugging the program. The primary control loop uses both P and PD control to navigate the drone through the course.
    </p>

  </section>


  <!-- RESULTS -->

  <section class="project-section">

    <h2>Results</h2>

    <p>
      I successfully passed the first qualifying course of the AI Grand Prix using my autonomy stack. I didn’t manage to complete the second qualifying course, which increased difficulty significantly and hit the limits of my controller. I believe improving my image processor, especially for gates close-range, and exploring a different avenue for the drone control loop would lead me to more successful results.
    </p>

    <video class="project-video" controls preload="metadata">
        <source src="/ai_gp/qr1_controller_overlay_web.mp4?v=2" type="video/mp4">
    </video>

    <video class="project-video" controls preload="metadata">
        <source src="/ai_gp/qr2_first3_overlay_web.mp4?v=2" type="video/mp4">
    </video>

  </section>


  <!-- FINAL THOUGHTS -->

  <section class="project-section">

    <h2>Final Thoughts</h2>

    <p>
      This summer project was a worthwhile effort in exploring autonomous software and control for the first time. I learned not only about drone control and image processing, but also furthered my design thinking and engineering mindset as a whole. Progressing through the full design process—specifications, research, conceptual control architecture design, implementation, testing and revising—was rewarding and it was fun to see my work culminate in the drone racing setting.
    </p>

  </section>

</div>
