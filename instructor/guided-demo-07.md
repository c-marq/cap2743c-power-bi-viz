# Guided Demo 07 — Building a Report App

**Course:** CAP2743C — Power BI: Data Visualization and Analysis
**Session:** Class 7 · Tuesday, June 2, 2026 · Block A
**Chapter:** Chapter 4 — Interactive Storytelling (Sections 4.5–4.7)
**Demo length:** ~30 minutes (instructor-led; students watch, do not build along)
**Dataset:** AdventureWorks (`AdventureWorks_Sales.xlsx`, already loaded)

---

## How to run this demo

Instructor-led walkthrough. Students watch and take notes — they do **not** build
along. The hands-on follow-along is Guided Practice and Lab 6. Today covers the
**second half of Chapter 4**: drill-down recap, drill-through, custom tooltips, and
the bookmarks-plus-buttons "report app." This is the demo that pairs with Lab 6.

Pace markers (`⏱`) tell you roughly where you should be. If you fall behind, the
custom-tooltip section (Part 4) is the most trimmable — name it and move on.

**Field discipline note (read before class):** this demo uses a **Reseller**-themed
main page and a **Product Category** drill-through detail page. Lab 6 deliberately
uses different fields — a **Sales Territory** bookmark app and a **Customer**
drill-through page. The graded lab is new application, not a replay of the demo. Do
not improvise the demo onto Lab 6's fields.

---

## What students should leave the demo able to picture

1. **Drill-through** carries the audience to a *separate detail page* filtered to the
   point they right-clicked — different from drill-down, which stays inside one visual.
2. A **custom tooltip** is a whole mini report page that floats up on hover.
3. **Bookmarks + the Selection pane + navigation buttons** package a report into an
   *app*: saved states, controlled visibility, and buttons that move between them.

---

## Setup before students arrive

1. Open Power BI Desktop with `AdventureWorks_Sales.xlsx` loaded.
2. Apply the **`AW-Demo-Navy`** theme from earlier demos so the report already
   looks convincing — today is about interaction, not formatting.
3. Build a clean main page named **`Demo 7`** with three visuals:
   - A **Column chart**: `Reseller` on the X-axis, `Sales Amount` on the Y-axis.
   - A **Line chart**: `Date` on the X-axis, `Sales Amount` on the Y-axis.
   - A **Table**: `Reseller` and `Sales Amount`.
4. Add a second page named **`Category Detail`** — leave it nearly empty for now;
   you will build it live in Part 3.
5. Add a third page named **`Tooltip`** — also empty; built live in Part 4.
6. Confirm a **Sales Territory hierarchy** (Group → Country → Region) is available
   in the Data pane for the Part 1 drill-down recap.

> 💡 **Why pre-build the visuals:** Weeks 1–3 covered building visuals and applying
> themes. Starting with the visuals already on the canvas keeps all 30 minutes on
> Chapter 4's actual skill — the interaction layer.

---

## PART 1 — Drill-down recap, then the clean line (⏱ 0:00–0:05)

**Frame it:** *"Last session you saw drill-down — going deeper inside one visual
through a hierarchy. Today is its cousin, drill-through, and three more tools that
together turn a report into a small app. First, one fast reminder of the difference,
because everyone mixes these two up — working analysts mix them up."*

**Quick recap, said not demoed (~1 min):**
- **Drill-down** = deeper inside *one visual*, same page. The phone-map zoom.
- **Drill-through** = jump to a *separate page* built for detail. The player-stats
  click — the league table did not change; a new page came forward.

*"Same page versus new page. That is the whole line. Today is the new-page one."*

Then put the `Demo 7` page on screen and let the room see the starting state — three
visuals, themed, static. *"This is a report that shows. By the end of the half hour
it will be a report you can walk through."*

---

## PART 2 — Drill-through to a detail page (⏱ 0:05–0:14)

This is the centerpiece of the demo. Build it slowly.

### 2a. Build the detail page first

**Say this:** *"Drill-through is backwards from how it feels. You build the
destination page first, then wire the trip to it."*

