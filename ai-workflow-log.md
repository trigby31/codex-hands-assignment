AI Workflow Log

Tristen Rigby, 10.18

Note: The original Codex session was not saved. The prompts below are the exact prompts I used. Codex’s responses are summarized from memory in my own words, not quoted. The numerical results were reproduced from the supplied AmesHousing-1.csv file.

Prompt 1: Check the data

Prompt: Load AmesHousing.csv in this folder using Python and pandas. Report the number of rows and columns, and the data types and missing-value counts for SalePrice, Gr Liv Area, and Neighborhood. Note that column names contain spaces. Don’t create any files yet.

What Codex did: The reproduced data check found 2,930 rows and 82 columns. SalePrice and Gr Liv Area were integers, and Neighborhood contained text. None of the three columns had missing values.

What I checked or changed: Checking the data first established the starting row count and confirmed that the columns contained the expected types of information. It also showed whether missing values might affect the analysis.

Prompt 2: Remove large houses

Prompt: Write a script analysis/analysis.py that loads the data and removes houses with Gr Liv Area over 4000 square feet. Print how many rows were removed and how many remain. Run it.

What Codex did: The reproduced analysis removed 5 houses and left 2,925.

What I checked or changed: The numbers add up to the original total: 5 plus 2,925 equals 2,930. I cannot verify whether the original script ran on the first try.

Prompt 3: Fit the regression

Prompt: Extend analysis.py to fit a linear regression of SalePrice on Gr Liv Area. Print the slope, intercept, and R-squared. Add a column with each house’s residual (actual minus predicted price). Run it.

What Codex did: The reproduced regression had a slope of about $116.23 per square foot, an intercept of $6,773.48, and an R-squared of 0.518. NumPy was used for the reproduction; the library used in the original session is unknown.

What I checked or changed: The positive slope makes sense as an estimated increase in sale price for each additional square foot. The R-squared means living area accounted for about 52% of the variation in sale price in the filtered data.

Prompt 4: Build the neighborhood table

Prompt: Extend analysis.py to build a table by Neighborhood with: number of sales, median SalePrice, and mean residual. Exclude neighborhoods with fewer than 20 sales and print which ones were excluded. Sort by mean residual, highest first. Save it as analysis/neighborhood_summary.csv. Run it.

What Codex did: The reproduced analysis excluded Blueste, Greens, GrnHill, and Landmrk because each had fewer than 20 sales. StoneBr was at the top of the remaining table, with a mean residual of about $90,908. SWISU was at the bottom, with a mean residual of about negative $61,902.

What I checked or changed: The reproduced table used the requested sales count, median sale price, and mean residual and sorted the neighborhoods from highest to lowest mean residual. I cannot verify whether I opened the original CSV.

Prompt 5: Make the chart

Prompt: Extend analysis.py to create a horizontal bar chart of mean residual by neighborhood, in the same order as the table, with a vertical line at zero, axis labels, and a title. Save it as analysis/neighborhood_residuals.png. Run it.

What Codex did: The original chart cannot be verified from the data alone. The requested order would put StoneBr at the top and SWISU at the bottom.

What I checked or changed: I cannot verify whether the original chart had the requested labels and zero line or whether I asked for fixes.

Prompt 6: Explain and verify

Prompt: Explain in plain language what a positive mean residual means for a neighborhood in this analysis. Then recompute the mean residual for NAmes a second way to confirm the table value.

What Codex did: A positive mean residual means houses in a neighborhood sold for more, on average, than the regression predicted based on their living area. The reproduced mean residual for NAmes was about negative $11,845.48. A second calculation, subtracting the predicted price at NAmes’s average living area from its average sale price, gave the same result.

What I checked or changed: A second calculation helps catch errors in the residual or grouping calculation. The negative result means NAmes houses sold for less, on average, than the model predicted based on size.

Prompt 7: Summarize carefully

Prompt: Write a short plain-language paragraph summarizing which neighborhoods sell for more or less than expected given their size. Only make claims the table supports.

What Codex did: In the reproduced table, StoneBr and NridgHt had the largest positive mean residuals, meaning their houses sold for more than the model predicted based on living area. SWISU and OldTown had the most negative mean residuals. These are neighborhood averages relative to a model using living area alone.

What I checked or changed: Asking for claims supported by the table helps prevent conclusions about why prices differed or assumptions that every house in a neighborhood followed the average.
