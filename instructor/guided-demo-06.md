# Guided Demo 06 — Making a Report Answer Back

**Course:** CAP2743C — Power BI: Data Visualization and Analysis
**Session:** Class 6 · Thursday, May 28, 2026 · Block A
**Chapter:** Chapter 4 — Interactive Storytelling (Sections 4.2–4.4)
**Demo length:** ~30 minutes (instructor-led; Capstone reveal follows in the session, see Part 7)
**Dataset:** AdventureWorks (`AdventureWorks_Sales.xlsx`, already loaded)

---

## How to run this demo

Instructor-led walkthrough. Students watch and take notes — they do **not** build
along. Today covers the **first half of Chapter 4**: the three-layer filter
hierarchy, slicers, and editing interactions. Drill-through, tooltips, and bookmarks
are Session 7's demo (Demo 07) — do **not** pull them forward, even if a student asks.

This session also carries the **Capstone reveal**. The demo is Part 1–6; the reveal
is Part 7 and uses a different file. Keep them separate in your head — finish the
Chapter 4 demo cleanly, take the break, then switch into reveal mode.

**Field discipline note (read before class):** this demo uses a **column chart of
Sales Amount by Customer**, a **Year slicer**, and a **KPI card**. Lab 5 deliberately
uses different fields — **Product Category** and **Sales Territory Country** slicers,
and the **Sales Territory hierarchy** for drill-down. The graded lab is new
application, not a replay of the demo. Do not improvise the demo onto Lab 5's fields.

---

## What students should leave the demo able to picture

1. A filter has a **scope** — visual, page, or report — and picking too wide a scope
   is the quietest, most common mistake in Power BI.
2. A **slicer** is just a filter promoted to a visual the audience can touch; it is
   **page-scoped by default**, and **sync slicers** is what widens it.
3. **Editing interactions** decides what a click does to the *other* visuals:
   **Filter**, **Highlight**, or **None** — and a total card should be **None**.

---

## Setup before students arrive

1. Open Power BI Desktop with `AdventureWorks_Sales.xlsx` loaded.
2. Build a clean page named **`Demo 6`** with three visuals:
   - A **Column chart**: `Customer` on the X-axis, `Sales Amount` on the Y-axis.
     (Customer has many values — that is intentional; it makes filtering visible.)
   - A **Line chart**: `Date` on the X-axis, `Sales Amount` on the Y-axis.
   - A **Card**: `Sales Amount` (the $109.8M total).
3. Apply the **`AW-Demo-Navy`** theme from Demo 05 so the page already looks
   convincing — today is about *interaction*, not formatting.
4. Add a **second page** named **`Demo 6 — Page 2`** with one small visual on it
   (a Card showing `Sales Amount` is enough). You need a second page to demo sync
   slicers honestly.
5. Confirm the **`Year`** column (the plain calendar Year Carlos added to the Date
   table) is available in the Data pane. **Use calendar `Year`, not Fiscal Year** —
   FY2017 has no sales and will confuse the slicer.
6. Have the **Capstone reveal materials** open in a separate window/tab, ready for
   Part 7 — do not hunt for them live.

> 💡 **Why pre-build the visuals:** Weeks 1–2 already covered building visuals.
> Starting with three visuals on the canvas keeps all 30 minutes on Chapter 4's
> actual skill — making those visuals talk to each other.

---

## PART 1 — The problem this chapter solves (⏱ 0:00–0:03)

**Tell the opening story briefly** (it is in the chapter — the regional managers
meeting). The shape of it:

*"Camila built a great report. In the meeting, a manager asked 'can we see only the
bikes?' The report had no control for that. So she said 'I'll send a version this
afternoon.' Then someone asked for Q3 only. Another version. By the end she had a
list of five reports to build — all the same report, filtered five ways."*

**Land the framing:** *"Marcus told her: I don't want five versions. I want one
report where they ask those questions themselves, in the room. That is this whole
demo. We make the report answer back."*

---

## PART 2 — The three-layer filter hierarchy (⏱ 0:03–0:11)

**Frame it first.** Draw or show the three tiers, narrowest to widest:

> **Filters on this visual** → one visual.
> **Filters on this page** → every visual on this page.
> **Filters on all pages** → every visual on every page. *This is the report filter.*

**The office-keys analogy lands well — use it:** room key opens one office (visual),
floor key opens one floor (page), master key opens the whole building (report). *"You
don't hand out a master key for a job that needs a room key."*

### Demo the report filter

**See it → Name it → Find it → Do it:**
- **See it:** the **Filter pane** is the vertical panel on the right of Report View.
  It has three grey section headers.
