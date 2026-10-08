---
title: Processing errors and warnings
description: What each Product 3D & AR processing error and warning means, why it happens and how to fix your model file in Blender, 3ds Max, Maya, SketchUp or a converter.
lead: When the app finds a problem in a model file, it shows a short title and a "How to fix this" link to the matching section below.
---

**Errors** stop the upload from being used: your storefront keeps showing what it showed before (the previous version
of the model, or no 3D). **Warnings** don't stop it: the model is ready, but something was changed or one feature (for
example Android AR) isn't available.

On the model page, each problem shows a plain explanation; the exact technical text (for example the name of a
missing texture or the list of extensions) is behind **Technical detail**. Open it: it often names exactly what to fix.

You can upload a fixed file at any time: open the model and use **Upload fixed file**, or **Versions › Replace the
model file**. Each run counts against your [processing allowance](/docs/plan-and-usage/#processing), except as noted
in [Which failed runs count](#allowance).

<nav class="toc" aria-label="On this page">
<p class="toc-title">On this page</p>
<ul>
  <li><a href="#statuses">Model statuses</a></li>
  <li><a href="#before-upload">Messages before the upload</a></li>
  <li><a href="#errors">Errors</a></li>
  <li><a href="#warnings">Warnings</a></li>
  <li><a href="#android-ar-unsupported-extensions">Android AR uses simplified materials</a></li>
  <li><a href="#limits">Limits and "not processed"</a></li>
  <li><a href="#allowance">Which failed runs count</a></li>
  <li><a href="#contact-support">When to contact support</a></li>
</ul>
</nav>

| Code | Title in the app | Kind |
|---|---|---|
| [`UNSUPPORTED_FORMAT`](#unsupported-format) | Unsupported file format | Error |
| [`ZIP_UNSAFE`](#zip-unsafe) | Zip file rejected | Error |
| [`AMBIGUOUS_MAIN_FILE`](#ambiguous-main-file) | More than one model file in the zip | Error |
| [`INVALID_GLTF`](#invalid-gltf) | Part of the model’s shape data is missing | Error |
| [`OVER_BUDGET`](#over-budget) | Model is too large or too complex | Error |
| [`CONVERSION_FAILED`](#conversion-failed) | Conversion failed | Error |
| [`CONVERSION_TIMEOUT`](#conversion-timeout) | Conversion took too long | Error |
| [`OPTIMIZE_FAILED`](#optimize-failed) | We couldn’t optimize this model | Error (on our side) |
| [`USDZ_OVERRIDE_MISMATCH`](#usdz-override-mismatch) | iOS AR file does not match its slot | Error |
| [`UPLOAD_EXPIRED`](#upload-expired) | Upload expired or changed | Error |
| [`UPLOAD_SIZE_MISMATCH`](#upload-size-mismatch) | Uploaded file size does not match | Error |
| [`SUPERSEDED`](#superseded) | Replaced by a newer upload | Error |
| [`MISSING_TEXTURES`](#missing-textures) | Missing textures | Warning |
| [`ANIMATION_STRIPPED`](#animation-stripped) | Animation removed | Warning |
| [`SKIN_STRIPPED`](#skin-stripped) | Skeleton removed | Warning |
| [`MORPH_STRIPPED`](#morph-stripped) | Shape keys removed | Warning |
| [`WEB_OVER_TARGET`](#web-over-target) | Web model is larger than recommended | Warning |
| [`SCENE_VIEWER_UNAVAILABLE`](#scene-viewer-unavailable) | Android AR is not available | Warning |
| [`ANDROID_AR_UNSUPPORTED_EXTENSIONS`](#android-ar-unsupported-extensions) | Android AR uses simplified materials | Warning |
| [`AR_OVER_BUDGET`](#ar-over-budget) | AR file is too large | Warning |
| [`USDZ_FAILED`](#usdz-failed) | iOS AR file could not be created | Warning |
| [`QUICK_LOOK_UNAVAILABLE`](#quick-look-unavailable) | iOS AR is not available | Warning |
{: .codes}

## Model statuses {#statuses}

Each model on **Models** has one status:

| Status | Meaning | What to do |
|---|---|---|
| **Uploading** | The file is on its way. | Wait. You can use other pages of the app meanwhile; don't close the browser tab. |
| **Processing** | The app is checking and optimizing the file (usually under 2 minutes). | Wait. You can leave the page. |
| **Ready** | Shoppers can see it on products that use it. | — |
| **Not processed** | The file arrived but processing didn't start, usually because a limit was reached. | See [Limits and "not processed"](#limits). |
| **Upload not finished** | The file didn't arrive completely (the page was closed or the session ended). | **Finish upload** if the file was fully sent, or **Upload again**. |
| **Couldn’t process** | A problem on our side, not your file. | **Try again**. See [`OPTIMIZE_FAILED`](#optimize-failed). |
| **File needs a fix** | The file has a problem listed on this page. | **See the problem**, fix the file, upload it again. |
| **Hidden (plan limit)** | Kept, but not shown to shoppers because your plan's model limit is reached. | See [Plan and usage](/docs/plan-and-usage/#model-limit). |

If a model is already **Ready** and a newer upload of it fails, the status stays **Ready** with a note such as
"Last update failed". Shoppers keep seeing the ready version.

## Messages before the upload {#before-upload}

When you choose a file, the app checks it in your browser before uploading. These messages appear under the file and
the **Upload** button stays disabled:

| Message | What to do |
|---|---|
| The file is empty. | Export the file again; the file you chose has no content. |
| The zip file could not be read. | Create the zip again with your computer's standard Compress feature. |
| The zip contains no .gltf, .glb, .obj or .fbx file. | Put the model file in the zip. |
| The zip contains N model files; keep exactly one. | See [`AMBIGUOUS_MAIN_FILE`](#ambiguous-main-file). |
| This file type is not supported. Use GLB, glTF (zip), OBJ (zip), FBX or STL. | See [`UNSUPPORTED_FORMAT`](#unsupported-format). |
| The file is larger than 100 MB. (or 200 MB for a zip) | Reduce textures and polygons ([`OVER_BUDGET`](#over-budget)) and export again. |

## Errors {#errors}

### Unsupported file format {#unsupported-format}

<span class="kind kind-error">Error</span> <span class="code">UNSUPPORTED_FORMAT</span>

**What it means.** The app can't read this kind of file. It's not GLB, glTF, OBJ, FBX or STL; or a zip has no model
file in it; or a texture is not PNG, JPEG or WebP.

**Why it happens.** A file was renamed to `.glb` but is really another format; a `.gltf` or `.obj` was uploaded
without zipping; textures were saved as KTX2, TGA, TIFF, BMP, AVIF or PSD.

**How to fix it.**

1. Upload a GLB, a zip with a glTF, OBJ or FBX model, a single FBX, or an STL file. Renaming a file doesn't change
   its format; export it in the right format instead.
2. Convert textures to PNG or JPEG (or WebP), relink them in your 3D software, and export again.
   - **Blender:** in each material's image texture node, open the image and use **Image › Save As** with PNG or JPEG.
     Then export as GLB ([steps](/docs/preparing-3d-files/#blender)).
   - **3ds Max / Maya:** save the bitmaps as PNG or JPEG, relink them in the material editor, export again.
   - **SketchUp:** materials using other image formats should be re-imported as PNG or JPEG before export.
3. If unsure, export GLB from your 3D software. GLB is the most reliable format.

**Contact support** if the file opens in a glTF viewer but the app still says the format is unsupported.

### Zip file rejected {#zip-unsafe}

<span class="kind kind-error">Error</span> <span class="code">ZIP_UNSAFE</span>

**What it means.** The zip breaks one of the app's safety rules, or it's damaged.

**Why it happens.** The zip has more than 500 files, expands to more than 1 GB, has a file compressed more than 100
times, has paths that start at the root or contain `..`, contains links, is password protected, uses the zip64 format
or an unusual compression method, or has two files whose names differ only in upper and lower case. Some archive
tools and online services create such zips.

**How to fix it.**

1. Make a fresh zip with your computer's standard **Compress** (Mac) or **Send to › Compressed (zipped) folder**
   (Windows). No password.
2. Put only the model file and the textures it uses inside. Remove backups and source files (`.blend`, `.max`,
   `.psd`).
3. Keep it under 500 files and 1 GB unzipped.
4. Or skip the zip: export a single **GLB**.

### More than one model file in the zip {#ambiguous-main-file}

<span class="kind kind-error">Error</span> <span class="code">AMBIGUOUS_MAIN_FILE</span>

**What it means.** The zip has more than one `.gltf`, `.glb`, `.obj` or `.fbx` file, so the app can't tell which one
is the model. The technical detail lists the files found.

**How to fix it.**

1. Remove every model file except the one you want (exporters often leave an older copy or a second format next to it).
2. Upload other models separately: one model per upload.
3. Zip again and upload.

### Part of the model’s shape data is missing {#invalid-gltf}

<span class="kind kind-error">Error</span> <span class="code">INVALID_GLTF</span>

**What it means.** The glTF or GLB file is damaged or doesn't follow the glTF 2.0 standard. Typically a mesh points to
more data than the file contains.

**Why it happens.** The export was interrupted, the file was cut off while copying or downloading, it was edited by
hand, or it came from an exporter or converter that writes invalid glTF. Duplicated, empty or overly long (more than
64 characters) material option names cause this error too.

**How to fix it.**

1. Export the model again from your 3D software as glTF 2.0 / GLB.
   - **Blender:** **File › Export › glTF 2.0** ([settings](/docs/preparing-3d-files/#blender)).
   - **3ds Max / Maya:** use an up-to-date glTF exporter; or export FBX and let the app convert it.
   - **SketchUp:** use an up-to-date glTF exporter extension, or export OBJ and zip it with its textures.
2. Open the result in a free viewer such as the Khronos glTF Sample Viewer or a glTF validator to confirm it loads
   without errors.
3. If you use material options, give each one a different short name.
4. If the file came from an online converter, export from the original software instead, or try another converter.

**Contact support** if the file passes the Khronos glTF Validator with no errors and the app still shows this error.

### Model is too large or too complex {#over-budget}

<span class="kind kind-error">Error</span> <span class="code">OVER_BUDGET</span>

**What it means.** The model is over one of the limits. The technical detail shows the value measured.

| Limit | Value |
|---|---|
| Triangles | 500,000 |
| Texture size | 8,192 px per side; 64 million pixels for all textures together |
| Objects (nodes) | 5,000 |
| Material options | 20 |
| Website model after optimization | 15 MB |

It also appears when processing stopped repeatedly while reading or converting the file because it is too heavy.

**How to fix it.**

1. **Triangles:** reduce to 500,000 or fewer; 100,000 or fewer is much better for phones.
   - **Blender:** add a **Decimate** modifier (Collapse, ratio for example 0.3), check the shape, then export with
     **Apply Modifiers** on.
   - **3ds Max:** **ProOptimizer** modifier. **Maya:** **Mesh › Reduce**.
   - **SketchUp / CAD exports:** lower the export tessellation or curve quality; remove hidden inner parts (screws,
     internal components) that shoppers never see.
2. **Textures:** resize each texture to 2,048 px or less per side (the app shrinks larger ones anyway); combine many
   small textures into fewer.
3. **Objects:** join parts that don't need to stay separate (Blender: select them and press <kbd>Ctrl</kbd>+<kbd>J</kbd>).
4. **Material options:** keep 20 or fewer.
5. Export again and upload.

### Conversion failed {#conversion-failed}

<span class="kind kind-error">Error</span> <span class="code">CONVERSION_FAILED</span>

**What it means.** The app couldn't convert the file into a model it can optimize. The technical detail gives the
cause when it's known.

**Why it happens.**

- a file the model refers to (a `.bin` buffer or a texture) is missing from the zip;
- a file refers to a web address or to a path outside the zip;
- an OBJ has no faces, or faces that point to missing data;
- an FBX file could not be converted;
- a texture can't be read;
- the model has no visible geometry;
- the model is posed by a skeleton, or its shape keys are in use (the app shows still models).

**How to fix it.**

1. Put every file the model uses in the zip, with relative paths. In Blender, **File › External Data › Pack
   Resources** and exporting GLB avoids missing files altogether.
2. Posed or animated models: apply the pose and remove the armature, or set all shape key values to 0, before
   exporting. In Blender: select the mesh, apply the **Armature** modifier, delete the armature; for shape keys, use
   **Shape Keys › New Shape from Mix**, then remove the others.
3. FBX: export GLB (or OBJ) instead. In 3ds Max / Maya, use a glTF exporter if you have one.
4. Check that the model has at least one visible mesh with a size above zero.
5. Upload again.

**Contact support** if it keeps failing with a GLB that opens in other glTF viewers. Include the code and the file name.

### Conversion took too long {#conversion-timeout}

<span class="kind kind-error">Error</span> <span class="code">CONVERSION_TIMEOUT</span>

**What it means.** A processing step didn't finish within its 10-minute limit, or processing stopped unexpectedly
several times, or the run still hadn't finished after 24 hours.

**How to fix it.**

1. Simplify the model: fewer triangles, fewer and smaller textures (see [`OVER_BUDGET`](#over-budget)).
2. For FBX files, export GLB instead.
3. Upload again.

**Contact support** if a small, simple GLB times out.

### We couldn’t optimize this model {#optimize-failed}

<span class="kind kind-error">Error</span> <span class="code">OPTIMIZE_FAILED</span>

**What it means.** Your file passed every check, but the website model our optimizer made from it didn't. **This is a
problem on our side, not in your file.** It is logged automatically and we'll fix it.

**What to do.**

1. Nothing needs to change in your file. Click **Try again** now or later. Your storefront keeps showing the current
   version meanwhile.
2. This failed run is returned to your allowance (up to 3 such runs per store per day, UTC). When it is, the app says
   "This attempt didn't count toward your allowance."
3. If it fails again, **Contact support** from the model page. Open **Details for support** and copy the reference
   into your email.

### iOS AR file does not match its slot {#usdz-override-mismatch}

<span class="kind kind-error">Error</span> <span class="code">USDZ_OVERRIDE_MISMATCH</span>

**What it means.** On the model's **AR** tab you added your own USDZ file for **Floor placement** or **Wall
placement**, but the file is set to be placed on the other kind of surface, or is not set to a surface at all. The app
doesn't change this setting in your file.

**How to fix it.**

1. Check that the floor and wall files aren't swapped.
2. **Floor placement** needs a USDZ anchored to a horizontal plane; **Wall placement** one anchored to a vertical
   plane. Set this in the tool that made the USDZ (for example Reality Composer), export again and upload.
3. Or don't add your own file, and keep **Create the iPhone & iPad file for me when I don’t add one** checked.

### Upload expired or changed {#upload-expired}

<span class="kind kind-error">Error</span> <span class="code">UPLOAD_EXPIRED</span>

**What it means.** The upload wasn't completed within 24 hours, or the uploaded file changed or disappeared before it
was processed.

**How to fix it.** Upload the file again and leave the browser tab open until the upload finishes.

### Uploaded file size does not match {#upload-size-mismatch}

<span class="kind kind-error">Error</span> <span class="code">UPLOAD_SIZE_MISMATCH</span>

**What it means.** The file that arrived isn't the size your browser announced, so it was probably cut off.

**How to fix it.** Upload again, if possible on a stable connection.

### Replaced by a newer upload {#superseded}

<span class="kind kind-error">Error</span> <span class="code">SUPERSEDED</span>

**What it means.** You uploaded a newer file for the same model (or deleted the model) before this one finished, so
this one was stopped. Nothing is wrong with your file.

**What to do.** Nothing. The newer upload is the one that counts. If the stopped run hadn't started yet, it's returned
to your allowance.

## Warnings {#warnings}

The model is ready and published where you use it. A warning tells you something was changed or isn't available.
Warnings show on the model's **AR** tab.

### Missing textures {#missing-textures}

<span class="kind kind-warning">Warning</span> <span class="code">MISSING_TEXTURES</span>

**What it means.** The model points to image files (or an OBJ's `.mtl` file) that aren't in the upload. The model is
published without them, so it can look plain or grey. The technical detail names the missing file.

**How to fix it.** Add the missing file to the zip, next to the model and with the same name the model uses, and
upload again. In Blender, **File › External Data › Report Missing Files** lists them; exporting GLB packs textures
into the file.

### Animation removed {#animation-stripped}

<span class="kind kind-warning">Warning</span> <span class="code">ANIMATION_STRIPPED</span>

**What it means.** The model had animation. Product 3D & AR shows still models, so the animation was removed and the
model is shown in its rest pose.

**How to fix it.** Nothing, if a still model is what you want. To choose the pose, set it in your 3D software and
export without animation (Blender: turn off **Animation** in the glTF export settings).

### Skeleton removed {#skin-stripped}

<span class="kind kind-warning">Warning</span> <span class="code">SKIN_STRIPPED</span>

**What it means.** The model had a skeleton (armature) in its neutral pose. The skeleton was removed so the model
loads on every device. A model posed by its skeleton is refused instead ([`CONVERSION_FAILED`](#conversion-failed)).

**How to fix it.** Nothing needed. To avoid the warning, export without the armature (Blender: turn off **Skinning**).

### Shape keys removed {#morph-stripped}

<span class="kind kind-warning">Warning</span> <span class="code">MORPH_STRIPPED</span>

**What it means.** The model had shape keys (morph targets), all at 0. They were removed so the model loads on every
device. A model with shape keys in use is refused instead ([`CONVERSION_FAILED`](#conversion-failed)).

**How to fix it.** Nothing needed. To avoid the warning, apply or delete the shape keys before exporting (Blender:
turn off **Shape Keys** in the export settings).

### Web model is larger than recommended {#web-over-target}

<span class="kind kind-warning">Warning</span> <span class="code">WEB_OVER_TARGET</span>

**What it means.** The optimized model for the website is above 5 MB or above 200,000 triangles. It's published, but
it may load slowly on phones and uses more of your plan's data transfer. The target is 3 MB or less.

**How to fix it.**

1. Resize textures to 2,048 px or less (1,024 px is often enough for small products), and use JPEG for photos-like
   color textures.
2. Reduce triangles (see [`OVER_BUDGET`](#over-budget)); 100,000 or fewer is a good target.
3. Remove parts shoppers never see.
4. Upload the lighter file with **Versions › Replace the model file**.

### Android AR is not available {#scene-viewer-unavailable}

<span class="kind kind-warning">Warning</span> <span class="code">SCENE_VIEWER_UNAVAILABLE</span>

**What it means.** For the material option named in the message, the app couldn't create the Android AR file. The
website viewer and iPhone & iPad AR are not affected. On Android, shoppers still get the 3D view, without the AR button.

**Why it happens.** One of these (the technical detail says which):

- the model uses an **extension Android AR can't show that isn't a material effect** (for example GPU instancing,
  or spec-gloss materials): the detail reads "unsupported extensions: …";
- a material uses a **second UV map**: the detail reads "material "…" uses a second UV set";
- the Android AR file failed its final check.

Material effects such as sheen, clearcoat or transmission no longer block Android AR: see
[Android AR uses simplified materials](#android-ar-unsupported-extensions).

**How to fix it.**

- Extensions: export without them (in most exporters, turn off instancing, and use metallic-roughness PBR materials).
- Second UV map: make every texture use the first UV map. In Blender, in **Object Data Properties › UV Maps**, keep
  one UV map (or make sure every Image Texture node uses the first one), then export again.
- Final check failed: upload again; if it repeats, contact support with the model name.

### Android AR uses simplified materials {#android-ar-unsupported-extensions}

<span class="kind kind-warning">Warning</span> <span class="code">ANDROID_AR_UNSUPPORTED_EXTENSIONS</span>

**What it means.** The model uses material effects that Android's AR viewer (Google Scene Viewer) cannot show, such as
sheen (fabric), clearcoat (a glossy top layer) or transmission (glass). The app still creates the Android AR file:
there the model shows its base colours, metalness and roughness, without those effects. The website viewer and
iPhone & iPad AR keep the full look. The model's **AR** tab names the effects for the material option you select.

Effects that are simplified for Android AR:

| Effect | glTF extension | Blender Principled BSDF input that writes it |
|---|---|---|
| fabric sheen | `KHR_materials_sheen` | **Sheen** weight above 0 |
| clear varnish layer | `KHR_materials_clearcoat` | **Coat** (Clearcoat) weight above 0 |
| glass-like see-through | `KHR_materials_transmission` (with `KHR_materials_volume`) | **Transmission** weight above 0 |
| rainbow-like film | `KHR_materials_iridescence` | **Thin Film** / iridescence settings |
| specular strength and color | `KHR_materials_specular` | **Specular** settings changed from default |
| index of refraction | `KHR_materials_ior` | **IOR** changed from the exporter's default |
| emission brighter than 1 | `KHR_materials_emissive_strength` | **Emission Strength** above 1 |
| brushed metal, dispersion | `KHR_materials_anisotropy`, `KHR_materials_dispersion` | **Anisotropic**, **Dispersion** |

(Input names vary slightly between Blender versions.)

**Nothing is required.** For the closest match in Android AR, bake the look of these effects into the basic inputs
before you export.

*In Blender* (also works for a GLB you got from someone else: **File › Import › glTF 2.0**):

1. In every **Principled BSDF**, get the look with **Base Color** (or its texture), **Roughness**, **Metallic** and
   **Normal**. For example, velvet or fabric: darker base color, roughness 0.8–1.0; varnished wood: roughness 0.2–0.3;
   brushed or polished metal: metallic 1 with roughness 0.2–0.5; glass: a low **Alpha** with the material's render
   method set to blended or dithered.
2. If you want the same simple look everywhere, set **Sheen**, **Coat** and **Transmission** weights to 0 and reset
   **Specular** and **IOR** (right-click › **Reset to Default Value**).
3. **File › Export › glTF 2.0**, format **glTF Binary (.glb)**, and upload it with **Versions › Replace the model file**.

*3ds Max, Maya, SketchUp or other tools:* standard PBR materials (base color, metallic, roughness, normal) look the
same in Android AR as on the website.

<div class="note" markdown="1">
A model processed before this change may still say Android AR is not available. Upload the file again
(**Versions › Replace the model file**) to get the simplified Android AR file.
</div>

### AR file is too large {#ar-over-budget}

<span class="kind kind-warning">Warning</span> <span class="code">AR_OVER_BUDGET</span>

**What it means.** For the material option named in the message, the Android AR file is above 15 MB, or the iPhone &
iPad AR file (USDZ) is above 25 MB. That AR isn't available for it; the website viewer still works.

**Why it happens.** AR files carry less compression than the website model, so large textures and dense meshes add up.

**How to fix it.** Reduce texture sizes (2,048 px or less, fewer textures) and the triangle count (see
[`OVER_BUDGET`](#over-budget)), then upload again.

### iOS AR file could not be created {#usdz-failed}

<span class="kind kind-warning">Warning</span> <span class="code">USDZ_FAILED</span>

**What it means.** The iPhone & iPad AR file (USDZ) couldn't be generated, or the USDZ you uploaded didn't pass the
checks, for the material option named in the message. The website viewer and Android AR still work.

**How to fix it.**

1. Upload again: a one-off problem goes away.
2. If it repeats, simplify the model (see [`OVER_BUDGET`](#over-budget)).
3. Or add your own USDZ on the model's **AR** tab ([how](/docs/ar/#own-usdz)).

**Contact support** if it keeps happening with a simple model.

### iOS AR is not available {#quick-look-unavailable}

<span class="kind kind-warning">Warning</span> <span class="code">QUICK_LOOK_UNAVAILABLE</span>

**What it means.** For the placement named in the message (floor or wall), there's no USDZ file you uploaded, and
**Create the iPhone & iPad file for me when I don’t add one** is off, so iPhone & iPad AR isn't available for that
placement. The website viewer and Android AR are not affected.

**How to fix it.** On the model's **AR** tab, check **Create the iPhone & iPad file for me when I don’t add one**, or
add your own USDZ for that placement, then click **Upload AR files**.

## Limits and "not processed" {#limits}

These messages are about your plan's limits, not about the file.

### Processing limit reached {#processing-allowance}

Titles: **Daily processing limit reached**, **Monthly processing limit reached**, **Daily limit for presentation
changes reached**, **Monthly limit for presentation changes reached**.

**What it means.** Your plan's allowance for processing new model files (or for saving starting view and lighting
changes) is used up for today or this month. The message says when it resets, in your time zone. Days and months
reset at midnight UTC.

**What to do.** The upload is kept and the model shows **Not processed**. When the allowance resets, open the model
and click **Process now**. The file is kept for 24 hours after the upload; if the allowance resets later than that,
upload the file again after the reset, or change your plan. See [processing allowances](/docs/plan-and-usage/#processing).

### Daily upload limit reached {#upload-allowance}

Titles: **Daily upload limit reached**, **File too large for your plan**.

**What it means.** Your plan allows a total amount of uploaded data per day (for example 5 GB on the beta plan). The
message shows how much you uploaded today and when it resets. **File too large for your plan** means one file is
bigger than the whole daily upload allowance.

**What to do.** Wait for the reset, upload a smaller file, or change your plan.

### Model limit reached {#model-limit}

**What it means.** Your plan includes a number of models and all of them are in use, so a new model can't be added.

**What to do.** Delete a model you no longer need, or change your plan. Replacing the file of an existing model
doesn't need a free slot.

### Several models are processing {#too-many-jobs}

**What it means.** Many uploads are waiting to be processed for your store at the same time.

**What to do.** Wait until one of them is ready, then try again.

### Processing did not start {#contended}

<a id="network"></a>A temporary problem stopped processing from starting (a busy moment or a lost connection).

**What to do.** Click **Process now** again in a moment.

## Which failed runs count {#allowance}

- A run that fails while the file is being **checked** (the first step) or **validated** is returned to your
  allowance.
- A run that fails later (conversion or optimization) is not returned, except [`OPTIMIZE_FAILED`](#optimize-failed),
  which is our problem: it's returned, up to 3 runs per store per day (UTC).
- A run replaced by a newer upload before it started is returned.
- Automatic retries on our side don't use extra allowance.

## When to contact support {#contact-support}

Email [contact@papathemes.com](mailto:contact@papathemes.com) when:

- the error is [`OPTIMIZE_FAILED`](#optimize-failed) and **Try again** fails again;
- the section above says to contact us;
- you followed the fix and the same error comes back;
- the file opens without errors in other glTF viewers but the app refuses it.

Include your store name, the model name, the error code, the file name, and the text under **Technical detail** (or
**Details for support**). If you can, attach the file or a download link. See [Support](/docs/support/).
