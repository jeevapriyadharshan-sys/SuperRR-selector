# SuperRR-selector
Win-probability leverage model that ranks IPL and T20I batters and bowlers by how much they add in high-pressure moments. Built for SupeRR Selector Season 2, Round 1. Measures runs and wickets above expected, adjusts for opponents, and tests reliability with split-half and bootstrap checks.
# Who Delivers Under Pressure? A Leverage-Based Player Rating for T20 Cricket

SupeRR Selector Season 2, Round 1 submission. Ranks the most reliable batters and
bowlers in high-pressure situations using IPL and T20I ball-by-ball data (2022 to 2026).

## Approach
1. **Pressure = leverage.** Win-probability models estimate the batting side's chance
   of winning before every ball. Leverage is the expected win-probability swing of the
   next ball. High pressure is the top 25% of leverage (47,409 of 189,633 balls).
2. **Performance = value above expected.** An outcome model gives expected runs and
   wicket probability for an average player in the same match state. Each player is
   scored on runs and wickets above that benchmark, adjusted for opponent quality.
3. **Rating = Level (50%) + Resilience (25%) + Consistency (25%).** Each component is
   shrunk with empirical Bayes so small samples cannot top the list.
4. **Reliability checks.** Split-half, forward test, 200 match bootstraps and
   sensitivity runs. Pressure skill repeats only modestly, and batters less than bowlers.

## Results
Top 10 batters and bowlers are in `results/`. Full methodology is in the report.

## Run it
Python 3.13 with pandas, numpy, scikit-learn, scipy and matplotlib.
Put the competition CSVs in a data folder (not included) and set the paths at the top
of each script. Run in this order:

| Step | Script |
|---|---|
| 1 | `prep.py`, then `prep_truncation_filter.py` |
| 2 | `model.py` |
| 3 | `prep_rows.py` |
| 4 | `rating2.py` |
| 5 | `robust2.py` |
| 6 | `final.py`, `charts.py` |

## Notes
Paths are set for the original working folders and need editing for your machine.
The raw competition data is not redistributed here.
