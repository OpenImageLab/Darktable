![](/data/data/com.termux/files/home/storage/downloads/media/media/image76.png){width="6.637382983377078in"
height="1.5889107611548556in"}

Tutorial\
**Processing Plustek 8200i\
scanned Slides\
with Darktable 5.x**

![ligne
courte](/data/data/com.termux/files/home/storage/downloads/media/media/image2.png){width="0.4895833333333333in"
height="6.25e-2in"}

Jacques Morand\
December 5th, 2025

# Table of Content

[**Table of Content 1**](#table-of-content)

[**1. Introduction 3**](#introduction)

> [1.1 A Note for the Beginners 3](#a-note-for-the-beginners)
>
> [1.1.1 The Beginner's Nightmare 3](#the-beginners-nightmare)
>
> [1.1.2 Common Beginner Pitfalls (short list)
> 4](#common-beginner-pitfalls-short-list)
>
> [1.1.3 What you can expect from this tutorial
> 4](#what-you-can-expect-from-this-tutorial)
>
> [1.2 Copyright and Disclaimer 5](#copyright-and-disclaimer)
>
> [1.3 Context 6](#context)
>
> [1.3.1 Darktable Version 6](#darktable-version)
>
> [1.3.2 Processing of raw Images 6](#processing-of-raw-images)
>
> [Where do the raw images come from for this tutorial ?
> 6](#where-do-the-raw-images-come-from-for-this-tutorial)
>
> [The Process Workflow 7](#the-process-workflow)
>
> [Crucial Distinction: Scanner Raw vs. Digital Camera Raw
> 7](#crucial-distinction-scanner-raw-vs.-digital-camera-raw)
>
> [1.3.3 Scene-referred Workflow a new Approach
> 8](#scene-referred-workflow-a-new-approach)
>
> [1.4 The 4 most important basic Adjustments
> 8](#the-4-most-important-basic-adjustments)
>
> [1.4.1 White balance and color calibration - Module Color calibration
> 8](#white-balance-and-color-calibration---module-color-calibration)
>
> [1.4.2 Exposure - Module Exposure 9](#exposure---module-exposure)
>
> [1.4.3 Set white and black points - Module Sigmoid
> 9](#set-white-and-black-points---module-sigmoid)
>
> [1.4.4 Color Calibration - Module Color calibration
> 9](#color-calibration---module-color-calibration)

[**3. Darktable initial Settings 10**](#darktable-initial-settings)

> [3.1 Import raw Images from PC to darktable Library
> 10](#import-raw-images-from-pc-to-darktable-library)
>
> [3.2 Import Style for scanner Plustek 8300i
> 12](#import-style-for-scanner-plustek-8300i)
>
> [3.3 Set Darktable Preferences 13](#set-darktable-preferences)

[**4. Workflow to process raw Images
15**](#workflow-to-process-raw-images)

> [4.1 Image Selection and Processing in darktable
> 15](#image-selection-and-processing-in-darktable)
>
> [4.2 Clear Modules History 16](#clear-modules-history)
>
> [4.3 Apply Style "Plustek-8300i" 17](#apply-style-plustek-8300i)
>
> [4.4 Process the Exposure 18](#process-the-exposure)
>
> [4.5 Process the Color Calibration 19](#process-the-color-calibration)
>
> [4.6 Store the processed image in darktable database
> 21](#store-the-processed-image-in-darktable-database)

[**5. Export processed Images 22**](#export-processed-images)

> [5.1 Export processed image in TIFF Format
> 23](#export-processed-image-in-tiff-format)
>
> [5.2 Export processed image in JPEG Format
> 25](#export-processed-image-in-jpeg-format)

[**6. Modules of Style Plustek-8300i
27**](#modules-of-style-plustek-8300i)

> [6.1 Module White balance 28](#module-white-balance)
>
> [6.2 Module Highlight reconstruction
> 28](#module-highlight-reconstruction)
>
> [6.3 Module Orientation 28](#module-orientation)
>
> [6.4 Module Tone equalizer Plustek-8200i
> 28](#module-tone-equalizer-plustek-8200i)
>
> [6.5 Module Crop - Plustek-8200i 29](#module-crop---plustek-8200i)
>
> [6.6 Module Input color profile 30](#module-input-color-profile)
>
> [6.7 Module Color calibration 31](#module-color-calibration)
>
> [6.8 Module Diffuse or sharpen - Dehaze - Default
> 31](#module-diffuse-or-sharpen---dehaze---default)
>
> [6.9 Module Diffuse or sharpen - Plustek 8200i
> 32](#module-diffuse-or-sharpen---plustek-8200i)
>
> [6.10 Module Color Balance RGB - Plustek-8200i
> 34](#module-color-balance-rgb---plustek-8200i)
>
> [6.11 Module Sigmoid - Plustek-8200i
> 35](#module-sigmoid---plustek-8200i)
>
> [6.12 Module Local contrast - Plustek-8200i
> 36](#module-local-contrast---plustek-8200i)
>
> [6.13 Module Output color profile 37](#module-output-color-profile)

[**7. Other useful Modules 39**](#other-useful-modules)

> [7.1 Module Rotate and perspective 39](#module-rotate-and-perspective)
>
> [7.2 Module Retouch 40](#module-retouch)
>
> [7.3 Red Eyes Removal 40](#red-eyes-removal)

[**8. Annexes 44**](#annexes)

> [dtstyles 44](#dtstyles)
>
> [Mel265 44](#mel265)
>
> [Jade-nl 44](#jade-nl)
>
> [Joao Pedro Almedia 44](#joao-pedro-almedia)

# 1. Introduction

## 1.1 A Note for the Beginners

### 1.1.1 The Beginner's Nightmare

![](/data/data/com.termux/files/home/storage/downloads/media/media/image29.png){width="2.7958442694663166in"
height="3.401042213473316in"}

Darktable is a powerful, free, open-source RAW developer and photo
workflow manager --- but for many newcomers it feels more like a toolbox
full of unfamiliar instruments than a clear, guided image-processing
workflow-tool.

The [[official Darktable user]{.underline}
[manual]{.underline}](https://docs.darktable.org/usermanual/development/en/guides-tutorials/)[^1]
is an indispensable technical reference, yet for beginners it can be
dense: it introduces a lot of image-processing vocabulary and modules
without showing how those pieces fit together in a practical sequence.
Likewise, video tutorials and walkthroughs can be fast, idiosyncratic,
and assume background knowledge; instructors often click through
darktable modules and presets quickly, perform trial-and-error presets
adjustments, or explain advanced concepts that aren't necessary for a
first solid edit. That makes it hard to build confidence and to
understand why particular corrections are made at specific stages of the
pipeline.

This tutorial was written from the perspective of a new Darktable user
who learned by doing and reading, taking careful notes and distilling
the essential steps into a repeatable, easy-to-follow pipeline. The aim
is pragmatic: to show what to do, why it matters, and how to do it
step-by-step. Each section explains the purpose of the processing step,
the typical problems it solves, and concrete actions you can take in
Darktable --- with enough explanation to understand cause → effect
without drowning in theory.

Beginners typically encounter recurring problems that make progress feel
confusing. These include uncertainty about color spaces and when to
apply white balance, misunderstanding which modules are mutually
exclusive or redundant within a given workflow (for example, modules
relevant for scene-referred workflows versus display-referred
workflows), and difficulty knowing the right order of operations so that
later edits don't undo earlier corrections. This tutorial highlights
those decision points and explains simple rules of thumb to avoid common
pitfalls. It focuses on robust, repeatable choices rather than chasing
small, image-specific tweaks that complicate learning.

If you follow the guided pipeline here you'll gain two things:
predictable, high-quality results for most images, and a clearer mental
model of how Darktable's modules interact. Once those foundations are
solid, the official user manual and advanced tutorials will make a lot
more sense --- you'll recognize when a topic is worth diving into and
when it's safe to skip. The goal is practical competence: enough
understanding to edit confidently and enough curiosity to learn more
intentionally.

### 1.1.2 Common Beginner Pitfalls (short list)

-   Confusing scene-referred vs display-referred modules --- using
    > certain modules together can produce unexpected results.

-   Applying white balance or color calibration at the wrong stage and
    > then losing those corrections during later operations.

-   Overusing local adjustments early in the pipeline; global
    > corrections (exposure, contrast, color) should usually come first.

-   Relying on a single tutorial or workflow: different image types
    > (portraits, landscapes, scanned slides) need different emphases.

-   Skipping soft-proofing or output considerations --- editing for the
    > final medium (screen, web, print) avoids surprises later.

### 1.1.3 What you can expect from this tutorial

This tutorial walks you through a clear sequence of steps, explains the
reasoning behind each decision, and includes practical tips to avoid the
most frequent mistakes. It's intended to help you move from confusion to
control --- reliably and efficiently --- so you spend more time making
creative choices and less time fighting the interface.

## 1.2 Copyright and Disclaimer

**© 2025 Jacques Morand. All rights reserved.**

This tutorial is an original work based on practical experience acquired
while processing more than hundreds of images in Darktable. The
workflow, module choices, and recommendations presented here reflect the
author's personal understanding of the software at the time of writing.
They are offered as learning guidance for beginners and are not intended
to represent the only valid approach, nor the most advanced or
professional methodology available.

Although great care has been taken to ensure accuracy, clarity, and
consistency, the content is provided *"as is"* without any
guarantee---explicit or implied---regarding correctness, completeness,
or suitability for a specific purpose. Darktable evolves continuously,
and future versions may change certain behaviors, defaults, or
recommended practices.

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

This tutorial is based on the [[Darktable version
5.2.1]{.underline}](https://github.com/darktable-org/darktable/releases/download/release-5.2.1/darktable-5.2.1-win64.exe)[^2]
for Windows 64 bits.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image17.png){width="1.9895833333333333in"
height="1.4791666666666667in"}

### 1.3.2 Processing of raw Images

#### Where do the raw images come from for this tutorial ?

​The raw images (.DNG) were produced by scanning 24x36 positive films
(Kodachrome, Agfachrome, Fujichrome) on a **Plustek OpticFilm 8300i
Scanner** using the 48-bit HDR raw mode from **SilverFast SE Plus 9**.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image54.png){width="3.334070428696413in"
height="3.651042213473316in"}

#### The Process Workflow

The workflow to process raw images includes operations like fixing white
balance and color calibration, fixing the exposure, reconstructing
highlights, fixing geometry, sharpening and dehazing images, aligning
histogram channels (color cast/fading), and optimizing dynamic range.

#### Crucial Distinction: Scanner Raw vs. Digital Camera Raw

It is vital to understand that a \"Raw\" file from a scanner behaves
differently than a Raw file from a digital camera (like a Nikon
D-Series, Canon R-Series , or modern Smartphones). While a **digital
camera** records a **3D scene** influenced by changing light (sun,
tungsten), the **scanner** records a **2D physical object** under fixed
internal lighting.

This leads to three specific challenges in Darktable:

> **Linear Gamma (Darkness):**\
> The \"48-bit HDR\" mode outputs linear gamma data (Gamma 1.0). Unlike
> camera raw files---which Darktable automatically adjusts using a base
> curve or filmic defaults based on metadata---scanner files will appear
> extremely dark and flat initially. This is not underexposure; it is
> simply uncorrected gamma.
>
> **Missing Color Profiles**:\
> Darktable contains a built-in database of color matrices for almost
> every digital camera (e.g., it knows exactly how a Canon R50V sees
> red). It does not have built-in data for a Plustek scanner. You cannot
> rely on \"White Balance\" presets (Daylight, Cloudy) because the
> \"light source\" is the scanner\'s lamp, not the sun. You must rely on
> the Input Color Profile module, ideally using a custom ICC profile
> created via IT8 calibration, or manually correcting color casts.
>
> **Physical Artifacts**:\
> Digital camera noise is electronic; film \"noise\" is physical grain
> and emulsion damage. Algorithms designed for digital noise (denoise
> profiled) often smudge film grain.

The Workflow To process these .DNG files in Darktable, the standard
scene-referred workflow must be adapted:

> **Input Color Profile:**\
> Assigning the correct scanner ICC profile (if available) or a generic
> linear RGB profile to interpret the device\'s colors.
>
> **Exposure & Tone Mapping:**\
> Because the file is linear, significant exposure compensation is
> required, followed by Sigmoid or Filmic RGB to apply the necessary
> gamma correction and expand the dynamic range for display.
>
> **White Balance & Color Calibration:**\
> Correcting the color temperature of the scanner\'s lamp and
> neutralizing the color cast of the film base (aging).
>
> **Channel Alignment:**\
> Using the Color Calibration or RGB Curve to fix \"fading,\" where
> specific channels (often Blue or Magenta) have degraded faster than
> others over decades.
>
> **Corrections:**\
> Cropping (geometry), Dehazing (for oxidized slides), and Sharpening
> (High Pass or Contrast Equalizer) to enhance perceived detail without
> exaggerating grain.

### 1.3.3 Scene-referred Workflow a new Approach

If you have used other Raw processing software in the past (or darktable
prior to version 3.0) you may notice some significant differences from
what you are used to -- darktable now uses a **scene-referred approach**
for most of its processing modules. This new approach is used
extensively in cinematography and is known to be much more robust than
the traditional display-referred approach.

In **display-referred processing** (used for instance by Photoshop raw
Image Processing) the data from your raw file is initially compressed
into a range that represents pure black as 0 and pure white as 1, fixing
mid-gray at 0.5. A tone curve is automatically (and irreversibly)
applied to this data to make the image look "good" on your display and
subsequent edits are carried out on top of this already highly-modified
image data. The cost of display-referred is an early loss of the
relationship between pixel luminosity and saturation (usually also
involving hue shifts), which is responsible for the infamous "HDR look"
when the dynamic range increases.

In the real world, "pure black" does not really exist (there is always
some light) and there is no limit to how bright things can be (so no
"pure white" either). **Scene-referred processing** attempts to retain
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
-- for example, for a high-key image you will set the average brightness
to be lighter than for a low-key image. The color assessment mode
provides you with two reference points to assist with this by
surrounding the image with a white frame against a middle-gray
background.

At this point, don't worry if the brightest parts of your image lose
detail -- this can be recovered in the next step.

*Note: The lens correction module can also affect the image brightness
so you may want to consider enabling it before adjusting exposure.*

### 1.4.3 Set white and black points - Module Sigmoid

With Sigmoid, the setting of white and black points is done using the
parameters "Target black/white luminance" of the **Sigmoid module**.

### 1.4.4 Color Calibration - Module Color calibration

Traditional white balance correction attempts to ensure that whites and
grays are really neutral (R = G = B) and doesn't really try to manage
the impact on other colors. The CAT tab of the **Color calibration
module** extends this treatment to handle the remainder of the color
range and works in a color space designed specifically for chromatic
(color) adaptation. As with traditional white balance controls you can
select a patch of neutral gray in your image to calculate the white
balance, or use a selection of other automatic and manual methods. The
default settings use the white balance from the image's Exif data and
are usually sufficient.

*Note: If you need to make adjustments in the color calibration module,
you may want to also revisit any saturation corrections you made earlier
in the color balance rgb module.*

# 3. Darktable initial Settings

![](/data/data/com.termux/files/home/storage/downloads/media/media/image25.png){width="0.3937007874015748in"
height="0.33742344706911637in"}Do these initial settings only once after
installing darktable.

Initial Settings:

-   Import raw Images from PC to darktable Library

-   Import Style for scanner Plustek 8300i

-   Set Darktable Preferences

-   Useful darktable Keyboard Shortcuts

## 3.1 Import raw Images from PC to darktable Library

[►]{.mark}Select \[Lightable\] from darktable top menu bar or click on
key \[**l**\] on the keyboard.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image46.png){width="6.5in"
height="0.3194444444444444in"}

►Open "Import" from left panel, then click on "Add to library"

![](/data/data/com.termux/files/home/storage/downloads/media/media/image24.png){width="2.96875in"
height="4.8125in"}

►Click on \[+\] to add a new Place from where the images should be
found, then select the place.

►Select the folder(s) where the images should be found

►Activate the option:

-   Select only new images

    > Recursive directory

    > Ignore non-raw images

►Click on \[Add to library\] to import the raw images into the darktable
database.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image11.png){width="6.5in"
height="5.152777777777778in"}

## 3.2 Import Style for scanner Plustek 8300i

A special style with according Presets for required Modules has been
created in order to process 48 bits HDR raw images scanned with the
scanner Plustek-8300i Series.

This style is named
**"Plustek-8300i-Exposure-ColorCalibration-Regular"**

►On right Panel of Lighttable, open sheet "Styles"

►Under "Filter style names" select
"Plustek-8300i-Exposure-ColorCalibration-Regular"

►Click on "Import..."

*Note: This special style is now imported into darktable and ready to be
used for the workflows.*

![](/data/data/com.termux/files/home/storage/downloads/media/media/image66.png){width="4.4520056867891515in"
height="6.390625546806649in"}

## 3.3 Set Darktable Preferences

►Click on the Preference Button

![](/data/data/com.termux/files/home/storage/downloads/media/media/image36.png){width="6.5in"
height="0.6111111111111112in"}

►Select the "Processing" tab.

►Make sure that the option "Scene-referred(Sigmoid)" is selected.

►Click on \[Escape\] to store the preferences

![](/data/data/com.termux/files/home/storage/downloads/media/media/image40.png){width="6.5in"
height="1.7777777777777777in"}

►Select the "General" tab

►Set the interface language to "English(en@truecase)

![](/data/data/com.termux/files/home/storage/downloads/media/media/image27.png){width="6.5in"
height="2.1805555555555554in"}

**3.4 Useful darktable Keyboard Shortcuts**

These shortcuts are very useful and can be used in any workspace of
Darktable.

+-----------+---------------+-----------------------------------------+
| *         | **Shortcut    | **Explanation**                         |
| *Shortcut | Name**        |                                         |
| Key**     |               |                                         |
+===========+===============+=========================================+
| **l**     | Lighttable    | Press keyboard letter **l** to switch   |
|           | workspace     | to Lighttable workspace.                |
|           |               |                                         |
|           |               | *The Lighttable workspace is used to    |
|           |               | select the raw image(s) to process in   |
|           |               | Darkroom workspace*                     |
+-----------+---------------+-----------------------------------------+
| **d**     | Darkroom      | Press keyboard letter **d** to switch   |
|           | workspace     | to Darkroom workspace.                  |
|           |               |                                         |
|           |               | The Darkroom workspace is used to       |
|           |               | process the raw images.                 |
+-----------+---------------+-----------------------------------------+

# 4. Workflow to process raw Images

![](/data/data/com.termux/files/home/storage/downloads/media/media/image25.png){width="0.3937007874015748in"
height="0.33742344706911637in"}Repeat this workflow for each raw image
to be processed.

## 4.1 Image Selection and Processing in darktable

►In Lighttable workspace, select the image to process by clicking once
on that image. A white box appears around the selected image.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image71.png){width="6.5in"
height="4.930555555555555in"}

►Click letter \[d\] on keyboard (d stands for darktable). The Darkroom
processing workspace appears.

*Note: Another way to active darkroom processing is to double-click on
the image to process.*

## 4.2 Clear Modules History

►In the Darkroom workspace, click on the triangle
![](/data/data/com.termux/files/home/storage/downloads/media/media/image34.png){width="0.19791666666666666in"
height="0.20833333333333334in"} to open the History menu, then click on
the Reset Symbol
![](/data/data/com.termux/files/home/storage/downloads/media/media/image64.png){width="0.1875in"
height="0.16666666666666666in"} in order to clear the history of the
image processing.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image73.png){width="4.802083333333333in"
height="6.052083333333333in"}

► Confirm the History Reset by clicking on \[Yes\] button

![](/data/data/com.termux/files/home/storage/downloads/media/media/image49.png){width="3.6145833333333335in"
height="1.03125in"}

## 4.3 Apply Style "Plustek-8300i"

A specific style "**Plustek-8300i-Exposure-ColorCalibration-Regular**"
with according modules has been created to process diapositives scanned
with the scanner Plustek 8300i in mode 48-bits HDR raw.

►On the bottom of the left darktable panel, click on button
![](/data/data/com.termux/files/home/storage/downloads/media/media/image16.png){width="0.2859678477690289in"
height="0.22709208223972002in"} to open the styles window.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image13.png){width="6.355458223972003in"
height="7.734375546806649in"}

►Click on Style "Plustek-8300i-Exposure-ColorCalibration-Regular" to
select it.

►Make sure that on the darktable right panel, the "Show only active
module" is activated
![](/data/data/com.termux/files/home/storage/downloads/media/media/image5.png){width="0.430495406824147in"
height="0.24479221347331584in"}\
The panel shows only active modules. Their ON button is lightened
![](/data/data/com.termux/files/home/storage/downloads/media/media/image5.png){width="0.430495406824147in"
height="0.24479221347331584in"}

> *The button is lightened*
> ![](/data/data/com.termux/files/home/storage/downloads/media/media/image5.png){width="0.41765529308836397in"
> height="0.23993000874890638in"} *if the command is activated*
>
> *The button is greyed*
> ![](/data/data/com.termux/files/home/storage/downloads/media/media/image44.png){width="0.3445220909886264in"
> height="0.24479221347331584in"} *if the command is not activated*

![](/data/data/com.termux/files/home/storage/downloads/media/media/image22.png){width="3.75in"
height="3.9270833333333335in"}

## 4.4 Process the Exposure

The **Exposure Module** allows the processing of the overall brightness
of an image.

To process the Exposure of the image, open the module "Exposure" on the
right panel.

►Click on "Exposure Bar" to open the menu of the Exposure Module

![](/data/data/com.termux/files/home/storage/downloads/media/media/image32.png){width="3.5520833333333335in"
height="0.7291666666666666in"}

►Make sure that the Exposure Mode is set to "Manual"

![](/data/data/com.termux/files/home/storage/downloads/media/media/image9.png){width="3.53125in"
height="0.6145833333333334in"}

![](/data/data/com.termux/files/home/storage/downloads/media/media/image25.png){width="0.3937007874015748in"
height="0.33742344706911637in"} Pay attention to not deactivate the
Exposure Module by clicking on its ON button

![](/data/data/com.termux/files/home/storage/downloads/media/media/image51.png){width="3.53125in"
height="0.5416666666666666in"}

►Under the Parameter Exposure,

> Move the triangle Slider
> ![](/data/data/com.termux/files/home/storage/downloads/media/media/image4.png){width="0.20833333333333334in"
> height="0.19791666666666666in"} left ← to [decrease]{.underline} the
> Exposure (lightness) or
>
> Move the triangle Slider
> ![](/data/data/com.termux/files/home/storage/downloads/media/media/image4.png){width="0.20833333333333334in"
> height="0.19791666666666666in"} right → to [increase]{.underline} the
> Exposure (lightness) of the image.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image42.png){width="3.5520833333333335in"
height="2.15625in"}

► On the image, use the scroll wheel up / down to zoom / de-zoom the
image, in order to set the correct exposure of the subject.

► Click on the Exposure bar again to store the Exposure in darkroom
database.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image32.png){width="3.5520833333333335in"
height="0.7291666666666666in"}

## 4.5 Process the Color Calibration

The **Color calibration module** is a powerful tool for adjusting color
balance, creating grayscale images, and performing color grading. It
serves as a reference point for ensuring whites and grays appear neutral
by correcting the \"color cast\" from the light source and allows for
fine-tuning white balance, saturation, and brightness. The module can
also be used for creative purposes, like creating black and white
conversions with film-like presets or adjusting RGB channels for color
grading.

The color calibration is done using the Module "Color calibration" on
the left panel.

►Open the module "Color calibration"

![](/data/data/com.termux/files/home/storage/downloads/media/media/image28.png){width="3.5104166666666665in"
height="0.3229166666666667in"}

►Click on button
![](/data/data/com.termux/files/home/storage/downloads/media/media/image47.png){width="0.40625in"
height="0.20833333333333334in"} to select the Chromatic Adaptation
Transform (CAT)

►By the parameter Adapdation, open the combobox
![](/data/data/com.termux/files/home/storage/downloads/media/media/image18.png){width="0.20833333333333334in"
height="0.15625in"}

►Select CAT16(CIECAM16)

![](/data/data/com.termux/files/home/storage/downloads/media/media/image63.png){width="3.5416666666666665in"
height="3.4583333333333335in"}

►Clink on eyedropper
![](/data/data/com.termux/files/home/storage/downloads/media/media/image20.png){width="0.2916666666666667in"
height="0.14583333333333334in"}to adapt automatically the chromatic of
the whole image

![](/data/data/com.termux/files/home/storage/downloads/media/media/image21.png){width="3.9270833333333335in"
height="1.21875in"}

►Click on the Color calibration bar again to close the color calibration
menu and store the color calibration in darktable database.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image28.png){width="3.5104166666666665in"
height="0.3229166666666667in"}

## 4.6 Store the processed image in darktable database

The workflow to process the raw image based on the "*Scene referred
Sigmoid*" method and the Style
"*Plustek8300i-Exposure-ColorCalibraton-Regular*" is now terminated.

►On keyboard, click on letter **l** to store the image into darktable
database and open the workspace lighttable to process the next image.

► On workspace Lighttable, the processed image appears in a white box
and the color of the image is now similar to the definitive result,
ready to be exported in format TIFF or JPEG.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image45.png){width="5.458333333333333in"
height="3.0208333333333335in"}

# 5. Export processed Images

The export workflow is done in the Lighttable workspace, using the right
panel.

►On the Lighttable workspace, click once on the image to be exported.

*Note: To export multiple images, use **SHIFT+Click** to select a range
or **CTRL+Click** to select multiple disseminated images.*

►Click on the triangle left to the bar "Export" to open the export menu.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image48.png){width="4.708333333333333in"
height="0.90625in"}

In the group "Storage options" :

> ►For the parameter "Target storage" select in the combobox
> ![](/data/data/com.termux/files/home/storage/downloads/media/media/image15.png){width="0.1875in"
> height="0.16666666666666666in"} "File on disk"
>
> ►For the filepath line, click on the folder icon
> ![](/data/data/com.termux/files/home/storage/downloads/media/media/image43.png){width="0.2604166666666667in"
> height="0.1875in"} to browse to the directory where to store the image
> to be exported

*Note: The directory path is terminated by the variable "/\$FILE_NAME".\
This variable will be replaced by the name of the original raw image.
This name will be extended with the extension corresponding to the
format of the exported image, ie .jpeg or .tiff.*

►For the parameter "On conflict", select in the combobox
![](/data/data/com.termux/files/home/storage/downloads/media/media/image15.png){width="0.1875in"
height="0.16666666666666666in"} the option "Create unique filename".

*Note: If the filename with extension already exists, a number will be
added to the filename.*

![](/data/data/com.termux/files/home/storage/downloads/media/media/image7.png){width="4.697916666666667in"
height="1.0729166666666667in"}

## 5.1 Export processed image in TIFF Format

In the group "**Format options**",

> ►Setup the following values to the following parameters

  ------------------------------------------------------------------------
  **Parameter**        **Value**              **Description**
  -------------------- ---------------------- ----------------------------
  File format          TIFF                   

  Bit depth            16 bits                

  Pixel type           Unsigned integer       

  Compression          Uncompressed           

  B&W grayscale        No                     
  ------------------------------------------------------------------------

![](/data/data/com.termux/files/home/storage/downloads/media/media/image14.png){width="4.697916666666667in"
height="1.375in"}

In the group "**Global options**",

> ►Setup the following parameters:

+-----------+------------+---------------------------------------------+
| **Pa      | **Value**  | **Description**                             |
| rameter** |            |                                             |
+===========+============+=============================================+
| Set size  | In pixels  | Maximum dimensions in pixels, inches, or    |
|           | (for       | cm. Setting a dimension to zero leaves it   |
|           | file): 0 x | unconstrained.                              |
|           | 0 px       |                                             |
|           |            | *Recommandations:*                          |
|           |            |                                             |
|           |            | -   *[Set to zero to export at original     |
|           |            |     > dimensions (after cropping).]{.mark}* |
|           |            |                                             |
|           |            | -   *[Use to downscale for specific uses    |
|           |            |     > like social media.]{.mark}*           |
+-----------+------------+---------------------------------------------+
| Allow     | No         | Option to allow the image to be exported at |
| upscaling |            | a larger size than the original.            |
|           |            |                                             |
|           |            | *Recommandations:*                          |
|           |            |                                             |
|           |            | -   *Disable (No).*                         |
|           |            |                                             |
|           |            | -   *Enable (Yes) only if you need to       |
|           |            |     > export at a higher resolution than    |
|           |            |     > the source file to mitigate           |
|           |            |     > pixelation.*                          |
+-----------+------------+---------------------------------------------+
| High      | No         | Algorithm used to create the new image.     |
| quality   |            | \"High quality resampling\" takes longer    |
| r         |            | but improves quality.                       |
| esampling |            |                                             |
|           |            | *Recommandations:*                          |
|           |            |                                             |
|           |            | -   *Disable (No)*                          |
|           |            |                                             |
|           |            | -   *Enable (Yes) only for better results   |
|           |            |     > for TIFF Format*                      |
+-----------+------------+---------------------------------------------+
| Store     | No         |                                             |
| masks     |            |                                             |
+-----------+------------+---------------------------------------------+
| Profile   | Image      | The color space for the exported image.     |
|           | settings   | sRGB is standard for web and most home      |
|           |            | printing.                                   |
|           |            |                                             |
|           |            | *Recommandations:*                          |
|           |            |                                             |
|           |            | -   *Image settings.*                       |
|           |            |                                             |
|           |            | -   *Use sRGB only for online use. Consider |
|           |            |     > other profiles for specific printers  |
|           |            |     > or workflows if needed.*              |
+-----------+------------+---------------------------------------------+
| Style     | None       | Add an additional style for the exporting   |
|           |            | of the image.                               |
|           |            |                                             |
|           |            | *Recommandations:*                          |
|           |            |                                             |
|           |            | -   *Do not add additional style for        |
|           |            |     > exporting (None)*                     |
+-----------+------------+---------------------------------------------+

![](/data/data/com.termux/files/home/storage/downloads/media/media/image31.png){width="4.697916666666667in"
height="2.0in"}

In the group "**Start export"**

> ►Click on the bar "Start export" to begin the export of the selected
> image(s).

![](/data/data/com.termux/files/home/storage/downloads/media/media/image33.png){width="4.614583333333333in"
height="0.3645833333333333in"}

## 5.2 Export processed image in JPEG Format

In the group "**Format options**",

> ►Setup the following parameters:

+--------------+-----------+-------------------------------------------+
| *            | **Value** | **Description**                           |
| *Parameter** |           |                                           |
+==============+===========+===========================================+
| File format  | JPEG      |                                           |
|              | (8-bits)  |                                           |
+--------------+-----------+-------------------------------------------+
| Quality      | 95        | JPEG compression level, 0-100. Higher     |
|              |           | values mean less compression and better   |
|              |           | quality, but larger file sizes.           |
|              |           |                                           |
|              |           | *Recommandations:*                        |
|              |           |                                           |
|              |           | -   *95 for high quality (archiving,      |
|              |           |     > printing);*                         |
|              |           |                                           |
|              |           | -   *90 for a good balance (web,          |
|              |           |     > uploads).*                          |
|              |           |                                           |
|              |           | -   *80 is a good starting point to see a |
|              |           |     > balance between file size and       |
|              |           |     > quality.*                           |
+--------------+-----------+-------------------------------------------+
| Chroma       | 4:2:0     | Chroma subsampling in Darktable JPEG      |
| subsampling  |           | exports reduces file size by lowering the |
|              |           | color detail, which is often unnoticeable |
|              |           | for most photos but can save space.       |
|              |           |                                           |
|              |           | *Recommandations:*                        |
|              |           |                                           |
|              |           | -   *The most common, highly compressed   |
|              |           |     > ratio is 4:2:0 (which significantly |
|              |           |     > reduces file size).*                |
|              |           |                                           |
|              |           | -   *The most common ratio for no         |
|              |           |     > subsampling is 4:4:4 (no            |
|              |           |     > subsampling)*                       |
+--------------+-----------+-------------------------------------------+

![](/data/data/com.termux/files/home/storage/downloads/media/media/image68.png){width="4.697916666666667in"
height="1.0729166666666667in"}

In the group "**Global options**",

> ►Setup the following parameters:

+-----------+------------+---------------------------------------------+
| **Pa      | **Value**  | **Description**                             |
| rameter** |            |                                             |
+===========+============+=============================================+
| Set size  | In pixels  | Maximum dimensions in pixels, inches, or    |
|           | (for       | cm. Setting a dimension to zero leaves it   |
|           | file): 0 x | unconstrained.                              |
|           | 0 px       |                                             |
|           |            | *Recommandations:*                          |
|           |            |                                             |
|           |            | -   *[Set to zero to export at original     |
|           |            |     > dimensions (after cropping).]{.mark}* |
|           |            |                                             |
|           |            | -   *[Use to downscale for specific uses    |
|           |            |     > like social media.]{.mark}*           |
+-----------+------------+---------------------------------------------+
| Allow     | No         | Option to allow the image to be exported at |
| upscaling |            | a larger size than the original.            |
|           |            |                                             |
|           |            | *Recommandations:*                          |
|           |            |                                             |
|           |            | -   *Disable (No).*                         |
|           |            |                                             |
|           |            | -   *Enable (Yes) only if you need to       |
|           |            |     > export at a higher resolution than    |
|           |            |     > the source file to mitigate           |
|           |            |     > pixelation.*                          |
+-----------+------------+---------------------------------------------+
| High      | No         | Algorithm used to create the new image.     |
| quality   |            | \"High quality resampling\" takes longer    |
| r         |            | but improves quality.                       |
| esampling |            |                                             |
|           |            | *Recommandations:*                          |
|           |            |                                             |
|           |            | -   *Disable (No)*                          |
|           |            |                                             |
|           |            | -   *Enable (Yes) only for better results   |
|           |            |     > for TIFF Format*                      |
+-----------+------------+---------------------------------------------+
| Profile   | Image      | The color space for the exported image.     |
|           | settings   | sRGB is standard for web and most home      |
|           |            | printing.                                   |
|           |            |                                             |
|           |            | *Recommandations:*                          |
|           |            |                                             |
|           |            | -   *Image settings.*                       |
|           |            |                                             |
|           |            | -   *Use sRGB only for online use. Consider |
|           |            |     > other profiles for specific printers  |
|           |            |     > or workflows if needed.*              |
+-----------+------------+---------------------------------------------+
| Style     | None       | Add an additional style for the exporting   |
|           |            | of the image.                               |
|           |            |                                             |
|           |            | *Recommandations:*                          |
|           |            |                                             |
|           |            | -   *Do not add additional style for        |
|           |            |     > exporting (None)*                     |
+-----------+------------+---------------------------------------------+

![](/data/data/com.termux/files/home/storage/downloads/media/media/image67.png){width="5.387634514435695in"
height="2.2656255468066493in"}

# 6. Modules of Style Plustek-8300i

The following modules are useful for raw image processing. They are
applied automatically by using the Style
"Plustek8300i-Exposure-ColorCalibration-Regular".

The modules are applied sequentially bottom-up by darktable.

Modules with the grayed ON button
![](/data/data/com.termux/files/home/storage/downloads/media/media/image38.png){width="0.19791666666666666in"
height="0.22916666666666666in"} are applied automatically and their
setting cannot be changed.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image74.png){width="3.932292213473316in"
height="6.477357830271216in"}

## 6.1 Module White balance

In darktable\'s scene-referred workflow, use the **Color Calibration
module** for white balancing by picking a neutral gray or by manually
adjusting the illuminant.

While the White Balance module is still used for demosaicing, you should
generally **leave its default settings** and perform the actual white
balance adjustments in the Color Calibration module, especially with the
modern chromatic adaptation settings enabled.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image10.png){width="3.46875in"
height="2.1145833333333335in"}

## 6.2 Module Highlight reconstruction

![](/data/data/com.termux/files/home/storage/downloads/media/media/image25.png){width="0.3937007874015748in"
height="0.33742344706911637in"}Use only if some highlight areas in the
image have been clipped on all channels.

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

![](/data/data/com.termux/files/home/storage/downloads/media/media/image25.png){width="0.3937007874015748in"
height="0.33742344706911637in"} A contrast soft curve is applied
automatically on the image in order to increase the contrast in the
mid-tones.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image19.png){width="3.5104166666666665in"
height="4.322916666666667in"}

## 6.5 Module Crop - Plustek-8200i

![](/data/data/com.termux/files/home/storage/downloads/media/media/image25.png){width="0.3937007874015748in"
height="0.33742344706911637in"}Use only if the image is not centered and
has unwanted borders, for example black or white borders.

The crop module is typically placed early in the pixelpipe, before the
sigmoid module. This ensures that any subsequent processing, including
the tone mapping done by sigmoid, is only applied to the area within the
defined crop.

To crop an image in the darkroom view:

►Locate and open the crop module (sometimes called \"crop and rotate\"
or similar depending on darktable version/configuration). It is usually
found in the \"utility modules\" group or the Quick Access Panel (QAP).

►Drag the edges or corners of the cropping rectangle that appears on
your image to define the desired composition.

►Or set the margins using the Left, Right, Top, Bottom sliders

►You can also use tools within the module for specific aspect ratios or
to straighten the image.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image55.png){width="3.5729166666666665in"
height="2.7083333333333335in"}

## 6.6 Module Input color profile

![](/data/data/com.termux/files/home/storage/downloads/media/media/image25.png){width="0.3937007874015748in"
height="0.33742344706911637in"}This module is applied automatically.

When you open a raw file in darktable with scene-referred defaults
enabled, the pixelpipe is automatically configured as follows:

-   **Input color profile (Default: linear Rec2020 RGB)**\
    > This module is one of the first in the pipeline. It takes the
    > specific color data from your camera\'s raw file (using a standard
    > or enhanced color matrix for your camera model) and converts it
    > into a standardized, linear working color space.

    -   **Recommendation**: The standard recommended practice in
        > darktable for film scans is to manually set the Input profile
        > parameter to match your chosen Working profile, which is
        > typically linear Rec2020 RGB.

    -   This tells darktable that the data coming in is already in the
        > linear working space, effectively bypassing a potentially
        > incorrect input matrix and ensuring the raw scanner data is
        > treated as linear scene-referred data from the start.

-   **Working Profile (Default: linear Rec2020 RGB)**:\
    > The image data between the input color profile module and the
    > sigmoid module resides in this high-gamut, linear working space.
    > The default is typically \"linear Rec. 2020 RGB,\" which is a good
    > choice for most cases due to its broad color range.

-   **Gamut clipping (Default: Off):**\
    > The gamut clipping option in the input color profile module is off
    > by default in the scene-referred workflow.

    -   **Purpose**: Highly saturated colors, especially in strong blues
        > or certain bright light sources, can sometimes cause \"black
        > pixel artifacts\" when converted into the working color space.
        > Activating gamut clipping helps mitigate these specific
        > artifacts by confining the colors to the selected RGB gamut of
        > the working profile (e.g., linear Rec. 2020 RGB).

    -   **Recommendation**: In most cases, leaving this option disabled
        > (\"off\") is recommended to maintain the full color dynamics
        > of your raw file. You only need to enable it if you notice
        > specific artifact issues in highly saturated regions of your
        > image.

    -   This module acts as the display transform, taking the high
        > dynamic range, scene-referred data from the linear working
        > profile and compressing it into the low dynamic range required
        > by your monitor (e.g., sRGB). It operates on the linear RGB
        > data provided by the working profile.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image41.png){width="3.5in"
height="1.09375in"}

## 6.7 Module Color calibration

See Process the color calibration in chapter 3.

## 6.8 Module Diffuse or sharpen - Dehaze - Default

In darktable\'s scene-referred workflow, the diffuse or sharpen
module\'s dehaze preset is the recommended tool for **removing
atmospheric haze**, and it works in concert with the sigmoid module.

The key to a successful scene-referred workflow is the order of
operations:

-   diffuse or sharpen (with the dehaze preset) should be placed in the
    > scene-referred part of the pixelpipe, before the sigmoid module.

-   The sigmoid module is the last step in the scene-referred pipeline,
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

![](/data/data/com.termux/files/home/storage/downloads/media/media/image56.png){width="3.5520833333333335in"
height="5.666666666666667in"}![](/data/data/com.termux/files/home/storage/downloads/media/media/image61.png){width="3.53125in"
height="1.6041666666666667in"}

## 6.9 Module Diffuse or sharpen - Plustek 8200i

In darktable\'s scene-referred workflow, the diffuse or sharpen
module\'s Plustek 8200i preset is the recommended tool for **increasing
the sharpness** of the image, and it works in concert with the sigmoid
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

![](/data/data/com.termux/files/home/storage/downloads/media/media/image35.png){width="3.5416666666666665in"
height="5.041666666666667in"}![](/data/data/com.termux/files/home/storage/downloads/media/media/image23.png){width="3.53125in"
height="2.28125in"}

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
applies a set of initial adjustments to the module\'s sliders of the
**Perceptual saturation grading**:

-   Global saturation: +20%

-   Shadows: +50%

-   Midtones: 0%

-   Highlights: -25%

**Scene-Referred Integration**:

This module is built for the scene-referred pipeline and operates
internally in a **linear RGB color space**, ensuring its calculations
are physically accurate and less prone to artifacts compared to older,
display-referred saturation methods (*now-deprecated vibrance module*).

![](/data/data/com.termux/files/home/storage/downloads/media/media/image58.png){width="3.2708562992125985in"
height="4.703125546806649in"}

![](/data/data/com.termux/files/home/storage/downloads/media/media/image72.png){width="3.4791666666666665in"
height="1.96875in"}

## 6.11 Module Sigmoid - Plustek-8200i

The preset "Plustek-8200i" of the module Sigmoid is based on the
\"**Scene referred default**\" preset for the sigmoid module. This
preset uses **conservative default values** intended to provide a
predictable and robust **conversion from your high-dynamic-range scene
data to a standard dynamic range** display output.

**Prioritize Exposure:**\
Before making changes in the sigmoid module, the first and most critical
step is to adjust the exposure module so that your image\'s midtones are
correctly positioned. The sigmoid curve works best when fed a properly
exposed scene-referred image.

**Contrast / Skew:**\
A moderate contrast value is applied by default, balancing the need for
an immediately pleasing image with the goal of preserving creative
freedom in other modules.

-   Contrast: 1.500

-   Skew: +0.00

**Preserve Hue:**\
The module aims to preserve hue reasonably well by default, avoiding
artificial color shifts like excessive yellowing in highlights, which
can occur with simpler tone mapping curves. The user manual notes that
an approximation of preserved perceptual hue is used by default.

**Display Luminance - Target White/Black**\
These values are set to sensible defaults (e.g., target white around
110-125 cd/m² and target black near zero) to fit the image to a typical
monitor\'s dynamic range. These settings ensure that the full range of
your 48-bit HDR scan is mapped appropriately without clipping important
data, especially in the highlights.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image60.png){width="3.5208333333333335in"
height="0.3125in"}![](/data/data/com.termux/files/home/storage/downloads/media/media/image6.png){width="3.5208333333333335in"
height="5.770833333333333in"}

## 6.12 Module Local contrast - Plustek-8200i

The Plustek-8200i preset uses the **Clarity** preset in darktable\'s
local contrast module and provides an effect similar to the \"clarity\"
slider found in other software, primarily by **boosting the contrast in
the mid-tones and enhancing local detail**. This is an effective way to
give your high-resolution positive slide scans a more defined, crisp
look.

The local contrast module achieves its effect using either a local
**laplacian filter** (default) or an unnormalized bilateral filter,
operating exclusively on the Luminance (L) channel from the Lab color
space.

The Clarity preset specifically adjusts the internal parameters to:

> **Boost Midtone Contrast:**\
> It applies an S-shaped curve to the midtones, making the darker
> midtones darker and the brighter midtones brighter. This enhances the
> perceived detail and texture without significantly altering global
> contrast, which affects the overall tonal range (highlights to
> shadows) of the image.
>
> **Balance Highlights and Shadows:**\
> The preset subtly adjusts highlight and shadow compression parameters
> to ensure a natural look and avoid clipping or harsh halos around
> edges.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image12.png){width="3.5833333333333335in"
height="2.3333333333333335in"}

## 6.13 Module Output color profile

![](/data/data/com.termux/files/home/storage/downloads/media/media/image25.png){width="0.3937007874015748in"
height="0.33742344706911637in"}This module is applied automatically by
darktable.

In darktable, the output color profile module determines the **final
color space for your exported images**. The choice of profile depends
entirely on the intended use of the image (web display, printing, etc.).

**Key Considerations for the Output Color Profile**

The primary goal of the output color profile module is to convert your
image data from darktable\'s internal working space (typically a wide
gamut linear RGB like **linear Rec2020 RGB**) to a smaller,
application-specific color space.

> **For Web and General Display and TIFF Printing:**\
> The general recommendation is to stick to **sRGB**. Nearly all
> consumer monitors, web browsers, and smartphones are optimized for the
> sRGB color space. Exporting in sRGB ensures that your images will
> appear as intended on the widest variety of devices.
>
> **For Professional Printing:**\
> If you are preparing files for a professional print lab and they
> specify a different profile, you should use that profile (commonly
> Adobe RGB or sometimes CMYK, though darktable works in RGB). Printers
> often prefer Adobe RGB because it has a wider gamut than sRGB, which
> can lead to better quality prints if the printer is capable of
> reproducing those colors.

**Recommandations:**

The most common and safest approach for general purposes is:

-   Set the output color profile in the module (or more commonly, in the
    > export module\'s settings in the lighttable or darkroom sidebar)
    > to **sRGB**.

-   Ensure you **embed the color profile in the output file** (*which
    > darktable does automatically for supported formats like JPEG and
    > TIFF*). This allows other color-managed applications to interpret
    > the colors correctly.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image59.png){width="3.5625in"
height="0.625in"}

# 7. Other useful Modules

![](/data/data/com.termux/files/home/storage/downloads/media/media/image25.png){width="0.3937007874015748in"
height="0.33742344706911637in"}These Modules are not included in the
style "Plustek-8300i". They can be added to the workflow when some
special processing is required.

►To add an additional module, type its name or part of it in the Search
bar of the Darkroom workspace, then click \[Return\] on the keyboard.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image53.png){width="3.7604166666666665in"
height="2.9583333333333335in"}

## 7.1 Module Rotate and perspective

The rotate and perspective module can be used to adjust the angle of the
image or to simulate the functionality of a tilt/shift lens by altering
the perspective, making converging horizontal and/or vertical lines
parallel (keystone correction). This latter technique is most commonly
used for architectural photography. If you just want to correct the
angle of the horizon you can do this by right-clicking and dragging
along the horizon line.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image69.png){width="3.53125in"
height="2.59375in"}

## 7.2 Module Retouch

Use the retouch module to remove spots and unwanted objects by replacing
pixels with detail from elsewhere in the image. This module also offers
powerful techniques for removing large-scale objects (such as spots or
blemishes) while leaving fine-scale details (like hairs and follicles)
intact. The most common use for this module is to remove dust spots from
images or blemishes from skin.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image39.png){width="3.5104166666666665in"
height="3.125in"}

## 7.3 Red Eyes Removal

In Darktable 5.2.1, there is not like in Photoshop a specific module to
remove red eyes in images.

The workflow is straightforward and requires a second instance of the
Color calibration Module and the use of masks to set the position and
size of the "red" pupils.

►Create a second instance of the "Color calibration Module" by clicking
on the "Multiple instance action" button
![](/data/data/com.termux/files/home/storage/downloads/media/media/image65.png){width="0.22916666666666666in"
height="0.21875in"} of the current Color calibration Module.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image8.png){width="2.4739588801399823in"
height="2.448713910761155in"}

►Select option "New instance"

![](/data/data/com.termux/files/home/storage/downloads/media/media/image30.png){width="1.5416666666666667in"
height="1.4166666666666667in"}

►On the bottom bar, click on the button
![](/data/data/com.termux/files/home/storage/downloads/media/media/image50.png){width="0.28125in"
height="0.2604166666666667in"} "Drawn mask", to draw a mask for the
eyes.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image26.png){width="3.5208333333333335in"
height="3.0208333333333335in"}

►Click on the circular button
![](/data/data/com.termux/files/home/storage/downloads/media/media/image37.png){width="0.20833333333333334in"
height="0.19791666666666666in"} to create a circular mask for the eye
pupils, then move the mouse cursor on an eye pupil.

Note: 2 concentric circles will be displayed on the image. The inner
circle (stright line) delimit the iris, the outer circle (dotted line)
delimits the eye pupil.

![](/data/data/com.termux/files/home/storage/downloads/media/media/image70.png){width="3.4375in"
height="2.1875in"}

►Move the mouse pointer to position the two concentric circles on an
eye.

►Then use the mouse wheel up / down to increase / decrease the diameter
of the circles. *Note: For the mouse wheel up / down, concentrate only
on the [inner circle]{.underline} (1) to match perfectly the size of the
pupil (not the size of the iris).*

►When done, click on the square right of the *external circle* (4) and
move the square left or right
![](/data/data/com.termux/files/home/storage/downloads/media/media/image57.png){width="0.3786570428696413in"
height="0.3489588801399825in"} to increase / decrease the diameter of
the external circle, to match perfectly the diameter of the iris (not
the pupil).

At the end of the marking, the inner circle (1) matches perfectly the
pupil and the external circle (2) matches perfectly the iris.

1.  Inner circle (for the eye pupil)

2.  Outer circle (for the eye iris)

3.  Square slider for the size of inner circle (size of the pupil)

4.  Square slider for the size of outer circle (size of the iris)

![](/data/data/com.termux/files/home/storage/downloads/media/media/image62.png){width="5.489583333333333in"
height="4.458333333333333in"}

►To create the concentric circles for the second eye, click on the
CTRL+Circle button on the bottom bar.

*Note: the CTRL add a second instance of the circular mask*

►Do the same steps to create the second mask for the second eye.

►Then click on the right mouse button to stop the definition of the
masks.

►To check if the two masks are defined correctly, hover over the eye
positions (without clicking on any mouse button) and you will see the
concentric circles on each eye hovered.

*Note: Both masks will not be displayed simultaneously on the image, you
will see only the hovered mask.*

# 8. Annexes

Some useful styles from different authors.

## dtstyles

dtstyles :
[[https://dtstyle.net/​]{.underline}](https://dtstyle.net/%E2%80%8B)

-   un grand choix

-   pas d\'organisation

-   pas de version

-   peut utiliser des modules qui sont déprécié ou simplement qui ont
    > été retiré de darktable.

## Mel265

Mel265 (Stefano Ferro) :
[[https://mel365.com/darktable-presets-and-styles/]{.underline}](https://mel365.com/darktable-presets-and-styles/)

-   A fait des style et des video montrant comment ils fonctionnent

-   devraient fonctionner avec darktable 4 sans soucis

## Jade-nl

Jade-nl :
[[https://github.com/jade-nl/dt.st\...​]{.underline}](https://github.com/jade-nl/dt.st...%E2%80%8B)

-   un répertoire de plusieurs style, a tester

-   télécharger sur le github

-   par de prévisualisation

## Joao Pedro Almedia

Joao Pedro Almedia :
[[https://blog.joaoalmeidaphotogra\...​]{.underline}](https://blog.joaoalmeidaphotography)

-   a certainement les style de qualité

-   prévisualisation

-   github :
    > [[https://github.com/t3mujin/t3muj\...​]{.underline}](https://github.com/t3mujin/t3muj...%E2%80%8B)

[^1]: Link:
    [[https://docs.darktable.org/usermanual/development/en/guides-tutorials/]{.underline}](https://docs.darktable.org/usermanual/development/en/guides-tutorials/)

[^2]: Link:
    [[https://github.com/darktable-org/darktable/releases/download/release-5.2.1/darktable-5.2.1-win64.exe]{.underline}](https://github.com/darktable-org/darktable/releases/download/release-5.2.1/darktable-5.2.1-win64.exe)