**Do this on screen — on the `Category Detail` page:**
1. Add a **Bar chart**: `Product` → `Category` on the axis, `Sales Amount` on values.
2. Add a **Card**: `Sales Amount`.
3. Add a small **Table**: `Product` → `Subcategory` and `Sales Amount`.

*"This is a detail page about whatever reseller someone right-clicks. Right now it
shows all resellers — watch what the drill-through well does to that."*

### 2b. Wire the Drill through well

**See it → Name it → Find it → Do it:**
- **See it:** with no visual selected, the Visualizations pane shows field wells for
  the *page itself*.
- **Name it:** one of them is the **Drill through** well.
- **Find it:** on `Category Detail`, click empty canvas so no visual is selected →
  locate the **Drill through** well in the Visualizations pane.
- **Do it:** drag **`Reseller`** into the **Drill through** well. Power BI
  automatically adds a **Back** button to the page corner.

> 🛑 **Stop and check (say it aloud):** "A Back button just appeared in the corner.
> Power BI added it for me — drill-through pages get one automatically, because the
> audience needs a way home."

### 2c. Take the trip

**Do this on screen:**
1. Go back to the **`Demo 7`** page.
2. **Right-click** any reseller's bar in the column chart.
3. In the menu, choose **Drill through → Category Detail**.
4. The detail page opens — every visual on it now filtered to that one reseller.

**Land it:** *"One right-click. The audience went from the overview to a full detail
page about exactly the thing they were curious about — and the overview is still
sitting there, unchanged, when they hit Back."*

> ⚠️ **Common mistake to name aloud:** if the detail page still shows every reseller,
> the field went into the *page filter* section, not the **Drill through** well —
> they are different wells. Check the well.

---

## PART 3 — 💜 Take a breath (⏱ 0:14–0:15)

**Say this:** *"Drill-through has a shape worth holding onto: build the detail page,
drop a field in the Drill through well, right-click to travel. The Back button is
free. That is the whole feature."*

A real one-minute pause. Then continue.

---

## PART 4 — Custom tooltips, named and shown once (⏱ 0:15–0:20)

Custom tooltips are in Chapter 4 and on the Lab 6 / HW 2 radar, so they need a real
*showing* — but a fast one.

**Frame it:** *"Drill-through answers a big follow-up by opening a whole page. Some
follow-ups are smaller — what is the exact number behind this bar, how did this point
get here. For those, the audience should not have to click and travel. They should
just hover."*

**Do this on screen — fast:**
1. Go to the empty **`Tooltip`** page.
2. With no visual selected, open **Format pane → Page information**. Turn on
   **Allow use as tooltip**.
3. In **Canvas settings**, set Type to **Tooltip** — the page shrinks to a small card.
4. Build one small visual on it — a **Sales Amount by Month** line chart.
5. Go to `Demo 7`. Select the **column chart** → **Format pane → General →
   Tooltips** → set Type to **Report page** → pick the `Tooltip` page.
6. Hover a bar. The mini line chart floats up.

**Land it:** *"The museum placard. You do not need it until you lean in — and when
you do, it is right there, then it is gone."*

Do not belabor this. If `⏱` says 0:20 already, you are on time.

---

## PART 5 — Bookmarks and the report app (⏱ 0:20–0:29)

This is the second big build. It is the heart of Lab 6, so it gets real time.

**Frame it:** *"Everything so far added controls to a page. The last step packages
those controls so the report behaves less like a document and more like a small
**app** — saved views the audience switches between, with buttons."*

**Name the three tools as a set:**
- A **bookmark** = a saved snapshot of the report's state — filters, slicer choices,
  sort, drill level, current page, *and* which visuals are shown or hidden.
- The **Selection pane** = lists every visual with an eye icon, so you show or hide
  visuals on purpose.
- A **navigation button** = what the audience presses to move between bookmarks.

### 5a. Make two states with the Selection pane

**Do this on screen — on `Demo 7`:**
1. **View tab → Show panes → Selection.** The Selection pane opens; every visual is
   listed with an eye icon.
