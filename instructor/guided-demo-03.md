# Guided Demo 03 — The Core Visual Toolkit, Part 1

**Course:** CAP2743C — Power BI: Data Visualization and Analysis
**Session:** 3 of 12 · Tuesday, May 19, 2026
**Audience:** Instructor (live-demo walkthrough — not student-facing)
**Tool:** Power BI Desktop
**Dataset:** AdventureWorks Sales
**Chapter:** [Chapter 2 — The Core Visual Toolkit](https://github.com/c-marq/cap2743c-power-bi-viz/blob/main/textbook/ch02-core-visual-toolkit.md)

---

## Purpose

This is the Block A live-demo script for Class 3. It covers the **comparison
family** (bar and column charts), the **time family** (line charts), and the
**part-to-whole family** (pie — and when to walk away from it).

The rhythm is build-watch-build-replicate: you build each visual slowly while
narrating, students watch, then they replicate it while you circulate.

**Field choices are deliberately different from Lab 2.** This demo uses
**Country, Month, and Subcategory**. Lab 2 uses Reseller, Region, and Date by
fiscal year. Same skills, different specifics — that is real transfer, not copying.

---

## Pre-flight (before class)

1. Open Power BI Desktop with the AdventureWorks model loaded.
2. **Save As** a working copy — `Session03_Demo.pbix` — so the starter stays clean.
3. Confirm you are in **Report View** (top icon, far-left sidebar).
4. Confirm the model: six dimensions connected to the Sales fact, `Total Sales` measure present.
5. Have the chapter open in a second tab for the encoding-hierarchy callbacks.

---

## Pacing (~40 min total)

| Part | Time | What happens |
|---|---|---|
| Demo 1 — Column chart | ~12 min | You build + narrate, students replicate |
| Demo 2 — Line chart | ~12 min | You build + narrate, students replicate |
| Demo 3 — Pie chart (the cautionary one) | ~12 min | You build, narrate the failure, students watch |
| Transition to lab | ~4 min | Recap, then long break, then Lab 2 |

---

## Demo 1 — Sorted Column Chart: Sales by Country (~12 min)

**Set the scene:**

> *"Chapter 2 opens with a tool wall — a pegboard of bicycle tools, each ground
> to fit one job. Our first tool is the workhorse: the column chart. The question
> it answers is comparison. Today's question: which COUNTRY sells the most for
> AdventureWorks? Six countries. Watch how fast the right tool answers that."*

**Build:**

1. Click an empty area of the canvas.
2. In the **Visualizations pane**, click the **Clustered column chart** icon — vertical bars, upper-left of the icon grid.
3. A blank chart frame appears. Keep it selected.
4. In the **Data pane**, expand **Sales Territory**. Drag **Country** into the **X-axis** field well.
5. Expand **Sales**. Drag **Total Sales** into the **Y-axis** field well.
6. The chart now shows six columns, one per country — but in default order.

**Sort it** (this is the teaching beat):

7. Click the **More options** button — the three dots **…** in the chart's top-right corner.
8. Point to **Sort axis** → choose **Total Sales**.
9. Open the **…** menu again → choose **Sort descending**.

**What students see:** Six columns, tallest to shortest, left to right. United States is the tallest by a wide margin.

**Narration:**

> *"Look at what just happened. Power BI grouped 121,000 rows into six country
> buckets, summed each, and now — because we sorted — the ranking is the first
> thing your eye lands on. That is the encoding hierarchy from Chapter 1 doing
> its job: position along the axis plus length of the bar, the two channels the
> eye reads most accurately.*
>
> *And the sort is not optional. Chapter 2 is blunt about this — an unsorted
> comparison chart makes the reader do the ranking work themselves. The whole
> point of a comparison chart is that the ranking is instant. If you leave it
> alphabetical, you have built a worse table."*

🛑 **Pause for student replication.** Circulate. Common stuck points:
- **Bars still alphabetical** — the sort didn't apply. Reopen **…** and confirm Sort axis is set to *Total Sales*, not *Country*.
- **Field in the wrong well** — Country in Y instead of X. Chart looks odd; show them the swap.
- **`Country-Region` from Customer instead of `Country` from Sales Territory** — both exist. The demo uses Sales Territory's `Country`.

---

## Demo 2 — Line Chart: Sales Over Time (~12 min)

**Set the scene:**

> *"New question, new family. Marcus asks: are sales growing or shrinking across
> the year? The keyword is 'across the year' — that is a time question. Time
> questions leave the comparison family and go to the line chart."*

**Build:**

1. Click an empty area of the canvas to deselect Demo 1's chart.
2. In the **Visualizations pane**, click the **Line chart** icon — looks like a zigzag.
3. A blank line chart appears. Keep it selected.
4. In the **Data pane**, expand **Date**. Drag **Month** into the **X-axis** field well.
5. From **Sales**, drag **Total Sales** into the **Y-axis** field well.
6. The chart now shows a line moving across the months.

**What students see:** A line tracing monthly sales — rises and dips, a visible seasonal shape.

**Narration:**

> *"Here is why a line, not columns. Chapter 2 makes the point with stone crab
> season — Miami has a rhythm, October to May, and every restaurant plans around
> it. AdventureWorks sells bikes, and bike sales have a rhythm too. The line
> chart makes that rhythm a SHAPE you can point at. The connecting line encodes
> rate of change as slope, and the eye reads slope well — a steep climb looks
> like growth because it IS a steep climb.*
>
> *Could I show twelve months as twelve columns? Technically yes. But Chapter 2's
> rule: if the horizontal axis is time and you care about the movement, use a
> line. A forest of columns asks the eye to compare heights one pair at a time.
> A line shows the whole trajectory at once."*

🛑 **Pause for student replication.** Circulate. Common stuck points:
- **Used `Date` instead of `Month`** — gives a daily line, very dense. Redirect to `Month`.
- **Line looks flat** — they may have dragged a Key field instead of `Total Sales`. Check the Y-axis well.
- **Drilled-down state** — if a student clicked into the chart, they may be one level deep. Show the "drill up" arrow.

---

## Demo 3 — The Pie Chart That Should Not Be (~12 min)

This demo is different. You build a pie **to show its failure** — it is the
chapter's central cautionary lesson, and seeing it live lands harder than reading it.

**Set the scene:**

> *"Last family for today: parts of a whole. The pie chart. Chapter 2 calls it
> the spoke key — a real tool, ground for one narrow job, reached for constantly
> for jobs it cannot do. Let me show you exactly where it breaks."*

**Build the pie that works:**

1. Click an empty canvas area.
2. In the **Visualizations pane**, click the **Pie chart** icon.
3. Expand **Product** in the Data pane. Drag **Category** into the **Legend** well.
4. Drag **Total Sales** into the **Values** well.
5. AdventureWorks has four product categories — the pie shows four slices.

**Narration:**

> *"Four slices. Bikes is clearly the giant. This is roughly the edge of where a
> pie still works — few slices, one clearly dominant. If the only message is
> 'Bikes is the big one,' a reader can see that."*

**Now break it:**

6. Remove `Category` from the Legend well (click the X next to it).
7. Expand **Product** and drag **Subcategory** into the **Legend** well instead.
8. The pie now explodes into many thin slices.

**Narration:**

> *"There it is. Chapter 2's colada story — eleven tiny cups of Cuban coffee, all
> close in size, and Marcus can't rank them. This is that, many times over. Ask
> the question a pie is supposed to answer: which subcategory is third-biggest?
> You can't tell. The area-and-angle encoding has completely failed.*
>
> *Now watch the fix."*

**The fix — same data, right visual:**

9. With the pie selected, click the **Clustered bar chart** icon in the Visualizations pane. The visual swaps type, keeping the data.
10. Open **…** → **Sort axis** → **Total Sales** → **Sort descending**.

**Narration:**

> *"Same data. Same question. But now every subcategory is rankable instantly,
> top to bottom. That is the lesson of the whole chapter in one swap: past two
> or three slices, the part-to-whole question is better answered by a sorted
> bar. The pie didn't fail because it's a bad chart — it failed because it was
> pointed at the wrong question."*

🛑 **Students watch this one — no replication needed.** It's a demonstration of a
principle, not a skill to drill. If time allows, have them call out the answer
to "which subcategory is third-biggest?" before and after the swap.

---

## Transition to the lab

> *"You've now seen all three families today — comparison, time, part-to-whole —
> and the question discipline that picks between them. In Lab 2 you do the
> choosing yourself: you'll get a set of business questions and decide which
> visual each one needs, then build them. Same skill you just watched, in your
> hands."*

Then: long break, then **Lab 2 — Visual Selection Practice** in Block B.

---

## Safety notes

- If a student's model is missing the `Total Sales` measure, it didn't carry
  over from their Chapter 1 file. Have a backup `.pbix` ready.
- The pie-explosion demo (step 7-8) is the memorable moment — don't rush it.
  Let the ugly chart sit on screen for a beat.
- If Block A runs long, Demo 3 can be shortened — the pie-breaks point can be
  made with Subcategory alone without the full bar-chart fix, since Lab 2 and
  the chapter both reinforce it.

---

*CAP2743C · Guided Demo 03 · Summer A 2026 · Instructor copy*
