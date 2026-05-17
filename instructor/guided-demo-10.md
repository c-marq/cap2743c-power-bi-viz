# Guided Demo 10 — Beyond the Report

**Course:** CAP2743C — Power BI: Data Visualization and Analysis
**Session:** 10 · Thursday, June 11, 2026 · Block A
**Chapter:** 7 — Beyond the Report (Dashboards, Mobile, and Distribution)
**Demo length:** ~30 minutes — standard (one breath)
**Dataset:** AdventureWorks — `AdventureWorks_Sales.xlsx`
**Paired graded work:** Lab 9 — Mobile Layout & Distribution-Ready Report (Block B, same day)

---

## How to run this demo

This is an **instructor-led** demo. You build; students watch. **Students do not build
along** — and a point to make explicitly: **students will not publish to the Service
themselves in this course.** The ND section does not have Power BI Service accounts, so
the publish, dashboard, and alert steps in this demo are *watch-and-understand* content.
They are still on the PL-300 exam, and students still build the Desktop side of
distribution — the mobile layout and a distribution-ready report — in Lab 9 this
afternoon. Say this plainly at the start so no one thinks they have missed a setup step.

This chapter **changes address.** Chapters 1–6 lived in Power BI Desktop. Chapter 7
hops between the **Power BI Service** (the cloud, in a browser) and Desktop, and names a
separate app, Power BI Report Builder. Every hop in this demo carries a **WHERE AM I?**
marker — say it out loud each time, because the venue switch is the single most
disorienting thing about Chapter 7 for a new analyst.

Project both Power BI Desktop **and** a browser signed in to `app.powerbi.com`, ready to
alt-tab between them.

---

## Setup before students arrive

1. **Have a finished report open in Desktop.** It must contain at least three visuals
   you will pin: a **Sales Amount card** (the new card visual — lightning-bolt icon), a
   **Sales Amount by Sales Territory Group** bar chart, and a **Sales Amount by Month**
   line chart (calendar `Year` → Month). Name the report something clear, e.g.
   `Demo 10 — AdventureWorks Sales`.
2. **Confirm Power BI Service sign-in on the *instructor* machine.** Sign in to
   `app.powerbi.com` in the browser before class and confirm you can reach a workspace
   you can publish into. This demo's Service portions run on your machine only — students
   do not have Service accounts, so they cannot follow these steps on their own machines,
   and that is expected. If your own sign-in fails, the demo's Parts 1–2 cannot run;
   resolve it the day before, or fall back to describing the publish/pin steps from
   prepared screenshots.
3. **Decide the target workspace in advance.** Know which workspace you will publish to
   so you are not browsing a list while students wait.
4. **Verify the Sales Amount card shows the expected total.** A clean card touching only
   the Sales table reads **$109,809,274.20**. If it does not, the model has a filter or
   relationship problem — fix it before class.
5. **Paginated reports — awareness only.** Power BI Report Builder is a separate app. You
   will *name* it in Part 3, not open it. Do not install or demo it.

---

## Field discipline note

Demo 10 and Lab 9 use **different fields** so the lab is new application, not a replay.
Lab 9 is **Desktop-only** (no Service access for students): students build a
distribution-ready report — a single monitor page, a mobile layout, and the Personalize
visuals setting — rather than publishing.

| Move | Demo 10 uses (you, now — Service) | Lab 9 uses (students — Desktop only) |
|---|---|---|
| Headline card | **Sales Amount** card | **Order Quantity** card |
| Category tile | **Sales Amount** by **SalesTerritory Group** | **Sales Amount** by **Category** |
| Trend tile | **Sales Amount** by **Month** | **Order Quantity** by **Year** |
| Fourth tile | *(territory bar above is the third)* | **Sales Amount** by **Channel** |
| Service step | data alert on the Sales Amount card | *(no Service — alert is a written-response question)* |

The overlap students *do* repeat is the **mobile layout** — you demo it here, they build
it in Lab 9 — so they build their phone layout on a different page and different visuals
than this demo's. Everything else in Lab 9 is Desktop work the demo only describes:
assembling a monitor page, and the Personalize visuals setting.

---

## What students should leave the demo able to picture

1. **The container choice comes first.** A **report** is multi-page and interactive — for
   an audience that *explores*. A **dashboard** is a single Service-only screen of pinned
   tiles — for an audience that *monitors*. An **app** is a packaged bundle behind one
   clean front door — for delivering to *many* people.
2. **A dashboard is built by pinning; a mobile layout is a separate arrangement.** Tiles
   are pinned from one or more reports. A phone layout is a deliberate choice of the few
   things that matter on a small screen — not the desktop report shrunk.
3. **Three ways to keep an audience current.** An **alert** fires on a *condition*; a
   **subscription** arrives on a *clock*; **automatic page refresh** runs on a *timer*.
   Condition, clock, timer.

---

## PART 1 — Publish and Choose the Container

⏱ **~9 minutes**

Open with the chapter's correction: for six chapters, *finished* meant correct, clear,
formatted, interactive, analytically sharp. Jamal's point is that a report that is
correct and **unread** has not finished its job. Distribution is a separate craft.

