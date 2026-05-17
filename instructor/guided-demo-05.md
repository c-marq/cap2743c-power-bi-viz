# Guided Demo 05 — Making a Report Convincing

**Course:** CAP2743C — Power BI: Data Visualization and Analysis
**Session:** Class 5 · Tuesday, May 26, 2026 · Block A
**Chapter:** Chapter 3 — Formatting, Conditional Logic, and Custom Visuals
**Demo length:** ~30 minutes (instructor at the front, students watching — not following along yet)
**Dataset:** AdventureWorks (`AdventureWorks_Sales.xlsx`, already loaded)

---

## How to run this demo

This is an **instructor-led walkthrough**. Students watch and take notes — they do
**not** build along. The hands-on follow-along happens later in Guided Practice and
in Lab 4. The point of this demo is to show the *moves* once, slowly, with the
projector large enough that the back row can read the Format pane.

Pace markers (`⏱`) tell you roughly where you should be. If you fall behind, cut
the R/Python aside in Part 5 — it is the most trimmable piece.

**Field discipline note (read before class):** This demo uses a **Table of Sales
Amount by Product Category** and a **KPI card**. Lab 4 deliberately uses different
fields (Sales Territory Region, Product Subcategory, Country) so the graded lab is
*new application*, not a repeat of what students just watched. Do not improvise the
demo onto the lab's fields.

---

## What students should leave the demo able to picture

By the end of the 30 minutes, a student who was watching should be able to say:

1. A **theme** is one switch that re-skins every visual on every page.
2. **Conditional formatting** has three drivers, and the first three steps are the
   same every time — select the visual, find the property, click **fx**.
3. **Accessibility** is a four-item checklist you walk at the end, not something you
   memorize while building.

You are not trying to make them experts in 30 minutes. You are making the Lab 4
worksheet *recognizable* when they open it.

---

## Setup before students arrive

1. Open Power BI Desktop with `AdventureWorks_Sales.xlsx` loaded.
2. Confirm the model still totals **$109,809,274.20** on a quick Card visual
   (drag `Sales Amount` onto a Card). Delete the Card after checking.
3. Build a clean starting page named **`Demo 5`** with exactly two visuals:
   - A **Table** with `Product` → `Category` in Rows and `Sales Amount` in Values.
     It will show four rows: Accessories, Bikes, Clothing, Components.
   - A **Card** showing `Sales Amount` (the $109.8M total).
4. Make sure the theme is set to **Default** so the "before" state is plain.
5. Open a WCAG contrast checker in a browser tab (search "WCAG contrast checker")
   so it is ready when you reach Part 6 — do not hunt for it live.

> 💡 **Why pre-build the visuals:** the demo is about *formatting*, not about
> building visuals — students did that in Weeks 1–2. Starting with the visuals
> already on the canvas keeps all 30 minutes on the Chapter 3 skill.

---

## PART 1 — The "before" (⏱ 0:00–0:03)

**Say this:** *"This is a correct report. The number is right. Watch what happens to
how seriously you take it over the next half hour — the data will not change once."*

**Do this on screen:**
1. Show the `Demo 5` page. Plain teal table, plain card, off-white background.
2. Let it sit for three seconds of silence. That silence is the point — it is the
   "3-second glance" from the chapter's Figure 3.2.

**Land the framing:** formatting is a *second argument* the report makes alongside
the data. Today we add that second argument.

---

## PART 2 — Apply and customize a theme (⏱ 0:03–0:11)

### 2a. A built-in theme

**See it → Name it → Find it → Do it:**
- **See it:** the **View** tab of the ribbon has a **Themes** group with a gallery.
- **Name it:** that gallery is the **Themes gallery**.
- **Find it:** **View** tab → **Themes** group → **Themes** dropdown.
- **Do it:** open the dropdown, **hover** slowly over two or three presets so the
  class sees the live preview, then click **Executive**.

**Say this:** *"One click. Every visual, every page. That is the whole idea of a
theme — it is the paint scheme of the report."*

### 2b. Customize the active theme

**Do this on screen:**
1. **View** tab → **Themes** group → small drop arrow on the Themes button →
   **Customize current theme**.
2. The dialog opens. Point out the tabs: **Name and colors**, **Text**, **Visuals**,
   **Page**, **Filter pane**.
