# NHL Draft Value ROI

An analysis of every NHL draft pick from 2004 to 2016, measuring what teams get back from the picks they make.

**Tools:** Python, pandas, matplotlib, Google Colab

## Summary

- Picks 1 to 5 made the NHL 95.4% of the time. Picks 181 to 210 made it 8.2% of the time.
- Pittsburgh, St. Louis, Los Angeles, and Detroit drafted above expectations on both career games and career points. Vancouver was the worst on both.
- Steals like Nikita Kucherov, picked 58th overall in 2011 and now one of the best scorers in the league, show how much talent gets overlooked early.
- The 200-game cutoff holds up. Players drafted from 2011 to 2016 reached it at similar or higher rates than players drafted from 2004 to 2010.

## Why I Built This

I have played competitive ice hockey my whole life and fell in love with the sport as a kid. My favorite team is the Washington Capitals because of Alex Ovechkin, so I started this project with the 2004 draft, the year he was picked first overall.

I have always known that drafts do not go as expected. While looking at Washington's prospect pool recently, I noticed that some players picked with high hopes, like Ivan Miroshnichenko and Hendrix Lapierre, had not turned out the way I expected. That made me want to measure how often picks work out, and which teams are good or bad at drafting.

I also wanted to connect hockey to business. In this project, return on investment (ROI) means return on a draft pick. A team invests a pick in a player, a bit like investing in a stock, and the return is what that player produces in the NHL. There are no dollar figures here. The investment is the pick itself.

This is my first coding project. I built it in Python with pandas, in Google Colab.

## Questions

1. How often does a player drafted at each spot make the NHL?
2. Which teams get the most and the least out of their picks?
3. Who are the biggest steals and busts?

The steals interest me most. They show that talent can be overlooked early, and that a career depends on more than where a player was selected.

## Data

- **Source:** [Hockey-Reference](https://www.hockey-reference.com/) draft pages, every pick from 2004 to 2016 (13 drafts).
- **"Made the NHL"** means at least 200 career games played. I stopped at 2016 so that every player had about 10 seasons to reach it.
- **Pick range:** the chance-of-making-the-NHL charts use picks 1 to 210 (seven rounds), so every pick slot has data from all 13 drafts.
- **Goalies** are included in those charts. They are left out of any chart that uses points, because goalies do not score them.
- **Team names:** Winnipeg includes the Atlanta Thrashers, and Arizona includes the Phoenix Coyotes.

## Method

**What "expected" means.** A fifth overall pick should produce more than a 150th pick, so comparing raw totals would not be fair. Instead, I compare each player to an expected level: the average career games or points of skaters picked in the same draft year and a similar range of pick numbers. For steals and busts, forwards and defensemen are compared separately, since defensemen score fewer points.

**How it is calculated**

1. Keep picks 1 to 210 and skaters only. Goalies are left out because they do not score points.
2. Sort each pick into a group by pick number: 1 to 10, 11 to 30, 31 to 60, 61 to 120, and 121 to 210.
3. For each draft year and pick group, take the average career games and the average career points. That average is the expected level for every player in that group.
4. Over expected is the player's actual career total minus that average.
5. For a team, average the over-expected number across every pick the team made.

For example, if skaters picked 31 to 60 in the 2011 draft averaged 300 career games and one of them played 900, he is 600 games over expected. The numbers in this example are made up to show the math.

For steals and busts, step 3 also separates forwards from defensemen, and the last group includes picks after 210.

**Over expected** is the player's actual total minus the expected total. A positive number means the pick returned more than normal for that spot, and a negative number means less.

**Why each player is compared to his own draft class.** A player drafted in 2004 has had far more time to play than one drafted in 2016. Comparing everyone against all 13 drafts mixed together would favor the older drafts. My first versions of the team charts did exactly that, so I rebuilt them.

**Team charts** average the over-expected number across every pick a team made ("per pick"), so a team with more picks does not get an advantage.

## Findings

### Chance of making the NHL, by pick

![Chance of making the NHL by draft pick](%281%29%20Chance%20of%20Making%20the%20NHL.png)

- Picks 1 to 5 made the NHL 95.4% of the time. Picks 181 to 210 made it 8.2% of the time.
- The end of the first round is close to a coin flip: picks 21 to 30 made it 50.0% of the time.

### Chance of making the NHL, by round

| Round | Chance of Making the NHL |
|---|---|
| 1 | 69.7% |
| 2 | 34.1% |
| 3 | 22.6% |
| 4 | 18.8% |
| 5 | 13.8% |
| 6 | 11.5% |
| 7 | 8.2% |

![Share of NHL players by draft round](%282%29%20Draft%20Rounds%20of%20Players.png)

Round 1 produced 39.0% of all the players who reached 200 games. The other six rounds produced the rest.

### Does the 200-game cutoff treat newer drafts fairly?

Players drafted in 2016 have had less time to reach 200 games than players drafted in 2004, so I split the drafts into two groups and compared them.

![Chance of making the NHL, 2004 to 2010 drafts vs 2011 to 2016 drafts](%285%29%20Chance%20of%20Making%20NHL%20Comparison.png)

The 2011 to 2016 drafts reached 200 games at a higher rate in 8 of the 11 pick ranges, and at a lower rate in the other 3. The newer drafts did not fall behind, so the cutoff does not appear to penalize them. Each group has only 6 or 7 drafts, so small gaps in the narrow ranges, like picks 1 to 5, are likely noise.

### Teams

![Draft value by team](%284%29%20Draft%20Value%20By%20Team.png)

- Pittsburgh, St. Louis, Los Angeles, and Detroit were above expectations on both career games and career points.
- Vancouver, Winnipeg, Arizona, and Florida were below on both. Vancouver was last on both measures.
- Washington ranked near the top on points but near the middle on games, so I do not draw a strong conclusion about them.

### Steals and busts

![Biggest steals and busts](%283%29%20Steals%20%26%20Busts.png)

- Nikita Kucherov was picked 58th overall by Tampa Bay in 2011 and has become one of the best scorers in the league.
- Scott Glennie was picked 8th in 2009 and played 1 game.
- The notebook has the full top 15 for each.

## Limitations

- **Newer drafts have had less time.** A 2016 pick has had about 10 seasons, and some players develop late. The comparison above suggests this has not held back the newer drafts, but a few late bloomers could still be missing.
- **Goalies are left out of the points-based charts.** Goalie value is not captured there.
- **Credit goes to the team that made the pick,** even if it traded the player right away.
- **Pick ranges are grouped,** so a pick near the start of a range is treated the same as one near the end.
- **Team rankings are a rough ordering.** Each team made about 70 to 105 picks, so a few stars or a few misses can move a team. I only make claims where the games and points measures agree.

## What I Learned

This was my first coding project. I learned how to load and clean a messy dataset in pandas, build charts in Python, and fix problems as they came up, like a blocked download and files that disappeared between sessions.

The biggest lesson was that a chart can look right and still be unfair. My first team charts favored older drafts because those players had more time, so I rebuilt them to compare each player only with his own draft class. I also learned to check what a measure really says before trusting it. Games played alone did not tell the full story, so I added points as a second measure, and I tested the 200-game cutoff instead of assuming it was fair.

A next step would be adding salary cap data, so return could be measured in dollars as well as production.

## Files

- `NHL_Draft_Value_ROI.ipynb`: the full analysis and all five charts
- `nhl_drafts_2004_2016.csv`: the combined dataset for all 13 drafts
- The PNG files: images of the charts shown above
