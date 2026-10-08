---
title: Preparing 3D files
description: Supported 3D formats and limits, scale and orientation, materials, textures, polygon budgets, what Product 3D & AR optimizes, and what AR needs on each device.
lead: A well-prepared file processes in a couple of minutes, loads fast on phones and looks right in AR.
---

<nav class="toc" aria-label="On this page" markdown="1">
<p class="toc-title">On this page</p>

* TOC
{:toc}
</nav>

## Supported formats {#formats}

| Format | How to upload | Size limit |
|---|---|---|
| **GLB** (recommended) | one `.glb` file | 100 MB |
| **glTF** | a `.zip` with the `.gltf`, its `.bin` files and its textures | 200 MB (zip) |
| **OBJ** | a `.zip` with the `.obj`, its `.mtl` and its textures | 200 MB (zip) |
| **FBX** | one `.fbx` with embedded textures, or a `.zip` with the `.fbx` and its `.fbm` texture folder | 100 MB (single file), 200 MB (zip) |
| **STL** | one `.stl` file (no colors or textures) | 100 MB |
| **USDZ** | optional: your own iPhone & iPad AR file, added on a model's **AR** tab ([details](/docs/ar/#own-usdz)) | 25 MB |

- **GLB works best.** It holds the model, materials and textures in one file and needs no conversion.
- A `.gltf` or `.obj` file on its own is not accepted: zip it together with the files it uses.
- The app reads the file type from the file's contents, not from its name. Renaming a file doesn't change its format.
- Sizes use 1 MB = 1,048,576 bytes.

<div class="tip" markdown="1">
**Don't have a 3D file?** Ask your product's manufacturer or designer for a GLB or glTF file (many already have CAD or
3D files for their catalogs), or have one made by a 3D artist or a 3D scanning service. Ask for real-world scale in
metres, a single still pose, and textures no larger than 2,048 px.
</div>

### Zip files {#zip-files}

When you upload a zip:

- it must contain **exactly one** model file (`.gltf`, `.glb`, `.obj` or `.fbx`);
- every file the model uses must be inside the zip, with relative paths (no web addresses, no paths that go outside
  the zip);
- at most 500 files and 1 GB once unzipped; no password; no file compressed more than 100 times;
- no two files whose names differ only in upper and lower case.

