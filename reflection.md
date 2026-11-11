# Reflection

Tristen Rigby

## How the session went

I ran seven prompts in Codex to answer which Ames neighborhoods sell for more or less than expected given their living area. Each prompt built on the last one: exploring the data, removing very large houses, fitting a regression, building a neighborhood table, making a chart, checking a result, and writing a summary. Codex wrote and ran all of the code in `analysis/analysis.py`, and the full conversation is saved in `prompts/session.md`.

## What worked well

Breaking the work into small prompts made it easy to check each step before moving on. When I asked for something specific, like printing which neighborhoods were excluded or calculating residuals as actual minus predicted, Codex did exactly that. It also followed the limit in Prompt 7 to only make claims the table supports, and it pointed out on its own that the residuals show differences from the model rather than reasons for them.

## What went wrong and how I fixed it

The session failed on the very first prompt because `AmesHousing.csv` wasn't in my repo folder. The file was still in my Downloads folder under a different name, `AmesHousing-1 (1).csv`. Codex didn't guess or make up numbers; it stopped and asked where the file was. Once I pointed it to the right file, everything after that ran without errors. I also typed `codex` into the chat box by mistake at the start, which didn't change anything but showed me I need to keep track of whether I'm in the terminal or already inside Codex.

## How I checked Codex's work

I checked that the numbers were consistent with each other: 2,930 rows minus 5 removed gives 2,925, and all four excluded neighborhoods had fewer than 20 sales. I checked that the slope (about $116 per square foot) and R-squared (about 0.52) made sense for house prices. In Prompt 6, I had Codex recompute the NAmes mean residual a different way, by subtracting the average predicted price from the average actual price, and it matched the table at about −$11,845.

## What I'd do differently

First, I would put the data file into my repo folder with the exact name my prompts use before starting. Right now the script depends on a file in my Downloads folder, so someone else running my repo couldn't reproduce it without that file. Second, I would ask Codex to print the full summary table in its reply instead of only saving it, so the values show up in the session record and are easier to check. Third, I would check at least one neighborhood myself instead of only asking Codex to check its own work, for example by filtering the CSV in Excel to NAmes and confirming the 443 sales and the median price. Finally, I would save the session from the start the way my instructor asked, so I wouldn't have to redo the run to get a real record.
