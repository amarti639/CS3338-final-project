# CS 3338 Final Project - Group 2 - MoonTrek Augmented Reality

**Jira Project URL:** https://your-team-domain.atlassian.net/jira/software/projects/MTAR

## Team

* Alexander Daiz
* Howard Ngo
* Adan Trejo
* Steve Gonzalez
* Angel Martinez

## Overview

The MoonTrek Augmented Reality Application is a web-based platform that allows amateur astronomers to upload telescope or smartphone images of the Moon and receive automatic annotations with lunar feature names, craters, maria (lunar seas), and Apollo landing sites. The application provides a user-friendly interface designed to bridge the gap between amateur astronomers and NASA's professional-grade lunar database.

The system comprises:

**A Vue.js Web Application:** For users to upload moon images, view 3D Earth-Moon-Sun models, and interact with annotated results.

**An Express.js Backend Server:** For handling image uploads, metadata extraction, and API integration with NASA MoonTrek.

**A Python Image Processing Service:** For circle detection and SIFT-based image registration.

**A Three.js 3D Model Service:** For generating dynamic Earth-Moon-Sun models with accurate planetary positioning.

## System Architecture

The application follows this general workflow:

1. **Image Upload:** Users upload moon images through the Vue.js web interface via the UploadPage.vue component, which are sent to the Express.js backend using Multer middleware.

2. **Metadata Extraction:** The backend extracts EXIF data (timestamp and GPS coordinates) from uploaded images and stores it in a MySQL database. If metadata is missing, users manually enter the information through a form.

3. **Circle Detection:** The Python service uses OpenCV to detect and isolate the moon within the uploaded image using the Hough Circle Transform algorithm.

4. **3D Model Generation:** The Three.js service creates a dynamic 3D model of Earth, Moon, and Sun positioned accurately based on the user's timestamp and GPS coordinates, with LRO WAC texture mapping applied to the moon sphere.

5. **Reference Image Generation:** The 3D model captures a reference image matching the user's viewing angle and moon orientation for image registration.

6. **SIFT Image Registration:** The Python service performs SIFT (Scale-Invariant Feature Transform) algorithm to match features between the user image and reference image, calculating a transformation matrix that accounts for rotation, scale, and translation.

7. **NASA API Integration:** The backend fetches crater names, maria, and Apollo landing site coordinates from NASA's MoonTrek API.

8. **Coordinate Mapping:** Using the transformation matrix from SIFT, the system maps lunar feature coordinates from the WAC composite image to the user's image pixel positions.

9. **Overlay Display:** The Vue.js frontend displays the annotated image with crater names, maria labels, and landing site markers positioned accurately on the moon surface.

10. **Interactive Controls:** Users can toggle different overlay layers (craters, maria, landing sites) and adjust opacity using dropdown menus and sliders in the ImageCanvas.vue component.

## Features

* **Web Application:**
   * Image upload with drag-and-drop or click-to-select interface.
   * Automatic EXIF metadata extraction (timestamp, GPS coordinates).
   * Manual metadata entry form when EXIF data is missing.
   * Circle detection to automatically identify and isolate the moon.
   * 3D Earth-Moon-Sun model generation with accurate planetary positioning.
   * LRO WAC texture mapping for photorealistic moon surface.
   * SIFT-based context-aware image registration.
   * NASA MoonTrek API integration for crater, maria, and landing site data.
   * Automatic overlay positioning with coordinate mapping.
   * Interactive layer toggling (craters, maria, landing sites).
   * Adjustable overlay opacity (0-100%).
   * YourMoon database submission with image cropping interface.
   * Machine learning validation for submitted moon images.
   * Responsive design for desktop, tablet, and mobile devices.
   * Real-time processing status indicators.

## Technologies Used

* **Frontend:**
   * Vue.js 3.x
   * Vue Router
   * Three.js (WebGL)
   * HTML5, CSS3, JavaScript (ES6+)

* **Backend:**
   * Node.js 18.x
   * Express.js
   * Multer
   * EXIF-js

* **Database:**
   * MySQL 8.0
   * MySQL Workbench

* **Image Processing:**
   * Python 3.11
   * OpenCV
   * NumPy

* **External APIs:**
   * NASA MoonTrek API
   * NASA JPL LRO WAC

* **Development Tools:**
   * Docker & Docker Compose
   * Git & GitHub
   * Jira
   * TestRail
   * LaTeX
   * Nodemon
   * XAMPP Control Panel
