# Guided Demo 11 — Production-Ready BI

**Course:** CAP2743C — Power BI: Data Visualization and Analysis
**Date:** Tuesday, June 16, 2026 · Block A
**Chapter:** 8 — Production-Ready BI (Workspaces, Security, and Governance)
**Demo length:** ~30 minutes — standard (one breath)
**Dataset:** AdventureWorks — `AdventureWorks_Sales.xlsx`
**Paired graded work:** Lab 10 — Row-Level Security Configuration (Block B, same day)

---

## How to run this demo

This is an **instructor-led** demo. You build; students watch. **Students do not build
along.** As in Chapter 7, **students do not have Power BI Service accounts** — so the
workspace, endorsement, refresh, and deployment-pipeline steps in this demo are
*watch-and-understand* content. They are on the PL-300 exam, so students see them and
answer questions about them; they do not click them.

One part is different. **Defining a Row-Level Security role is a Desktop skill** — and it
is exactly what students do themselves in Lab 10 this afternoon. So when you reach PART 2,
say plainly: *"This next part — the role and the View As test — is your lab. Watch how it
works; you will build your own version after the break."* That frames the demo as a
preview of their graded task, not a thing they have missed.

This chapter is a **governance** chapter, and governance lives in the cloud. The demo
hops between the **Power BI Service** (a browser at `app.powerbi.com`) and **Power BI
Desktop**, and every hop carries a **WHERE AM I?** marker — say it out loud each time.

Project both Power BI Desktop **and** a browser signed in to `app.powerbi.com`, ready to
alt-tab between them.

---

## Setup before students arrive

1. **Have a finished report open in Desktop.** It must contain at least one visual that
   breaks Sales Amount out by region — a **Sales Amount by SalesTerritory Region** bar
   chart — and a **Sales Amount card** (the new card visual, lightning-bolt icon), so the
   View As filter in PART 2 is visibly dramatic. Name it clearly, e.g.
   `Demo 11 — AdventureWorks Sales`.
2. **Confirm Power BI Service sign-in on the *instructor* machine.** Sign in to
   `app.powerbi.com` and confirm you can reach a workspace you are able to manage and
   publish into. The Service portions run on your machine only — students cannot follow
   them, and that is expected. If your sign-in fails, resolve it the day before, or fall
   back to prepared screenshots for PARTS 1 and 3.
3. **Have a second name ready for the access demo.** PART 1 and PART 2 both add a person —
   a colleague, a test account, or a security group. Know the name before class so you
   are not searching while students wait.
4. **Verify the Sales Amount total.** A clean card touching only the Sales table reads
   **$109,809,274.20**. If it does not, the model has a filter or relationship problem —
   fix it before class.
5. **Sensitivity labels and certification — awareness only.** If your tenant has not
   configured sensitivity labels in Microsoft Purview, or has not named certification
   reviewers, those controls will be greyed out. That is normal. Name them, describe
   them, and move on — do not block the demo trying to make them clickable.

---

## Field discipline note

Demo 11 and Lab 10 use **different regions** so the lab is new application, not a replay.
Lab 10 is **Desktop-only** (no Service access for students): students define and test
a Row-Level Security role, rather than assigning members or touching workspaces.

| Move | Demo 11 uses (you, now) | Lab 10 uses (students — Desktop only) |
|---|---|---|
| RLS role | `Southwest Region` role | `Northeast Region` role |
| RLS DAX filter | `[Region] = "Southwest"` | `[Region] = "Northeast"` |
| RLS Service half | you assign a member to the role in the Service | a written-response question (Phase 4) |
| Workspaces, endorsement, refresh, pipelines | demonstrated at awareness level | not in the lab |

The overlap students *do* repeat is **defining a role and testing it with View As** — you
demo it on the Southwest region here, they build it on the Northeast region in Lab 10.
Everything else in this demo — workspaces, member assignment, endorsement, refresh,
pipelines — is Service work the lab only references.

---

## What students should leave the demo able to picture

1. **A workspace is the back room; an app is the storefront.** Four **workspace roles**
   set who does what: a **Viewer** consumes, a **Contributor** builds but cannot publish,
   a **Member** publishes and shares, an **Admin** controls everything. Grant the *least*
   role that does the job.
2. **Row-Level Security has two halves.** The **DAX role filter** is defined in
   **Desktop**; the **member assignment** is done in the **Service**. RLS constrains
   **Viewers** — Members and Admins see all the data by design. **View As** tests the
   filter, not the assignment.
3. **Trust and reliability have their own tools.** **Promoted** vs **Certified**
   endorsement; **scheduled refresh** (a timetable), **incremental refresh** (big tables,
   recent rows only), a **gateway** (only when the source is on-premises); and a
   **dev → test → production** deployment pipeline.

---

## PART 1 — Workspaces, Roles, and Apps

⏱ **~9 minutes**