- **Name it:** the bottom section is **Filters on all pages**.
- **Find it:** if the pane is closed — **View** tab → **Show panes** → **Filters**.
- **Do it:** from the Data pane, drag **`Year`** into **Filters on all pages**. Tick
  the most recent year (2020). *Both* pages now show 2020 only.

**Land it:** *"I changed every visual on every page and I never touched a single
visual. That is the report filter. It is powerful, which is also why it is
dangerous."*

> ⚠️ **Common mistake — say this aloud:** a filter at the wrong scope is **silent**.
> Power BI does not warn you. If you mean to filter one chart to Bikes but you drop
> the field into *Filters on all pages*, you just stripped every other category out
> of the whole report. *"When a number looks wrong across a whole report — check the
> report filter first."*

**Then remove the year filter** so the rest of the demo starts clean. Narrate it:
*"Watch — I pull it back out, and the whole report returns to all years."*

---

## PART 3 — 💜 Take a breath (⏱ 0:11–0:12)

**Say this:** *"One sentence holds this together: a filter is anything that decides
which data a visual shows. The only two questions are — who controls it, you or the
audience, and how far does it reach. Everything else in this chapter is a variation
on those two questions."*

A real one-minute pause. Then continue.

---

## PART 4 — Slicers, the filter the audience can touch (⏱ 0:12–0:20)

**Frame it:** *"The Filter pane is mostly yours — the analyst's. Your audience can
open it, but they won't; it reads as a developer tool. A **slicer** is a filter
promoted to a visual. It sits on the canvas, in plain sight, and it invites the
audience to use it."*

### 4a. Build a slicer

**See it → Name it → Find it → Do it:**
- **See it:** the Visualizations pane has a grid of visual icons; one looks like a
  small funnel.
- **Name it:** that is the **Slicer** visual.
- **Find it:** with nothing selected, click the Slicer icon.
- **Do it:** a blank slicer appears. From the Data pane, drag **`Year`** into its
  Field well. The slicer fills with years. Click **2020**.

**Land it:** *"Every other visual on the page redrew to 2020. The audience did that —
not me. That is the difference between a report and a conversation."*

> 🛑 **Stop and check (out loud):** after you click a year, the other visuals
> redraw *and* the slicer shows that item in a filled, selected state. If nothing
> changed — the slicer has no field in its well. An empty slicer draws fine and
> filters nothing.

### 4b. Single select

**Do this on screen:**
1. With the slicer selected, open the **Format pane** → find **Selection**.
2. Turn **Single select** on.
3. Click between years — show that picking one *releases* the last one, like radio
   station presets.

**Land it:** *"For a slicer that drives a headline number, single select keeps the
number honest. Multi-select is flexible but it is also how an audience member ends up
reading a filtered number they think is the total."*

### 4c. Sync slicers — name and show the pane

**Do this on screen:**
1. **View** tab → **Show panes** → **Sync slicers**.
2. The pane shows a row per page with two checkboxes: **sync** and **visible**.
3. Tick **sync** for both pages so the Year selection follows the audience across
   pages. Tick **visible** only where there is room.
4. Flip to `Demo 6 — Page 2` and show that it now obeys the same year.

**Land it (tell the "slicer that lied" story short):** *"Camila once built three
pages, each with its own Year slicer. She set the one on page one. Pages two and
three still showed every year — because each slicer only filters its own page.
Different pages, identical-looking slicers, filtering different things. Sync slicers
is the fix: one selection, every page."*

---

## PART 5 — Editing interactions (⏱ 0:20–0:27)

**Frame it:** *"Slicers aren't the only clickable thing. Every regular visual is
clickable too — click a bar, and the *other* visuals respond. That cross-visual
behavior is **on by default**. **Editing interactions** lets you control it, visual
by visual."*

**The three behaviors — name them with the bar-chart picture:**
- **Filter** — the receiving visual *refilters* down to only the clicked slice.
- **Highlight** — the receiving visual keeps all its data but *dims* everything that
  does not match, so the audience sees the slice *and* its context.
- **None** — the receiving visual *ignores* the click entirely.

### Demo it

**See it → Name it → Find it → Do it:**
- **See it:** select any visual — a contextual **Format** tab appears on the ribbon.
- **Name it:** on that tab, in the Interactions group, is **Edit interactions**.
- **Find it:** select the **Customer column chart** → **Format** tab →
  **Edit interactions**.
- **Do it:** small icons now sit on the corner of every *other* visual. On the
  **Card**, click the **None** icon. On the **Line chart**, leave it on Filter.
  Click **Edit interactions** again to exit editing mode.

**Now demonstrate the payoff:**
1. Click a customer's bar in the column chart.
2. The line chart refilters to that customer. The **card stays at $109.8M**.

