# Attempt Before AI

## Statistics

Both cities are pooled (24 observations per item). First-to-last change is the change in the two-city average between 1 January and 19 March 2026.

| Item | Mean (PKR/kg) | Median (PKR/kg) | First-to-last change | Statistic I would report and why |
|---|---:|---:|---:|---|
| Oil B | 324.83 | 324.00 | 15.28% | [ADD] |
| Pulse C | 205.92 | 206.00 | 3.69% | [ADD] |
| Staple A | 111.17 | 111.75 | 12.98% | [ADD] |
| Sweetener D | 166.75 | 166.75 | 19.41% | [ADD] |

## With and without a flagged value: Sweetener D

The flagged observation is Sweetener D, City 1, 22 January 2026. The cleaned file holds PKR 157.50 there. The "with flag" row substitutes the earlier flagged value, PKR 9,999, at that row. That value is not in the current file, so the row is a reconstruction.

| Sweetener D | Mean (PKR/kg) | Median (PKR/kg) |
|---|---:|---:|
| Cleaned (157.50) | 166.75 | 166.75 |
| With flagged value (9,999) | 576.81 | 167.75 |
| Difference | +410.06 | +1.00 |

**Explanation:** [ADD one or two sentences in your own words on why the mean moved much more than the median.]

## Referee's note

**O:** The teaching dataset has four staple items recorded in two cities on twelve weekly dates, from 1 January to 19 March 2026.
**O:** With both cities pooled, Oil B has the highest mean price (PKR 324.83 per kg) and Staple A the lowest (PKR 111.17 per kg).
**O:** Sweetener D has the largest first-to-last increase in the two-city average (19.41%) and Pulse C the smallest (3.69%).
**O:** For every item, the City 2 mean is higher than the City 1 mean.
**E:** The city gap may exist because the two series start at different levels and stay apart, but the file does not say why.
**E:** The increases may reflect a general upward movement within this illustrative series, but the figures do not identify the reasons.
**O:** For Sweetener D, the mean and median are both PKR 166.75. With the flagged PKR 9,999 restored, the mean rises to PKR 576.81 and the median to PKR 167.75.
**E:** A mean can be pulled by an unusually high or low value, while the median is the middle value after sorting, so reporting both describes the centre better.
**O:** The file labels itself as illustrative teaching data, not actual PBS observations.
**O:** All four items have a higher average price on the last date than on the first.
**E:** The size of the increase differs by item, so a statement such as "all prices rose by the same amount" would be wrong.
