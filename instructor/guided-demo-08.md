# Guided Demo 08 — Making the Report Analyze

**Course:** CAP2743C — Power BI: Data Visualization and Analysis
**Session:** Class 8 · Thursday, June 4, 2026 · Block A
**Chapter:** Chapter 5 — Insights That Tell a Story
**Demo length:** ~35 minutes (instructor-led; students watch, do not build along)
**Dataset:** AdventureWorks (`AdventureWorks_Sales.xlsx`, already loaded)

> **⚠️ HEAVY SESSION.** The handoff flags Session 8 as a heavy cognitive-load
> session, and it is: Chapter 5 carries the Analyze feature, the Analytics pane,
> *and* the two skills new for the January 2026 PL-300 exam — visual calculations
> and Copilot narratives. This demo runs ~35 minutes instead of the usual 30, with
> an extra breath built in. Do not try to compress it back to 30. If anything must
> be cut, cut the Play Axis (Part 4b) — it is the most trimmable.

---

## How to run this demo

Instructor-led walkthrough. Students watch and take notes — they do **not** build
along. The hands-on follow-along is Guided Practice and Lab 7. Pace markers (`⏱`)
assume a 35-minute run.

The chapter's own framing is the spine of the whole demo, so open with it and keep
returning to it: a report that only **shows** leaves three questions unanswered —
*is this normal, why did it change, what comes next*. Every feature today answers one
of those three. Say that sentence at the top and name which question each feature
answers as you reach it.

**Field discipline note (read before class):** this demo uses **Sales Amount by
Month** as its main chart and a **Month table** for the visual calculation. Lab 7
deliberately uses different fields — Analyze on a **Sales by Quarter** chart, a
**Top N on Reseller**, a visual calculation on a distinct table. The graded lab is
new application, not a replay. Do not improvise the demo onto Lab 7's fields.

---

## What students should leave the demo able to picture

1. The **Analyze feature** is a right-click that has Power BI explain a change — it
   *narrows the search*, it does not prove cause.
2. The **Analytics pane** adds reference lines and a **forecast** — and a forecast
   is always shown *with* its confidence band.
3. A **visual calculation** is DAX written *on a visual*, computed on the visual's
   own rows — different from a measure, which lives in the model and travels.
4. **Smart Narrative / Copilot** drafts the report's summary in words — and the
   analyst, not Copilot, owns the final text.

---

## Setup before students arrive

1. Open Power BI Desktop with `AdventureWorks_Sales.xlsx` loaded, `AW-Demo-Navy`
   theme applied.
2. Build a page named **`Demo 8`** with two visuals:
   - A **Column chart**: `Date` (set to month level) on the X-axis, `Sales Amount`
     on the Y-axis. This is the chart you will run Analyze on.
   - A **Line chart**: `Date` on the X-axis, `Sales Amount` on the Y-axis. This is
     the chart you will add a constant line and a forecast to.
3. Add a second visual area / blank space for the **Table** you build in Part 5
   (`Date` at month level + `Sales Amount`).
4. **Confirm before class which Analyze result the data gives.** Right-click a
   low month → Analyze → Explain the decrease, and *see what Power BI returns* on
   the actual AdventureWorks data. Do not promise the class a specific factor you
   have not verified live — Analyze results depend on the model. Know your result
   before you stand up.
5. **Copilot check (do this the day before, not live):** confirm whether the
   classroom tenant has **Copilot enabled**. If it does, you can demo the Copilot
   narrative option. If it does not, you will demo **Smart Narrative** instead and
   *describe* Copilot. Either is fine — but know which one before class so you are
   not discovering it on the projector. See Part 6.

> 💡 **Why verify the Analyze result beforehand:** the chapter's story has Camila
> find "one German reseller," but that is the textbook's narrative. Your live
> AdventureWorks model may rank factors differently. The teaching point is the
> *feature*, not a specific answer — so demo whatever your data actually returns,
> honestly.

---

