---
title: Storefronts
description: Turn 3D on per storefront, choose where 3D appears, how it fits your theme and the button labels, check the installation, and fix 3D that doesn't show.
lead: Each BigCommerce storefront (channel) has its own 3D settings. Changes reach your storefront within a few minutes.
---

<nav class="toc" aria-label="On this page" markdown="1">
<p class="toc-title">On this page</p>

* TOC
{:toc}
</nav>

## Your storefronts {#list}

**Storefronts** shows one card per storefront channel of your BigCommerce store, with one status:

| Status | Meaning |
|---|---|
| **3D on** | Products you publish with 3D show it on this storefront. |
| **Off** | 3D is not shown on this storefront (it was never turned on, or you turned it off). |
| **Not installed** | 3D is on, but the app couldn't find its snippet on this storefront yet ([see below](#manual-snippet)). |
| **Coming soon** | A headless storefront ([Catalyst](#catalyst)). |

Under the name you see the platform ("Stencil · {theme} theme"). For a storefront with 3D on, the card also shows
**Shows 3D** (where it appears), **Fits your theme** (for example **Automatically**), **Script** (**Added for you** or
**Added by hand**) and **Storefront** (**Up to date**, or **Updating…** while your latest change is on its way).
Its buttons are **Test on storefront** and **Settings**.

## Turn on 3D {#turn-on}

On a storefront that is **Off**, click **Turn on 3D**. The app uses the recommended settings: 3D in the image gallery,
the layout picked for your theme, and its storefront script added for you. You'll see "Saved. {storefront} updates
within a few minutes."

3D only appears on products you have [published with 3D](/docs/products-and-variants/#publish). Product pages
without 3D are left as they are.

## Settings {#settings}

Click **Settings** on a storefront card to open its settings panel. Click **Save** to apply, or **Cancel**.

### Show 3D on this storefront {#turn-off}

Switch it off to hide 3D everywhere on that storefront. Product settings are kept, so switching it back on restores
everything. After saving, the message "3D is off on {storefront}." offers **Undo**.

### Where 3D appears {#where-3d-appears}

| Choice | What shoppers see |
|---|---|
| **In the image gallery** (default) | Shoppers open 3D from an extra thumbnail next to your photos. The 3D view opens in the main image area, and shoppers go back with **Back to photos**. |
| **Instead of the main image** | 3D takes the place of the main product image. |
| **In a pop-up** | A **View in 3D** button opens 3D in a pop-up window. Works with any theme. |

In every mode, the product page first loads with your normal images. The 3D model only loads when a shopper opens
it, so pages stay fast and only real 3D views [count toward your plan](/docs/plan-and-usage/#what-counts).

### How 3D fits your theme {#theme-fit}

| Choice | When to use it |
|---|---|
| **Automatic (recommended)** | Most stores. The app looks for a supported gallery on the product page: a PapaThemes theme's 3D gallery hooks first, then the Cornerstone gallery. If it finds neither, it falls back to a **View in 3D** button under the add-to-cart form that opens 3D in a pop-up. |
| **Cornerstone theme** | Cornerstone and themes built on its product gallery. The 3D thumbnail is added to the thumbnail strip. |
| **PapaThemes theme** | PapaThemes themes with the app's gallery hooks. The 3D thumbnail goes into a slot the theme reserves. |
| **Custom selectors (advanced)** | A custom theme the automatic choice doesn't recognize. See [custom selectors](#custom-selectors). |
| **Pop-up (works with any theme)** | Always use the button under the add-to-cart form and the pop-up. |

When a theme is set up, the panel shows the automatic choice as "Automatic (recommended for {theme})".

### Button labels {#button-labels}

Change the words on the storefront buttons, or leave a field empty to use the default:

- **3D button**: the label of the button that opens 3D (default **View in 3D**).
- **AR button**: the label of the AR button on phones and tablets (default **View in AR**).

On a computer, the AR button that shows the QR code reads **View in your space**.

### Installation {#installation}

- **The script was added for you.** For up to 10 storefronts, the app adds its storefront script through BigCommerce
  itself. Nothing to do. The **Check it** link opens your storefront with the [installation check](#installation-check).
- **Add the snippet by hand** (from the 11th storefront on), see [below](#manual-snippet).

## Add the snippet by hand {#manual-snippet}

BigCommerce lets an app add its script to 10 storefronts. For the 11th storefront and beyond, the panel shows a
snippet instead:

1. Click **Copy** next to the snippet.
2. In BigCommerce, open **Storefront › Script Manager** for that storefront and create a script: placement
   **Footer**, location **All pages**, and paste the snippet.
3. Back in the app, click **Check installation**. It shows "Found · {time}" when the snippet is on the storefront, or
   "Not found yet · checked {time}". Until it's found, the card shows **Not installed**.

If you uninstall the app later, remove this snippet from Script Manager.

## Custom selectors {#custom-selectors}

Use custom selectors only if your theme isn't recognized automatically and you want 3D on the main image instead of
the pop-up button.

1. In **Settings**, open **Advanced: custom selectors** (or choose **Custom selectors (advanced)** under **How 3D fits
   your theme**).
2. Enter the **Main image selector** and the **Thumbnail list selector**: CSS selectors for your theme's main product
   image container and its thumbnail list. Each must match exactly one element on the product page.
3. Click **Save**.
4. Open a product page with 3D and add `?p3d-debug=1` to its address (see [Installation check](#installation-check)).
   With custom selectors, the overlay shows a checklist. Check on the page that:
   - zoom does not open when you drag the 3D model;
   - the lightbox does not open on click;
   - swiping the gallery does not move the 3D model.
5. Back in the panel, under **Check the custom selectors**, click **I checked the overlay: the 3D model shows in the
   gallery**. It then shows **Confirmed**. Changing the selectors later needs a new check.

With custom selectors, a 3D badge appears on the main image and 3D opens in a pop-up. If a selector matches nothing
(or more than one element), the app falls back to the pop-up button. If you're not sure which selectors to use,
[contact us](/docs/support/).

## Installation check (?p3d-debug=1) {#installation-check}

Open a product page that has a published 3D model and add `?p3d-debug=1` to its address, for example
`https://your-store.com/oak-chair/?p3d-debug=1` (use `&p3d-debug=1` if the address already has a `?`). A small dark
overlay appears in the bottom-right corner with what the app detected:

- the first line, **Product 3D & AR**, shows `mounted` when 3D is set up on the page, or `no-op` with a reason;
- **adapter**: how the app fitted your theme (`cornerstone`, `papathemes`, `generic-selectors` or `modal`);
- **selection** and **appearance**: the options chosen and the model shown;
- **AR**: which AR this device gets (`quick-look`, `scene-viewer`, `webxr`, `qr` or `-`).

**Open my storefront** in the setup guide and **Check it** in Settings open your storefront with this check already
added. The overlay is only shown to whoever opens the page with `?p3d-debug=1`; shoppers never see it.

Common reasons after `no-op`:

| Reason | What it usually means |
|---|---|
| `disabled` | 3D is off for this storefront. |
| `entitlement` | 3D is paused by your plan's limits ([Plan and usage](/docs/plan-and-usage/#limits-reached)). |
| `not-pdp` | The page isn't a product page. |
| `bloom-negative`, `manifest-404` | This product has no published 3D on this storefront (or the storefront hasn't picked it up yet). |
| `manifest-disabled` | 3D is turned off for this product. |
| `no-gallery` | The app couldn't find this product's add-to-cart form on the page. |

## Catalyst (headless) {#catalyst}

Support for Catalyst (headless) storefronts is coming soon: a React package for Catalyst is on the way. Headless
storefronts appear in the list as **Coming soon**, and we'll email you when the package is ready.

## 3D doesn't show on my storefront {#troubleshooting}

Check these in order:

1. **The storefront shows 3D.** On **Storefronts**, the card says **3D on** and **Storefront: Up to date**. Changes
   take a few minutes to reach the storefront.
2. **The product is live.** On the product page in the app, the pill says **Live** (not **Draft**, **Published** or
   **3D off**). See [Products and variants](/docs/products-and-variants/#publish).
3. **The variant isn't hidden.** A rule with **Hide 3D** removes 3D for that variant. Choose other options on the
   product page, or check **What shoppers will see** in the app.
4. **The model is shown.** On **Models**, the model is **Ready**, not **Hidden (plan limit)**.
5. **Your plan hasn't paused 3D.** If the app shows "3D is turned off on your storefront", shoppers see your normal
   images until the limit resets or you change plan ([details](/docs/plan-and-usage/#limits-reached)).
6. **Reload without cache.** Your browser may show an older copy of the page: reload with
   <kbd>Shift</kbd> + reload, or try a private window.
7. **Run the installation check.** Add `?p3d-debug=1` to the product page address and read the reason in the overlay
   ([table above](#installation-check)).
8. **Storefront 11 and beyond:** add the snippet by hand and click **Check installation** ([steps](#manual-snippet)).
9. **3D appears as a button, not in the gallery.** Your theme wasn't recognized, so the app used the pop-up. Try
   **Custom selectors** or contact us.
10. **Headless storefront:** not supported yet ([Catalyst](#catalyst)).

Still not showing? Email [contact@papathemes.com](mailto:contact@papathemes.com) with the product page address and
a screenshot of the `?p3d-debug=1` overlay. See [Support](/docs/support/).
