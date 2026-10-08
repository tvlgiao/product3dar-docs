---
title: Products and variants
description: Give a product a 3D model, show different models or materials per variant with rules, review and publish, restore an earlier version, turn 3D off, and set one model for many products.
lead: Each product has a default model, optional variant rules, and display and AR settings. Nothing reaches shoppers until you publish.
---

<nav class="toc" aria-label="On this page" markdown="1">
<p class="toc-title">On this page</p>

* TOC
{:toc}
</nav>

## Open a product {#open-a-product}

- In the app, go to **Products**, search by name or SKU, and click the product. The filters **With 3D**, **Without 3D**
  and **Needs attention** narrow the list.
- Or, in your BigCommerce control panel, go to **Products**, open a product's **⋯** menu and choose **3D & AR**.

The product page has the cards **3D model**, **Variant rules**, **Display and AR**, **What shoppers will see** and
**Version history**. Its status pill reads **No 3D**, **Draft**, **Published** (the storefront is updating),
**Live**, or **3D off**.

## Default model {#default-model}

In the **3D model** card, choose a model under **Choose a model** (or **Upload a new model**). The default model is
shown for every variant unless a rule says otherwise. Only models that are **Ready** can be chosen; others show "Not
ready yet".

If the model has [material options](/docs/preparing-3d-files/#materials), a **Material** field appears: keep
**Default material** or pick one. To change the model later, click **Change**.

## Variant rules {#variant-rules}

Variant rules show a different model, a different material, or no 3D for some variants. Each rule reads as a
sentence:

> When **[option]** is **[value]** show **[model or Hide 3D]**

1. Click **Add rule**.
2. Choose the option (for example **Color**) and its value (for example **Blue**).
3. Choose what to show: another model, the same model with another **Material**, or **Hide 3D**.
4. To match more than one option, click **And…** and add another condition (for example Color is Blue **and** Size is
   Large). To remove a condition, use its **×** button.
5. To match one exact variant, choose **A variant (SKU)** as the option, then pick the variant by SKU.

Variants that no rule matches show the default model (the card says so under the rules).
Products without options show "This product has no options, so every shopper sees the same model."

### Which rule wins {#rule-precedence}

When more than one rule matches the variant a shopper chose:

1. **A rule for one variant (SKU) wins.**
2. Otherwise, **the rule with the most conditions** wins (Color is Blue and Size is Large beats Color is Blue).
3. **Between equal rules, the first one** (highest in the list) wins.

Use the **Move rule up** and **Move rule down** buttons to change the order, and **Remove rule** to delete one (the
message that confirms it offers **Undo**).

<div class="note" markdown="1">
Until a shopper has chosen a value for every option, the 3D view shows the default model and the AR button stays
off. Once all options are chosen, the matching rule applies. Modifier options (such as text engraving) are not used by
rules; only the options that make up variants are.
</div>

### Hide 3D for a variant {#hide-3d}

Choose **Hide 3D** in a rule's "show" field. Shoppers who choose that variant see your product images only, with no 3D
thumbnail or AR button.

### Materials per rule {#materials-per-rule}

If the chosen model has material options, a material field appears next to it in the rule. Use one model with several
materials (for example fabric colors) and one rule per color, instead of uploading one model per color.

### Limits {#rule-limits}

- Up to 200 rules per product.
- Up to 10 different models per product.
- Products with more than 600 variants are not supported.

### When the catalog changes {#catalog-changes}

If you delete an option, an option value or a variant in BigCommerce that a rule uses, the rule shows an error such
as "The option value “Blue” was deleted from this product in BigCommerce. Choose another value or remove the rule."
To avoid showing the wrong model, the app turns 3D off for that product, marks it **3D off**, lists it under
**Needs attention** and emails you. Fix or remove the rule (the message has a **Go to rule** button), then publish
again.

## Display and AR {#display-and-ar}

- **Show 3D on this product**: turn it on to review and publish; turn it off to [turn off 3D](#turn-off-3d).
- **Let shoppers view it in their space (AR)**: shows the AR button on phones and the QR code on computers.
- **AR placement**: **On the floor** or **On a wall**.
- **Size in AR**: **Real size** (shoppers can't resize it) or **Let shoppers resize**.

More in [AR (view in your space)](/docs/ar/#placement-and-size).

## What shoppers will see {#what-shoppers-will-see}

This card previews the saved draft: choose option values and the preview shows the model (and material) shoppers will
get for that variant, with pills for **Website 3D**, **iPhone & iPad AR**, **Android AR** and **Computer: QR code**.
A variant with no 3D says "No 3D for this variant: shoppers see your product images."

## Save draft, Review and publish {#publish}

Any change shows a bar at the bottom of the page: "Unsaved changes", with **Discard**, **Save draft** and
**Review and publish**. While you edit, the live version stays live.

- **Save draft** keeps your changes without publishing. Other people with access to the app see the draft too. If you
  leave the page with unsaved changes, the app asks first ("Leave without saving?"). If the page reloads or your
  session expires, unsaved changes are kept in that browser tab and offered back ("You have unsaved changes from …")
  when you return.
- **Review and publish** opens a window: "This is exactly what shoppers will get. Choose options to check each
  variant." For each value it shows which model shoppers see, whether a rule or the default model matched, and the AR
  for that variant. Click **Publish** (or **Back to editing**).
- **Preview** (at the top of the page) opens the same window read-only.

After publishing you see "Published version {n}. Live on {storefront} in about a minute." The pill shows
**Published** until the storefront has the new version, then **Live**. If no storefront shows 3D yet, the page tells
you, with **Go to Storefronts**.

If someone else saved a draft of the same product while you were editing, a window "This product changed while you
were editing" lets you **Load their version** (discarding yours) or **Keep mine** (replacing theirs).

## Version history and Restore {#version-history}

Every publish creates a version. The **Version history** card lists them, newest first, with who published and when
(for example "Published Oct 7, 10:14 AM by …"); the current one is marked **Live**. Other entries include
**Restored**, **Updated to the new model version** (a model's file was replaced), **Updated after a catalog change**,
**Published with bulk assign** and **3D turned off**. Use **Show older versions** for more.

To go back to an earlier version:

1. Click **Restore** next to it.
2. Confirm: "Restore version 1? It becomes version 3 and goes live." The old settings are published again as a new
   version.

About your draft when you restore:

- If your draft had **no edits of its own** (it was the same as what was live), it follows the restore, so the editor
  shows what is now live.
- If your draft **had unpublished edits**, they are kept as they are.

A version can't be restored if a model file it used no longer exists ("A model file of that version no longer exists,
so it can’t be restored.").

## Turn off 3D {#turn-off-3d}

Open the product's **⋯** menu and choose **Turn off 3D** (or switch off **Show 3D on this product**). Confirm in the
window "Turn off 3D for {product}?". Shoppers then see only your product images. Your model, rules and version history
are kept, so you can publish again any time.

To turn 3D off for a whole storefront instead, see [Storefronts](/docs/storefronts/#turn-off).

## Set 3D model for many products {#bulk}

From **Products**:

1. Tick the products (up to 50 at a time; the selection is kept when you change pages).
2. In the bar that appears ("{n} selected"), click **Set 3D model…**.
3. Choose a **Model** (only ready models can be chosen) and, if it has material options, a **Material**.
4. Click **Set model and publish**.

Each product gets this model as its **default** and is **published right away**. Its variant rules and display
settings stay as they are. The window shows the progress ("Publishing · {done} of {n} done") and a result per product:

- **Published**;
- **Skipped**: "Someone edited this product after you started, so we left it as it was." Open it to check;
- **Failed**: for example "This product was deleted from your catalog."

You can close the window while it runs; only one bulk assignment runs at a time.

From a model: on the model page, **Assign to products** opens the same window with that model already chosen; search
for the products to add.

The same bar has **Turn off 3D**, which turns 3D off for the selected products after you confirm.
