# Data Science Challenge

### Question 1
There is a laundry bin with 20% blue socks.
You randomly draw 10.
What is the probability that 2 are blue?

Answer: The probability of getting a blue ball can be obtained from:
P(blue) = nCkpk(1-p)(n-k) 

Here, n = 10 randomly drawn balls 
k=2 to find the probability of finding 2 out of 10 drawn balls 
p is the probability of ball being blue. 
Here,
P(blue) = 10!/2!*8!x(0.2)2x(0.8)8
	  = 0.3019

### Question 2
Out of a set of 1000 emails, 700 are spam.
400 of the emails have the word "free"; 300 of those are spam.
100 of the emails have the word "credit"; 90 of those are spam.
You get an email that contains both "free" and "credit".
What is the probability it is spam?

Answer: We know that,
Probability of spam mail = 700/1000 = 0.7
Probability of having �free� in given spam mail = 300/700 = 0.4286
Probability of having �credit� in given spam mail = 90/700 = 0.1286
Probability of having �free� and �credit� given spam = 0.4286*0.1286 �(1)
Probability of having �free� = 400/1000 = 0.4
Probability of having �credit� = 100/1000 = 0.1
Probability of having �free� and �credit� = 0.4*0.1 �(2)

To find probability of credit given that mail contains �free� and �credit�:

P(S|F and C) = P(F and C|S)*P(S)/P(F and C) � (3 - Bayes� rule)
P(S|F and C) = (3/7*9/70)*(7/10)/(4/10*1/10) = 96.43%

### Question 3
Using `scatter.csv`: how do you interpret the linear regression? (Answer in Jupyter notebook)

### Question 4
Using `scatter.csv`: Plot a histogram of the x values.

### Question 5
SQL: There are two tables.
One table contains a list of tests and the other contains the positive results of the tests.
Positives and tests are matched by their ID.
There is at most one positive matching to a test.

Tables:
```
test:
	column: name = 'id', type = int
	column: name = timestamp, type = timestamp
	
positive:
	column: name = 'id', type = int
```
Write an SQL query that shows the daily positive rate.

Example output of your query would look something like:
```
| date       | rate |
----------------------
| 2022-01-01 | 0.23 |
| 2022-01-02 | 0.33 |
... etc.
```

Answer: 
SELECT t.timestamp as date, (COUNT(p.id)/COUNT(t.id)) as rate
FROM test t LEFT JOIN positive p ON (p.id = t.id)
GROUPBY t.timestamp 

### Challenge 6
Train a prediction model with `train.csv` using the final column as the labels.
Use this model to create labels for the entries in `test.csv`.
Though the labels in `train.csv` are 0/1, the labels created for `test.csv` can be continuous [0 to 1].
Output should be a file called `labels.txt`.
Each line of `labels.txt` is a predicted label for the corresponding line in `test.csv`.
For example, `labels.txt` line 6 will be the predicted label for line 6 in `test.csv`.
The contents of `labels.txt` will look something like:
```bash
0.5355877
0.128361
0.2841359
0.4216329
...etc
```
The quality of the predictions will be judged by RMSE.
Please include the source code used to create your model as well as a write-up of your technique.


