# Guided Demo 09 — AI-Powered Analysis

**Course:** CAP2743C — Power BI: Data Visualization and Analysis
**Session:** 9 · Tuesday, June 9, 2026 · Block A
**Chapter:** 6 — AI-Powered Analysis (Patterns, Anomalies, and Copilot)
**Demo length:** ~35 minutes — **flagged Heavy** (new Copilot content; two breaths)
**Dataset:** AdventureWorks — `AdventureWorks_Sales.xlsx`
**Paired graded work:** Lab 8 — AI Visuals (Block B, same day)

---

## How to run this demo

This is an **instructor-led** demo. You build; students watch. **Students do not build
along.** They build the same skills — on different fields — in Lab 8 this afternoon.
Say that out loud at the start: *"Watch how the moves work now. You drive in the lab."*
It lowers the pressure and lets them follow the reasoning instead of chasing your clicks.

Project Power BI Desktop. Move at the ⏱ markers. The two 💜 breaths are not optional —
Chapter 6 is dense, and Section 6.7's ethics close lands harder if students arrive at it
depleted.

This is a **Heavy** demo for one reason: Part 3 covers Copilot, which is **new for the
January 2026 PL-300 exam**. Give Part 3 its full time even if Parts 1–2 run long; cut
depth from the clustering walk-through before you cut Copilot.

---

## Setup before students arrive

Do all of this before class. The demo time is for the skill, not for loading data.

1. **Open the model.** Launch Power BI Desktop, open `AdventureWorks_Sales.xlsx`'s
   report, start a fresh report page named `Demo 09`.
2. **Confirm the calendar field.** Use the plain calendar **`Year`** column on the Date
   table for any date axis — **not** Fiscal Year (FY2017 has no sales and will distort
   the anomaly line).
3. **Pre-build the scatter for Part 1.** A scatter chart: **Product** in the details
   well, **Sales Amount** on the X axis, **Order Quantity** on the Y axis. Have it on the
   page, sized large.
4. **Run every AI feature once, live, before class.** This is non-negotiable. Clustering,
   anomaly detection, Key Influencers, and the Decomposition Tree all return
   *model-dependent* results. Run each one on the live AdventureWorks model and note
   what it actually returns. **Demo the real output — never the chapter's narrative.**
   The chapter's stories (the Northwest helmet decline, the second-year reseller churn,
   Jamal's two models) are illustrations, not predictions about this dataset.
5. **Confirm the Explain-by field names.** Parts 2–3 use **Category** (in the *Product*
   table), **Region** and **Country** (in the *SalesTerritory* table), and **Channel**
   (in the *Sales* table). These names are verified against the model — but confirm them
   on screen during setup so your spoken cues match the Data pane exactly.
6. **Check the Copilot tenant status the day before.** Copilot must be enabled by an
   admin on supported capacity. If it is enabled, demo Part 3 live. If it is not, use the
   Part 3 fallback (open the pane, describe the two abilities) — Lab 8 does not depend on
   Copilot, so a disabled tenant does not break the day.
7. **Card visual / terminology note.** Power BI's late-2025 update replaced the old Card
   with a new card (the icon carries a **lightning bolt**), and the "Fields pane" is now
   the **Data pane**. Use the current names throughout — students see them on screen.

---

## Field discipline note

Demo 09 and Lab 8 deliberately use **different fields** so the lab is new application,
not a replay of what students just watched.

| Feature | Demo 09 uses (you, now) | Lab 8 uses (students, Block B) |
|---|---|---|
| Clustering (scatter) | **Product** — Sales Amount × Order Quantity | **Reseller** — Sales Amount × Total Product Cost |
| Anomaly detection (line) | **Sales Amount** by Month | **Order Quantity** by Month |
| Decomposition Tree | Analyze **Sales Amount** — Category / Country / Channel | Analyze **Order Quantity** — Group / Subcategory / Year |
| Key Influencers | Analyze **Sales Amount** — Category / Region / Channel | *(not graded in Lab 8 — demoed only)* |
| Q&A | products by sales amount | order quantity by country |

If a student in the lab says "we did this in the demo," the honest answer is: *you saw
the move; you have not done it on these fields. Same skill, new data — that is the job.*

---

## What students should leave the demo able to picture

1. **Each AI visual answers a different question.** Clustering and anomaly detection
   *find* what stands out; Key Influencers explains *what moves* a number; the
   Decomposition Tree breaks a number *into its parts*; Q&A answers a *typed* question;
   Copilot *drafts and summarizes*.
2. **Every AI result is a draft to verify, never a finding to forward.** The five checks
   from Section 6.7 sit between an AI answer and a decision — every time.
3. **Where each feature lives.** AI visuals are placed on the canvas from the
   Visualizations pane; anomaly detection is in the **Analytics** tab of an existing line
   chart; Copilot opens from the **Home** ribbon.

---

## PART 1 — Find the Unusual: Clustering and Anomaly Detection

⏱ **~10 minutes**

Open with the chapter's framing: Chapter 5's tools all needed *you* to aim them. These
features do not wait to be aimed — they sweep the whole dataset and raise a hand.

