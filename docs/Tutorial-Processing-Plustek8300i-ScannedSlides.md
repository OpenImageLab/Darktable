---

# Basic parameters for jekyll and liquid
layout: default 
title: "Tutorial: Process and improve RAW Images with Darktable 5.x"
author: "Jacques Morand"
date: 2025-12-12 10:30:00 -0500
permalink: /index.html # Use a short, keyword-rich URL

# CRITICAL SEO FIELDS
description: "A highly comprehensive, step-by-step tutorial for beginners on processing RAW image files scanned with a Plustek 8300i using Darktable 5.x for superior and professional film photography results."
keywords: darktable, raw image processing, png files, optifilm scanner plustek 8300i, film or diapositives scanning, tutorial, photography, raw image processing workflow, scene-referred sigmoid workflow, darktable modules and presets
category: darktable # Used for filtering, can also help SEO by association

---

<img src="./media/image75.png"
style="width:6.26772in;height:1.44444in" />

**Tutorial  
Processing RAW Images from Plustek 8300i scanned Slides  
with Darktable 5.x**

<img src="./media/image2.png" style="width:0.48958in"
alt="ligne courte" />

<img src="./media/image21.png" style="width:0.78125in;height:0.75in" />**OpenImageLab**

Jacques Morand  
December 11th, 2025

**© 2025 Jacques Morand. All rights reserved**

# 1. Introduction

## 1.1 A Note for the Beginners

### 1.1.1 The Beginner’s Nightmare

<img src="./media/image19.png"
style="width:2.79584in;height:3.40104in" />

Darktablae is a powerful, free, open-source RAW developer and photo
workflow manager — but for many newcomers it feels more like a toolbox
full of unfamiliar instruments than a clear, guided image-processing
workflow-tool.

