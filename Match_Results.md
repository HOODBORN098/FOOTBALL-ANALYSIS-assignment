# Match Results

This section focuses on winning patterns and identifying the most successful nations.

9. What percentage of matches are home wins?
- Code:
```python
home_win_pct = (df["result"] == "Home Win").mean() * 100
```
- Answer: 48.91%.
- Logic: We filter for rows categorized as "Home Win" and calculate their proportion relative to the total dataset size.

10. Does home advantage exist?
- Answer: Yes.
- Logic: We compare the win rates: Home Wins (48.91%) are nearly double the Away Wins (28.23%). This statistical gap proves a strong home advantage.

11. Which country has the most wins historically?
- Code:
```python
most_wins = df["winner"].value_counts().idxmax()
```
- Answer: Brazil.
- Logic: After identifying a winner for every match, we count the occurrences of each team name. Brazil's top ranking highlights their historical dominance in international football.
