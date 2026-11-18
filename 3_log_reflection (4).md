# AI Audit, Transcript and Reflection

## A. Prompt used

> Please review my written interpretation of the descriptive statistics from the illustrative teaching dataset. Focus only on refining my existing work. Correct grammar, spelling, punctuation, sentence structure, and formatting while preserving my original meaning and academic voice. Identify any unclear statements, inconsistencies, or possible factual errors, but do not independently interpret the data, generate new explanations, introduce arguments, or write conclusions on my behalf. If you identify an issue, point it out and explain why so I can make the correction myself. Do not change my reasoning or add content that I have not written. Ensure that all references to the figures remain consistent with their status as illustrative teaching data and do not present them as actual PBS prices.

## B. Audit table

Every sentence of the AI's interpretation is listed. Green: recomputed from the data. Amber: an explanation the data do not establish. Red: a causal claim or a reference to data not shown.

| # | AI sentence | Colour | How checked | Decision |
|---|---|---|---|---|
| 1 | The pooled results show different price levels and different rates of change. | Green | Compared item means and percentage changes in the summary table | Accepted |
| 2 | Oil B has the highest mean (PKR 324.83/kg) and Staple A the lowest (PKR 111.17/kg). | Green | Recomputed with `groupby("item")["price"].mean()` | Accepted |
| 3 | The largest first-to-last increase is Sweetener D (19.41%), not Oil B. | Green | Averaged the two cities per date, applied the change formula to all four items | Accepted |
| 4 | Pulse C has the smallest increase (3.69%). | Green | Same calculation | Accepted |
| 5 | The mean and median describe the centre in different ways. | Green | Checked against the formulas in `2_work.ipynb` | Accepted |
| 6 | The mean uses all observations and can be influenced by extreme values; the median is the middle value. | Green | Sweetener D with PKR 9,999: mean 166.75 to 576.81, median 166.75 to 167.75 | Accepted |
| 7 | Pooled means and medians are close, so the two measures tell a broadly similar story for these series. | Green | Largest mean-median gap is 0.83 (Staple A) | Accepted for these series only |
| 8 | This does not prove the mean is always the typical price. | Green | Logical caveat, supported by sentence 6 | Accepted |
| 9 | City 2 has a higher mean than City 1 for each item. | Green | Recomputed with `groupby(["item", "city"])` | Accepted |
| 10 | The data show the city difference but do not explain its cause. | Green | The file has only date, item, city, price, unit and label | Accepted |
| 11 | The increases describe changes between two dates and do not establish why prices changed. | Green | Same check as sentence 10 | Accepted |
| 12 | The values are illustrative teaching data, not actual PBS observations, so they should not be reported as official statistics. | Green | The `data_label` column says so | Accepted |

No sentence needed correction. All checks were run in `2_work.ipynb`.

## C. Confused classmate excerpt

**AI Roleplay: Confused Classmate**

**Classmate:** I don't understand why we need both the mean and median. Isn't the mean always the best way to find the typical price of an item?

**Me:** Not necessarily. The mean gives us the average price by adding all the prices and dividing by the number of observations. However, it can be affected by unusually high or low prices.

**Classmate:** But why does that matter? An average is an average, isn't it?

**Me:** The problem is that an unusually high price can pull the mean upwards, making it seem like prices are generally higher than what most people actually pay. The median helps us understand the middle price without being heavily affected by extreme values.

**Classmate:** But why would the median be better than the mean?

**Me:** It depends on the data. If the prices are fairly consistent and there are no extreme values, the mean can represent the typical price quite well. However, if there are some unusually high or low prices, the median might provide a more representative picture.

**Classmate:** So are you saying that the mean is useless?

**Me:** No, not at all. Both statistics are useful. The mean considers every observation, while the median tells us the middle value when all observations are arranged in order. We should choose based on the distribution of the data.

**Classmate:** But why can't we just report both?

**Me:** We actually can report both. That gives readers a better understanding of the data. However, if we have to choose one statistic to represent a typical price, we should consider whether extreme values are influencing the mean.

**Classmate:** Okay, so if most prices are around Rs. 100 but one price is Rs. 500, the mean could become higher than what most people actually pay?

**Me:** Exactly. In that situation, the median may better represent the typical price because it is less affected by that unusually high observation.

**Classmate:** I think I understand now. So the mean is not always the typical price. We need to look at the data first and decide which measure represents it more accurately.

**Me:** Exactly. The important thing is not to automatically assume that one measure is always better than the other. We should interpret the data before deciding which statistic to report.

**Classmate:** That makes sense now. I was assuming that average and typical always meant the same thing, but they don't necessarily mean the same thing when the data contains extreme values.

## D. Reflection

My first draft said more than the data allow in one place. It said the first-to-last increases "may reflect a general upward movement" in the series, but a first-to-last change compares only two dates and shows nothing about the ten dates between them. It also said Sweetener D had the highest mean price, which was wrong: Oil B has the highest mean (PKR 324.83) and Sweetener D is third (PKR 166.75). I found this when I recomputed the means by item.

The file has no information on transport costs, taxes, shortages or demand, so any reason for the city gap or the rises can only be a possible explanation. The `data_label` column also says the file is illustrative teaching data, so I kept the conclusions to this series.

The Sweetener D comparison also shows why the mean should not automatically be called the typical price. A single extreme value moved the mean by PKR 410.06 and the median by PKR 1.00.

## E. Use and verification note

All numbers were recomputed from `teaching_prices_clean.csv`. The with-flag comparison substitutes PKR 9,999 for PKR 157.50 at the Sweetener D, City 1, 22 January row. That value is not in the current file. The AI interpretation was used as a draft to check, not as my note. No personal or confidential data were shared with an AI tool.