### Clustering — letting the data draw the groups

Bring up the pre-built scatter (Product · Sales Amount × Order Quantity). Each dot is one
of the 397 products.

- **See it.** The scatter is a cloud of dots; some sit together, some sit apart.
- **Name it.** The tool that finds groups inside that cloud is **Automatically find
  clusters**.
- **Find it.** Hover the scatter chart → click **More options (...)** in its header →
  **Automatically find clusters**.
- **Do it.** Power BI proposes a number of clusters. Accept the proposal. It adds a new
  **Cluster** field and recolors the dots by cluster.

Say plainly: *"I did not pick those groups. I did not write a rule. The data's own shape
decided."* Then deliver the COMMON MISTAKE from 6.2 out loud — **a cluster is a
hypothesis, not a finding.** Power BI found products that sit near each other
mathematically; whether they share anything a business cares about is a separate
question, and it is yours.

> Contrast with the other two ways to make a category, so the trio is fixed:
> **grouping** is you picking the members by hand; **binning** is you setting a numeric
> rule; **clustering** is the machine. Who decides the buckets is the whole distinction.

### Anomaly detection — a flag on a single suspicious month

Switch to a line chart of **Sales Amount by Month** (use calendar `Year` → Month).

- **See it.** Select the line chart. The Visualizations pane shows its three tabs —
  **Build**, **Format**, **Analytics**.
- **Name it.** The Analytics tab has a section called **Find anomalies**.
- **Find it.** Visualizations pane → **Analytics** tab → **Find anomalies** → **Add**.
- **Do it.** Power BI shades an *expected band* along the line and drops a marker on any
  point that falls outside it. Click a flagged point to open its explanation pane, which
  ranks the factors associated with the anomaly.

