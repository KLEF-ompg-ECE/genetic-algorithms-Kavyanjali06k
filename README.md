# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :** Angirekula Kavyanjali
**Student ID    :** 2310040033
**Date Submitted:** 17-03-2026

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

```
[The fitness() function returns the total value (profit) of selected items in the knapsack solution. If the total weight exceeds the allowed capacity, it returns 0. This penalizes invalid (overweight) solutions so they are not selected in future generations.]
```

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

```
[ tournament_select() randomly picks a small group of individuals and selects the one with the highest fitness among them. Since selection is based on fitness comparison, individuals with higher fitness have a greater chance of winning the tournament and being chosen.]
```

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

```
[This line copies the best chromosome from the current generation into the next generation (elitism). It ensures the best solution is not lost due to crossover or mutation, helping the algorithm retain progress and converge faster.]
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of generations | 50|
| Best value at generation 1 | 60|
| Final best value | 77|
| Total weight of best solution (kg) | 14.4/15.0 kg|
| Is solution valid (Yes / No) |yes |

**Copy the printed packing list here:**
```
Best Packing List
--------------------------------------
  + Water bottle
  + First aid kit
  + Sleeping bag
  + Torch
  + Energy bars (x6)
  + Rain jacket
  + Map & compass
  + Cooking stove
  + Rope (10 m)
  + Sunscreen
  + Power bank
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
[ The biggest improvement happens in the first few generations (around 0–5), where the best value quickly rises from about 60 to around 75+. After that, the curve shows only small improvements and eventually flattens around 77, indicating the algorithm has converged. This means further generations are not significantly improving the solution.]
```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve |
|--------------|-----------------|-------------|--------|----------------|
| 0.01         |       75        |14.9/15.0 kg |  yes   |Step function   |
| 0.05         |       77        |14.4 /15.0 kg|  yes   |Staircase curve- multiple steps|
| 0.30         |       78        |14.1/15.0 kg |  yes   |Noise-Fluctuating step curve   |

**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
[When the mutation rate is too low (0.01), the algorithm quickly converges but gets stuck early due to lack of diversity. With a moderate mutation rate (0.05), the algorithm balances exploration and exploitation, leading to steady improvements and a better final solution. When the mutation rate is too high (0.30), the search becomes more random, causing fluctuations and slower convergence. The sweet spot is around 0.05, where the algorithm explores enough without losing good solutions.]
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
[The mutation_rate = 0.05 gave the best result. This is because it maintains a good balance between exploration (finding new solutions) and exploitation (refining existing good solutions), leading to higher final fitness.]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 |77|this gives best convergence and solution quality|
| 2 — Mutation rate | mutation_rate =0.01|75-78|Too low causes early stagnation; too high increases randomness|

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
[The most important thing I learned is that parameter tuning, especially mutation rate, is critical in Genetic Algorithms. A very low mutation rate reduces diversity and causes premature convergence, while a very high mutation rate makes the search unstable and random. The best performance comes from a balanced mutation rate that allows both exploration and exploitation. This shows that Genetic Algorithms are powerful but highly sensitive to parameter settings.]
```

---

## Submission Checklist

- [x] Student name and ID filled in
- [x] Q1, Q2, Q3 answered
- [x] Experiment 1: table filled, packing list pasted, plot observation written
- [x] Experiment 2: results table filled (3 rows), observation and answer written
- [x] Summary table completed and reflection written
- [x] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
