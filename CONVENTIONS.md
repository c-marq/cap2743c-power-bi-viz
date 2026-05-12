# Conventions

Working rules for this course repo. Read once at the start of the semester; refer back when something feels off.

---

## Raw GitHub URLs for `.pbix` data sources

Every Power BI data source in this course connects via a **GitHub raw URL**. Local file paths break when you move between machines, so we never use them in lab work.

**The pattern:**

```
https://github.com/c-marq/cap2743c-power-bi-viz/raw/main/datasets/<filename>
```

**Examples:**

```
https://github.com/c-marq/cap2743c-power-bi-viz/raw/main/datasets/AdventureWorks_Sales.xlsx
https://github.com/c-marq/cap2743c-power-bi-viz/raw/main/datasets/SouthFloridaBeachDays_Summer2025.csv
```

**How to use one in Power BI Desktop:**

1. Get Data → **Web**
2. Paste the raw URL into the URL field
3. Click OK
4. Pick the table(s) you want in the Navigator
5. Click **Load** (or **Transform Data** if you need Power Query first)

If the URL gives you HTML instead of the file, double-check that `/raw/main/` is in the path. The `/blob/main/` version returns the GitHub preview page, not the file.

---

## File naming — Save As discipline

The first thing you do when you open a lab starter file is **Save As** with your name on it. This protects the clean starter file for the next lab, and makes your submission easy to identify.

**Format:**

```
LastName_FirstName_LabXX.pbix
```

**Examples:**

```
Marquez_Carlos_Lab01.pbix
Rodriguez_Maria_Lab03.pbix
Patel_Aanya_Capstone.pbix
```

Same convention applies to homework files (`LastName_FirstName_HW1.pbix`) and the capstone (`LastName_FirstName_Capstone.pbix`).

---

## Folder navigation

| If you're looking for… | Go to… |
|---|---|
| Today's class materials | `sessions/session-XX/` |
| The data files | `datasets/` |
| Lab starter `.pbix` files | `starter-files/` |
| Take-home assignments | `homeworks/` |
| Capstone brief, rubric, template | `capstone/` |
| Chapter readings | `textbook/` |

Tutors get a parallel folder under `tutoring/` with answer keys and behavioral guidance for each session. Students don't open those.

---

## Date format

The AdventureWorks dataset uses **US date locale** (MM/DD/YYYY). When you load Excel data into Power Query and a column should be a date, use:

**Transform → Data Type → Using Locale → English (United States) → Date**

(Not the standard data-type icon. The locale-aware path prevents MM/DD/YYYY-vs-DD/MM/YYYY misreads.)

This is the same convention from CAP2791C with Sabor Miami. If a date column ever looks "off" — wrong year, wrong month — locale is almost always the culprit.

---

## What goes in this repo (and what doesn't)

**In the repo:** Course materials, datasets, lab starters, answer keys, syllabus, chapter drafts, assets used in materials.

**NOT in the repo:** Student submissions (those go to Canvas), graded files, grades, personal data, anything covered by FERPA.

---

## A note on the AdventureWorks dataset

AdventureWorks is Microsoft's official sample dataset. We use the clean Excel version distributed at:

`https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx`

It is mirrored in this repo's `datasets/` folder for course stability — if Microsoft restructures their samples mid-semester, our links don't break.