The [<u>official Darktable user</u>
<u>manual</u>](https://docs.darktable.org/usermanual/development/en/guides-tutorials/)[^1]
is an indispensable technical reference, yet for beginners it can be
dense: it introduces a lot of image-processing vocabulary and modules
without showing how those pieces fit together in a practical sequence.
Likewise, video tutorials and walkthroughs can be fast, idiosyncratic,
and assume background knowledge; instructors often click through
darktable modules and presets quickly, perform trial-and-error presets
adjustments, or explain advanced concepts that aren’t necessary for a
first solid edit. That makes it hard to build confidence and to
understand why particular corrections are made at specific stages of the
pipeline.

This tutorial was written from the perspective of a new Darktable user
who learned by doing and reading, taking careful notes and distilling
the essential steps into a repeatable, easy-to-follow pipeline. The aim
is pragmatic: to show what to do, why it matters, and how to do it
step-by-step. Each section explains the purpose of the processing step,
the typical problems it solves, and concrete actions you can take in
Darktable — with enough explanation to understand cause → effect without
drowning in theory.

Beginners typically encounter recurring problems that make progress feel
confusing. These include uncertainty about color spaces and when to
apply white balance, misunderstanding which modules are mutually
exclusive or redundant within a given workflow (for example, modules
relevant for scene-referred workflows versus display-referred
workflows), and difficulty knowing the right order of operations so that
later edits don’t undo earlier corrections. This tutorial highlights
those decision points and explains simple rules of thumb to avoid common
pitfalls. It focuses on robust, repeatable choices rather than chasing
small, image-specific tweaks that complicate learning.

If you follow the guided pipeline here you’ll gain two things:
predictable, high-quality results for most images, and a clearer mental
model of how Darktable’s modules interact. Once those foundations are
solid, the official user manual and advanced tutorials will make a lot
more sense — you’ll recognize when a topic is worth diving into and when
it’s safe to skip. The goal is practical competence: enough
understanding to edit confidently and enough curiosity to learn more
intentionally.

### 1.1.2 Common Beginner Pitfalls (short list)

- Confusing scene-referred vs display-referred modules — using certain
  > modules together can produce unexpected results.

- Applying white balance or color calibration at the wrong stage and
  > then losing those corrections during later operations.

- Overusing local adjustments early in the pipeline; global corrections
  > (exposure, contrast, color) should usually come first.

- Relying on a single tutorial or workflow: different image types
  > (portraits, landscapes, scanned slides) need different emphases.

- Skipping soft-proofing or output considerations — editing for the
  > final medium (screen, web, print) avoids surprises later.

### 1.1.3 What you can expect from this tutorial

This tutorial walks you through a clear sequence of steps, explains the
reasoning behind each decision, and includes practical tips to avoid the
most frequent mistakes. It’s intended to help you move from confusion to
control — reliably and efficiently — so you spend more time making
creative choices and less time fighting the interface.

## 1.2 Copyright and Disclaimer

**© 2025 Jacques Morand. All rights reserved.**

This tutorial is an original work based on practical experience acquired
while processing more than hundreds of images in Darktable. The
workflow, module choices, and recommendations presented here reflect the
author’s personal understanding of the software at the time of writing.
They are offered as learning guidance for beginners and are not intended
to represent the only valid approach, nor the most advanced or
professional methodology available.

Although great care has been taken to ensure accuracy, clarity, and
consistency, the content is provided *“as is”* without any
guarantee—explicit or implied—regarding correctness, completeness, or
suitability for a specific purpose. Darktable evolves continuously, and
future versions may change certain behaviors, defaults, or recommended
practices.

The author cannot be held responsible for any errors, misunderstandings,
or results arising from the use of this material. Readers are encouraged
to verify information against the official Darktable documentation and
to adapt the workflow to their own needs, preferences, and evolving
level of expertise.

Reproduction, distribution, or translation of this tutorial, in whole or
in part, is permitted only with prior written permission from the
author.

## 1.3 Context

### 1.3.1 Darktable Version

This tutorial is based on the [<u>Darktable version
5.2.1</u>](https://github.com/darktable-org/darktable/releases/download/release-5.2.1/darktable-5.2.1-win64.exe)[^2]
for Windows 64 bits.

<img src="./media/image26.png"
style="width:1.98958in;height:1.47917in" />

### 1.3.2 Processing of raw Images

#### Where do the raw images come from for this tutorial ?

​The raw images (.DNG) were produced by scanning 24x36 positive films
(Kodachrome, Agfachrome, Fujichrome) on a **Plustek OpticFilm 8300i
Scanner** using the 48-bit HDR raw mode from **SilverFast SE Plus 9**.

<img src="./media/image51.png"
style="width:3.33407in;height:3.65104in" />

#### The Process Workflow

The workflow to process raw images includes operations like fixing white
balance and color calibration, fixing the exposure, reconstructing
highlights, fixing geometry, sharpening and dehazing images, aligning
histogram channels (color cast/fading), and optimizing dynamic range.

#### Crucial Distinction: Scanner Raw vs. Digital Camera Raw

It is vital to understand that a "Raw" file from a scanner behaves
differently than a Raw file from a digital camera (like a Nikon
D-Series, Canon R-Series , or modern Smartphones). While a **digital
camera** records a **3D scene** influenced by changing light (sun,
tungsten), the **scanner** records a **2D physical object** under fixed
internal lighting.

This leads to three specific challenges in Darktable:

> **Linear Gamma (Darkness):**  
> The "48-bit HDR" mode outputs linear gamma data (Gamma 1.0). Unlike
> camera raw files—which Darktable automatically adjusts using a base
> curve or filmic defaults based on metadata—scanner files will appear
> extremely dark and flat initially. This is not underexposure; it is
> simply uncorrected gamma.
>
> **Missing Color Profiles**:  
> Darktable contains a built-in database of color matrices for almost
> every digital camera (e.g., it knows exactly how a Canon R50V sees
> red). It does not have built-in data for a Plustek scanner. You cannot
> rely on "White Balance" presets (Daylight, Cloudy) because the "light
> source" is the scanner's lamp, not the sun. You must rely on the Input
> Color Profile module, ideally using a custom ICC profile created via
> IT8 calibration, or manually correcting color casts.
>
> **Physical Artifacts**:  
> Digital camera noise is electronic; film "noise" is physical grain and
> emulsion damage. Algorithms designed for digital noise (denoise
> profiled) often smudge film grain.

The Workflow To process these .DNG files in Darktable, the standard
scene-referred workflow must be adapted:

> **Input Color Profile:**  
> Assigning the correct scanner ICC profile (if available) or a generic
> linear RGB profile to interpret the device's colors.
>
> **Exposure & Tone Mapping:**  
> Because the file is linear, significant exposure compensation is
> required, followed by Sigmoid or Filmic RGB to apply the necessary
> gamma correction and expand the dynamic range for display.
>
> **White Balance & Color Calibration:**  
> Correcting the color temperature of the scanner's lamp and
> neutralizing the color cast of the film base (aging).
>
> **Channel Alignment:**  
> Using the Color Calibration or RGB Curve to fix "fading," where
> specific channels (often Blue or Magenta) have degraded faster than
> others over decades.
>
> **Corrections:**  
> Cropping (geometry), Dehazing (for oxidized slides), and Sharpening
> (High Pass or Contrast Equalizer) to enhance perceived detail without
> exaggerating grain.

### 1.3.3 Scene-referred Workflow a new Approach

If you have used other Raw processing software in the past (or darktable
prior to version 3.0) you may notice some significant differences from
what you are used to – darktable now uses a **scene-referred approach**
for most of its processing modules. This new approach is used
extensively in cinematography and is known to be much more robust than
the traditional display-referred approach.

In **display-referred processing** (used for instance by Photoshop raw
Image Processing) the data from your raw file is initially compressed
into a range that represents pure black as 0 and pure white as 1, fixing
mid-gray at 0.5. A tone curve is automatically (and irreversibly)
applied to this data to make the image look “good” on your display and
subsequent edits are carried out on top of this already highly-modified
image data. The cost of display-referred is an early loss of the
relationship between pixel luminosity and saturation (usually also
involving hue shifts), which is responsible for the infamous “HDR look”
when the dynamic range increases.

In the real world, “pure black” does not really exist (there is always
some light) and there is no limit to how bright things can be (so no
“pure white” either). **Scene-referred processing** attempts to retain
the physical properties of the scene for as long as possible by
**placing the raw data on an unbounded linear scale** and only
compressing the data to the dynamic range of your display after image
processing is complete.

In a scene-referred workflow many common tools (tone curves and levels
by Photoshop for example) are *no longer useful ways to manipulate the
image*, since they rely on now-invalid definitions of black, white and
gray. Experienced users may need to learn new techniques and discard old
ones, but will be rewarded with much more robust and predictable
outputs.

*Note: The scene-referred workflow in darktable enables the filmic rgb /
sigmoid and exposure modules by default when you open new images in the
darkroom view.*

## 1.4 The 4 most important basic Adjustments

The following basic adjustments are fundamental to scene-referred
editing and will be required, to some extent, on the majority of images.
You can usually produce a good-looking image with these steps alone.

### 1.4.1 White balance and color calibration - Module Color calibration

Most processing software uses a traditional temperature/tint model for
adjusting the white balance of an image. In darktable, the **Color
calibration module** provides a much more robust and flexible approach,
allowing you to explicitly define the color of the light source. This is
particularly useful for scenes illuminated by artificial lighting.

*Note: The white balance module is still enabled in this approach, but
its settings normally should not be altered.*

### 1.4.2 Exposure - Module Exposure

First, set the overall (average) brightness of the image (the mid-gray
point) by adjusting the exposure slider in the **Exposure module**. This
is a purely artistic setting and should be defined based on your intent
– for example, for a high-key image you will set the average brightness
to be lighter than for a low-key image. The color assessment mode
provides you with two reference points to assist with this by
surrounding the image with a white frame against a middle-gray
background.

At this point, don’t worry if the brightest parts of your image lose
detail – this can be recovered in the next step.

*Note: The lens correction module can also affect the image brightness
so you may want to consider enabling it before adjusting exposure.*

### 1.4.3 Set white and black points - Module Sigmoid

With Sigmoid, the setting of white and black points is done using the
parameters “Target black/white luminance” of the **Sigmoid module**.

### 1.4.4 Color Calibration - Module Color calibration

Traditional white balance correction attempts to ensure that whites and
grays are really neutral (R = G = B) and doesn’t really try to manage
the impact on other colors. The CAT tab of the **Color calibration
module** extends this treatment to handle the remainder of the color
range and works in a color space designed specifically for chromatic
(color) adaptation. As with traditional white balance controls you can
select a patch of neutral gray in your image to calculate the white
balance, or use a selection of other automatic and manual methods. The
default settings use the white balance from the image’s Exif data and
are usually sufficient.

*Note: If you need to make adjustments in the color calibration module,
you may want to also revisit any saturation corrections you made earlier
in the color balance rgb module.*

# 3. Darktable initial Settings

<img src="./media/image13.png"
style="width:0.3937in;height:0.33742in" />Do these initial settings only
once after installing darktable.

Initial Settings:

- Import raw Images from PC to darktable Library

- Import Style for scanner Plustek 8300i

- Set Darktable Preferences

- Useful darktable Keyboard Shortcuts

## 3.1 Import raw Images from PC to darktable Library

<span class="mark">►</span>Select \[Lightable\] from darktable top menu
bar or click on key \[**l**\] on the keyboard.

<img src="./media/image35.png" style="width:6.5in;height:0.31944in" />

►Open “Import” from left panel, then click on “Add to library”

<img src="./media/image30.png"
style="width:2.96875in;height:4.8125in" />

►Click on \[+\] to add a new Place from where the images should be
found, then select the place.

►Select the folder(s) where the images should be found

►Activate the option:

- Select only new images

  > Recursive directory

  > Ignore non-raw images

►Click on \[Add to library\] to import the raw images into the darktable
database.

<img src="./media/image10.png" style="width:6.5in;height:5.15278in" />

## 3.2 Import Style for scanner Plustek 8300i

A special style with according Presets for required Modules has been
created in order to process 48 bits HDR raw images scanned with the
scanner Plustek-8300i Series.

This style is named
**“Plustek-8300i-Exposure-ColorCalibration-Regular”**

►On right Panel of Lighttable, open sheet “Styles”

►Under “Filter style names” select
“Plustek-8300i-Exposure-ColorCalibration-Regular”

►Click on “Import…”

*Note: This special style is now imported into darktable and ready to be
used for the workflows.*

<img src="./media/image78.png"
style="width:4.45201in;height:6.39063in" />

## 3.3 Set Darktable Preferences

►Click on the Preference Button

<img src="./media/image41.png" style="width:6.5in;height:0.61111in" />

►Select the “Processing” tab.

►Make sure that the option “Scene-referred(Sigmoid)” is selected.

►Click on \[Escape\] to store the preferences

<img src="./media/image47.png" style="width:6.5in;height:1.77778in" />

►Select the “General” tab

►Set the interface language to “English(en@truecase)

<img src="./media/image34.png" style="width:6.5in;height:2.18056in" />

**3.4 Useful darktable Keyboard Shortcuts**

These shortcuts are very useful and can be used in any workspace of
Darktable.

<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 23%" />
<col style="width: 59%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Shortcut Key</strong></th>
<th><strong>Shortcut Name</strong></th>
<th><strong>Explanation</strong></th>
</tr>
<tr class="odd">
<th><strong>l</strong></th>
<th>Lighttable workspace</th>
<th><p>Press keyboard letter <strong>l</strong> to switch to Lighttable
workspace.</p>
<p><em>The Lighttable workspace is used to select the raw image(s) to
process in Darkroom workspace</em></p></th>
</tr>
<tr class="header">
<th><strong>d</strong></th>
<th>Darkroom workspace</th>
<th><p>Press keyboard letter <strong>d</strong> to switch to Darkroom
workspace.</p>
<p>The Darkroom workspace is used to process the raw images.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# 4. Workflow to process raw Images

<img src="./media/image13.png"
style="width:0.3937in;height:0.33742in" />Repeat this workflow for each
raw image to be processed.

## 4.1 Image Selection and Processing in darktable

►In Lighttable workspace, select the image to process by clicking once
on that image. A white box appears around the selected image.

<img src="./media/image68.png" style="width:6.5in;height:4.93056in" />

►Click letter \[d\] on keyboard (d stands for darktable). The Darkroom
processing workspace appears.

*Note: Another way to active darkroom processing is to double-click on
the image to process.*

## 4.2 Clear Modules History

►In the Darkroom workspace, click on the triangle
<img src="./media/image23.png"
style="width:0.19792in;height:0.20833in" /> to open the History menu,
then click on the Reset Symbol <img src="./media/image77.png"
style="width:0.1875in;height:0.16667in" /> in order to clear the history
of the image processing.

<img src="./media/image81.png"
style="width:4.80208in;height:6.05208in" />

► Confirm the History Reset by clicking on \[Yes\] button

<img src="./media/image61.png"
style="width:3.61458in;height:1.03125in" />

## 4.3 Apply Style “Plustek-8300i”

A specific style “**Plustek-8300i-Exposure-ColorCalibration-Regular**”
with according modules has been created to process diapositives scanned
with the scanner Plustek 8300i in mode 48-bits HDR raw.

►On the bottom of the left darktable panel, click on button
<img src="./media/image18.png"
style="width:0.28597in;height:0.22709in" /> to open the styles window.

<img src="./media/image12.png"
style="width:6.35546in;height:7.73438in" />

►Click on Style “Plustek-8300i-Exposure-ColorCalibration-Regular” to
select it.

►Make sure that on the darktable right panel, the “Show only active
module” is activated
<img src="./media/image6.png" style="width:0.4305in;height:0.24479in" />  
The panel shows only active modules. Their ON button is lightened
<img src="./media/image6.png" style="width:0.4305in;height:0.24479in" />

> *The button is lightened* <img src="./media/image6.png"
> style="width:0.41766in;height:0.23993in" /> *if the command is
> activated*
>
> *The button is greyed* <img src="./media/image38.png"
> style="width:0.34452in;height:0.24479in" /> *if the command is not
> activated*

<img src="./media/image29.png" style="width:3.75in;height:3.92708in" />

## 4.4 Process the Exposure

The **Exposure Module** allows the processing of the overall brightness
of an image.

To process the Exposure of the image, open the module “Exposure” on the
right panel.

►Click on “Exposure Bar” to open the menu of the Exposure Module

<img src="./media/image37.png"
style="width:3.55208in;height:0.72917in" />

►Make sure that the Exposure Mode is set to “Manual”

<img src="./media/image15.png"
style="width:3.53125in;height:0.61458in" />

<img src="./media/image13.png"
style="width:0.3937in;height:0.33742in" /> Pay attention to not
deactivate the Exposure Module by clicking on its ON button

<img src="./media/image56.png"
style="width:3.53125in;height:0.54167in" />

►Under the Parameter Exposure,

> Move the triangle Slider <img src="./media/image9.png"
> style="width:0.20833in;height:0.19792in" /> left ← to <u>decrease</u>
> the Exposure (lightness) or
>
> Move the triangle Slider <img src="./media/image9.png"
> style="width:0.20833in;height:0.19792in" /> right → to <u>increase</u>
> the Exposure (lightness) of the image.

<img src="./media/image49.png"
style="width:3.55208in;height:2.15625in" />

► On the image, use the scroll wheel up / down to zoom / de-zoom the
image, in order to set the correct exposure of the subject.

► Click on the Exposure bar again to store the Exposure in darkroom
database.

<img src="./media/image37.png"
style="width:3.55208in;height:0.72917in" />

## 4.5 Process the Color Calibration

The **Color calibration module** is a powerful tool for adjusting color
balance, creating grayscale images, and performing color grading. It
serves as a reference point for ensuring whites and grays appear neutral
by correcting the "color cast" from the light source and allows for
fine-tuning white balance, saturation, and brightness. The module can
also be used for creative purposes, like creating black and white
conversions with film-like presets or adjusting RGB channels for color
grading.

The color calibration is done using the Module “Color calibration” on
the left panel.

►Open the module “Color calibration”

<img src="./media/image27.png"
style="width:3.51042in;height:0.32292in" />

►Click on button <img src="./media/image60.png"
style="width:0.40625in;height:0.20833in" /> to select the Chromatic
Adaptation Transform (CAT)

►By the parameter Adapdation, open the combobox
<img src="./media/image28.png"
style="width:0.20833in;height:0.15625in" />

►Select CAT16(CIECAM16)

<img src="./media/image74.png"
style="width:3.54167in;height:3.45833in" />

►Clink on eyedropper <img src="./media/image5.png"
style="width:0.29167in;height:0.14583in" />to adapt automatically the
chromatic of the whole image

<img src="./media/image24.png"
style="width:3.92708in;height:1.21875in" />

►Click on the Color calibration bar again to close the color calibration
menu and store the color calibration in darktable database.

<img src="./media/image27.png"
style="width:3.51042in;height:0.32292in" />

## 4.6 Store the processed image in darktable database

The workflow to process the raw image based on the “*Scene referred
Sigmoid*” method and the Style
“*Plustek8300i-Exposure-ColorCalibraton-Regular*” is now terminated.

►On keyboard, click on letter **l** to store the image into darktable
database and open the workspace lighttable to process the next image.

► On workspace Lighttable, the processed image appears in a white box
and the color of the image is now similar to the definitive result,
ready to be exported in format TIFF or JPEG.

<img src="./media/image42.png"
style="width:5.45833in;height:3.02083in" />

# 5. Export processed Images

The export workflow is done in the Lighttable workspace, using the right
panel.

►On the Lighttable workspace, click once on the image to be exported.

*Note: To export multiple images, use **SHIFT+Click** to select a range
or **CTRL+Click** to select multiple disseminated images.*

►Click on the triangle left to the bar “Export” to open the export menu.

<img src="./media/image58.png"
style="width:4.70833in;height:0.90625in" />

In the group “Storage options” :

> ►For the parameter “Target storage” select in the combobox
> <img src="./media/image33.png"
> style="width:0.1875in;height:0.16667in" /> “File on disk”
>
> ►For the filepath line, click on the folder icon
> <img src="./media/image62.png"
> style="width:0.26042in;height:0.1875in" /> to browse to the directory
> where to store the image to be exported

*Note: The directory path is terminated by the variable
“/\$FILE_NAME”.  
This variable will be replaced by the name of the original raw image.
This name will be extended with the extension corresponding to the
format of the exported image, ie .jpeg or .tiff.*

►For the parameter “On conflict”, select in the combobox
<img src="./media/image33.png"
style="width:0.1875in;height:0.16667in" /> the option “Create unique
filename”.

*Note: If the filename with extension already exists, a number will be
added to the filename.*

<img src="./media/image14.png"
style="width:4.69792in;height:1.07292in" />

## 5.1 Export processed image in TIFF Format

In the group “**Format options**”,

> ►Setup the following values to the following parameters

| **Parameter** | **Value**        | **Description** |
|---------------|------------------|-----------------|
| File format   | TIFF             |                 |
| Bit depth     | 16 bits          |                 |
| Pixel type    | Unsigned integer |                 |
| Compression   | Uncompressed     |                 |
| B&W grayscale | No               |                 |

<img src="./media/image11.png" style="width:4.69792in;height:1.375in" />

In the group “**Global options**”,

> ►Setup the following parameters:

<table>
<colgroup>
<col style="width: 16%" />
<col style="width: 18%" />
<col style="width: 65%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Parameter</strong></th>
<th><strong>Value</strong></th>
<th><strong>Description</strong></th>
</tr>
<tr class="odd">
<th>Set size</th>
<th>In pixels (for file): 0 x 0 px</th>
<th><p>Maximum dimensions in pixels, inches, or cm. Setting a dimension
to zero leaves it unconstrained.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em><mark>Set to zero to export at original dimensions (after
cropping).</mark></em></p>
</blockquote></li>
<li><blockquote>
<p><em><mark>Use to downscale for specific uses like social
media.</mark></em></p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Allow upscaling</th>
<th>No</th>
<th><p>Option to allow the image to be exported at a larger size than
the original.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em>Disable (No).</em></p>
</blockquote></li>
<li><blockquote>
<p><em>Enable (Yes) only if you need to export at a higher resolution
than the source file to mitigate pixelation.</em></p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>High quality resampling</th>
<th>No</th>
<th><p>Algorithm used to create the new image. "High quality resampling"
takes longer but improves quality.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em>Disable (No)</em></p>
</blockquote></li>
<li><blockquote>
<p><em>Enable (Yes) only for better results for TIFF Format</em></p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Store masks</th>
<th>No</th>
<th></th>
</tr>
<tr class="odd">
<th>Profile</th>
<th>Image settings</th>
<th><p>The color space for the exported image. sRGB is standard for web
and most home printing.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em>Image settings.</em></p>
</blockquote></li>
<li><blockquote>
<p><em>Use sRGB only for online use. Consider other profiles for
specific printers or workflows if needed.</em></p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Style</th>
<th>None</th>
<th><p>Add an additional style for the exporting of the image.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em>Do not add additional style for exporting (None)</em></p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<img src="./media/image55.png" style="width:4.69792in;height:2in" />

In the group “**Start export”**

> ►Click on the bar “Start export” to begin the export of the selected
> image(s).

<img src="./media/image45.png"
style="width:4.61458in;height:0.36458in" />

## 5.2 Export processed image in JPEG Format

In the group “**Format options**”,

> ►Setup the following parameters:

<table>
<colgroup>
<col style="width: 21%" />
<col style="width: 16%" />
<col style="width: 61%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Parameter</strong></th>
<th><strong>Value</strong></th>
<th><strong>Description</strong></th>
</tr>
<tr class="odd">
<th>File format</th>
<th>JPEG (8-bits)</th>
<th></th>
</tr>
<tr class="header">
<th>Quality</th>
<th>95</th>
<th><p>JPEG compression level, 0-100. Higher values mean less
compression and better quality, but larger file sizes.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em>95 for high quality (archiving, printing);</em></p>
</blockquote></li>
<li><blockquote>
<p><em>90 for a good balance (web, uploads).</em></p>
</blockquote></li>
<li><blockquote>
<p><em>80 is a good starting point to see a balance between file size
and quality.</em></p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Chroma subsampling</th>
<th>4:2:0</th>
<th><p>Chroma subsampling in Darktable JPEG exports reduces file size by
lowering the color detail, which is often unnoticeable for most photos
but can save space.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em>The most common, highly compressed ratio is 4:2:0 (which
significantly reduces file size).</em></p>
</blockquote></li>
<li><blockquote>
<p><em>The most common ratio for no subsampling is 4:4:4 (no
subsampling)</em></p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<img src="./media/image48.png"
style="width:4.69792in;height:1.07292in" />

In the group “**Global options**”,

> ►Setup the following parameters:

<table>
<colgroup>
<col style="width: 16%" />
<col style="width: 18%" />
<col style="width: 64%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Parameter</strong></th>
<th><strong>Value</strong></th>
<th><strong>Description</strong></th>
</tr>
<tr class="odd">
<th>Set size</th>
<th>In pixels (for file): 0 x 0 px</th>
<th><p>Maximum dimensions in pixels, inches, or cm. Setting a dimension
to zero leaves it unconstrained.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em><mark>Set to zero to export at original dimensions (after
cropping).</mark></em></p>
</blockquote></li>
<li><blockquote>
<p><em><mark>Use to downscale for specific uses like social
media.</mark></em></p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Allow upscaling</th>
<th>No</th>
<th><p>Option to allow the image to be exported at a larger size than
the original.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em>Disable (No).</em></p>
</blockquote></li>
<li><blockquote>
<p><em>Enable (Yes) only if you need to export at a higher resolution
than the source file to mitigate pixelation.</em></p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>High quality resampling</th>
<th>No</th>
<th><p>Algorithm used to create the new image. "High quality resampling"
takes longer but improves quality.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em>Disable (No)</em></p>
</blockquote></li>
<li><blockquote>
<p><em>Enable (Yes) only for better results for TIFF Format</em></p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Profile</th>
<th>Image settings</th>
<th><p>The color space for the exported image. sRGB is standard for web
and most home printing.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em>Image settings.</em></p>
</blockquote></li>
<li><blockquote>
<p><em>Use sRGB only for online use. Consider other profiles for
specific printers or workflows if needed.</em></p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Style</th>
<th>None</th>
<th><p>Add an additional style for the exporting of the image.</p>
<p><em>Recommandations:</em></p>
<ul>
<li><blockquote>
<p><em>Do not add additional style for exporting (None)</em></p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<img src="./media/image66.png"
style="width:5.38763in;height:2.26563in" />

# 6. Modules of Style Plustek-8300i

The following modules are useful for raw image processing. They are
applied automatically by using the Style
“Plustek8300i-Exposure-ColorCalibration-Regular”.

The modules are applied sequentially bottom-up by darktable.

Modules with the grayed ON button <img src="./media/image50.png"
style="width:0.19792in;height:0.22917in" /> are applied automatically
and their setting cannot be changed.

<img src="./media/image76.png"
style="width:3.93229in;height:6.47736in" />

## 6.1 Module White balance

In darktable's scene-referred workflow, use the **Color Calibration
module** for white balancing by picking a neutral gray or by manually
adjusting the illuminant.

While the White Balance module is still used for demosaicing, you should
generally **leave its default settings** and perform the actual white
balance adjustments in the Color Calibration module, especially with the
modern chromatic adaptation settings enabled.

<img src="./media/image4.png"
style="width:3.46875in;height:2.11458in" />

## 6.2 Module Highlight reconstruction

<img src="./media/image13.png"
style="width:0.3937in;height:0.33742in" />Use only if some highlight
areas in the image have been clipped on all channels.

The highlight reconstruction module rebuilds areas where highlights have
been clipped on all channels or individually.

To use it, enable the display mask to see the areas that need
reconstruction.

Adjust the threshold to select the highlight areas you want to
reconstruct.

Use the blur control to soften the transition between clipped and
non-clipped pixels for a smoother blend.

## 6.3 Module Orientation

The orientation of the image is done automatically.

Rotate only if the image is inverted or rotated 90°.

## 6.4 Module Tone equalizer Plustek-8200i

In a darktable scene-referred workflow, the Sigmoid module is used for
global dynamic range compression and tone mapping, while the **Tone
Equalizer** is used for **targeted, localized adjustments to specific
brightness zones**.

While Sigmoid can be used to achieve a basic tone mapping effect, the
Tone Equalizer provides finer control over highlights, shadows, and
midtones after the initial Sigmoid-based tone compression has been
applied. This combination allows for a highly flexible and precise
approach to image editing in the scene-referred pipeline.

<img src="./media/image13.png"
style="width:0.3937in;height:0.33742in" /> A contrast soft curve is
applied automatically on the image in order to increase the contrast in
the mid-tones.

<img src="./media/image20.png"
style="width:3.51042in;height:4.32292in" />

## 6.5 Module Crop - Plustek-8200i

<img src="./media/image13.png"
style="width:0.3937in;height:0.33742in" />Use only if the image is not
centered and has unwanted borders, for example black or white borders.

The crop module is typically placed early in the pixelpipe, before the
sigmoid module. This ensures that any subsequent processing, including
the tone mapping done by sigmoid, is only applied to the area within the
defined crop.

To crop an image in the darkroom view:

►Locate and open the crop module (sometimes called "crop and rotate" or
similar depending on darktable version/configuration). It is usually
found in the "utility modules" group or the Quick Access Panel (QAP).

►Drag the edges or corners of the cropping rectangle that appears on
your image to define the desired composition.

►Or set the margins using the Left, Right, Top, Bottom sliders

►You can also use tools within the module for specific aspect ratios or
to straighten the image.

<img src="./media/image39.png"
style="width:3.57292in;height:2.70833in" />

## 6.6 Module Input color profile

<img src="./media/image13.png"
style="width:0.3937in;height:0.33742in" />This module is applied
automatically.

When you open a raw file in darktable with scene-referred defaults
enabled, the pixelpipe is automatically configured as follows:

- **Input color profile (Default: linear Rec2020 RGB)**  
  > This module is one of the first in the pipeline. It takes the
  > specific color data from your camera's raw file (using a standard or
  > enhanced color matrix for your camera model) and converts it into a
  > standardized, linear working color space.

  - **Recommendation**: The standard recommended practice in darktable
    > for film scans is to manually set the Input profile parameter to
    > match your chosen Working profile, which is typically linear
    > Rec2020 RGB.

  - This tells darktable that the data coming in is already in the
    > linear working space, effectively bypassing a potentially
    > incorrect input matrix and ensuring the raw scanner data is
    > treated as linear scene-referred data from the start.

- **Working Profile (Default: linear Rec2020 RGB)**:  
  > The image data between the input color profile module and the
  > sigmoid module resides in this high-gamut, linear working space. The
  > default is typically "linear Rec. 2020 RGB," which is a good choice
  > for most cases due to its broad color range.

- **Gamut clipping (Default: Off):**  
  > The gamut clipping option in the input color profile module is off
  > by default in the scene-referred workflow.

  - **Purpose**: Highly saturated colors, especially in strong blues or
    > certain bright light sources, can sometimes cause "black pixel
    > artifacts" when converted into the working color space. Activating
    > gamut clipping helps mitigate these specific artifacts by
    > confining the colors to the selected RGB gamut of the working
    > profile (e.g., linear Rec. 2020 RGB).

  - **Recommendation**: In most cases, leaving this option disabled
    > ("off") is recommended to maintain the full color dynamics of your
    > raw file. You only need to enable it if you notice specific
    > artifact issues in highly saturated regions of your image.

  - This module acts as the display transform, taking the high dynamic
    > range, scene-referred data from the linear working profile and
    > compressing it into the low dynamic range required by your monitor
    > (e.g., sRGB). It operates on the linear RGB data provided by the
    > working profile.

<img src="./media/image65.png" style="width:3.5in;height:1.09375in" />

## 6.7 Module Color calibration

See Process the color calibration in chapter 3.

## 6.8 Module Diffuse or sharpen - Dehaze - Default

In darktable's scene-referred workflow, the diffuse or sharpen module's
dehaze preset is the recommended tool for **removing atmospheric haze**,
and it works in concert with the sigmoid module.

The key to a successful scene-referred workflow is the order of
operations:

- diffuse or sharpen (with the dehaze preset) should be placed in the
  > scene-referred part of the pixelpipe, before the sigmoid module.

- The sigmoid module is the last step in the scene-referred pipeline,
  > acting as the display transform.

By applying dehazing before tone mapping, you work on the linear light
data (scene-referred space), which is physically accurate and helps
avoid artifacts that can occur when processing tone-mapped
(display-referred) data.

Dehazing (diffuse or sharpen): The dehaze preset within the diffuse or
sharpen module uses physical diffusion models to reverse the effects of
light scattering in the atmosphere. It increases local and global
contrast by targeting specific spatial frequencies (detail sizes) where
haze causes diffusion.

<img src="./media/image57.png"
style="width:3.55208in;height:5.66667in" /><img src="./media/image64.png"
style="width:3.53125in;height:1.60417in" />

## 6.9 Module Diffuse or sharpen - Plustek 8200i

In darktable's scene-referred workflow, the diffuse or sharpen module's
Plustek 8200i preset is the recommended tool for **increasing the
sharpness** of the image, and it works in concert with the sigmoid
module.

This is the recommended, modern module for sharpening in a
scene-referred RGB space, preferred over the legacy sharpen module which
operates in the less optimal Lab color space.

**Sharpness Option:** Using the strong sharpness preset is an available
option. This preset, like others in the module, uses a multi-scale
approach and is designed to deblur or enhance local contrast without
introducing the unwanted halos often seen with older sharpening methods
when pushed too far. The exact visual impact will depend on your
specific image content and resolution.

**Judgement:** Local contrast and sharpness adjustments are best judged
when zoomed out, as viewing at 100% does not represent the final image
size.

<img src="./media/image36.png"
style="width:3.54167in;height:5.04167in" /><img src="./media/image8.png"
style="width:3.53125in;height:2.28125in" />

## 6.10 Module Color Balance RGB - Plustek-8200i

**Using the basic color fullness:**

The Plustek-8200i preset applying the **vibrant colors preset** in the
darktable color balance RGB module is a valid and effective approach for
**enhancing the saturation** of your scanned positive slides within the
scene-referred workflow. This preset is designed to **make colors pop,
especially less saturated ones, without pushing already vibrant colors
too far out of gamut.**

**Preset Application:**

The basic color fullness: **vibrant colors preset** for Plustek-8200i
applies a set of initial adjustments to the module's sliders of the
**Perceptual saturation grading**:

- Global saturation: +20%

- Shadows: +50%

- Midtones: 0%

- Highlights: -25%

**Scene-Referred Integration**:

This module is built for the scene-referred pipeline and operates
internally in a **linear RGB color space**, ensuring its calculations
are physically accurate and less prone to artifacts compared to older,
display-referred saturation methods (*now-deprecated vibrance module*).

<img src="./media/image72.png"
style="width:3.27086in;height:4.70313in" />

<img src="./media/image80.png"
style="width:3.47917in;height:1.96875in" />

## 6.11 Module Sigmoid - Plustek-8200i

The preset “Plustek-8200i” of the module Sigmoid is based on the
"**Scene referred default**" preset for the sigmoid module. This preset
uses **conservative default values** intended to provide a predictable
and robust **conversion from your high-dynamic-range scene data to a
standard dynamic range** display output.

**Prioritize Exposure:**  
Before making changes in the sigmoid module, the first and most critical
step is to adjust the exposure module so that your image's midtones are
correctly positioned. The sigmoid curve works best when fed a properly
exposed scene-referred image.

**Contrast / Skew:**  
A moderate contrast value is applied by default, balancing the need for
an immediately pleasing image with the goal of preserving creative
freedom in other modules.

- Contrast: 1.500

- Skew: +0.00

**Preserve Hue:**  
The module aims to preserve hue reasonably well by default, avoiding
artificial color shifts like excessive yellowing in highlights, which
can occur with simpler tone mapping curves. The user manual notes that
an approximation of preserved perceptual hue is used by default.

**Display Luminance - Target White/Black**  
These values are set to sensible defaults (e.g., target white around
110-125 cd/m² and target black near zero) to fit the image to a typical
monitor's dynamic range. These settings ensure that the full range of
your 48-bit HDR scan is mapped appropriately without clipping important
data, especially in the highlights.

<img src="./media/image59.png"
style="width:3.52083in;height:0.3125in" /><img src="./media/image7.png"
style="width:3.52083in;height:5.77083in" />

## 6.12 Module Local contrast - Plustek-8200i

The Plustek-8200i preset uses the **Clarity** preset in darktable's
local contrast module and provides an effect similar to the "clarity"
slider found in other software, primarily by **boosting the contrast in
the mid-tones and enhancing local detail**. This is an effective way to
give your high-resolution positive slide scans a more defined, crisp
look.

The local contrast module achieves its effect using either a local
**laplacian filter** (default) or an unnormalized bilateral filter,
operating exclusively on the Luminance (L) channel from the Lab color
space.

The Clarity preset specifically adjusts the internal parameters to:

> **Boost Midtone Contrast:**  
> It applies an S-shaped curve to the midtones, making the darker
> midtones darker and the brighter midtones brighter. This enhances the
> perceived detail and texture without significantly altering global
> contrast, which affects the overall tonal range (highlights to
> shadows) of the image.
>
> **Balance Highlights and Shadows:**  
> The preset subtly adjusts highlight and shadow compression parameters
> to ensure a natural look and avoid clipping or harsh halos around
> edges.

<img src="./media/image25.png"
style="width:3.58333in;height:2.33333in" />

## 6.13 Module Output color profile

<img src="./media/image13.png"
style="width:0.3937in;height:0.33742in" />This module is applied
automatically by darktable.

In darktable, the output color profile module determines the **final
color space for your exported images**. The choice of profile depends
entirely on the intended use of the image (web display, printing, etc.).

**Key Considerations for the Output Color Profile**

The primary goal of the output color profile module is to convert your
image data from darktable's internal working space (typically a wide
gamut linear RGB like **linear Rec2020 RGB**) to a smaller,
application-specific color space.

