# Guided Demo 04 — The Core Visual Toolkit, Part 2

**Course:** CAP2743C — Power BI: Data Visualization and Analysis
**Session:** 4 of 12 · Thursday, May 21, 2026
**Audience:** Instructor (live-demo walkthrough — not student-facing)
**Tool:** Power BI Desktop
**Dataset:** AdventureWorks Sales
**Chapter:** [Chapter 2 — The Core Visual Toolkit](https://github.com/c-marq/cap2743c-power-bi-viz/blob/main/textbook/ch02-core-visual-toolkit.md)

---

## Purpose

This is the Block A live-demo script for Class 4. It covers the back half of the
Chapter 2 toolkit: the **relationship family** (scatterplot), the **exact-numbers
family** (table and matrix), the **map family** (filled and bubble maps), and the
**single-value family** (cards and KPI).

The rhythm stays build-watch-build-replicate. Scatter and map get a lighter touch
— the chapter treats them as "recognize it" visuals — while the matrix and the
card get full hands-on builds, since those are two of the four workhorses.

**Field choices are deliberately different from Lab 3.** This demo uses
**List Price vs Order Quantity, Category x Year, and Country**. Lab 3 builds a
filled map on Region/State and KPI cards on different measures. Same skills,
different specifics.

---

## Pre-flight (before class)

1. Open Power BI Desktop with the AdventureWorks model loaded.
2. **Save As** a working copy — `Session04_Demo.pbix`.
3. Confirm **Report View** and the `Total Sales` measure.
4. Have a fresh page ready, or add one with the **+** on the page tab strip.
5. Chapter open in a second tab for the encoding-hierarchy callbacks.

---

## Pacing (~45 min total — heavier session, watch the clock)

| Part | Time | What happens |
|---|---|---|
| Demo 1 — Scatterplot (recognize-it) | ~8 min | You build + narrate, students watch |
| Demo 2 — Matrix | ~14 min | You build + narrate, students replicate |
| Demo 3 — Filled map (recognize-it) | ~9 min | You build + narrate, students watch |
| Demo 4 — Card row | ~10 min | You build + narrate, students replicate |
| Transition to lab | ~4 min | Recap, then long break, then Lab 3 |

---

## Demo 1 — Scatterplot: Do Price and Volume Move Together? (~8 min)

The chapter treats scatter as recognition, not configuration — so this is a
quick build, students watch.

**Set the scene:**

> *"Every visual we built Tuesday charted ONE measure across categories or time.
> This family is different — it charts the relationship BETWEEN two measures.
> The question: do our higher-priced bikes sell in lower volume? That is a
> relationship question, and the tool is the scatterplot."*

**Build:**

1. New visual: click the **Scatter chart** icon in the Visualizations pane.
2. From **Product**, drag **List Price** into the **X-axis** well.
3. From **Sales**, drag **Order Quantity** into the **Y-axis** well.
4. From **Product**, drag **Product** into the **Values** well — one dot per product.

**What students see:** A cloud of dots, each one a product, placed by price and quantity.

**Narration:**

> *"Read the shape. If the cloud drifted down-and-right — high price, low volume —
> that would confirm Marcus's hunch. If it's a shapeless blob, the two measures
> don't move together. The scatterplot's whole job is turning 'is there a
> relationship' into a shape your eye can judge. You won't build many of these,
> but you need to recognize one on sight — and on the PL-300 exam."*

🛑 **Students watch — no replication.** Recognition is the goal.

---

## Demo 2 — Matrix: Sales by Category and Year (~14 min)

This one gets a full hands-on build. The matrix is a workhorse — one of the four
visuals the chapter says do 80% of the work.

**Set the scene:**

> *"Sometimes the reader doesn't want a shape — they want the NUMBER, exact, to
> paste into an email. That's the table and the matrix. A table is a flat grid.
> A matrix is the powerful one: row groups, column groups, subtotals. If you've
> built a PivotTable in Excel, the matrix is its Power BI cousin."*

**Build:**

1. New visual: click the **Matrix** icon in the Visualizations pane.
2. From **Product**, drag **Category** into the **Rows** well.
3. From **Date**, drag **Year** into the **Columns** well.
4. From **Sales**, drag **Total Sales** into the **Values** well.

**What students see:** A grid — product categories down the side, years across the top, Total Sales in every cell, with row and column subtotals.

**Narration:**

> *"Look at what the matrix gives you that a chart can't: the exact figure in
> every cell, plus subtotals down the side and across the top. No length to
> misjudge, no area to misread — the number is the number. That's the matrix's
> superpower and its trade-off. It makes zero encoding compromise, but the reader
> has to READ it, not glance at it. A matrix can't show a trend as a shape.*
>
> *That's why Chapter 2 says tables and charts work as a PAIR — the chart shows
> the pattern, the matrix backs it with exact figures. A good report page often
> has both."*

**One quick enhancement — show the drill-down:**

5. Hover the matrix; in its top corner the drill controls appear.
6. Click into a Category row to show it expands. Note: with Category alone there's
   one level, but mention that adding Subcategory under Rows creates a drillable
   hierarchy.

🛑 **Pause for student replication.** Circulate. Common stuck points:
- **Built a Table instead of a Matrix** — Table has no Columns well. Point out the difference; they need Matrix.
- **`Year` not found** — it's the calendar Year column on the Date table. If a student's model only has the date hierarchy, have them use the Year level.
- **Numbers look wrong / not aggregating** — they dragged a raw column, not the `Total Sales` measure.

---

## Demo 3 — Filled Map: Where Is Revenue Happening? (~9 min)

Recognition-level, like the scatter. Students watch.

**Set the scene:**

> *"When a field holds geography and the question is literally 'where' — the map
> family answers it. Two kinds: a filled map shades whole regions, a bubble map
> drops sized circles on points. Watch the filled one."*

**Build:**

1. New visual: click the **Filled map** icon (a shaded-region globe icon).
2. From **Sales Territory**, drag **Country** into the **Location** well.
3. From **Sales**, drag **Total Sales** into the **Tooltips** well (and Power BI
   will shade by it — or drag into the color/legend well if the version exposes it).
4. The map shades the six AdventureWorks countries, darker for higher sales.

**What students see:** A world map with the sales countries shaded by revenue.

**Narration:**

> *"Here's the honest assessment Chapter 2 makes you give every map. A map spends
> a LOT of canvas, and it shades or sizes by area and color — low on the accuracy
> hierarchy. Use a map only when the geographic PATTERN itself is the insight —
> the clustering, the spread, the empty regions. If the real question is just
> 'which three countries sold the most,' a sorted bar chart answers it more
> precisely in less space. The map is for 'where,' not for 'rank.'"*

🛑 **Students watch — no replication.** Recognition is the goal. Maps can also be
slow to render or need a network connection — another reason this one is a watch.

---

## Demo 4 — Card Row: The Headline Numbers (~10 min)

Full hands-on build. The card is the fourth workhorse.

**Set the scene:**

> *"Last family. Some numbers are important enough to stand alone — total revenue,
> order count. They don't need a chart. They need to be big, clear, unmissable.
> That's the card."*

**Build:**

1. New visual: click the **Card** icon. (Note for students: in current Power BI the
   card icon carries a small lightning bolt — Microsoft updated the card visual in
   late 2025. It works the same: one field in, one number out.)
2. From **Sales**, drag **Total Sales** into the **Data**/Fields well.
3. The card shows one large number — total revenue across the whole model.
4. Build a second card: **Total Orders** (or Order Quantity, depending on the model's measures).
5. Build a third card: **Average Order Value** if the measure exists; otherwise a second meaningful measure.
6. Line all three cards in a row across the top of the page, equal in size.

**What students see:** Three big headline numbers in a tidy row.

**Narration:**

> *"This is exactly the swap Camila made on Marcus's dashboard — she replaced two
> side-by-side pie charts with a row of cards. Chapter 2's rule for the
> single-value family: the card wins for almost every 'one number' job. The KPI
> visual is the card's cousin for when the number has a TARGET. And the gauge —
> the chapter calls it the spoke key of this family — wastes canvas and encodes
> by angle. A row of cards beats a row of gauges every time."*

🛑 **Pause for student replication.** Circulate. Common stuck points:
- **Card shows a tiny number like 1, or a giant raw count** — wrong field. They need the `Total Sales` measure, not a Key column.
- **Can't find the card icon** — it's the one with the lightning bolt now. Reassure them it's the right one.
- **Multi-row card confusion** — if a student grabs the multi-row card, show the difference; the demo wants three single cards.

---

## Transition to the lab

> *"You've now seen the whole toolkit — all seven families across two sessions.
> Today's lab puts the geography and single-value families in your hands: Lab 3
> is a filled map plus a row of KPI cards. Then Homework 1 over the weekend asks
> you to assemble six visual types into one report — your first full gallery."*

Then: long break, then **Lab 3 — Maps & KPI Cards** in Block B.

---

## Safety notes

- This is a heavier session — four demos. If the clock is tight, Demo 1 (scatter)
  and Demo 3 (map) are the compressible ones; they're recognition-level and the
  chapter reinforces them in text.
- Maps need a network connection and can render slowly. If the map fails to draw,
  don't burn time debugging live — describe it, show the chapter figure, move on.
- The matrix and card builds are the ones students must leave able to do — Lab 3
  depends on the card skill directly. Protect those two.

---

*CAP2743C · Guided Demo 04 · Summer A 2026 · Instructor copy*