Then deliver the STOP AND CHECK as a teaching beat, not a warning: a flagged point sits
clearly outside the shaded band. **If nothing is flagged, that is a finding, not a
failure** — the series stayed inside its expected range. (If *Find anomalies* is greyed
out, the chart's axis is not a continuous date.)

Close Part 1 by connecting it to the opening story: the Northwest helmet decline was
exactly an anomaly-detection problem — a slice no human would chart, that a line with
*Find anomalies* on would have flagged weeks early.

---

## 💜 TAKE A BREATH

⏱ **~2 minutes** — *first breath*

Stretch, look away from the screen, breathe. Two features, one job: **noticing.**
Clustering and anomaly detection both sweep the whole dataset and surface what stands
out. Neither one *judges* what it finds — that part is still ours, and it is coming.

---

## PART 2 — Explain a Number: Key Influencers and the Decomposition Tree

⏱ **~9 minutes**

Frame the pair before you build either one: two AI visuals, two different questions.
**Key Influencers** answers *what moves this number?* The **Decomposition Tree** answers
*what is this number made of?*

### Key Influencers — what moves the number

- **See it.** The Visualizations pane's grid of icons includes the Key Influencers icon.
- **Name it.** The **Key Influencers** visual.
- **Find it.** With no visual selected, click the **Key Influencers** icon in the
  Visualizations pane.
- **Do it.** Drag **Sales Amount** into the **Analyze** well. Drag **Category** (Product
  table), **Region** (SalesTerritory table), and **Channel** (Sales table) into the
  **Explain by** well. Read the ranked influencers it returns, then click the **Top
  Segments** tab — it finds *combinations* of factors that form a notably high or low
  group.

Read the result it actually produced (you ran this in setup, so you know what it says).
Then say the sentence the exam rewards: Key Influencers reports what is *associated with*
a metric. **Association is correlation, not proven cause.** It points; confirming *why*
is a separate human step.

### Decomposition Tree — what the number is made of

- **See it.** One Visualizations-pane icon is shaped like a small branching tree.
- **Name it.** The **Decomposition tree** visual.
- **Find it.** With no visual selected, click the **Decomposition tree** icon.
- **Do it.** Drag **Sales Amount** into **Analyze**. Drag **Category** (Product table),
  **Country** (SalesTerritory table), and **Channel** (Sales table) into **Explain by**.
  Click the **+** on the root node and pick a field to split by — *then* click **+**
  again and choose **High value**, letting Power BI pick the dimension that most explains
  where the number is high.

Show both moves explicitly: choosing the split yourself keeps you in control; **High
value** hands the choice to the AI. Both are valid. The tree is interactive — break it
apart, collapse it, follow a branch.

---

## 💜 TAKE A BREATH

⏱ **~2 minutes** — *second breath (Heavy demo)*

Fix one pair in memory before the last part. **Key Influencers — what moves this number?
Decomposition Tree — what is this number made of?** If the question is about cause and
effect, it is a Key Influencers question. If it is about breaking a total into parts, it
is a tree. The exam rewards telling them apart.

---

## PART 3 — Converse and Generate: Q&A and Copilot

⏱ **~12 minutes** — *the new exam content; protect this time*

### The Q&A visual — analysis from a typed question

- **See it.** One Visualizations-pane icon shows a question-mark speech bubble.
- **Name it.** The **Q&A** visual.
- **Find it.** With no visual selected, click the **Q&A** icon.
- **Do it.** In the text box, type `top 5 products by sales amount`. Power BI generates a
  bar chart. Change the text to `top 5 products by order quantity` — the chart updates
  live. Point at the **suggested questions** that appear below the box.

Make the dependency explicit: Q&A reads the **semantic model**. It understands *sales*,
*revenue*, *amount* when the model's fields are clearly named and **synonyms** have been
added. Name a column `f_amt_2` and Q&A is lost — and so is the audience. The model
underneath is what makes Q&A work.

### Copilot — drafting pages and summarizing the model

> **Tenant check.** Copilot must be enabled by an admin on supported capacity. You
> confirmed its status yesterday (setup step 6). Run whichever path matches.

**If Copilot is enabled — demo it live:**

- **See it.** The **Home** tab of the ribbon has a **Copilot** button near the right.
- **Name it.** It opens the **Copilot pane**.
- **Find it.** **Home** tab → **Copilot**.
- **Do it.** Type `Give me an overview of this model` and read the summary aloud. Then
  type `Create a page showing sales by territory` and review the page it drafts —
  out loud, visual by visual. Keep what works, name what you would fix, delete what
  misses. Treat both outputs as **drafts**.

**If Copilot is not enabled — describe it:**

Open the Copilot pane so students see where it lives, then describe the two abilities:
Copilot can **draft a report page** from a typed description, and can **summarize a
semantic model** in plain language. Tell them Lab 8 does not require Copilot, and they
will likely meet it in industry on a properly licensed tenant.

**Either way, deliver the Jamal "two models" point.** Copilot's model summary is only as
good as the model's metadata. Same data, two copies: the copy with cryptic names
(`Tbl1`, `M2`) summarized into gibberish; the copy with real names, descriptions, and
synonyms summarized into something a manager could read. *"Copilot did not get smarter.
The model did."* Preparing a clear model **is** the skill.

### Close — the five checks

End the demo on Section 6.7, briefly and seriously. Every feature in this demo finds
patterns and **cannot judge them**. Correlation is not cause. Biased data makes biased
output. Generative text sounds certain when it is wrong. Precision can be real and the
meaning still empty. Before any AI insight informs a decision, run the five checks: *does
it make business sense, is it correlation or cause, could the data be biased, can you
trace the numbers, would you sign your name to it.* The analyst owns the answer — not the
AI. Students apply this checklist directly in Lab 8's final phase.

---

## Instructor answer key

Likely student questions and the answers to give:

- **"Why did clustering give a different number of clusters than the chapter?"** Because
  clustering reads *this* data's shape, and the count depends on the data and the two
  axes chosen. The chapter's count is illustrative. The live model's answer is the real
  one.
- **"Is the Key Influencers result the cause?"** No. It reports *association* —
  correlation. Confirming a cause is a separate, human step. This is the single most
  important idea in the chapter.
- **"Find anomalies is greyed out — what's wrong?"** The chart's axis is not a continuous
  date. Anomaly detection needs a date axis.
- **"Nothing got flagged as an anomaly — did it fail?"** No. A clean line is a finding:
  the series stayed inside its expected range.
- **"Copilot isn't showing up / is greyed out."** Copilot must be enabled in the tenant
  by an administrator; it is not on every machine by default. Lab 8 does not require it.
- **"Decomposition Tree — should I pick the split or use High value?"** Either. Picking
  the field yourself keeps you in control of the question; High value lets the AI pick
  the dimension that explains the most. Use High value when you do not know which split
  is revealing.
- **"The Copilot summary came back full of `Tbl1` and `M2` — is Copilot broken?"** No.
  The model's metadata is cryptic. Fix the model's names and descriptions, not Copilot.
- **"Can Q&A answer anything?"** Only what the model can support. Its quality is the
  model's field names and synonyms. A vague model gives vague answers.

---

## Do / Don't — for the embedded tutor or co-instructor

Carlos does not stay for the tutoring block. Whoever runs it should hold these.

**DO**

- Run every AI feature on the live AdventureWorks model **before class** so the demo
  shows real output.
- Check the Copilot tenant status the day before, and have the fallback (open-and-
  describe) ready in case it is disabled.
- Let a "nothing flagged" anomaly result stand as a finding — do not hunt for a different
  chart that flags something just for show.
- Say the verification idea out loud while demoing — model the habit, do not just
  mention it at the end.
- Use the current terminology: the new card visual (lightning-bolt icon) and **Data
  pane**, not "Fields pane."

**DON'T**

- Don't present a Key Influencers bar or a Copilot paragraph as a proven fact. Both
  *look* finished; looking finished and being correct are unrelated.
- Don't promise the chapter's narrative results (helmet decline, second-year churn,
  Jamal's two models) — those are teaching stories, not predictions about this dataset.
- Don't let students build along. They watch here; they drive in Lab 8.
- Don't skip the second breath to buy time. If Parts 1–2 run long, trim the clustering
  walk-through — protect Copilot and protect both breaths.

---

*End of Guided Demo 09. Paired graded work: Lab 8 — AI Visuals, Block B.*
