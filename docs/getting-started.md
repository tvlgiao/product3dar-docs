---
title: Getting started
description: Install Product 3D & AR, turn on 3D for a storefront, upload your first model, add it to a product and see it on your storefront.
lead: From install to a product page with 3D and AR, in about 5 minutes.
---

<nav class="toc" aria-label="On this page" markdown="1">
<p class="toc-title">On this page</p>

* TOC
{:toc}
</nav>

## Install the app {#install}

1. Find **Product 3D & AR** in the BigCommerce App Marketplace and install it while you're signed in to your store,
   then approve the app's access.
2. The app opens inside your control panel. Later, open it from **Apps › My Apps › Product 3D & AR**.

The app only works inside the BigCommerce control panel. If you open its address in a separate tab, it asks you to
go back to **Apps › My Apps** and open it there.

Store staff can use the app too. A few things are for the store owner only: choosing or cancelling a plan, editing the
billing details and changing the notification emails.

Every store starts on the Free plan. See [Plan and usage](/docs/plan-and-usage/#plans) for the paid plans.

## The quick start {#setup-guide}

The first time you open the app, **Overview** shows the quick start: a card called **Set up 3D on your store** with
four steps, a count of the steps done (**0/4**) and the next step to do ("Next: Show 3D on your storefront · ~5 min").
A bar of four segments shows your progress; click a segment or a step's title to open that step. Each step ticks
itself off when the app sees it done, so you don't need to mark anything. When a step is done, the step shows
"Done. Next: {step}" and a **Continue** button that opens the next one.

Below the guide, **What shoppers get** sums up the features and **Need a hand?** links to this guide
(**Read the guide**) and to email support (**Contact support**).

### Hide or bring back the quick start {#hide-setup-guide}

- To hide it, open the **⋯** menu on the guide and choose **Hide quick start**. The same menu can also offer **Show me
  around**, a short tour of the page.
- To bring it back, click **Quick start** at the top of the Overview, next to **Upload model**. You can also click
  **Help** (top right of the app), then **Show the setup guide** in the **Setup guide** card.

When all four steps are done, Overview starts showing your 3D views and anything that needs attention. If you bring
the guide back with **Quick start** after that, it shows **Setup complete** with **Show tour again** and **Hide quick
start**.

## Step 1: Show 3D on your storefront {#step-1}

Step 1 lists your storefronts (BigCommerce channels). Next to a storefront, click **Show 3D**, then confirm
**Show 3D** in the dialog (it lists what changes and how many products in your store have 3D).

- The app adds its storefront script for you and picks the layout that fits your theme. You don't edit your theme.
- 3D appears **in the image gallery** by default: shoppers open it from an extra thumbnail next to your photos.
- Your storefront updates within a few minutes.

The step is done as soon as one Stencil storefront has 3D on. Headless (Catalyst) storefronts aren't supported yet:
the step says "Headless storefronts are coming soon".
To change where 3D appears, the button labels or the theme fit, see [Storefronts](/docs/storefronts/).

## Step 2: Upload your first 3D model {#step-2}

1. Click **Upload model**. The **Upload a 3D model** window opens.
2. Drag your file onto it, or click **Choose file**. The app checks the file type and size right away.
3. Check the **Name**. It's filled in from the file name; only you see it.
4. Click **Upload**.

<div class="tip" markdown="1">
**Which file?** GLB works best. glTF and OBJ work when zipped together with their textures; FBX and STL also work.
Single files can be up to 100 MB, zip files up to 200 MB. See [Preparing 3D files](/docs/preparing-3d-files/).
No 3D file yet? The same page explains where to get one.
</div>

**No file at hand?** Click **Try a sample model** next to **Upload model**, pick one of the sample models (CC0, from
Poly Haven) and click **Add to my models**. It processes like an upload and uses one of your plan's model slots, but
not your processing allowance. Delete it later to free the slot.

You can also try a real upload with a sample: under **No file? Try a sample** in the **Upload a 3D model** window,
click a sample to download its file, then upload that file.

While the file uploads you can close the window: the upload keeps going while you use other pages, and processing
starts when it arrives. Processing usually takes under 2 minutes. The model page shows each stage: **File received**,
**File checked**, **Optimizing for the website**, **Creating AR files for phones**, **Ready to use**.

When the model is **Ready**, step 2 is done. If the app reports a problem with the file, it shows what's wrong and a
**How to fix this** link to [Processing errors and warnings](/docs/processing-errors/).

## Step 3: Add the model to a product {#step-3}

1. In step 3, search for a product by name or SKU.
2. Click **Add 3D** next to the product. With one ready model, the app adds that model; with several, it asks which
   one. The product is published with 3D and shows **Live**; it reaches your storefront in about a
   minute.
3. Next to a live product, **View live** opens its page on your storefront, and the undo button (**Undo: remove 3D
   from {product}**) takes the 3D off again.

Step 3 is done when at least one product shows 3D. **Add 3D** appears once your model is ready.

To add [variant rules](/docs/products-and-variants/#variant-rules) or check what shoppers will get before publishing,
open the product from **Products** instead. More in [Products and variants](/docs/products-and-variants/).

## Step 4: See it on your storefront {#step-4}

- **Open my storefront** opens the product page in a new tab, with `?p3d-debug=1` added to the address. That shows a
  small overlay with what the app detected on the page (see
  [Installation check](/docs/storefronts/#installation-check)).
- **Show QR code** shows a QR code. Scan it with your phone's camera to open the product page on the phone and try
  **View in AR** there.

On the product page, open 3D from the 3D thumbnail (or the **View in 3D** button), drag to turn the model and scroll
or pinch to zoom. On a computer, **View in your space** shows a QR code that opens the page on a phone for AR.

Step 4 is done once you've opened the storefront or the QR code from the guide, or once 3D first opens on your
storefront.

If 3D doesn't appear, see [3D doesn't show on my storefront](/docs/storefronts/#troubleshooting).

## What's next {#next}

- Show a different model or material per color or size: [Variant rules](/docs/products-and-variants/#variant-rules).
- Give many products the same model at once: [Set 3D model for many products](/docs/products-and-variants/#bulk).
- Change the starting view, lighting or real-world size of a model: [Model settings](/docs/preparing-3d-files/#model-settings).
- Learn what counts toward your plan: [Plan and usage](/docs/plan-and-usage/).