## PART 1 — From showing to finding (⏱ 0:00–0:04)

**Tell the opening briefly** (it is the chapter's opening — Marcus at the conference
screen). The shape of it:

*"Marcus had the interactive report. His managers could filter it themselves. Then
he pointed at a dip in the Q3 line and said: every manager can see that dip now —
that is the part you built. But not one of them can tell me why it dropped. I do not
want to send someone off to investigate for two days. I want the report to do the
first pass. Show me the dip, then tell me where to look."*

**Land the framing — write it up and leave it up:**

> A report that only **shows** leaves three questions:
> *Is this normal? · Why did it change? · What comes next?*
> Today's features answer those three.

*"As we hit each feature, I will tell you which of the three it answers."*

---

## PART 2 — The Analyze feature: why did it change? (⏱ 0:04–0:11)

**Frame it:** *"This one answers* ***why did it change.*** *It is a right-click."*

**See it → Name it → Find it → Do it:**
- **See it:** on the column chart of Sales Amount by Month, each column is a data
  point you can right-click.
- **Name it:** the right-click menu has an **Analyze** submenu — *Explain the
  increase*, *Explain the decrease*, *Find where this distribution is different*.
- **Find it:** right-click the column for a month that dropped → **Analyze**.
- **Do it:** choose **Explain the decrease**. Power BI opens a pop-up with candidate
  explanations drawn as waterfall and scatter charts. Page through them with the
  arrows. When one explains the drop, click the small **+** to add that chart to the
  page.

**Land it honestly:** *"Power BI just ran a machine-learning pass across every table
related to this chart and ranked what moved the number. Last year this kind of answer
took Marcus's team two days of spreadsheets."*

**Then the critical caveat — say it slowly:** *"But read what it gave us carefully.
Analyze reports statistical* ***contribution*** *— what the drop* ***coincided
with.*** *It does not know* ***cause.*** *It found the factor; it did not find the
reason. That last step — checking the finding against reality — stays human. Analyze
narrows two days to one chart. It does not close the case."*

> 🛑 **Stop and check (say it aloud):** "If the pop-up says it could not find an
> explanation, the model has no related table carrying the answer. Analyze can only
> reach fields connected to the visual through a relationship."

---

## PART 3 — 💜 Take a breath (⏱ 0:11–0:12)

**Say this:** *"One feature down, and it answered* ***why did it change.*** *Quick
reset — this is a heavy session, so we will breathe twice today, not once."*

A real one-minute pause.

---

## PART 4 — The Analytics pane: is this normal? what next? (⏱ 0:12–0:21)

**Frame it:** *"This pane answers the other two questions —* ***is this normal*** *and*
***what comes next.*** *A bare number floats. $4.1M means nothing until you know the
target was $3.8M. The Analytics pane puts the* ***compared to what*** *right on the
chart."*

### 4a. A constant line and a forecast

**See it → Name it → Find it → Do it:**
- **See it:** select the **line chart** of Sales Amount by month. The Visualizations
  pane shows three tabs across the top.
- **Name it:** the third tab — a magnifying glass over a line — is the **Analytics**
  pane.
- **Find it:** Visualizations pane → **Analytics** tab.
- **Do it — constant line:** open the **Constant line** section → **Add** → set the
  value to a target, e.g. `5000000`. A target line lands on the chart. *"Now the dip
  is read against the plan, not in a vacuum."*
- **Do it — forecast:** open the **Forecast** section → **Add**. Set *Forecast
  length* to 3 months, *Confidence interval* to 95%. The chart extends with a
  projected line inside a shaded band.

**Land the forecast hard — this is a tested idea:** *"See that shaded band? That is
the honest part. South Florida knows this picture — every hurricane season the
forecast cone widens the further out it reaches, because uncertainty grows with
distance. The band is the cone. You* ***always*** *present the forecast with its
band. The line alone overstates how sure the report is."*

