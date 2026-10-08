---
title: FAQ
description: Short answers to common questions about Product 3D & AR.
---

<nav class="toc" aria-label="On this page" markdown="1">
<p class="toc-title">On this page</p>

* TOC
{:toc}
</nav>

## Setup {#setup}

### Do I need to edit my theme? {#theme-edits}

No, not on most Stencil themes. **Turn on 3D** adds the app's script for you and picks the layout for your theme. From
the 11th storefront on, you paste one snippet in Script Manager ([how](/docs/storefronts/#manual-snippet)).

### Which themes are supported? {#themes}

Stencil themes. On Cornerstone-based themes and PapaThemes themes with the app's gallery hooks, 3D appears inside the
image gallery. On other themes the app uses a **View in 3D** button that opens a pop-up, or you can set
[custom selectors](/docs/storefronts/#custom-selectors). Catalyst (headless) support is coming soon.

### Does the app slow down my product pages? {#speed}

The 3D model only loads when a shopper opens 3D. Until then the page shows your normal images. Keep models light
(3 MB or less is the target) so they open quickly on phones.

### I hid the setup guide. How do I get it back? {#setup-guide}

Click **Help**, then **Show the setup guide**. See [The setup guide](/docs/getting-started/#hide-setup-guide).

## Models {#models}

### What's the best file format? {#best-format}

GLB. glTF and OBJ work when zipped with their textures, and FBX and STL also work.
See [Preparing 3D files](/docs/preparing-3d-files/#formats).

### I don't have a 3D file. What can I do? {#no-3d-file}

Ask the manufacturer or designer of the product for a GLB or glTF file, or have one made by a 3D artist or a 3D
scanning service. The app doesn't create 3D models from photos.

### How long does processing take? {#processing-time}

Usually under 2 minutes. You can leave the page while it runs.

### Can I replace a model's file without changing my products? {#replace-file}

Yes. Open the model, **Versions › Replace the model file** (or **⋯ › Replace file**). Products keep showing the
current version until the new one is ready, then switch to it.

### My model is the wrong size in AR. {#wrong-size}

Open the model, **Presentation › Size and orientation**, change **Size (%)**, and save. See
[Scale, units and orientation](/docs/preparing-3d-files/#scale).

### Does the app reduce the number of polygons? {#decimation}

No. It compresses the model and shrinks textures larger than 2,048 px, but it doesn't remove polygons. Reduce them in
your 3D software if the model is heavy ([budgets](/docs/preparing-3d-files/#budgets)).

### Are animations supported? {#animations}

No, the app shows still models. Animation is removed ([details](/docs/processing-errors/#animation-stripped)).

### Why can't I delete a model? {#delete-model}

A model that is live on products can't be deleted. Choose another model for those products, or turn off their 3D,
then delete it.

## Products {#products}

### Can each color have its own model? {#per-color}

Yes, with [variant rules](/docs/products-and-variants/#variant-rules). If one file holds all colors as material
options, use one model and pick a material per rule.

### Can I hide 3D for some variants? {#hide-variant}

Yes: a rule that shows **Hide 3D** ([details](/docs/products-and-variants/#hide-3d)).

### Can I give many products the same model at once? {#bulk}

Yes: on **Products**, select up to 50 products and click **Set 3D model…**
([details](/docs/products-and-variants/#bulk)).

### I published but don't see 3D on the storefront. {#not-showing}

Wait a minute or two, then see [3D doesn't show on my storefront](/docs/storefronts/#troubleshooting).

### Why did 3D turn off for a product by itself? {#auto-off}

An option, value or variant that a rule uses was deleted in BigCommerce. To avoid showing the wrong model, the app
turned 3D off for that product. Fix the rule and publish again
([details](/docs/products-and-variants/#catalog-changes)).

## AR {#ar}

### Which devices support AR? {#ar-devices}

iPhone and iPad (AR Quick Look) and Android phones that support Google's AR services. On a computer, shoppers get a QR
code to open the product on their phone. See [AR](/docs/ar/).

### AR works on iPhone but not on Android. {#android-only}

The model probably uses material features Android AR doesn't support. See
[Android AR: unsupported material extensions](/docs/processing-errors/#android-ar-unsupported-extensions).

### Can I use my own USDZ file? {#own-usdz}

Yes, for iPhone and iPad ([how](/docs/ar/#own-usdz)).

## Plan and billing {#plan}

### How much does it cost? {#cost}

The private beta is free. We'll email beta stores before anything changes. See [Plan and usage](/docs/plan-and-usage/).

### Do AR launches count toward my plan? {#ar-count}

No. Only 3D views count ([what counts](/docs/plan-and-usage/#what-counts)).

### What happens if I go over my 3D views? {#over-views}

3D stays on up to 110% of your monthly views. Above that, 3D turns off until the next month, and shoppers see your
normal images ([details](/docs/plan-and-usage/#limits-reached)).

### What happens to my models if I uninstall? {#uninstall}

They're kept for 30 days, then deleted. Reinstall within 30 days to continue where you left off.

## Access {#access}

### The app says my session expired. {#session-expired}

In the BigCommerce control panel, go to **Apps › My Apps** and open Product 3D & AR again. Product changes you
hadn't saved are kept in that browser tab and come back when you return.

### Can my staff use the app? {#staff}

Yes. Only the store owner can change the plan and the notification emails.
