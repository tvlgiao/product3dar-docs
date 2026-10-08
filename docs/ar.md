---
title: AR (view in your space)
description: How shoppers view your products in their room with AR on iPhone, iPad and Android, the desktop QR code, floor or wall placement, real size, and your own USDZ files.
lead: AR places the product in the shopper's room through the phone's camera, at real size.
---

<nav class="toc" aria-label="On this page" markdown="1">
<p class="toc-title">On this page</p>

* TOC
{:toc}
</nav>

## How shoppers open AR {#how-it-opens}

AR is available from the 3D view. Once a shopper opens 3D on a product page (and has chosen every option, if the
product has options), an AR button appears at the bottom of the viewer:

| Device | Button | What happens |
|---|---|---|
| iPhone, iPad | **View in AR** | Apple's AR Quick Look opens the product in the camera view. |
| Android (most phones) | **View in AR** | Google's AR viewer (Scene Viewer) opens the product in the camera view. |
| Android, Chrome with WebXR | **Prepare AR**, then **Launch AR** | AR starts inside the browser. If it fails, **Open in AR app** opens Google's AR viewer instead. |
| Computer | **View in your space** | A QR code appears: "Scan with your phone". Scanning it opens the same product, with the same options, on the phone. **Back to 3D** closes it. |

The button is hidden on a device that can't show AR for this model (and on a computer when AR is off for the
product). The **AR button** label can be changed per storefront ([Button labels](/docs/storefronts/#button-labels)).

<div class="note" markdown="1">
**Beta:** AR on real iPhone and Android devices is still being confirmed during the beta, and the AR files use a
cautious format until then. AR availability depends on the shopper's device: Android AR needs a phone that supports
Google's AR services.
</div>

## iPhone and iPad (Quick Look, USDZ) {#iphone-ipad}

iPhone and iPad AR uses USDZ files. The app creates them for you from your model, one for floor placement and one for
wall placement, for each material option. You can also [use your own USDZ files](#own-usdz).

On the model's **AR** tab, **iPhone & iPad AR (floor)** and **iPhone & iPad AR (wall)** show **Created
automatically**, **Your file** or **Not available**. If they say **Not available**, see
[iOS AR file could not be created](/docs/processing-errors/#usdz-failed),
[AR file is too large](/docs/processing-errors/#ar-over-budget) or
[iOS AR is not available](/docs/processing-errors/#quick-look-unavailable).

## Android (Scene Viewer) {#android}

Android AR uses a separate AR file that the app creates from your model for each material option. Android's AR viewer
supports fewer material features than the website viewer, so some models get no Android AR. The model's **AR** tab
shows **Android AR: Yes** or **Not available**.

The usual causes and fixes:

- the model uses advanced material extensions (sheen, clearcoat, transmission and others):
  [Android AR: unsupported material extensions](/docs/processing-errors/#android-ar-unsupported-extensions);
- a material uses a second UV map, or the file is over 15 MB:
  [Android AR is not available](/docs/processing-errors/#scene-viewer-unavailable),
  [AR file is too large](/docs/processing-errors/#ar-over-budget).

## The QR code on a computer {#desktop-qr}

On a computer, **View in your space** shows a QR code inside the viewer: "Point your phone’s camera at the code to see
{product} in your room. Works on iPhone, iPad and Android." The code opens the same product page on the phone, with
the options the shopper chose, ready for AR.

In the app, the setup guide's **Show QR code** and the **View in your space (QR code)** button under the preview on a
model page do the same for you, so you can try AR on your own phone. On the model page it works once the model is live
on a product ("Add the model to a product first").

## Placement: floor or wall {#placement-and-size}

Set these per product, in the **Display and AR** card ([Products and variants](/docs/products-and-variants/#display-and-ar)):

- **Let shoppers view it in their space (AR)**: turn AR on or off for the product. With AR off, shoppers get the 3D
  view only.
- **AR placement**: **On the floor** (furniture, lamps, rugs) or **On a wall** (art, mirrors, shelves, TVs).
  On iPhone and iPad the matching USDZ file is used; on Android the AR viewer allows wall placement.
- **Size in AR**:
  - **Real size**: the product appears at its real size and shoppers can't resize it. Best for furniture, where size
    is the point.
  - **Let shoppers resize**: shoppers can pinch to make it bigger or smaller.

Real size depends on the model being in the right units. Check **Real-world size in AR** on the model's **AR** tab
and fix it with **Change size** if needed ([Scale, units and orientation](/docs/preparing-3d-files/#scale)).

## Your own USDZ files {#own-usdz}

If you already have USDZ files made for AR Quick Look (for example from Reality Composer or a 3D agency), you can use
them for iPhone and iPad instead of the generated ones:

1. Open the model, then the **AR** tab, and find **Your own iPhone & iPad AR files (optional)**.
2. Add a `.usdz` file (up to 25 MB) for **Floor placement**, **Wall placement**, or both. A floor file must be
   anchored to a horizontal plane and a wall file to a vertical plane.
3. Keep **Create the iPhone & iPad file for me when I don’t add one** checked if you want the app to create the
   placement you didn't add (and the files for other material options).
4. Click **Upload AR files**. A new version of the model is processed.

Notes:

- Your files are used as they are, for the model's default material. Material options get the generated file while
  **Create the iPhone & iPad file for me…** is checked.
- Saving a new size or rotation for the model removes your own USDZ files; add them again afterwards.
- A file anchored to the wrong surface is refused: see
  [iOS AR file does not match its slot](/docs/processing-errors/#usdz-override-mismatch).

## AR and your plan {#ar-and-plan}

Opening AR does not count as a 3D view: [AR launches don't count toward your plan](/docs/plan-and-usage/#what-counts).
The AR files still count toward data transfer.