Use your computer's standard **Compress** (Mac) or **Send to › Compressed (zipped) folder** (Windows). Leave out
backups and large source files such as `.blend`, `.max` or `.psd`.
See [Zip file rejected](/docs/processing-errors/#zip-unsafe) if a zip is refused.

## Scale, units and orientation {#scale}

AR shows your product at its real size, so the model's size matters.

| Format | Units the app assumes | Up direction the app assumes |
|---|---|---|
| GLB, glTF | metres (the glTF standard) | Y up |
| OBJ | millimetres | Y up |
| STL | millimetres | Z up |
| FBX | the units the converter reads from the file (not always reliable) | Y up |

After processing, check the size on the model's **AR** tab ("Real-world size in AR: … cm") or in the
**File and optimization** card. If it's wrong or the model lies on its side:

1. Open the model, then the **Presentation** tab, and open **Size and orientation**.
2. Change **Size (%)** (for example 10% if a model in centimetres came out 10 times too big), or use
   **Rotate around X / Y / Z (°)** in steps of 90°.
3. Click **Save presentation**.

Changing size or orientation processes the model again (a few minutes) and counts as a new model file in your
[processing allowance](/docs/plan-and-usage/#processing). It also removes any USDZ files you uploaded yourself.

Best practice: export from your 3D software in metres, with the product standing upright and its base at the origin.

## Materials {#materials}

- Use standard **PBR materials** (base color, metallic, roughness, normal, occlusion, emissive). In Blender, that is
  the **Principled BSDF** shader.
- Advanced glTF material extensions (sheen, clearcoat, transmission, volume, iridescence and others) show in the
  website viewer, but **Android AR does not support them**. A model that uses them has no Android AR. See
  [Android AR: unsupported material extensions](/docs/processing-errors/#android-ar-unsupported-extensions).
- **Material options** (the glTF `KHR_materials_variants` extension) let one file hold several materials, for example
  fabric colors. You can then pick a material for each product or variant rule. Up to 20 material options per model,
  each with a unique name of 1 to 64 characters.
- Animations, skeletons (armatures) and shape keys are not shown: the app shows still models. See
  [Animation removed](/docs/processing-errors/#animation-stripped).

## Textures {#textures}

- Formats: **PNG, JPEG or WebP**. Other formats (KTX2, TGA, TIFF, BMP, AVIF, PSD) are not accepted.
- Each side can be up to 8,192 px, and all textures together up to 64 million pixels.
- Textures larger than 2,048 px are shrunk to 2,048 px for the website, so there's no benefit in sending larger ones.
- Use **one UV map** for all textures. A material that reads a second UV map works on the website but has no Android AR.
- Fewer, combined textures (a texture atlas) load faster than many small ones.

## Polygon and size budgets {#budgets}

| What | Recommended | Warning | Refused |
|---|---|---|---|
| Triangles (website model) | 100,000 or fewer | above 200,000 | above 500,000 |
| Website model after optimization | 3 MB or less | above 5 MB | above 15 MB |
| Android AR file (each material option) | 5 MB or less | — | above 15 MB: no Android AR |
| iPhone & iPad AR file (USDZ) | — | — | above 25 MB: no iPhone & iPad AR |
| Objects (nodes) in the scene | — | — | above 5,000 |

The app does not reduce your polygon count. If a model is too heavy, reduce it in your 3D software (in Blender, a
**Decimate** modifier) and upload again. See [Model is too large or too complex](/docs/processing-errors/#over-budget).

## What the app does with your file {#processing}

Every upload goes through these stages (shown on the model page):

1. **File received** and **File checked**: the type, size, zip contents and textures are checked; other formats are
   converted to glTF; the file is validated against the glTF 2.0 standard.
2. **Optimizing for the website**: duplicate and unused data is removed, objects are merged where possible, textures
   are shrunk to 2,048 px at most and compressed (WebP), and the geometry is compressed. Your original file is kept.
3. **Creating AR files for phones**: an Android AR file and iPhone & iPad AR files (USDZ, one for floor and one for
   wall placement) for each material option, and preview images.
4. **Ready to use**.

Processing usually takes under 2 minutes. You can leave the page while it runs. Each run counts against your plan's
[processing allowance](/docs/plan-and-usage/#processing).

<div class="note" markdown="1">
**Beta:** the AR files use a cautious format while device testing finishes. They work today; they may get smaller or
sharper later. The model's **AR** tab notes this under **Details**.
</div>

## What AR needs on each device {#ar-requirements}

| Device | How AR opens | What the model needs |
|---|---|---|
| iPhone, iPad | AR Quick Look, from **View in AR** | an iPhone & iPad AR file (created for you, or your own USDZ) for the placement you chose |
| Android phone or tablet | Google's AR viewer (Scene Viewer), or AR in Chrome where the phone supports it | an Android AR file: no unsupported material extensions, one UV map, 15 MB or less |
| Computer | **View in your space** shows a QR code that opens the page on a phone | — |

The model's **AR** tab, under **Where shoppers can see it**, shows for each material option whether **Website 3D
viewer**, **Android AR**, **iPhone & iPad AR (floor)** and **iPhone & iPad AR (wall)** are available. More in
[AR (view in your space)](/docs/ar/).

## Model settings {#model-settings}

Open a model from **Models**. The page shows the 3D preview, **Used on products**, **File and optimization**, and
three tabs:

- **Presentation**
  - **Starting view**: how shoppers first see the model. Turn the preview, then click **Use the current view**, or
    use **Turn around** and **Height of view**. **Fit the whole model in view** sets the distance for you.
  - **Lighting**: **Style** (**Neutral studio (recommended)** or **Classic, brighter**) and **Brightness**.
  - **Size and orientation**: see [Scale, units and orientation](#scale).
  - Click **Save presentation**. Shoppers keep the current view until the new one is ready (about a minute).
    Starting view and lighting changes count as presentation changes in your allowance.
- **AR**: where the model works, its real-world size, any warnings, and your own USDZ files
  ([details](/docs/ar/#own-usdz)).
- **Versions**: every version of the model, newest first, with the one **Shown now**.
  - **Replace the model file**: upload a new file for the same model. Products keep showing the current version until
    the new one is ready, then switch to it.
  - **Re-optimize**: process the same file again with the app's latest improvements.

From the **⋯** menu (on the model page or on a model tile) you can **Rename**, **Replace file**, **Re-optimize** or
**Delete** a model. The name is only for you. A model that is live on products can't be deleted: choose another model
for those products, or turn off their 3D, first. A model used only in unpublished drafts can be deleted with
**Delete and remove from drafts**.

## Exporting from common tools {#exporting}

### Blender {#blender}

1. Select the objects to export, then **File › Export › glTF 2.0 (.glb/.gltf)**.
2. **Format**: **glTF Binary (.glb)**.
3. **Include**: turn on **Selected Objects**.
4. **Mesh**: turn on **Apply Modifiers**.
5. **Animation**: turn it off (and **Shape Keys** and **Skinning** unless you need them).
6. Export and upload the `.glb`.

Blender works in metres by default, which matches what the app expects.

### 3ds Max and Maya {#max-maya}

Export **glTF/GLB** if your version or a glTF exporter plugin supports it; otherwise export **FBX** with
**Embed Media** turned on (so the textures are inside the file), or zip the `.fbx` with its `.fbm` folder. Check the
export units: FBX units are not always read correctly, so check the real-world size after processing and fix it
with **Size (%)** if needed.

### SketchUp {#sketchup}

Export through a glTF/GLB exporter extension if you have one; otherwise export **OBJ** and zip it with its `.mtl` and
texture files. Remember the app reads OBJ in millimetres: check the real-world size after processing.

### CAD and online converters {#converters}

CAD files (STEP, IGES) must be converted first. An online converter can produce a GLB, but check the result in a free
glTF viewer before uploading, and prefer exporting from the original software when you can. STL files have no colors
or textures, so the model shows in a plain material.
