# UPI Spending Behavior and Financial Awareness

A data science mini-project that analyses how people use UPI and whether their habits are linked to running out of balance, borrowing money, or delaying a payment.

Done as part of the Data Science Practicals course (BCA, Stella Maris College, Autonomous).

## Problem

UPI makes payments quick, but it can also make it harder to keep track of spending. This project looks at survey data on UPI usage and budgeting habits to see which factors are linked to a person borrowing money or delaying a payment because their balance ran out unexpectedly.

## Data

- Collected through a survey on UPI usage and financial habits
- 101 responses (100 after removing one with no answer for the target)
- 12 attributes used, e.g. age, weekly UPI transactions, whether the person checks their balance, whether they set a budget, how often their balance was lower than expected, and a self-rated financial awareness score (1-5)
- **Target:** `BorrowedMoney` (Yes / No)
- Names and timestamps have been removed from `upi.csv` to protect respondents' privacy

## Approach

1. Loaded and renamed columns, checked missing values and duplicates
2. Cleaned data (dropped rows with no target, filled other gaps with the most common answer)
3. Encoded categorical answers as numbers
4. Statistical analysis (mean, median, mode, variance, standard deviation, correlation)
5. Visualisation (histogram, bar charts, crosstab, boxplot)
6. Logistic regression (75/25 train-test split) with confusion matrix and classification report
7. Predicted the outcome for a new person

## Results

| Metric | Value |
| --- | --- |
| Training accuracy | 80% |
| Testing accuracy | 80% |
| Baseline (always predict "No") on the test set | 64% |
| Recall for "No" | 0.94 |
| Recall for "Yes" | 0.56 |

Main findings:

- 30 of 100 respondents had borrowed money or delayed a payment.
- How often the balance was lower than expected was the strongest pattern: only 3 of 37 people who never faced this had borrowed or delayed, compared with 8 of 11 who faced it frequently.
- People who borrowed or delayed rated themselves as less financially aware (about 3.0 vs 3.8 on average).
- Setting a budget and checking the balance before paying showed only a weak relationship in this dataset.

## Limitations

- Small sample: 100 responses, only 25 in the test set, so every mistake changes the accuracy by 4 points.
- The model finds people who will borrow or delay less reliably (recall 0.56) than people who will not.
- Survey answers are self-reported.

## Future scope

- Collect more responses and add more features (savings, spending categories)
- Use cross-validation and try other models such as decision trees or random forests
- Build an app that warns users when their spending pattern puts them at risk of running out of balance

## Tools

Python, Jupyter Notebook, Pandas, Matplotlib, scikit-learn

## Files

- `UPI_Spending_Behavior_Analysis.ipynb` - full analysis
- `upi.csv` - anonymised survey data

## Run it

```bash
pip install pandas matplotlib scikit-learn jupyter
jupyter notebook UPI_Spending_Behavior_Analysis.ipynb
```

Keep `upi.csv` in the same folder as the notebook.
