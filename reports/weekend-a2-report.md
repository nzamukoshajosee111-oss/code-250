\# Assignment 2 Report: Titanic Survival Analysis



\## Dataset

The Titanic passenger dataset (891 rows, loaded via seaborn, originally from the

\[Kaggle Titanic competition](https://www.kaggle.com/c/titanic/data), CC0/public domain).

After cleaning, 889 rows remain (two rows with missing embarkation data were dropped).

\## Question Explored

Did survival on the Titanic depend more on gender, passenger class, or the fare paid —

or was it a combination of these factors?



\## What I Found

Survival was strongly tied to both class and gender together, not just one factor alone.

First-class women survived at roughly 97%, while third-class men survived at only about

13.5% (see `reports/a2\_chart1.png`). This is a much bigger gap than either factor alone

would suggest — third-class women still survived at 50%, well above any category of men.



The fare-vs-age scatter plot (`reports/a2\_chart2.png`) reinforces this: survivors cluster

noticeably in the higher fare brackets across nearly all ages, while non-survivors dominate

the lower fare range regardless of age. This suggests ticket price (and by extension,

class and cabin location) mattered more to survival odds than age did.



\## Limitation

The `age` column had a meaningful number of missing values that I imputed with the median.

This likely flattens some of the real age-based patterns in the data, since imputing a

single median value for all missing ages assumes those passengers were "typical," which

may not be true — for example, if missing ages were disproportionately common among a

specific class or ticket type, the imputation could be masking a real relationship between

age and survival within certain subgroups.



\## Reflection

The groupby + merge step took the longest to get right. My first attempt merged the class

averages back without using `observed=True`, which produced an extra empty category row I

didn't expect, and it took some trial and error with `print(df.shape)` at each step to catch

that mismatch. If I had another dataset this weekend, I would spend more time up front looking

at `.nunique()` and `.value\_counts()` for each categorical column before writing any group-by

logic, since that early sanity check would have caught the issue before shape checks were

technically needed.