3. In **Name and colors**, set Theme name to `AW-Demo-Navy`.
4. Set the first data color to navy `#1B2A47` and the second to gold `#C9A23A`.
5. In **Text**, set the default font family to **Segoe UI**.
6. Click **Apply**.

> 🛑 **Stop and check (do this out loud):** "Watch the table and the card redraw."
> If a visual does not update, click it once then click off — Power BI sometimes
> waits for a re-render trigger. Name this for students now so it does not scare
> them in Lab 4.

### 2c. Name the JSON idea — do not demo it deeply

**Say this:** *"If I clicked* ***Save current theme*** *here, I would get a `.json`
file. A team keeps that one file in a shared folder, everyone imports it, every
report matches. You do not need to build a JSON file by hand — you need to know it
is the right answer when a question asks how a whole team stays on-brand."*

That sentence is the entire PL-300 point for JSON themes. Do not open a JSON editor
on screen — it is a time sink and not a tested skill.

---

## PART 3 — 💜 Take a breath (⏱ 0:11–0:12)

**Say this:** *"That was a lot of dialog navigation. Look away from the screen for a
second. The theme stuff is one idea wearing three coats: built-in, customized, and
JSON. Same idea, more control each time."*

A real one-minute pause. Then continue.

---

## PART 4 — Conditional formatting, two drivers (⏱ 0:12–0:22)

The chapter teaches three drivers. **Demo only two live** — Gradient and Rules.
Field Value needs a DAX measure and is better named than shown in a 30-minute demo.

**Frame the shared pattern first.** Write this on the board or a slide and leave it
up the whole part:

> Select the visual → find the property in the **Format pane** → click **fx** →
> choose a **Format style** → configure → **OK**.

*"Three of those steps never change. Only the Format style changes."*

### 4a. Driver 1 — Gradient

**Do this on screen:**
1. Click the **Table** (Sales Amount by Category) to select it.
2. Open the **Format pane** → **Cell elements**.
3. Find the **Sales Amount** field in Cell elements → toggle **Background color**
   on → click **fx**.
4. In the dialog: **Format style** = **Gradient**. **Based on field** = Sales
   Amount. **Minimum** = white. **Maximum** = the navy from the theme.
5. Click **OK**.

**Land it:** *"Bikes is the deepest navy because Bikes sells the most. I did not tell
the table which row was biggest — the color did. That is pre-attentive processing
from Chapter 1, doing the work for the audience."*

### 4b. Driver 2 — Rules

**Do this on screen:**
1. Same Table still selected. **Format pane** → **Cell elements** → switch the
   target to **Font color** → click **fx**.
2. **Format style** = **Rules**.
3. Click **+ New rule** to add bands. Keep it to two for time:
   - If value `>= 0` and `< 10000000` → **red**.
   - If value `>= 10000000` → **green**.
4. Click **OK**.

**Land it:** *"Gradient asked 'how much.' Rules asks 'which side of a line.' A
gradient is for smooth amounts; rules are for business thresholds you draw
yourself — under quota, at quota, over quota."*

### 4c. Name the third driver

**Say this, do not demo:** *"There is a third driver — ***Field value***. Instead of
writing the rule inside the visual, you write a DAX measure that returns a hex color
like* `"#27AE60"` *, and the visual just reads that color. It is the most powerful
one and the one the exam asks about most — but it is a Chapter 5 / DAX-flavored move,
so today you just need the name and the shape of it."*

> ⚠️ **Common mistake to name aloud:** a hex string in DAX must be in double quotes
> *and* start with `#`. A measure returning `27AE60` with no hash fails **silently** —
> no color, no error. Worth saying even though you are not demoing it.

---

## PART 5 — Small multiples + custom visuals, named fast (⏱ 0:22–0:26)

These two are in Chapter 3 and on the Lab 4 worksheet, so they need a *mention*, but
neither needs a slow build in this demo.

### 5a. Small multiples — one quick build

**Do this on screen:**
1. Add a **Line chart** to a blank spot on the page.
2. `Date` on the X-axis, `Sales Amount` on the Y-axis.
3. Drag **`Sales Territory` → `Country`** into the **Small multiples** well.
4. The single line splits into a tile grid — one mini line chart per country.