> ⚠️ **Common mistake to name aloud:** removing the confidence band to make the
> projection "look more authoritative." That is backwards — it makes the report
> lie about its own certainty. The band stays.

### 4b. The Play Axis — fast, trimmable

**Say this, demo only if time allows:** *"One more — the Play Axis. On a scatter
chart, drop a date field into the Play Axis well and a play button appears. Press it
and the bubbles travel across time, each leaving a trail. It is time-lapse for data
— three years of history in eight seconds."* If `⏱` is past 0:21, just name it and
move on; it is the trimmable piece of this demo.

---

## PART 5 — Visual calculations: the new exam skill (⏱ 0:21–0:29)

**Flag it plainly:** *"This next one is new for the January 2026 PL-300 exam, and it
is the one most worth your patience. It trips people up — not because it is hard, but
because it sits somewhere new. Slow down with me here."*

**Frame the difference — this is the whole concept:**

> A **measure** is computed against the model's tables, *before* the visual is drawn.
> A **visual calculation** is computed *afterward* — on the visual's own grid of
> rows that are already sitting in front of you.

*"Because a visual calculation can see the visual's rows, in order, it can do things
measures find awkward — a running total down the rows, the change from the row above,
a moving average. Row-aware math. The visual is where the rows live."*

**See it → Name it → Find it → Do it:**
- **See it:** select the **table** visual showing Sales Amount by Month.
- **Name it:** the control that adds a calculation onto the visual is **New visual
  calculation**.
- **Find it:** with the table selected → **Home tab → New visual calculation**. An
  edit screen opens showing the visual's data as a grid with a formula bar.
- **Do it:** in the formula bar, type:
  `Running Total = RUNNINGSUM([Sales Amount])`
  Confirm. Close the edit screen. The table now carries a Running Total column that
  accumulates down the months — one line of DAX, living on this visual only.

**Land it with the chapter's image:** *"The company handbook versus a note in the
margin. A measure is a formula in the handbook — written once, used by every team,
in force everywhere. A visual calculation is a number you work out in the margin of
the one page in front of you — quick, shaped to that page, and it does not exist
anywhere else. The deciding question is one sentence:* ***does this result need to
leave the visual?*** *If yes, measure. If no, visual calculation."*

> ⚠️ **Common mistake to name aloud:** expecting a visual calculation to be reusable.
> It is not. It does not appear in the Data pane, no other visual can use it, no
> measure can reference it. Need the same figure on a second visual? You write it
> again there. When a result must travel, it has to be a measure.

---

## PART 6 — 💜 Breath, then Smart Narrative / Copilot (⏱ 0:29–0:35)

**Quick breath first (~30 sec):** *"Heavy session, second reset. If the
measure-versus-visual-calculation line still feels blurry, that is the expected place
to be — professional developers worked through this same confusion when visual
calculations arrived. Hold the one question: does it need to leave the visual?"*

**Then the last feature.** *"A chart shows a number. It does not say a sentence.
Someone still has to write 'sales fell 6% in Q3.' Two features now draft that
sentence — both new territory for the 2026 exam."*

**Name the two — they are not the same tool:**
- **Smart Narrative** — a built-in visual, rules-based and template-driven. Drop it
  on the page, it writes a plain-prose summary with dynamic values that update when
  the page is filtered. No special licensing.
- **Copilot narrative visual** — powered by Copilot, more fluent and flexible, can
  answer a request like "summarize this for an executive." **Requires Copilot
  enabled in the tenant** by an administrator.

**Demo whichever your tenant supports** (you checked this before class — see Setup):
- **Do it — Smart Narrative:** with no visual selected, click the **Smart narrative**
  icon in the Visualizations pane. Power BI generates a text box summarizing the
  page. **Read every sentence out loud.** Click into the text to show it is
  editable; show the **+ Value** control for adding a dynamic value.

