---
title: Plan and usage
description: Product 3D & AR plans and prices, choosing and changing a plan with PayPal, cancelling, invoices and receipts, what counts as a 3D view, data transfer, processing allowances, the notices and emails you get, and what happens when you reach a limit.
lead: The Plan & usage page shows your plan, this month's 3D views and data transfer, what the app has processed for you, and your invoices.
---

<nav class="toc" aria-label="On this page" markdown="1">
<p class="toc-title">On this page</p>

* TOC
{:toc}
</nav>

## Plans {#plans}

Every store starts on **Free**. Paid plans are billed monthly or yearly through PayPal, at the list price.

| | Free | Starter | Growth | Pro |
|---|---|---|---|---|
| Price, billed monthly | $0 | $29 a month | $79 a month | $199 a month |
| Price, billed yearly | — | $24.65 a month ($295.80 a year) | $67.15 a month ($805.80 a year) | $169.15 a month ($2,029.80 a year) |
| Models | 3 | 25 | 100 | 500 |
| 3D views per month | 1,000 | 10,000 | 50,000 | 200,000 |
| Data transfer per month | 8 GB | 80 GB | 400 GB | 1,600 GB |
| New model files processed per day / per month | 3 / 9 | 5 / 75 | 10 / 300 | 25 / 1,500 |
| Presentation changes processed per day / per month | 6 / 15 | 10 / 125 | 20 / 500 | 50 / 2,500 |
| Uploads per day | 0.5 GB | 2 GB | 5 GB | 20 GB |
| "Powered by Product 3D & AR" link in the viewer | yes | no | no | no |
| Catalyst storefronts | — | — | coming soon | coming soon |

