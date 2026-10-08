---
title: Plan and usage
description: The Product 3D & AR beta plan, its limits, what counts as a 3D view, data transfer, processing allowances, the notices and emails you get, and what happens when you reach a limit.
lead: The Plan & usage page shows your plan, this month's 3D views and data transfer, and what the app has processed for you.
---

<nav class="toc" aria-label="On this page" markdown="1">
<p class="toc-title">On this page</p>

* TOC
{:toc}
</nav>

## The beta plan {#beta-plan}

During the private beta, invited stores are on the **Free beta** plan: "Growth limits and features at no cost while
the beta lasts. We’ll email you before anything changes." A **Beta** label shows next to **Help** in the app.

| Limit | Free beta | Free |
|---|---|---|
| Models | 100 | 3 |
| 3D views per month | 50,000 | 1,000 |
| Data transfer per month | 400 GB | 8 GB |
| New model files processed per day / per month | 10 / 300 | 3 / 9 |
| Presentation changes processed per day / per month | 20 / 500 | 6 / 15 |
| Uploads per day | 5 GB | 0.5 GB |
| "Powered by Product 3D & AR" link in the viewer | no | yes |

3D in the gallery and AR are included in both. The **Free** plan applies to a store that is not in the beta.
Data sizes on this page are decimal: 1 GB = 1,000,000,000 bytes.

Paid plans are not available to buy during the beta. **Change plan** on Plan & usage (store owner only) opens an
email to us; staff see the button disabled ("Only the store owner can change the plan").

## What Plan & usage shows {#page}

- **Your plan**: the plan name, a status pill (**3D on**, **Over your limit — 3D still on**, or **3D off until
  {date}**) and three meters:
  - **Models**: models used and how many are left (or how many are hidden, with **Choose shown**);
  - **3D views**: this month's views, and where you'll likely end the month at the current pace;
  - **Data transfer**: this month's data, against your allowance.

  Meters turn orange at 80% and red at 100%, with the percentage written next to them.
- **3D views per day**: a chart of this month. Views from the last 48 hours are still being counted and show hatched;
  **Show as a table** lists the numbers with AR launches.
- **Processing allowances**: today's and this month's new model files, presentation changes, and today's uploads,
  each with the time it resets.
- **Top models**: your most viewed models this month.
- **Recent notices**: notices from the last 31 days, and whether they were emailed.
- **Email notifications**: who gets the emails ([below](#emails)).

## What counts as a 3D view {#what-counts}

A **3D view** is counted when a shopper's browser loads a model's 3D file for the website viewer, which happens when
the shopper opens 3D on a product page. Product pages where nobody opens 3D don't count.

- The same visitor viewing the same model again within the same 30-minute window counts once.
- Views served from the shopper's browser cache don't count.
- Search engine and bot traffic doesn't count.
- Previews inside the app don't count.
- **AR launches don't count toward your plan.** They're shown for information only.

**Data transfer** is the total size of all 3D files sent to shoppers: website models, AR files, preview images and
thumbnails. Lighter models use less of it ([size budgets](/docs/preparing-3d-files/#budgets)).

Months and days follow UTC: the monthly counters reset on the 1st at 00:00 UTC, the daily ones at 00:00 UTC. The app
shows reset times in your own time zone.

## Processing allowances {#processing}

Processing your files has its own allowances, separate from 3D views:

- **New model files**: each upload, replaced file, size or rotation change, and retry of a failed run.
- **Presentation changes**: saving a new starting view or lighting, or adding your own AR files.
- **Re-optimize** counts as a new model file when our processing has been updated since the model's last run, and
  as a presentation change otherwise.
- **Uploads**: the total size of files uploaded per day.

When one is used up, uploads still arrive but wait as **Not processed** until the allowance resets; then click
**Process now** on the model. Some failed runs are returned to your allowance: see
[Which failed runs count](/docs/processing-errors/#allowance).

## When you reach a limit {#limits-reached}

### 3D views {#views-limit}

- At **100%** of your monthly 3D views, 3D stays on: you get a 10% grace. Plan & usage shows "Over your limit — 3D
  still on" and **Needs your attention** on Overview shows "You’re over your 3D views".
- Above **110%**, 3D is turned off on your storefront until the next month (or until you change plan). Shoppers see
  your normal product images meanwhile, and the app shows "3D is turned off on your storefront".

### Data transfer {#data-limit}

- At **120%** of your monthly data transfer, 3D is turned off on your storefront until the next month (or until you
  change plan).

While 3D is off, your models, products and settings are all kept. 3D comes back by itself when the month resets.

### Models {#model-limit}

- When all your plan's models are in use, you can't add a new model ("Model limit reached"). Delete a model you no
  longer need, or change your plan.
- If you have more models than your plan includes (for example after a plan change), the most recently published
  models stay shown, up to the limit. The others show **Hidden (plan limit)**: they are kept, not deleted, just not
  shown to shoppers. Use **Choose shown models** on **Models** to pick which ones are shown.

### Processing allowances {#processing-limit}

Uploads wait as **Not processed** until the allowance resets: see [Processing allowances](#processing).

## Notices and emails {#emails}

The app emails the store owner, and shows a notice in the app, when you get close to or reach a limit:

| What | Emails at |
|---|---|
| 3D views this month | 50%, 80%, 95%, 100% (grace starts), above 110% (3D turned off) |
| Data transfer this month | 50%, 80%, 95%, 100%, 120% (3D turned off) |
| Models | 80%, 100% |
| New model files / presentation changes this month | 80%, 100% |
| Daily processing or upload allowance | 100% |

You also get an email when, at the pace of the last 7 days, you're on track to go over your monthly 3D views, when
models are hidden by the plan limit, and when a product's 3D is turned off because its rules no longer match the
catalog. Each notice is sent once per month (or per day for daily allowances).

**Email notifications** card (on Plan & usage):

- **Store owner**: the owner's email from BigCommerce always receives the emails.
- **Also send to (optional)**: up to 3 more addresses (**Add another address**).
- **Remind me at 50% and 80% of a limit**: untick to stop the 50% and 80% reminder emails. The others are always sent.
- Click **Save**. Only the store owner can change these; staff see them read-only.

## If you uninstall the app {#uninstall}

Your models and settings are kept for 30 days after you uninstall. Reinstall before then to continue where you left
off; after that they are deleted. You get an email when you uninstall and a reminder before the deletion. If you added
the [snippet by hand](/docs/storefronts/#manual-snippet) on any storefront, remove it from Script Manager.
