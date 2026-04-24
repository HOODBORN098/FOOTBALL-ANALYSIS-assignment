# Football Analysis Exercise - Basic Exploration

This report provides the detailed answers and logic for the assignment using a bulleted format for clarity.

## 1. How many matches are in the dataset?
- Code:
```python
print(f"Total matches: {df.shape[0]}")
```
- Answer: 49,287 matches.
- Logic: We use the `.shape` attribute of the Pandas DataFrame, where the first element `[0]` represents the total number of rows (matches) in the dataset.

## 2. What is the earliest and latest year in the data?
- Code:
```python
df['date'] = pd.to_datetime(df['date'])
print(f"Earliest Year: {df['date'].dt.year.min()}")
print(f"Latest Year: {df['date'].dt.year.max()}")
```
- Answer: Earliest: 1872 | Latest: 2026.
- Logic: We convert the `date` column to a datetime object, then extract the `.year` property. Applying `.min()` and `.max()` allows us to find the full chronological range of the data.

## 3. How many unique countries are there?
- Code:
```python
print(f"Unique Countries: {df['country'].nunique()}")
```
- Answer: 269 unique hosting countries.
- Logic: The `.nunique()` method counts the number of distinct entries in the `country` column, which identifies every unique nation or territory that has hosted an international match.

## 4. Which team appears most frequently as home team?
- Code:
```python
print(df["home_team"].value_counts().head(1))
```
- Answer: Brazil.
- Logic: We use `.value_counts()` on the `home_team` column, which sorts teams by the number of occurrences in descending order. The top result identifies the team that has played at home most often.

---

# Goals Analysis

## 5. What is the average number of goals per match?
- Code:
```python
df["total_goals"] = df["home_score"] + df["away_score"]
print(f"Average goals: {df['total_goals'].mean():.2f}")
```
- Answer: 2.94 goals.
- Logic: By summing the home and away scores for each row, we get a `total_goals` column. Taking the `.mean()` of this column gives the average scoring rate across all historical matches.

## 6. What is the highest scoring match?
- Code:
```python
highest_match = df.loc[df["total_goals"].idxmax()]
```
- Answer: Australia vs American Samoa (31-0).
- Logic: We find the index of the maximum value in the `total_goals` column using `.idxmax()` and retrieve that specific row to see the teams and score.

## 7. Are more goals scored at home or away?
- Code:
```python
print(f"Home: {df['home_score'].sum()}, Away: {df['away_score'].sum()}")
```
- Answer: Home (86,426 vs 58,192).
- Logic: We compare the grand totals of the `home_score` and `away_score` columns. The data shows a significant skew towards goals scored by the home team.

## 8. What is the most common total goals value?
- Code:
```python
print(df["total_goals"].mode()[0])
```
- Answer: 2.0 goals.
- Logic: The `.mode()` function identifies the most frequently occurring value in the dataset, revealing that matches most often end with exactly 2 goals.

---

# Match Results

## 9. What percentage of matches are home wins?
- Code:
```python
home_win_pct = (df["result"] == "Home Win").mean() * 100
```
- Answer: 48.91%.
- Logic: We filter for rows categorized as "Home Win" and calculate their proportion relative to the total dataset size.

## 10. Does home advantage exist?
- Answer: Yes.
- Logic: We compare the win rates: Home Wins (48.91%) are nearly double the Away Wins (28.23%). This statistical gap proves a strong home advantage.

## 11. Which country has the most wins historically?
- Code:
```python
most_wins = df["winner"].value_counts().idxmax()
```
- Answer: Brazil.
- Logic: After identifying a winner for every match, we count the occurrences of each team name. Brazil's top ranking highlights their historical dominance in international football.

---

# Visualization

## Histogram of Goals
- Code:
```python
import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(10, 6))
df["total_goals"].hist(bins=15, color='skyblue', edgecolor='black')
plt.title("Distribution of Goals Per Match")
plt.xlabel("Total Goals")
plt.ylabel("Number of Matches")
plt.show()
```
- Logic: A histogram allows us to see the distribution of goals. By setting `bins=15`, we group the goal counts into meaningful intervals, showing that most matches result in 2-3 goals and higher scores are increasingly rare.

## Bar Chart of Match Outcomes
- Code:
```python
df["result"].value_counts().plot(kind='bar', color=['#4CAF50', '#f44336', '#2196F3'])
plt.title("Match Outcomes")
plt.ylabel("Count")
plt.xticks(rotation=0)
plt.show()
```
- Logic: A bar chart is the most effective way to compare categorical data. Here, it visually confirms the "Home Advantage" by showing the "Home Win" bar is significantly taller than "Away Win" or "Draw".

## Top 10 Teams by Total Wins
- Code:
```python
df["winner"].value_counts().head(10).plot(kind='barh', color='gold').invert_yaxis()
plt.title("Top 10 Teams by Total Historical Wins")
plt.xlabel("Number of Wins")
plt.show()
```
- Logic: We use a horizontal bar chart (`kind='barh'`) to rank the top 10 teams. Sorting them by the number of wins and inverting the Y-axis puts the most successful team (Brazil) at the top for easy comparison.
