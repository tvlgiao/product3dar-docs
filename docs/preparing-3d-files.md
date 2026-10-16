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

## One-minute checklist {#checklist}

Before you upload, check that:

1. **The file is a GLB if you can choose.** It's the most reliable [format](#formats); zipped glTF and OBJ, FBX and
   STL work too.
2. **The textures are inside the file.** A model whose textures stayed behind shows white or grey
   ([why](#model-shows-white)).
3. **It's light enough for phones:** about 3 MB for the website model and 100,000 triangles or fewer
   ([budgets](#budgets)).
4. **Textures are 2,048 px or less** on each side ([textures](#textures)).
5. **It's the right size and standing upright.** GLB and glTF are read in metres; OBJ and STL in millimetres; FBX
   in the units saved in the file ([scale](#scale)).
6. **Every texture uses the same UV map** ([one UV map](#one-uv-map)).
7. **A GLB or glTF opens in a free online viewer** such as glTF Viewer ([free tools](#software)). If it looks right
   there, it almost always looks right in the app. These viewers read glTF only: check an OBJ, FBX or STL in the 3D
   software you made it with, or on the model page after you upload.

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
[processing allowance](/docs/plan-and-usage/#processing). It also removes any USDZ files you uploaded yourself: export them again at the new size and orientation before you
add them back ([your own USDZ files](/docs/ar/#own-usdz)).

Best practice: export from your 3D software in metres, with the product standing upright and its base at the origin.

## Materials {#materials}

- Use standard **PBR materials** (base color, metallic, roughness, normal, occlusion, emissive). In Blender, that is
  the **Principled BSDF** shader.
- Advanced glTF material extensions (sheen, clearcoat, transmission, volume, iridescence and others) show in the
  website viewer, but **Android AR does not support them**. Android AR then shows the model with its base colours,
  metalness and roughness only. See
  [Android AR uses simplified materials](/docs/processing-errors/#android-ar-unsupported-extensions).
- **Material options** (the glTF `KHR_materials_variants` extension) let one file hold several materials, for example
  fabric colors. You can then pick a material for each product or variant rule. Up to 20 material options per model,
  each with a unique name of 1 to 64 characters.
- Animations, skeletons (armatures) and shape keys are not shown: the app shows still models. See
  [Animation removed](/docs/processing-errors/#animation-stripped).

## Textures {#textures}

- Formats: **PNG, JPEG or WebP**. Other formats (KTX2, TGA, TIFF, BMP, AVIF, PSD) are not accepted.
- Each side can be up to 8,192 px, and all textures together up to 64 million pixels.
- Textures larger than 2,048 px are shrunk to 2,048 px for the website, so there's no benefit in sending larger ones.
- Use **one UV map** for all textures ([details](#one-uv-map)).
- Fewer, combined textures (a texture atlas) load faster than many small ones.

### Textures inside the file {#embedded-textures}

The app needs the model and all its textures in one upload:

- A **GLB** holds the textures inside the file. That's why we recommend it.
- A **glTF** keeps its textures as separate image files: zip the `.gltf`, its `.bin` and all its images together,
  keeping the folders as they are.
- A **GLB can still point at separate image files.** Some free model packs ship a GLB with its textures in a
  `Textures` folder beside it. Zip the GLB with that folder, or make a self-contained GLB:
  - **Blender:** import the model, choose **File › External Data › Pack Resources**, check that the colours show in
    Material Preview, then export a GLB ([Blender](#blender)). Leave the exporter's **Images** option on
    **Automatic**, not **None**.
  - **gltf-transform** ([free tools](#software)): `gltf-transform copy model.gltf model.glb` reads the `.gltf` with
    its images and writes one GLB with the images inside.

### My model shows white or grey {#model-shows-white}

If the model has the right shape but shows plain white or grey, its textures didn't reach the app. The app shows the
[Missing textures](/docs/processing-errors/#missing-textures) warning and names the image it couldn't find; the model
is published with a plain white surface in place of each missing image.

This happens when a GLB refers to an image file next to it (common with free model packs, for example a
`colormap.png` in a `Textures` folder), when a glTF zip is missing its images or has them in a different folder than
the `.gltf` expects, or when your 3D software links textures from elsewhere on your computer. Make a GLB with the
textures inside ([above](#embedded-textures)), or zip the model with its images, and upload again.

### Making textures smaller {#texture-sizes}

The app shrinks textures larger than 2,048 px for you, but big textures make the upload and processing slower and
can reach the 8,192 px or 64 million pixel limits. To shrink them yourself:

- **gltf-transform:** `gltf-transform resize --width 2048 --height 2048 in.glb out.glb` keeps each texture's shape
  and never makes one larger.
- **Blender:** open each image in the Image Editor, choose **Image › Resize**, save it and export again.

### One UV map {#one-uv-map}

A UV map tells the model where each part of a texture goes. Android AR supports only one. If a colour, normal,
metal/roughness or glow texture uses a second UV map, the model has no Android AR
([Android AR is not available](/docs/processing-errors/#scene-viewer-unavailable)); an ambient occlusion texture on a
second UV map is just left out of the Android AR file. The website viewer and iPhone & iPad AR still work. In Blender,
check **Object Data properties › UV Maps**. If a texture uses a second UV map, deleting that map doesn't move the
texture onto the first one: the texture would then sit wrong everywhere. Bake the texture onto the first UV map
instead (Cycles **Bake**, with the first UV map active), connect the baked image in place of the old one, and only
then delete the extra UV map and export.

## Polygon and size budgets {#budgets}

| What | Recommended | Warning | Refused |
|---|---|---|---|
| Triangles (website model) | 100,000 or fewer | above 200,000 | above 500,000 |
| Website model after optimization | 3 MB or less | above 5 MB | above 15 MB |
| Android AR file (each material option) | 5 MB or less, 100,000 triangles or fewer | — | above 15 MB: no Android AR for that material option |
| iPhone & iPad AR file (USDZ, each placement) | — | — | above 25 MB: no iPhone & iPad AR for that floor or wall placement; the other placement still works |
| Textures | 2,048 px on each side (larger ones are shrunk) | — | above 8,192 px on a side, or above 64 million pixels for all textures together |
| Objects (nodes) in the scene | — | — | above 5,000 |
| Material options | — | — | above 20 |

The app does not reduce your polygon count. If a model is too heavy, reduce it in your 3D software (in Blender, a
**Decimate** modifier) or with one of the [free tools](#software), and upload again. See
[Model is too large or too complex](/docs/processing-errors/#over-budget).

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
| Android phone or tablet | Google's AR viewer (Scene Viewer), or AR in Chrome where the phone supports it | an Android AR file: one UV map, 15 MB or less, and no glTF extension that Android AR can't read. Material effects such as sheen, clearcoat or transmission don't block it: they are simplified ([materials](#materials)) |
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

Blender works in metres by default, which matches what the app expects. Keep **Unit Scale** at 1.0 (Scene properties
› Units), apply your objects' scale (**Object › Apply › Scale**) and keep **+Y Up** on when you export.

- **Too many triangles:** add a **Decimate** modifier (Modifier properties › Add Modifier › Generate › Decimate),
  lower **Ratio** until the count is low enough and the shape still looks right, and keep **Apply Modifiers** on.
- **Textures outside the file:** **File › External Data › Pack Resources**, then export a GLB.
- **Too many separate objects:** select the parts that never move on their own and join them (**Object › Join**,
  Ctrl+J).

### 3ds Max and Maya {#max-maya}

Export **glTF/GLB** if your version or a glTF exporter plugin supports it; otherwise export **FBX** with
**Embed Media** turned on (so the textures are inside the file), or zip the `.fbx` with its `.fbm` folder. Check the
export units: FBX units are not always read correctly, so check the real-world size after processing and fix it
with **Size (%)** if needed.

### SketchUp {#sketchup}

Export through a glTF/GLB exporter extension if you have one; otherwise export **OBJ** and zip it with its `.mtl` and
texture files. Remember the app reads OBJ in millimetres: check the real-world size after processing.

### CAD and online converters {#converters}

CAD files (STEP, IGES) must be converted first. An online converter can produce a GLB, but check the result in a
[free glTF viewer](#software) before uploading, and prefer exporting from the original software when you can. STL
files have no colors or textures, so the model shows in a plain material.

## Free tools {#software}

### gltf-transform

[gltf-transform](https://gltf-transform.dev/cli) is a free command-line tool (it needs Node.js):

- `gltf-transform copy model.gltf model.glb`: makes one GLB with its textures inside.
- `gltf-transform resize --width 2048 --height 2048 in.glb out.glb`: shrinks textures.
- `gltf-transform simplify in.glb out.glb --ratio 0.5`: aims to keep about half of the vertices, and stops earlier
  if going further would visibly change the shape.
- `gltf-transform optimize in.glb out.glb --instance false`: does everything at once (joins meshes, simplifies,
  shrinks and compresses textures, compresses the geometry). Keep `--instance false`: without it, a model with many
  copies of the same part can be saved with GPU instancing, which Android AR can't show. The app already optimizes
  the website model for you, so you only need this to make a very large file smaller.
- `gltf-transform inspect in.glb`: lists the meshes, triangles and textures, so you can see what makes a file heavy.

### gltfpack

[gltfpack](https://meshoptimizer.org/gltf/) packs a model into one compact GLB.
`gltfpack -i in.gltf -o out.glb -si 0.5` aims for about half of the triangles and puts the textures inside the GLB.
It can keep more than half where the shape doesn't allow it, so check the count afterwards (`gltf-transform
inspect out.glb`) before you upload.
Don't use its KTX2 texture option (`-tc`): the app accepts PNG, JPEG and WebP textures only.

### Apple Reality Converter and Reality Composer Pro

Apple's free Mac apps for iPhone & iPad AR files. **Reality Converter** turns a glTF, OBJ or USD file into a USDZ
and lets you check it under different lighting; **Reality Composer Pro** opens, edits and exports USD scenes. You
need them only to make [your own USDZ files](/docs/ar/#own-usdz); otherwise the app creates the iPhone & iPad AR
files for you.

### Online viewers and validators

- [glTF Viewer](https://gltf-viewer.donmccurdy.com/): drag in a GLB, or a `.gltf` with its files, to see the model
  and any problems in the file.
- [Khronos glTF Validator](https://github.khronos.org/glTF-Validator/): checks the file against the glTF 2.0
  standard. Errors here usually mean [Part of the model's shape data is missing](/docs/processing-errors/#invalid-gltf).
- [Khronos glTF Sample Viewer](https://github.khronos.org/glTF-Sample-Viewer-Release/): the reference viewer, with
  material options and lighting choices.
- [modelviewer.dev editor](https://modelviewer.dev/editor/): previews the model in the same kind of viewer your
  storefront uses.