3D in the gallery and AR are included in every plan. Yearly billing costs 15% less than 12 monthly payments; the
limits stay monthly (for example 10,000 3D views each month on Starter yearly). Catalyst (headless) storefronts are
not supported yet on any plan ([Catalyst](/docs/storefronts/#catalyst)).
Data sizes on this page are decimal: 1 GB = 1,000,000,000 bytes.

## Choose or change your plan {#change-plan}

Only the store owner can choose a plan. Staff see **Change plan** disabled ("Only the store owner can change the
plan").

1. On **Plan & usage**, click **Change plan**. You can also click **Upgrade** at the top of the app, next to **Help**.
   (**Upgrade** isn't shown on Pro billed yearly, or while a plan change is still in progress.)
2. Choose **Monthly** or **Yearly · save 15%**. If you're on Free, the window opens on **Yearly** with **Starter**
   chosen and marked **Recommended**.
   - A yearly plan shows its price as a month's share, for example **$24.65 a month**, with the monthly price crossed
     out, "$295.80 billed yearly", **Save 15%** and how much you save a year.
3. Choose a plan. The terms appear under the plans, for example "Starter starts as soon as PayPal confirms your first
   payment of $295.80. Renews yearly at the list price. No refunds when you cancel, uninstall or change plans."
4. Tick **I agree to the no-refund terms** (it's required), then click **Continue to PayPal**.
5. Approve the subscription in the PayPal window.

Your new plan starts as soon as PayPal confirms your first payment. Plan & usage then shows "Payment received —
{plan} is active". While you wait:

- If the PayPal window was blocked or closed, click **Open PayPal** to open it again.
- After 10 minutes the app shows **Still waiting for PayPal**; click **Check again**.
- If you don't approve in time, the app shows **Approval expired**. Nothing was charged; choose a plan again.

The plan card then shows "Paid until {date}" and "Next charge: {amount} on {date}". Your plan renews monthly or yearly
at the list price until you cancel.

### Upgrades and other changes {#plan-changes}

When you already have a paid plan, each plan in **Change plan** says what choosing it does:

- **Upgrade now** (a higher plan): the new plan starts right away. The unused value of your current plan is
  converted into time on the new plan, and the window tells you until when ("Your unused Starter value covers Growth
  until {date}, then {price} monthly at the list price."). The switch time is rounded down by at most 2 hours.
- **Switch on {date}** (a lower plan, or the same plan billed monthly instead of yearly or the other way round): your
  current plan stays until the end of the period you paid for, and the new one starts then, with its first charge
  that day.

A plan change isn't possible in the last 24 hours before a renewal: the plan shows "Plan change available after
renewal on {date}". An upgrade also needs enough paid time left to convert; otherwise it shows "Upgrade available
after your renewal on {date}". Changes aren't refunded.

### Cancel your subscription {#cancel}

The store owner can click **Cancel subscription** on the plan card, then **Cancel subscription** again to confirm
(or **Keep subscription**). You keep your plan until the end of the period you paid for; the card then says "No
renewal — you move to Free on {date}". After that date your store is on Free and its limits apply: models above
Free's 3 are [hidden, not deleted](#model-limit). Payments are not refunded.

### If a renewal payment fails {#failed-payment}

If PayPal can't collect a renewal, your plan stays active for 7 more days while PayPal retries. You get an email
straight away and reminders 3 days and 1 day before the end. Update your payment method in PayPal, or subscribe
again, before then. If the payment still hasn't gone through, the subscription is cancelled and your store moves to
Free.

## Invoices and receipts {#invoices}

The **Invoices & receipts** card on Plan & usage lists each payment, newest first: **Date**, **Plan**, **Amount**,
**Status** (for example **Paid**) and **Receipt**. Click **View** to open the invoice in a new tab, or **Download**
to save it. Invoices are numbered (P3D-000001, P3D-000002, …) and show who is billed, the plan at its list price
with its service period, and the PayPal payment. To keep a PDF, print the invoice and choose **Save as PDF**.

PayPal also emails you its own receipt for each payment.

### Billing details {#billing-details}

The **Billing details** card holds what your invoices print under "Bill to". It's filled in from your BigCommerce
store profile. The store owner can click **Edit** to change the company or legal name, the address, a
**Tax or VAT ID** (optional), the **Billing email**, the store name and the store URL, then click **Save**. Staff see the details read-only. Each invoice keeps the details it was issued with; a change applies
to later invoices.

## What Plan & usage shows {#page}

- **Your plan**: the plan name, its models and 3D views a month, a status pill (**3D on**, **Over your limit — 3D still on**, or **3D off until
  {date}**) and three meters:
  - **Models**: models used and how many are left (or how many are hidden, with **Choose shown**);
  - **3D views**: this month's views, and where you'll likely end the month at the current pace;
  - **Data transfer**: this month's data, against your allowance.

  Meters turn orange at 80% and red at 100%, with the percentage written next to them. On a paid plan the card also
  shows until when it's paid and the next charge, and the owner sees **Cancel subscription**.
- **3D views per day**: a chart of this month. Views from the last 48 hours are still being counted and show hatched;
  **Show as a table** lists the numbers with AR launches.
- **Processing allowances**: today's and this month's new model files, presentation changes, and today's uploads,
  each with the time it resets.
- **Top models**: your most viewed models this month.
- **Recent notices**: notices from the last 31 days, and whether they were emailed.
- **Invoices & receipts** and **Billing details** ([above](#invoices)), once you have a paid plan.
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

The app emails you, and shows a notice in the app, when you get close to or reach a limit:

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

Billing emails go to the same addresses:

- a receipt for each payment, with a link to your invoices (Recent notices shows **Payment received**);
- a reminder to approve a subscription that is waiting in PayPal (**Approve your plan in PayPal**);
- a confirmation when an upgrade starts or a plan change is scheduled;
- a confirmation when you cancel, with the date you move to Free (**Subscription cancelled**);
- when PayPal can't collect a renewal, with reminders 3 days and 1 day before the end of the 7 days, and when your
  store moves to Free ([details](#failed-payment)).

**Email notifications** card (on Plan & usage):

- **Store owner**: the owner's email from BigCommerce always receives the emails.
- **Also send to (optional)**: up to 3 more addresses (**Add another address**).
- **Remind me at 50% and 80% of a limit**: untick to stop the 50% and 80% reminder emails. The others, billing
  emails included, are always sent.
- Click **Save**. Only the store owner can change these; staff see them read-only.

## If you uninstall the app {#uninstall}

Uninstalling cancels your paid subscription; payments are not refunded. Your models and settings are kept for 30
days after you uninstall, and so is the paid time you have left. Reinstall before then to continue where you left
off; after that they are deleted. You get an email when you uninstall and a reminder before the deletion. If you added
the [snippet by hand](/docs/storefronts/#manual-snippet) on any storefront, remove it from Script Manager.