2. This is the **Overview** state — clean. Open the **Bookmarks pane**
   (**View tab → Show panes → Bookmarks**), click **Add**, rename it `Overview`.
3. Now change the page: in the Selection pane, **hide** the line chart (click its
   eye) so only the column chart and table show. Click **Add** again in the
   Bookmarks pane, name it `Focus`.

> ⚠️ **Common mistake to name aloud:** a bookmark captures the state *at the moment
> you click Add*. A bookmark captured *before* you hid the visual cannot hide it —
> you would have to update it after. Capture the state first, then Add.

### 5b. Wire navigation buttons

**Do this on screen:**
1. **Insert tab → Buttons → Blank button.** A button appears on the canvas.
2. With it selected, **Format pane → Action →** turn **On →** Type **Bookmark →**
   pick `Overview`. Give the button text "Overview".
3. Add a second button the same way, wired to the `Focus` bookmark.
4. **Say this:** *"In the report — or holding Ctrl in Desktop — clicking these
   buttons snaps the page between the two states."* Demonstrate the Ctrl-click.

**Land it (tell Jamal's one-report rule short):** *"The BI Center used to ship three
separate files — an executive version, a manager version, an analyst version. Every
measure change had to be made three times, and someone always forgot one. Now: one
file. The audiences are bookmarks. One landing page of buttons, three doors into the
same model. Same data, three doors — not three buildings."*

---

## PART 6 — Close the demo (⏱ 0:29–0:30)

**Say this:** *"Four tools today: drill-through to a detail page, a custom tooltip on
hover, bookmarks for saved states, buttons to move between them. Together they are
the report app. In Guided Practice you build these yourself. In Lab 6 you build a
graded bookmark app — on Sales Territory, with a Customer drill-through page. Same
moves, your hands, new fields."*

---

## Instructor answer key — questions students ask in this demo

**"What is the difference between drill-down and drill-through again?"**
Drill-down goes deeper inside one visual through a hierarchy — same page.
Drill-through right-clicks a data point and jumps to a separate detail page filtered
to it. Same page versus new page. If a student can say that sentence, they have it.

**"My drill-through page still shows everything."**
The field went into the page filter section instead of the **Drill through** well.
They are different wells in the Visualizations pane. Move the field to Drill through.

**"My bookmark does not hide the visual I wanted hidden."**
The bookmark was captured before the visual was hidden. A bookmark is a snapshot of
the moment you click Add. Hide the visual in the Selection pane first, then either
Add a new bookmark or right-click the existing one and choose Update.

**"What does a bookmark actually save?"**
Filters, slicer selections, sort order, drill level, the current page, and visual
visibility from the Selection pane. That visibility part is what lets one page serve
as several different views.

**"Do we have to build the custom tooltip in Lab 6?"**
Check the Lab 6 worksheet — but the heart of Lab 6 is the bookmark app and the
drill-through. The tooltip is named in the demo for awareness and for the PL-300
exam; it is lighter than the other two.

---

## Do / Don't for the embedded tutor or co-instructor

**Do:**
- Repeat the "same page vs new page" line every time drill-down and drill-through
  come up together. It is the single most-confused pair in the chapter.
- Name the bookmark-timing trap out loud — capture state *first*, then Add — because
  every student hits it in Lab 6.
- Actually demonstrate the Ctrl-click on the navigation buttons in Desktop, so
  students know buttons do not "do nothing" in edit mode.

**Don't:**
- Don't spend more than five minutes on custom tooltips. It is the lightest of the
  four tools and the build is quick; lingering eats the bookmark time, which matters
  more for Lab 6.
- Don't drift the demo onto Lab 6's fields. If a student asks "can we do this on
  Sales Territory?", the answer is "that is exactly Thursday's lab."
- Don't skip the Selection pane and try to bookmark visibility some other way. The
  Selection pane *is* how visibility gets into a bookmark — it is not optional.

---

*End of Guided Demo 07.*
