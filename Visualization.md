# Visualization

Visual representation of the data trends.

Histogram of Goals
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

Bar Chart of Match Outcomes
- Code:
```python
df["result"].value_counts().plot(kind='bar', color=['#4CAF50', '#f44336', '#2196F3'])
plt.title("Match Outcomes")
plt.ylabel("Count")
plt.xticks(rotation=0)
plt.show()
```
- Logic: A bar chart is the most effective way to compare categorical data. Here, it visually confirms the "Home Advantage" by showing the "Home Win" bar is significantly taller than "Away Win" or "Draw".

Top 10 Teams by Total Wins
- Code:
```python
df["winner"].value_counts().head(10).plot(kind='barh', color='gold').invert_yaxis()
plt.title("Top 10 Teams by Total Historical Wins")
plt.xlabel("Number of Wins")
plt.show()
```
- Logic: We use a horizontal bar chart (`kind='barh'`) to rank the top 10 teams. Sorting them by the number of wins and inverting the Y-axis puts the most successful team (Brazil) at the top for easy comparison.
