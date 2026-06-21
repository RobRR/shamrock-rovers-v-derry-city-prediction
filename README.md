# shamrock-rovers-v-derry-city-prediction

---
title: "Match analysis: Shamrock Rovers v Derry City"
subtitle: "Dixon-Coles model probability & market efficiency evaluation"
date: "2026-06-21"
output: github_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$config(echo = TRUE, warning = FALSE, message = FALSE)
```

## Form & match context

Derry haven’t exactly pulled up any trees this season, and it seems unlikely that the Candystripes will uproot Shamrock Rovers on the Hoops’ home patch at Tallaght Stadium in one of two fixtures in the League of Ireland’s Premier Division on Monday (June 22, 2026; 8pm).

Tiernan Lynch’s side have won just one of their last nine games in the league (1W, 5D, 3L) and lost on their previous visit to the Dublin 24 venue in March, when a penalty from Dylan Watts nine minutes from time separated the sides. 

Only Waterford (no wins from 10 away games) have won fewer fixtures on the road this season compared to Derry’s solitary success on their travels (1W, 5D, 5L). Even Waterford (11) have scored more away goals than Derry (10) – and from one fewer game.

So, there isn’t much to recommend Derry, is there?

## Model predictions & football variance

The Dixon-Coles model predicts another **1-0 home win for Shamrock Rovers** as being the most likely outcome from this fixture between the league’s first- and sixth-placed sides. Were Rovers to win, they would stretch their lead over their nearest rivals, St Patrick’s Athletic, to eight points, but having played two more games.

> **Important analytical reminder:** Even the most likely outcome (in this instance, 16.3% for a 1-0 home win) is not that likely. 

The Dixon-Coles model treats goal scoring as a random process governed by a Poisson distribution, adjusted for team strengths. In a low-scoring sport like football, a single goal can define the outcome of the game, as matches average only two to three goals in total.

Because a single goal makes up such a huge part of the final score, one lucky or unlucky moment can completely change who wins. This makes football incredibly unpredictable. The model mathematically reflects this variance in scorelines by spreading out its probabilities, meaning even the most likely outcome still has a low chance of occurring.

The accompanying chart shows the respective goal distributions for both sides and the Dixon-Coles correct score matrix:

### Low-scoreline parameter adjustments ($\rho$)

A baseline independent Poisson model struggles with low-scoring football matches because it assumes team scores are entirely independent. To fix this, a Dixon-Coles parameter ($\rho$) adjusts the lowest scorelines:

* **Inflates 0-0 and 1-1:** Accounts for the real-world tendency of low-scoring matches to end in draws more often than pure randomness predicts.
* **Deflates 1-0 and 0-1:** Corrects the standard Poisson model's tendency to overstate narrow, single-goal victories.

_Note: This fix only changes low-scoring games. If either team scores two or more goals, the score is not affected._

---

## Market efficiency & EV assessment

At the time of writing, Paddy Power’s total book stood at **109.67%**, meaning they had built a sizeable overround of **9.67%** into this specific market. Efficiently-priced markets with heavy overrounds are mathematically impossible to beat over the long term. Consequently, there is no positive expected value (+EV) across any of the three 1X2 outcomes.

For a bet to have +EV, the bookmaker's odds must be higher than the model's fair odds. In this specific scenario, every single market price is lower than the model's calculated fair price:

| Selection | Paddy Power market price | Model 'fair' price | Value status |
| :--- | :---: | :---: | :---: |
| **Shamrock Rovers (home)** | 1.75 | 1.87 | -EV |
| **Draw** | 3.30 | 3.31 | -EV |
| **Derry City (away)** | 4.50 | 6.13 | -EV |

Because the bookmaker's odds are below the Dixon-Coles projections across the board, Paddy Power has once more completely eliminated the value across the entire 1X2 market. 

Regarding the draw odds, while a market price of 3.30 is as good as identical to the ‘fair’ price of 3.31, it is still mathematically lower. By definition, a price below the model's ‘fair’ estimation still yields a negative expected value. 

> **Trading discipline:** Passing up a match where the bookmaker has eliminated all value is just as important as finding a +EV edge. What’s good for the bookmaker is not good for you!

## Methodological notes

A time-decay factor was intentionally omitted from this run. Because the 2026 League of Ireland season only kicked off in February – with just 106 of the 180 total games played to date – the sample size is fresh enough that artificially discounting early-season data would introduce unnecessary noise rather than predictive signal.