Open with the chapter's story. Camila's report became the most-opened report in the
office — and then a Phoenix manager emailed, quoting a South Florida reseller's exact
margin, a number she had no business seeing. Nobody broke a rule. The report had been
built to be *seen*, and it was being seen, by everyone, completely. A report forty people
depend on is no longer a report — it is a **system**, and a system must be **safe**,
**trusted**, **reliable**, and **repeatable**. That set of practices is **governance**,
and it is this chapter.

### The workspace and its four roles

> 💜 **WHERE AM I?** Open the **browser** — `app.powerbi.com`. Governance lives in the
> Service; assume the browser unless a marker says otherwise.

A **workspace** is the container — every report, semantic model, and dashboard a team
builds lives inside one. It is the back room. Who can do what in that back room is set by
four **workspace roles**.

- **See it.** A workspace page has a toolbar across the top with a **Manage access**
  button.
- **Name it.** That panel assigns people to the four roles — **Viewer**, **Contributor**,
  **Member**, **Admin**.
- **Find it.** Open the workspace → **Manage access** → **Add people or groups**.
- **Do it.** Add the name from setup step 3 and assign a role. Narrate the ladder as you
  go: a **Viewer** reads published content and nothing more; a **Contributor** builds and
  edits inside the workspace but cannot publish the app; a **Member** can publish and
  share; an **Admin** controls everything, including the access list itself.

Deliver the governing principle — **least privilege**: give each person the *smallest*
role that lets them do their job. An analyst who only reads dashboards does not need
Contributor. Mention the practical tip: assign roles to **security groups**, not
individuals, where you can — far less to maintain.

### Workspace versus app

The workspace is the back room; **Chapter 7's app is the storefront** published out of
it. Make one subtlety explicit, because the exam tests it: **updating the report in the
workspace does not update the app.** The app is a separate, deliberate publication step —
the audience sees changes only when you update the app.

> Jamal's forty-one-reports story makes this concrete: consumers should receive an
> **app**, not raw workspace access. Tell it briefly — it is the *why* behind giving the
> audience a clean front door instead of a messy back room.

---

## PART 2 — Row-Level Security

⏱ **~10 minutes**

Tell students plainly: *"This part is your lab. Watch how the role works — you build your
own after the break."*

The Phoenix email had one root cause: every person who opened the report saw every row.
**Row-Level Security** — RLS — is the fix. It filters the data a person sees based on who
they are.

### Define the role — in Desktop

> 💜 **WHERE AM I?** Switch to **Power BI Desktop**. The *roles* are defined here.

- **See it.** The **Modeling** tab of the ribbon has a **Security** group.
- **Name it.** The control is **Manage roles**.
- **Find it.** **Modeling** tab → **Manage roles** → **Create**.
- **Do it.** Name the role `Southwest Region`. Select the **SalesTerritory** table, and
  in its filter box type the DAX filter `[Region] = "Southwest"`. Save. Then use
  **View as** → tick `Southwest Region` → the report filters to Southwest only. Click
  **Stop viewing** to leave the preview.

Say what just happened: a user assigned to this role will see only the rows that pass the
filter — one report, one model, but each viewer's screen loads only their slice.

### Assign the person — in the Service

> 💜 **WHERE AM I?** Switch to the **browser** — the Service. The *people* are assigned
> here.

- Publish the report, open the **semantic model** in the workspace, and go to its
  **Security** page.
- The role you defined in Desktop appears here. Add a person to it.

This is the two-halves point: the DAX filter is half the job, the assignment is the other
half — and they live in two different places.

### The mistake that undoes a perfect role

Deliver the **COMMON MISTAKE** from 8.3, and weight it — this is the one students miss:
**RLS does not protect Members and Admins.** People with edit access to the model see all
the data, by design. RLS constrains **Viewers**. A flawless filter still leaks if the
person who must be limited was given the Member role.

> **Tell the story:** Camila built her RLS roles, clicked *View as*, saw the report filter
> correctly, and was ready to call it done. Jamal asked her to publish it and watch the
> Orlando manager open it on a screen-share. It showed every region. The cause: Camila had
> made the Orlando manager a workspace **Member** because it felt friendlier than Viewer —
> and Members bypass RLS. The role was perfect; the assignment was wrong. **View As tests
> the filter. Only a real user on the published report tests the whole chain.**

Mention at awareness level: for a model with dozens of regions, one role per region does
not scale — **Dynamic RLS** uses `USERPRINCIPALNAME()` to match the signed-in user
against a mapping table, so one role covers everyone. Name it; do not build it.

---

## 💜 TAKE A BREATH

⏱ **~2 minutes**

Stretch, look away from the screen. Hold the two-halves idea before the last part: a
Row-Level Security **role** is a DAX filter defined in **Desktop**; the **assignment** of
real people happens in the **Service**. View As checks the filter. It cannot check the
assignment — and RLS only ever constrains **Viewers**.

---

## PART 3 — Trust, Refresh, and Production

⏱ **~9 minutes**

> 💜 **WHERE AM I?** Still in the **browser** — the Power BI Service.

This part rounds out the governance toolkit. Keep each one at **awareness** level — name
it, show where it lives, give the one-line rule. Students will not click these.

### Classify it — sensitivity labels

