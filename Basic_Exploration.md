# Basic Exploration

This part of the assignment covers the initial look at the dataset structure and timeframe.

1. How many matches are in the dataset?
- Code:
```python
print(f"Total matches: {df.shape[0]}")
```
- Answer: 49,287 matches.
- Logic: We use the `.shape` attribute of the Pandas DataFrame, where the first element `[0]` represents the total number of rows (matches) in the dataset.

2. What is the earliest and latest year in the data?
- Code:
```python
df['date'] = pd.to_datetime(df['date'])
print(f"Earliest Year: {df['date'].dt.year.min()}")
print(f"Latest Year: {df['date'].dt.year.max()}")
```
- Answer: Earliest: 1872 | Latest: 2026.
- Logic: We convert the `date` column to a datetime object, then extract the `.year` property. Applying `.min()` and `.max()` allows us to find the full chronological range of the data.

3. How many unique countries are there?
- Code:
```python
print(f"Unique Countries: {df['country'].nunique()}")
```
- Answer: 269 unique hosting countries.
- Logic: The `.nunique()` method counts the number of distinct entries in the `country` column, which identifies every unique nation or territory that has hosted an international match.

4. Which team appears most frequently as home team?
- Code:
```python
print(df["home_team"].value_counts().head(1))
```
- Answer: Brazil.
- Logic: We use `.value_counts()` on the `home_team` column, which sorts teams by the number of occurrences in descending order. The top result identifies the team that has played at home most often.