**Land the critical point — tell the "sentence Copilot got wrong" story short:**
*"Camila added a Copilot narrative and read it. Fluent, well organized, numbers
correct. One sentence stopped her: 'Sales fell in Q3 because of reduced demand in
Germany.' The numbers were right. The word* ***because*** *was not — one reseller had
paused ordering during a warehouse move; demand had not fallen. Copilot saw the drop
and reached for the most natural-sounding cause. It wrote a confident sentence about
something it could not know."*

*"The BI Center's rule is one line:* ***Copilot drafts, an analyst signs.*** *No
generated narrative reaches a stakeholder until a named analyst has read every
sentence and put their name on it. Copilot is excellent at the draft — structure,
phrasing, pulling the right numbers. It cannot be trusted with* ***because.***"

**Close the demo:** *"Four features, three questions. Analyze answered* ***why did it
change.*** *The Analytics pane answered* ***is this normal*** *and* ***what comes
next.*** *Visual calculations did row-aware math on the visual. And the narrative
drafted the summary — for a human to check and sign. In Lab 7 you build this
analytics-and-narrative layer yourselves, graded, on different fields."*

---

## Instructor answer key — questions students ask in this demo

**"Did the Analyze feature prove that reseller caused the drop?"**
No — and this is the most important point in the session. Analyze reports
statistical *contribution*: what the drop coincided with. It does not establish
cause. It narrows two days of searching to one chart; the human still confirms the
reason. If a student leaves thinking Analyze "finds the cause," re-correct it.

**"What's the difference between a measure and a visual calculation?"**
A measure is computed in the model before the visual draws, and it travels to every
visual. A visual calculation is computed on the visual's own row grid, after, and it
stays on that one visual. The deciding question: does the result need to leave the
visual? Yes → measure. No → visual calculation.

**"Why keep the forecast's shaded band? It looks messy."**
The band is an honest statement of uncertainty — the hurricane cone. Removing it does
not make the forecast better; it makes the report overstate how sure it is. The band
stays, always.

**"Can I use Copilot's narrative as the final text?"**
Not as-is. Copilot drafts; an analyst reviews, corrects, and signs. It is reliable
for structure and numbers, unreliable for *because* — it will phrase a guess as
confidently as a fact. The review step is what makes the output trustworthy.

**"Is Smart Narrative the same as Copilot?"**
No. Smart Narrative is rules-based and template-driven, needs no special licensing,
and ships with Power BI. The Copilot narrative visual is powered by a language model,
is more fluent, and requires Copilot enabled in the tenant. Two different tools that
do a similar job.

**"Quick Insights — is that in this demo?"**
Not demoed live — it is a Power BI Service feature (it lives at app.powerbi.com, not
in Desktop). The chapter covers it in 5.5. If asked: it auto-generates analyses from
a whole model, and every result is a *lead to verify*, not a finding to present —
the metal-detector-on-the-beach idea. Lab 7 / HW may reference it conceptually.

---

## Do / Don't for the embedded tutor or co-instructor

**Do:**
- Keep returning to the three-question frame — *is this normal, why did it change,
  what comes next*. Name which question each feature answers. It is the spine.
- Say the Analyze caveat — contribution, not cause — more than once. Students will
  over-trust the feature if it is said only in passing.
- Let both breaths actually happen. This is a heavy session by design; the resets
  are load-bearing, not filler.
- For visual calculations, slow down and let the measure-vs-visual-calc question
  land. It is the new exam skill and the most-confused idea in the chapter.

**Don't:**
- Don't promise a specific Analyze result you have not verified on the live model.
  Demo what the data actually returns.
- Don't try to demo Copilot if the tenant does not have it enabled — you will get a
  greyed-out option and lose the room. Demo Smart Narrative and *describe* Copilot.
- Don't compress this back to 30 minutes. If time is short, cut the Play Axis, not
  the visual-calculations section — the latter is tested.
- Don't drift onto Lab 7's fields. If asked "can we do this on Reseller?", the
  answer is "that is exactly the lab."

---

*End of Guided Demo 08.*
