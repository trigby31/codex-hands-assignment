# Codex Hands-On Assignment

Tristen Rigby, 10.18

## Question
Which neighborhoods in the Ames, Iowa housing data sell for more or less than
expected, given how much living area their houses have?

## Summary
After removing 5 houses with more than 4,000 square feet of living area
(2,925 remain), a linear regression of sale price on living area estimated about
$116 per additional square foot, with an R-squared of 0.52. Living area alone
explains about half the variation in sale price.

Among neighborhoods with at least 20 sales (Blueste, Greens, GrnHill, and
Landmrk were excluded), StoneBr had the highest mean residual, selling for about
$90,900 more on average than the model predicted, and NridgHt was also well
above prediction. SWISU had the lowest mean residual, about $61,900 below
prediction, with OldTown also well below. NAmes averaged about $11,845 below
prediction, a value I confirmed with a second calculation.

These are neighborhood averages from a model that uses living area only, so
they show where prices differ from what size alone predicts, not why they
differ, and individual houses may not follow their neighborhood's average.

## Files
- `analysis/analysis.py`: the analysis script
- `analysis/neighborhood_summary.csv`: neighborhood table
- `analysis/neighborhood_residuals.png`: bar chart of mean residuals
- `ai-workflow-log.md`: prompts and Codex responses
- `reflection.md`: reflection on working with Codex