### Publish the report to the Service

> 💜 **WHERE AM I?** You start in **Power BI Desktop**.

- **See it.** The **Home** tab of the ribbon has a **Publish** button.
- **Name it.** **Publish.**
- **Find it.** **Home** tab → **Publish**.
- **Do it.** Power BI asks for a destination workspace. Pick the workspace from setup
  step 3. The report uploads.

> 💜 **WHERE AM I?** Now switch to the **browser** — `app.powerbi.com`. Open the
> workspace and find the report you just published. From here on, the venue is the
> Service unless a marker says otherwise.

### The three containers — a teaching beat, no clicks

With the workspace on screen, give the precise definitions. Three words get used loosely
in every office; Power BI gives each one an exact meaning.

- A **report** — what students built across six chapters. Multi-page, interactive, bound
  to **one** semantic model. For an audience that wants to explore.
- A **dashboard** — a single screen, no scrolling, no pages. Built **only** in the
  Service, never in Desktop. Assembled from **tiles** pinned from reports. Its defining
  power: it can pull tiles from *several different reports and models* onto one canvas —
  a report cannot. For an audience that wants to monitor.
- An **app** — a packaged, polished bundle of dashboards and reports, published to a
  defined audience behind one clean front door. For delivering to many people without
  handing them a messy workspace.

Deliver the COMMON MISTAKE from 7.2: **calling every Power BI screen a "dashboard."** In
casual speech it does not matter; on the exam and in a real workspace it does. If someone
points at a multi-page interactive file and says "fix the dashboard," they mean a report.
Match the word to the object.

> Jamal's forty-one-reports story makes this concrete: a workspace is a back room; an app
> is the storefront. Consumers should almost always receive an **app**, not raw workspace
> access. Tell the story briefly — it is the *why* behind the precise vocabulary.

---

## PART 2 — Build a Dashboard: Pin, Theme, and Q&A

⏱ **~9 minutes**

> 💜 **WHERE AM I?** Still in the **browser** — the Power BI Service.

A dashboard is built by **pinning**: open a report, find a visual worth monitoring, pin
it to a dashboard as a tile.

### Pin the first tile

- **See it.** In the Service, open the published report. Hover the pointer over the
  **Sales Amount card** — a small toolbar appears in the visual's corner.
- **Name it.** The **pushpin** icon on that toolbar is **Pin visual**.
- **Find it.** Hover the visual → click the **pushpin** icon.
- **Do it.** A dialog asks for a destination. Choose **New dashboard**, name it
  `South Florida Monitor`, and pin.

### Pin the rest, then finish the dashboard

Repeat the pin for the **Sales Amount by Territory Group** bar and the **Sales Amount by
Month** line. Mention — without doing it — that to pin a *whole live page* as one
interactive tile you use the page's **Pin to a dashboard** command instead; a pinned
visual is a snapshot tile, a pinned live page is the entire interactive page embedded.

Then add the two finishing touches:

- **Dashboard theme** — from the dashboard's **edit** menu, set the background and tile
  styling for the whole dashboard at once (light, dark, or custom).
- **Q&A question box** — it sits across the top of every dashboard. A consumer types a
  plain-language question, Power BI answers with a visual, and they can pin that answer
  as a new tile themselves.

Deliver the STOP AND CHECK: open the dashboard from the workspace. Each tile should show
its visual, and clicking a tile should jump back to the report page it came from. **A
tile is only ever as current as the data feeding it** — a stale or errored tile means a
refresh problem in the underlying report or model, not in the dashboard.

---

## 💜 TAKE A BREATH

⏱ **~2 minutes**

Stretch, look away from the screen. Three containers, three jobs — fix them before the
last part. **Report** for the audience that explores. **Dashboard** for the audience that
monitors. **App** for delivering to everyone. The choice always follows the audience.

---

## PART 3 — Mobile and Staying Current

⏱ **~10 minutes**

### A phone layout for the report

> 💜 **WHERE AM I?** Switch back to **Power BI Desktop**. Designing a report's phone
> layout is a Desktop task.

A report built on a wide laptop canvas does not fit a phone held upright. Pan-and-zoom is
the default if you do nothing — and it is unusable. The fix is a separate **mobile
layout**.

- **See it.** In Power BI Desktop, the ribbon's **View** tab has a group for layout
  options.
- **Name it.** **Mobile layout.**
- **Find it.** **View** tab → **Mobile layout**. The canvas switches to a tall phone
  frame with a grid.
- **Do it.** The page's visuals wait in a side panel. Drag **only** the headline card and
  the trend line onto the phone grid — the two things a walking user needs — and size
  them for a thumb. Switch back with **View** tab → **Desktop layout**.

Say the guiding idea plainly: a phone layout is **not** the desktop report shrunk. It is
a deliberate choice of the few things that matter in the thirty seconds a walking user
will give it. You built a phone version without touching the desktop version — both now
exist in one file, and the Mobile app shows each user the right one. (A dashboard gets
the same treatment from its edit menu, in the Service.)