**Land it:** *"The card is on the page to be a fixed reference — the company total.
If it refiltered every time someone clicked a bar, it would stop being a total. So
its interaction is None. That is the one deliberate decision worth making on almost
every page."*

> ⚠️ **Common mistake — say this aloud:** Highlight is not offered by every visual.
> A card has nothing to dim, so it only shows **Filter** and **None** — two icons,
> not three. If a student expects three and sees two, that is the visual type, not a
> bug.

---

## PART 6 — 💜 Take a breath + close the demo (⏱ 0:27–0:30)

**Say this:** *"That was the densest stretch — three filter scopes, slicers, sync
slicers, three interaction modes. They all filter something. Here is the organizing
sentence again: a filter decides which data a visual shows; the only questions are
who controls it and how far it reaches."*

**Close:** *"In Guided Practice you do these moves yourselves. In Lab 5 you do them
graded — on Product Category and Country slicers, and a Sales Territory drill-down.
Same moves, your hands, new fields."*

Then take the room into the **between-block break** before Part 7.

---

## PART 7 — Capstone reveal (after the break — separate from the demo)

> This is **not** part of the Chapter 4 demo. It is a distinct segment. Switch files,
> switch tone — from "here is a skill" to "here is what the whole course builds
> toward."

**Run the reveal from the Capstone reveal package** (Capstone Brief, Rubric, and
Checklist — distributed today, May 28). Suggested flow, ~15 minutes:

1. **Open the Capstone Brief on screen.** Read the scenario aloud — students absorb
   the framing better heard than skimmed.
2. **Walk the deliverable list.** What they hand in, in what format, by when
   (Thursday June 18). Point out it is **200 points — 40% of the grade**.
3. **Walk the Rubric tiers.** Excellent / Good / Needs Work. Emphasize the redo path
   and that the capstone is *assembled from work they are already doing in labs* —
   it is not a cold-start project.
4. **Hand out / link the Checklist.** Tell them: *"This is your map. Every time we
   finish a lab, one or two checklist items get a check. By Week 6 the checklist is
   mostly done and the capstone is mostly built."*
5. **Name the calendar.** Capstone work time is built into Session 11 (June 16);
   presentations are Session 12 (June 18). Presenting is the default but a recorded
   walkthrough is an accepted alternative — say this now, it lowers a lot of anxiety.

**Do not** start capstone work today. Today is reveal only — the goal is that
students leave knowing what they are aiming at, not feeling they are behind.

---

## Instructor answer key — questions students ask in this demo

**"What's the difference between a filter and a slicer?"**
A slicer *is* a filter — it is just a filter rendered as a visual on the canvas so
the audience can operate it. The Filter pane is the analyst's tool; a slicer is the
audience's tool. Same underlying mechanism.

**"My slicer doesn't filter anything."**
Almost always an empty Field well. A slicer drawn on the canvas with no field looks
finished but filters nothing. Drag a field into its well.

**"Why are there only two interaction icons on my card?"**
A card has nothing to dim, so Highlight does not apply — it only offers Filter and
None. That is correct behavior, not a bug.

**"If I set the slicer, does it follow me to other pages?"**
Not by default — a slicer is page-scoped. Sync slicers is the feature that links one
slicer's selection across pages. Pair those two facts together; the exam tests them
as a pair.

**"What's the difference between drill-down and drill-through?"**
Good question — and it is *next* session (Demo 07). Short version so they are not
left hanging: drill-down goes deeper inside one visual; drill-through jumps to a
separate detail page. Full demo Thursday.

**"Is the capstone a brand-new project?"**
No. It assembles and extends the work from the labs. The checklist shows how lab work
maps onto capstone components. Starting from scratch the night before is exactly what
the structure is designed to prevent.

---

## Do / Don't for the embedded tutor or co-instructor

**Do:**
- Keep repeating the organizing sentence — "a filter decides which data a visual
  shows; who controls it and how far it reaches." It is the spine of the whole
  chapter.
- Name the silent traps aloud — wrong-scope filter, empty slicer well, two-icon
  cards — because students hit all three in Lab 5.
- Keep the Capstone reveal physically and tonally separate from the demo. Finish the
  skill, break, *then* reveal.

**Don't:**
- Don't pull drill-through, tooltips, or bookmarks into this demo. They are Demo 07.
  If asked, give the one-line answer above and move on.
- Don't use Fiscal Year on the slicer. Use the calendar **`Year`** column —
  FY2017 has no sales and a fiscal slicer shows a confusing empty year.
- Don't start capstone work in the reveal. Reveal is "here is the target," not "begin
  now." Beginning now creates the panic the structure is meant to remove.

---

*End of Guided Demo 06.*