> **For Web and General Display and TIFF Printing:**  
> The general recommendation is to stick to **sRGB**. Nearly all
> consumer monitors, web browsers, and smartphones are optimized for the
> sRGB color space. Exporting in sRGB ensures that your images will
> appear as intended on the widest variety of devices.
>
> **For Professional Printing:**  
> If you are preparing files for a professional print lab and they
> specify a different profile, you should use that profile (commonly
> Adobe RGB or sometimes CMYK, though darktable works in RGB). Printers
> often prefer Adobe RGB because it has a wider gamut than sRGB, which
> can lead to better quality prints if the printer is capable of
> reproducing those colors.

**Recommandations:**

The most common and safest approach for general purposes is:

- Set the output color profile in the module (or more commonly, in the
  > export module's settings in the lighttable or darkroom sidebar) to
  > **sRGB**.

- Ensure you **embed the color profile in the output file** (*which
  > darktable does automatically for supported formats like JPEG and
  > TIFF*). This allows other color-managed applications to interpret
  > the colors correctly.

<img src="./media/image40.png" style="width:3.5625in;height:0.625in" />

# 7. Other useful Modules

<img src="./media/image13.png"
style="width:0.3937in;height:0.33742in" />These Modules are not included
in the style “Plustek-8300i”. They can be added to the workflow when
some special processing is required.

►To add an additional module, type its name or part of it in the Search
bar of the Darkroom workspace, then click \[Return\] on the keyboard.

<img src="./media/image69.png"
style="width:3.76042in;height:2.95833in" />

## 7.1 Module Rotate and perspective

The rotate and perspective module can be used to adjust the angle of the
image or to simulate the functionality of a tilt/shift lens by altering
the perspective, making converging horizontal and/or vertical lines
parallel (keystone correction). This latter technique is most commonly
used for architectural photography. If you just want to correct the
angle of the horizon you can do this by right-clicking and dragging
along the horizon line.

<img src="./media/image63.png"
style="width:3.53125in;height:2.59375in" />

## 7.2 Module Retouch

Use the retouch module to remove spots and unwanted objects by replacing
pixels with detail from elsewhere in the image. This module also offers
powerful techniques for removing large-scale objects (such as spots or
blemishes) while leaving fine-scale details (like hairs and follicles)
intact. The most common use for this module is to remove dust spots from
images or blemishes from skin.

<img src="./media/image44.png" style="width:3.51042in;height:3.125in" />

## 7.3 Red Eyes Removal

Red-eye occurs because the flash reflects off the retina, blasting the
Red Channel with high values while the Green and Blue channels remain
naturally dark (which is what the pupil should look like).

In Darktable 5.2.1, there is not a specific module to remove red eyes in
images, like in Photoshop.

To fix this, we will use a Channel Mixer strategy: we will tell
Darktable to replace the data in the Red channel with a mix of the Green
and Blue channels only inside the pupil.

The workflow is straightforward and requires a second instance of the
Color calibration Module and the use of masks to set the position and
size of the “red” pupils.

#### 1. Create a New Instance of Color calibration Module

►Create a second instance of the “Color calibration Module” by clicking
on the “Multiple instance action” button <img src="./media/image70.png"
style="width:0.22917in;height:0.21875in" /> of the current Color
calibration Module.

<img src="./media/image16.png"
style="width:2.47396in;height:2.44871in" />

►Select option “New instance”

<img src="./media/image17.png"
style="width:1.54167in;height:1.41667in" />

#### 2. Disable Chromatic Adaptation Transform (CAT)

By default, this module tries to adapt colors (CAT). We need to disable
that math so it acts as a dumb mixer.

►Set the Chromatic Adaptation Transform (CAT) to None(bypass) to disable
color adaptation.

<img src="./media/image32.png"
style="width:3.5625in;height:1.59375in" />

#### 3. Create the Mask

►On the bottom bar, click on the button <img src="./media/image54.png"
style="width:0.28125in;height:0.26042in" /> “Drawn mask”, to draw a mask
for the eyes.

<img src="./media/image31.png"
style="width:3.52083in;height:3.02083in" />

►Click on button
<img src="./media/image67.png" style="width:0.19792in;height:0.25in" />
to display the masks on the image

<img src="./media/image22.png"
style="width:4.24479in;height:1.87392in" />

►Click on the circular button <img src="./media/image43.png"
style="width:0.20833in;height:0.19792in" /> to create a circular mask
for the eye pupils, then move the mouse cursor on an eye pupil.

*Note: 2 concentric circles will be displayed on the image. The inner
circle (straight line) delimits the iris, the outer circle (dotted line)
which represents the feathering should delimit the eye pupil.*

<img src="./media/image73.png" style="width:3.4375in;height:2.1875in" />

►Move the mouse pointer to position the two concentric circles on the
eye.

►Then use the mouse wheel up / down to increase / decrease the diameter
of the circles. *Note: For the mouse wheel up / down, concentrate only
on the <u>inner circle</u> (1) to match perfectly the size of the pupil
(not the size of the iris).*

►When done, click on the square right of the *external circle* (4) and
move the square left or right <img src="./media/image79.png"
style="width:0.37866in;height:0.34896in" /> to increase / decrease the
diameter of the external circle, to match perfectly the diameter of the
iris (not the pupil).

At the end of the marking, the inner circle (1) matches perfectly the
pupil and the external circle (2) matches perfectly the iris.

1.  Inner circle (for the eye pupil)

2.  Outer circle (for the eye iris)

3.  Square slider for the size of inner circle (size of the pupil)

4.  Square slider for the size of outer circle (size of the iris)

<img src="./media/image52.png"
style="width:5.48958in;height:4.45833in" />

►To create the concentric circles for the second eye, click on the
CTRL+Circle button on the bottom bar.

*Note: the CTRL add a second instance of the circular mask*

►Do the same steps to create the second mask for the second eye.

►Then click on the right mouse button to stop the definition of the
masks.

►To check if the two masks are defined correctly, hover over the eye
positions (without clicking on any mouse button) and you will see the
concentric circles on each eye hovered.

*Note: The inner circles of both masks will be displayed simultaneously
on the image. To display the outer circle, you will have to hover each
mask.*

#### 4. The Channel Mix (The Fix)

Now we perform the "surgery" on the Red channel.

► Go to the R (Red) tab within the Color Calibration module  
Currently, it says: Input R = 1.00, Input G = 0.00, Input B = 0.00.
(This means "Red looks like Red").

<img src="./media/image46.png"
style="width:3.51042in;height:1.79167in" />

►Change the R /G / B sliders to:

- Input R: 0.00 (Remove the blown-out red data).

- Input G: 0.50

- Input B: 0.50

*Note: What just happened? You told Darktable: "For the Red pixel
bucket, ignore the red signal. Instead, fill it with the average of the
Green and Blue signals." Since Green and Blue are naturally dark in a
pupil, the pupil instantly turns dark neutral gray/black.*

►Go to the Brightness tab within the Color Calibration module  
Currently, it says: Input R = 0.00, Input G = 0.00, Input B = 0.00.
(This means the same brightness for all colors R / G / B channels).

<img src="./media/image71.png" style="width:3.5625in;height:1.8125in" />

► Change the R /G / B sliders to:

- Input R: -0.50 (Darken the iris color).

- Input G: 0.00

- Input B: 0.00

*Note: Catchlights: If the mix kills the white reflection (catchlight)
in the eye too much, you may increase the R brightness from -0.50 to
+0.00.*

# 8. Annexes

Some useful styles from different authors.

## dtstyles

dtstyles : [<u>https://dtstyle.net/​</u>](https://dtstyle.net/%E2%80%8B)

- un grand choix

- pas d'organisation

- pas de version

- peut utiliser des modules qui sont déprécié ou simplement qui ont été
  > retiré de darktable.

## Mel265

Mel265 (Stefano Ferro) :
[<u>https://mel365.com/darktable-presets-and-styles/</u>](https://mel365.com/darktable-presets-and-styles/)

- A fait des style et des video montrant comment ils fonctionnent

- devraient fonctionner avec darktable 4 sans soucis

## Jade-nl

Jade-nl :
[<u>https://github.com/jade-nl/dt.st...​</u>](https://github.com/jade-nl/dt.st...%E2%80%8B)

- un répertoire de plusieurs style, a tester

- télécharger sur le github

- par de prévisualisation

## Joao Pedro Almedia

Joao Pedro Almedia :
[<u>https://blog.joaoalmeidaphotogra...​</u>](https://blog.joaoalmeidaphotography)

- a certainement les style de qualité

- prévisualisation

- github :
  > [<u>https://github.com/t3mujin/t3muj...​</u>](https://github.com/t3mujin/t3muj...%E2%80%8B)

[^1]: Link:
    [<u>https://docs.darktable.org/usermanual/development/en/guides-tutorials/</u>](https://docs.darktable.org/usermanual/development/en/guides-tutorials/)

[^2]: Link:
    [<u>https://github.com/darktable-org/darktable/releases/download/release-5.2.1/darktable-5.2.1-win64.exe</u>](https://github.com/darktable-org/darktable/releases/download/release-5.2.1/darktable-5.2.1-win64.exe)