### A data alert — the report reaches the audience

> 💜 **WHERE AM I?** Back to the **browser** — the Service. Alerts are set there.

> Re-publish first so the Service has the mobile layout: **Home** tab → **Publish** →
> **Replace**.

- **See it.** In the Service, open the `South Florida Monitor` dashboard and find the
  single-value **Sales Amount card** tile.
- **Name it.** The tile's **More options (...)** menu includes **Manage alerts**.
- **Find it.** Hover the tile → **More options (...)** → **Manage alerts** → **Add alert
  rule**.
- **Do it.** Set a condition — **Total Sales below $10M** — and a check frequency. When
  the model refreshes and the value crosses the line, Power BI sends a notification, and
  an email if you ask for one.

Deliver the COMMON MISTAKE from 7.5: an alert does **not** fire the instant the
real-world number changes. It is evaluated only when the **semantic model refreshes**.
If the model refreshes once a day, the alert can be a full day behind. Alerts are
*timely*, not *instant* — their speed is the refresh schedule's speed.

### Three more, at awareness level

Name these clearly; do not drill in. They round out the chapter; students will not do
them hands-on (no Service access for the first two; Report Builder is a separate app).

- A **subscription** — a scheduled email of a report page or dashboard. Where an alert
  fires on a *condition*, a subscription arrives on a *clock*.
- **Automatic page refresh** — a Desktop page setting that re-queries a DirectQuery
  source on a fixed *timer*, for a live wall-mounted screen.
- **Paginated reports** — for pixel-perfect, printable output: invoices, statements,
  every row of a long table. Built in a separate app, **Power BI Report Builder**. The
  signal words on the exam are *print*, *PDF*, *invoice*, *statement*.

### One thing students *will* do in Lab 9 — Personalize Visuals

**Personalize Visuals** is a Desktop report setting, so students *can* set it themselves
— and they will, in Lab 9. Once enabled, it lets a consumer reshape a visual into a
*private* view without changing the published report for anyone else. Show where it
lives: **File → Options and settings → Options → Current file → Report settings → tick
Personalize visuals.** It is the one piece of distribution control that does not need the
Service, which is why it is in the lab.

Close on the chapter's idea: building the report was half the job, maybe less. Getting it
to land — the right shape, on the right screen, in front of the right person, at the
right moment — is the other half, and it has its own tools.

---

## Instructor answer key

- **"Can I build a dashboard in Power BI Desktop?"** No. Dashboards exist **only** in the
  Service. Desktop builds reports.
- **"What's the difference between pinning a visual and pinning a live page?"** A pinned
  visual is a snapshot tile of one visual. A pinned live page is the entire report page,
  still interactive, embedded as one tile.
- **"My alert didn't fire when the number changed — why?"** Alerts are evaluated at
  **model refresh**, not in real time. The number must cross the line *on a refresh*.
- **"Do I need a paid license to publish?"** Publishing to a workspace needs a Power BI
  account; alerts, subscriptions, and sharing typically need Power BI Pro, or the
  workspace on Premium/Fabric capacity. Confirm what MDC provisions for the section.
- **"Mobile layout — do I have to rebuild every visual for the phone?"** No. The visuals
  already exist. You drag the few that matter onto the phone grid. The desktop layout is
  untouched.
- **"When is a paginated report the right answer?"** When the output must be
  pixel-perfect and printable — an invoice, a statement, every row of a long table. It is
  built in Power BI Report Builder, not Desktop.
- **"A dashboard tile shows an old number — is the dashboard broken?"** No. A tile is
  only as fresh as the data feeding it. The refresh problem is in the underlying report
  or model.

---

## Do / Don't — for the embedded tutor or co-instructor

Carlos does not stay for the tutoring block. Whoever runs it should hold these.

**DO**

- Confirm Power BI Service sign-in and a target workspace on the **instructor machine**
  **before class**. The Service portions run on your machine only.
- Say each **WHERE AM I?** marker out loud. The venue switch between browser and Desktop
  is the chapter's main source of confusion.
- Keep subscriptions, automatic page refresh, and paginated reports at **awareness**
  level — name them, do not open Report Builder or drill in.
- State clearly that students do not have Service accounts, so the publish, dashboard,
  and alert steps are watch-and-understand — and reassure them that is by design, not a
  missed setup step.
- Use the current terminology: the new card visual (lightning-bolt icon) and **Data
  pane**, not "Fields pane."

**DON'T**

- Don't let "dashboard" be used loosely. Model the precise vocabulary — report,
  dashboard, app are three different objects.
- Don't promise a specific alert speed. An alert's timeliness depends on the model's
  refresh schedule.
- Don't tell students they will publish or build a dashboard in Lab 9 — they will not.
  Lab 9 is Desktop work: a monitor page, a mobile layout, and the Personalize visuals
  setting.
- Don't skip the re-publish step before setting the alert — the Service needs the current
  version, including the mobile layout, for the rest of Part 3 to be honest.

---

*End of Guided Demo 10. Paired graded work: Lab 9 — Mobile Layout & Distribution-Ready
Report, Block B.*