A **sensitivity label** — *Public*, *General*, *Confidential*, *Highly Confidential* — is
a tag applied to a report or model. It is not decoration: it travels **downstream**.
Export a *Confidential* report to Excel and the spreadsheet carries the label, and its
protection, with it. Pair it with the RLS sentence: **RLS controls *who sees which rows*;
a sensitivity label controls *how the data is handled* once it leaves the report.** (The
Phoenix email needed both.) Labels are configured by administrators in Microsoft Purview.

### Trust it — promote and certify

**Endorsement** is the trust signal a consumer reads when a workspace has accumulated
forty reports. **Promoted** says *the team that built this stands behind it* — any
contributor can promote their own content. **Certified** says *the organization vouches
for this* — and only a small set of reviewers, named by an administrator, can certify.
Show the path: a semantic model's **Settings** → **Endorsement and discovery**. The exam
favorite: *promoted* is self-service and broad; *certified* is restricted and
authoritative.

### Keep it current — refresh and gateways

A published report is only as fresh as the data behind it. Three nested ideas:

- **Scheduled refresh** — a setting on the semantic model that re-imports the source on a
  timetable (every morning at 6 a.m.). Add a refresh-failure notification so a person
  finds out before the audience does.
- **Incremental refresh** — configured in Desktop, it refreshes only the recent
  partitions and leaves settled history untouched. The signal: a big, history-heavy table
  that takes too long to refresh.
- **Gateway** — needed only when the source lives **on-premises**. The cloud Service
  cannot reach a server inside a company's own network; an **on-premises data gateway** is
  the secure bridge. Cloud source → no gateway; on-prem source → gateway.

### Change it safely — deployment pipelines

Editing a live report that forty people depend on is no longer acceptable. A **deployment
pipeline** gives content three stages — **Development**, **Test**, **Production** — and a
controlled path between them. New work happens in Dev, is promoted to Test for real
review, and only then reaches Production. Mention the **lineage view**: one semantic model
often feeds many reports, and lineage shows what a change will touch before you make it.

Close the demo — and the course's content — on the chapter's idea: building the report
was the visible half of the job. Making it **safe, trusted, reliable, and repeatable** is
what turns an impressive report into a system an organization can actually run. That is
the difference between a junior analyst and a professional.

---

## Instructor answer key

- **"Where are RLS roles created — Desktop or the Service?"** The *roles* (the DAX
  filters) are created in **Desktop**, under Modeling → Manage roles. The *people* are
  assigned to those roles in the **Service**, on the semantic model's Security page.
- **"My role filtered fine in View As but a viewer still saw everything — why?"** View As
  tests only the filter. The viewer was almost certainly assigned a workspace role above
  Viewer — **Members and Admins bypass RLS**. RLS constrains Viewers.
- **"What's the difference between Promoted and Certified?"** Promoted — the building team
  stands behind it; any contributor can do it. Certified — the organization vouches for
  it; only admin-designated reviewers can do it.
- **"When do I need a gateway?"** Only when the data source is **on-premises** — inside a
  private network the cloud Service cannot reach. A cloud source needs no gateway.
- **"What's incremental refresh for?"** A big, history-heavy fact table that takes too
  long to refresh fully every day. It refreshes only the recent partitions.
- **"Difference between a workspace and an app?"** A workspace is the team's back room
  (build and collaborate). An app is the polished storefront published *from* it for an
  audience. Updating the report does not update the app — the app is a separate publish.
- **"Does sensitivity labelling stop someone from seeing data?"** No — that is RLS's job.
  A label classifies the data and travels with it (e.g. into an exported Excel file),
  controlling how it is *handled*, not who can *see* a row.

---

## Do / Don't — for the embedded tutor or co-instructor

Carlos does not stay for the tutoring block. Whoever runs it should hold these.

**DO**

- Confirm Power BI Service sign-in and a manageable workspace on the **instructor
  machine** **before class**. The Service portions run on your machine only.
- Say each **WHERE AM I?** marker out loud — the browser/Desktop switch is the chapter's
  main source of confusion.
- Frame PART 2 as a preview of Lab 10: defining the role and testing with View As is the
  Desktop skill students build themselves after the break.
- Weight the **COMMON MISTAKE**: RLS constrains Viewers, not Members or Admins. It is the
  single most-missed point in the chapter and a written-response question in Lab 10.
- Keep endorsement, refresh, gateways, and pipelines at **awareness** level — name them,
  give the one-line rule, move on.

**DON'T**

- Don't tell students they will assign members, set up workspaces, or publish in Lab 10 —
  they will not. Lab 10 is Desktop work: define an RLS role and test it with View As.
- Don't claim RLS protects everyone — it protects Viewers only.
- Don't promise a sensitivity label or certification will be clickable; if the tenant has
  not configured them, they are name-only for this section.
- Don't leave the demo report stuck in **View as** — click Stop viewing before moving on,
  or the rest of the demo shows filtered data.

---

*End of Guided Demo 11. Paired graded work: Lab 10 — Row-Level Security Configuration,
Block B.*
