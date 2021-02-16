# Lab 1 Webpage

## Questions

What would be the most commonly used level of measurement if the variable is the temperature of the air?

Answer: The temperature of air would be an interval level of measurement, because it is a numerical value where differences make sense in the context of using them.

Write a Python code to import the data file 'L1data.csv' (introduced in Lecture 1) and code an imputation for replacing the NaN values in the "Age" column with the median of the column. The NaN instances are replaced by:

```markdown
import numpy as np
import pandas as pd
data = pd.read_csv("L1Data.csv")

from sklearn.impute import SimpleImputer
imp = SimpleImputer(missing_values = np.nan, strategy = 'median')
imp.fit(data.loc[:,['Age']])
data.loc[:,['Age']] = imp.transform(data.loc[:,['Age']])
data.loc[:,['Age']]
```
Answer: 21.0

In Bayesian inference the "likelihood" represents: 

Answer: How probable is the data (evidence) given that our hypothesis is true.

The main goal of Monte Carlo simulations is to solve problems by approximating a probability value via carefully designed simulations.

Answer: True

Assume that during a pandemic 15% of the population gets infected with a respiratory virus while about 35% of the population has some general respiratory symptoms such as sneezing, stuffy nose etc. Assume that approximately 30% of the people infected with the virus are asymptomatic. What is the probability that someone who has the symptom actually has the disease?

Answer: According to the Bayesian Theoreom, you need to utilize the conditional probability rule. For this scenario, multiple 0.15 by 0.70 (percentage of symptomatic people with the virus) and then divide by 0.35, which is the percentage of the population with some general respiratory symptoms. The answer would then be 0.30 or 30%.

A Monte Carlo simulation should never include more than 1000 repetitions of the experiment.

Answer: False

One can decide that the number of iterations in a Monte Carlo simulation was sufficient by visualizing a Probability-Iteration plot and determining where the probability graph approaches a horizontal line.

Answer: True

Assume we play a slightly bit different version of the original Monte Hall problem such as having four doors one car and three goats. The rules of the game are the same, the contestant chooses one door (that remains closed) and one of the other doors who had a goat behind it is being opened. The contestant has to make a choice as to stick with the original choice or rather switch for one of the remaining closed doors. Write a Python code to approximate the winning probabilities, for each choice, by the means of Monte Carlo simulations. The probability that the contestant will ultimately win by sticking with the original choice is closer to:

```markdown
%matplotlib inline
%config InlineBackend.figure_format = 'retina'
import matplotlib as mpl
mpl.rcParams['figure.dpi'] = 150

import random
import matplotlib.pyplot as plt

doors = ["goat","goat","goat", "car"]

# approximated results
switch_win_probability = []
stick_win_probability = []

plt.axhline(y=0.66, color='red', linestyle='--')
plt.axhline(y=0.33, color='green', linestyle='--')

def monte_carlo(n):

  switch_wins = 0
  stick_wins = 0

  for i in range(n):
     random.shuffle(doors)

     k = random.randrange(4)

     if doors[k] != 'car':
       switch_wins +=1
    
     else:
       stick_wins +=1
    
     switch_win_probability.append(switch_wins/(i+1))
     stick_win_probability.append(stick_wins/(i+1))
    
  plt.plot(switch_win_probability,label='Switch')
  plt.plot(stick_win_probability,label='Stick')
  plt.tick_params(axis='x', colors='navy')
  plt.tick_params(axis='y', colors='navy')
  plt.xlabel('Iterations',fontsize=14,color='DeepSkyBlue')
  plt.ylabel('Probability of Winning',fontsize=14,color='green')
  plt.legend()
  print('Winning probability if you always switch:', switch_win_probability[-1])
  print('Winning probability if you always stick to your original choice:', stick_win_probability[-1])

monte_carlo(3000)
```
Answer: 25% (Original: 0.25433333)

In Python one of the libraries that we can use for generating repeated experiments in Monte Carlo simulations is:

Answer: random

In Python, for creating a random permutation of an array whose entries are nominal variables we used:

Answer: random.shuffle

### NOTE: random.randrange is incorrect, because its entries are numerical variables! 

Be very careful about which variables are being input
