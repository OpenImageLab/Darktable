# Processing Raw Images with Darktable 5.x

![Darktable Version](https://img.shields.io/badge/darktable-v5.x-darkgreen) ![License](https://img.shields.io/badge/license-CC%20BY--SA%204.0-blue)

## 👋 Welcome

Welcome to a pragmatic, "learn-by-doing" guide to processing raw images using the open-source power of **darktable 5.x**. 

This repository is designed for beginners who want to move beyond basic edits and achieve professional, predictable results. It provides a curated tutorial and a dedicated style file to help you build a solid processing pipeline without drowning in technical theory.

## 📘 The Philosophy

Darktable is incredibly powerful, but its learning curve can be steep. This project was born from the perspective of a new user who learned by doing, taking careful notes, and distilling complex documentation into a repeatable workflow.

**Our Goal:**

* **Pragmatism:** We focus on *what* to do and *why* it matters.
* **Mental Models:** Each step explains the cause-and-effect relationship of the modules, helping you understand how Darktable "thinks."
* **Competence:** By following this pipeline, you will gain the confidence to edit any image and the foundational knowledge to eventually tackle the official user manual and advanced techniques.

If you follow the guided pipeline here, you’ll gain two things: predictable, high-quality results for most images, and a clearer mental model of how Darktable’s modules interact.

## 📂 Resources

### 1. The Tutorial
**Title:** *Tutorial: Processing Raw Images with Darktable 5.x*

This tutorial guides you through a complete workflow: fixing white balance, exposure, geometry, reconstruction, color grading, and sharpening. We provide the tutorial in three specific formats to match your preferred learning style:

| Format | Filename | Best For... |
| :--- | :--- | :--- |
| **GitHub Page** | [Click here to view the web page](https://openimagelab.github.io/darktable/) | **Dual-Monitor Setup:** Perfect for displaying on a secondary screen while you work in darktable on your primary monitor. Includes an interactive Table of Contents. |
| **PDF** | `Tutorial_Processing_Raw_Images_Darktable_5.x.pdf`<br>Click on the Release on the right panel to download the document. | **Print & Read:** Ideal for users who prefer reading printed documents or viewing a fixed layout on a tablet. |
| **DOCX** | [`Tutorial_Processing_Raw_Images_Darktable_5.x.docx`](https://github.com/OpenImageLab/darktable/blob/main/Tutorials/Tutorial-Processing-Plustek8300i-ScannedSlides.docx) | **Personal Notes:** Intended for users who wish to annotate the guide, highlight key sections, or add their own observations directly into the document. |

### 2. The Darktable Style
**Filename:** `Plustek8300i-Exposure-ColorCalibration-Regular.dtstyle`

This `.dtstyle` file is a comprehensive preset pack designed to automate the heavy lifting of the scene-referred workflow. While optimized for Plustek 8200i/8300i raw scans, the logic applies to many raw sources.

**What is included in the style:**
* **Scene-Referred Defaults:** Correct setup for *Sigmoid* and *Exposure* modules.
* **Color & Sharpness:** Most efficient presets to produce well-saturated and sharp images with minimal user intervention.
* **Red Eye Workflow:** A dedicated, pre-configured instance of the *Color Calibration* module for correcting red eyes using channel mixing (as described in the tutorial).

## 🚀 Getting Started

### Installation
To install the style and begin learning:

1.  Download the **Tutorial** in your preferred format from the table above.
2.  Open the tutorial and navigate to the **Installation** section.
3.  Follow the step-by-step instructions to import the `.dtstyle` into your Darktable instance.

### The Workflow at a Glance
The tutorial guides you through a logical pipeline:

1.  **Preparation:** Importing and organizing.
2.  **Base Correction:** Fixing white balance, exposure, and geometry.
3.  **Restoration:** Reconstructing highlights and dehazing.
4.  **Grading:** Aligning histogram channels (fixing color casts/fading) and optimizing dynamic range.
5.  **Finishing:** Sharpening and noise reduction.

## 🤝 Contributing

If you find a typo, have a better explanation for a step, or want to suggest an improvement to the style:

1.  Fork this repository.
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your changes.
4.  Open a Pull Request.

## 📄 License

This project is licensed under the Creative Commons Attribution-ShareAlike 4.0 International License.