**Land it:** *"One chart, drawn once per category, tiled. You read the whole system
in a single sweep — which country climbs, which one collapses — no clicking."*

> ⚠️ Name the trap: small multiples are **not** on every visual. No Small multiples
> well = the current visual does not support it. Pies and cards never do.

### 5b. Custom visuals — name the safety rule only

**Say this, do not install anything:** *"Power BI has about thirty built-in visuals.
For the thirty-first thing — a Sankey, a calendar heatmap — there is **AppSource**,
Microsoft's marketplace. The catch: a custom visual is third-party code running
inside your report. Before you put one in a real report, check it is **Microsoft
Certified** — that badge means it passed Microsoft's security audit. Stars and review
counts are not the check. The certified badge is."*

The Jamal "Premium Funnel Pro" story from the chapter is a good 20-second retelling
here if you have the time. Skip it if `⏱` says 0:26 already.

---

## PART 6 — The accessibility checklist (⏱ 0:26–0:30)

**Frame it:** *"This is the part most reports skip and should not. Four checks. You
walk them at the **end**, like a pre-flight checklist — you do not hold them in your
head while building."*

Walk all four on screen, fast, on the table or card:

1. **Alt text.** Select the table → **Format pane** → **General** → **Alt text**.
   Type a real sentence: `Sales Amount by product category — Bikes highest at
   $94.6M, Clothing lowest.` *"Describe what it says, not that it is a table."*
2. **Tab order.** **View** tab → **Show panes** → **Selection** → **Tab order** tab.
   Show that you can drag the visuals into reading order.
3. **Color contrast.** Switch to the browser tab with the WCAG checker open. Paste
   the navy `#1B2A47` and white `#FFFFFF`. *"AA wants 4.5:1 for body text. This
   pair clears it easily."*
4. **Screen-reader title.** Back in Power BI, **Format pane** → **General** →
   **Title** → confirm it reads something descriptive, not blank. *"A blank title
   makes a screen reader say only 'chart.' That helps no one."*

**Close the demo:** *"The data was right when we started. Thirty minutes of
formatting is the difference between a board glancing at it and a board acting on it.
In Guided Practice you do these moves yourselves. In Lab 4 on Thursday you do them
graded, on different fields — Sales Territory, Subcategory, Country."*

---

## Instructor answer key — questions students ask in this demo

**"Why did my visual not change color when I applied the theme?"**
Power BI sometimes waits for a re-render trigger on a visual. Click the visual once
to give it focus, then click an empty part of the canvas. It redraws.

**"What is the difference between Gradient and Rules again?"**
Gradient = smooth color across a continuous amount; use it when *how much* matters.
Rules = explicit bands you define; use it when the value is judged against a
threshold. If a student can say "gradient for amounts, rules for thresholds," they
have it.

**"Do we have to write the DAX measure for Field Value in the lab?"**
No. Lab 4 uses Gradient and Rules only. Field Value is named for awareness and for
the PL-300 exam — it is not a graded build this week.

**"Is an uncertified custom visual always dangerous?"**
No — uncertified is not the same as unsafe. But certified is the *floor* for a report
that touches real or confidential data, because the badge means Microsoft audited it.
For a quick personal report, uncertified can be fine.

**"Which contrast number do we need — 4.5 or 3?"**
4.5:1 for normal body text, 3:1 for large text, under WCAG AA. If a student only
remembers one number, 4.5:1 is the safer one to remember.

---

## Do / Don't for the embedded tutor or co-instructor

**Do:**
- Repeat the "select → property → fx → style → OK" pattern every time conditional
  formatting comes up. Repetition is the teaching.
- Let the three-second silence in Part 1 actually happen. It does the framing.
- Name the silent-failure traps (theme not re-rendering, hex with no hash) out loud
  even though they are not being demoed — students hit them in the lab.

**Don't:**
- Don't open a JSON theme file in an editor. It is not a tested skill and it eats
  five minutes.
- Don't install an AppSource visual live. The gallery load is slow and unpredictable
  on classroom wifi, and a failed install mid-demo reads as "this is fragile."
- Don't drift the demo onto Lab 4's fields. If a student asks "can we do this on
  Sales Territory?", the answer is "that is exactly Thursday's lab — same moves, your
  hands."

---

*End of Guided Demo 05.*
