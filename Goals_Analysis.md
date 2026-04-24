# Goals Analysis

In this section, we analyze scoring trends across all historical matches.

5. What is the average number of goals per match?
- Code:
```python
df["total_goals"] = df["home_score"] + df["away_score"]
print(f"Average goals: {df['total_goals'].mean():.2f}")
```
- Answer: 2.94 goals.
- Logic: By summing the home and away scores for each row, we get a `total_goals` column. Taking the `.mean()` of this column gives the average scoring rate across all historical matches.

6. What is the highest scoring match?
- Code:
```python
highest_match = df.loc[df["total_goals"].idxmax()]
```
- Answer: Australia vs American Samoa (31-0).
- Logic: We find the index of the maximum value in the `total_goals` column using `.idxmax()` and retrieve that specific row to see the teams and score.

7. Are more goals scored at home or away?
- Code:
```python
print(f"Home: {df['home_score'].sum()}, Away: {df['away_score'].sum()}")
```
- Answer: Home (86,426 vs 58,192).
- Logic: We compare the grand totals of the `home_score` and `away_score` columns. The data shows a significant skew towards goals scored by the home team.

8. What is the most common total goals value?
- Code:
```python
print(df["total_goals"].mode()[0])
```
- Answer: 2.0 goals.
- Logic: The `.mode()` function identifies the most frequently occurring value in the dataset, revealing that matches most often end with exactly 2 goals.
