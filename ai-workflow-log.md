# AI Workflow Log

Tristen Rigby
Session date: November 11, 2026
Tool: Codex
Full session record: `prompts/session.md`

This log covers the rerun of my Codex session. Every Codex response described below comes from the saved session file, which is committed in the `prompts` folder. The session was saved at the end by asking Codex to download the full conversation as a Markdown file.

---

## Start of session

**What I typed:** `codex`

**What happened:** I typed the start command into the Codex chat box by mistake after Codex was already open. Codex just asked what I wanted to do. No effect on the analysis.

---

## Prompt 1: Load and explore the data

**Prompt:** Load AmesHousing.csv in this folder using Python and pandas. Report the number of rows and columns, and the data types and missing-value counts for SalePrice, Gr Liv Area, and Neighborhood. Note that column names contain spaces. Don't create any files yet.

**Codex response:** Codex could not find `AmesHousing.csv` in the repo folder, so it did not load anything. It asked me to add the file or give its location, and confirmed no files were created.

**Follow-up:** I gave Codex the file from my Downloads folder (`AmesHousing-1 (1).csv`).

**Codex response:** Loaded the data: 2,930 rows and 82 columns. SalePrice and Gr Liv Area are `int64`, Neighborhood is text, and all three have 0 missing values. No files created.

**My notes:** The first attempt failed because the data file was never in my repo folder; it was still in Downloads under a different name. Pointing Codex to the right file fixed it. The 2,930 rows match the size of the Ames dataset. Codex followed the instruction not to create files.

---

## Prompt 2: Remove very large houses

**Prompt:** Write a script analysis/analysis.py that loads the data and removes houses with Gr Liv Area over 4000 square feet. Print how many rows were removed and how many remain. Run it.

**Codex response:** Created and ran `analysis/analysis.py`. It removed 5 rows over 4,000 square feet, leaving 2,925.

**My notes:** 2,930 − 5 = 2,925, so the counts add up. Codex did not ask about the old `analysis.py`, so I didn't need the "fresh script" follow-up I had ready.

---

## Prompt 3: Regression

**Prompt:** Extend analysis.py to fit a linear regression of SalePrice on Gr Liv Area. Print the slope, intercept, and R-squared. Add a column with each house's residual (actual minus predicted price). Run it.

**Codex response:** Slope 116.2253, intercept 6,773.4837, R-squared 0.5176, using the 2,925 remaining houses. It added a `residual` column calculated as actual minus predicted price.

**My notes:** The slope means about $116 more per extra square foot, which is positive and reasonable. An R-squared of about 0.52 means living area explains roughly half the variation in price, which makes sense since size isn't the only thing that matters. These match the numbers in my README.

---

## Prompt 4: Neighborhood summary table

**Prompt:** Extend analysis.py to build a table by Neighborhood with: number of sales, median SalePrice, and mean residual. Exclude neighborhoods with fewer than 20 sales and print which ones were excluded. Sort by mean residual, highest first. Save it as analysis/neighborhood_summary.csv. Run it.

**Codex response:** Saved the table, sorted by mean residual from highest to lowest. It excluded four neighborhoods with fewer than 20 sales: Blueste (10), Greens (8), GrnHill (2), and Landmrk (1).

**My notes:** All four excluded neighborhoods are under 20 sales, so the cutoff worked. Codex's reply didn't print the table itself, so the actual values are in `analysis/neighborhood_summary.csv`.

---

## Prompt 5: Bar chart

**Prompt:** Extend analysis.py to create a horizontal bar chart of mean residual by neighborhood, in the same order as the table, with a vertical line at zero, axis labels, and a title. Save it as analysis/neighborhood_residuals.png. Run it.

**Codex response:** Created the chart in the table's order with a zero line, axis labels, and a title, saved as `analysis/neighborhood_residuals.png`.

**My notes:** Saved to the right place. The chart and table are both in the `analysis` folder.

---

## Prompt 6: Explanation and second check

**Prompt:** Explain in plain language what a positive mean residual means for a neighborhood in this analysis. Then recompute the mean residual for NAmes a second way to confirm the table value.

**Codex response:** A positive mean residual means houses in that neighborhood sold, on average, for more than the model predicted from their living area, and it doesn't explain why. For NAmes (443 sales), it subtracted the average predicted price ($156,942.83) from the average actual price ($145,097.35) and got −$11,845.48, matching the table.

**My notes:** The explanation matches how I understand residuals. Averaging actual and predicted prices separately and subtracting is a different method from averaging the residuals directly, and it gave the same answer, so the table value checks out. NAmes sold for about $11,845 less than its size predicts.

---

## Prompt 7: Summary paragraph

**Prompt:** Write a short plain-language paragraph summarizing which neighborhoods sell for more or less than expected given their size. Only make claims the table supports.

**Codex response:** StoneBr and NridgHt sold the most above prediction (about $90,900 and $89,500 on average). SWISU and OldTown sold the most below (about $61,900 and $49,200). It noted these differences describe sales compared with the model and don't explain what caused them.

**My notes:** Codex stuck to what the table shows and didn't make claims about causes. These numbers match my README summary.

---

## Saving the session

**What I typed:** Let me download all of these prompts and answers as a md file

**What happened:** Codex produced the full conversation as a Markdown file, which I saved as `prompts/session.md` and committed.
