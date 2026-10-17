# Midterm 1: answers

GitHub username: Nurdaulet978
Session code: my_data/DATA.md, my_data/retrieval_ranks.csv and my_data/doc_results.csv
Fingerprint:  bcb6a68a

> Fill in the three lines above from `my_data/DATA.md`. Do not rename headings or table columns: a script reads the numbers.
> Write only in the empty cells and lines. Percentages as 0.78 or 78 %, money as plain numbers.

## AI-use declaration

(About half a page: which assistants or tools you used and for what. If you used none, say so.)

## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

recall@k = (number of questions whose correct chunk has rank ≤ k) ÷ 60
MRR@10 = (1 ÷ 60) × the sum of 1 ÷ rank over questions with rank ≤ 10 (rank 11 adds nothing).

For A:
recall@1 = 30/60 = 1/2 = 0.5
recall@3 = (10+30) / 60 = 40/60 = 0.66
recall@5 = (10+30+4) / 60 = 0.73
MRP@10 = 

For B:
recall@1 = 18/60 = 0.3
recall@3 = (18+20) / 60 = 0.63 
recall@5 = (18+20+5) / 60 = 0.716



| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|----------|----------|----------|---|
| A | 0.5      | 0.66     | 0.73     | |
| B | 0.3      | 0.63     | 0.716    | |

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 | | | |
| A, k=5 | | | |
| B, k=3 | | | |
| B, k=5 | | | |

### 1c. Annual model cost in USD

| candidate | annual cost |
|---|---|
| A, k=3 | |
| A, k=5 | |
| B, k=3 | |
| B, k=5 | |

### 1d. Decision (at most 150 words)

Chosen candidate:

(Decision, using your intervals and the budget. Give the recall of your choice for EN, RU and KK separately.)

### 1e. Next measurement (at most 60 words)

## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H | | | | | | |
| L | | | | | | |

Personal-data pages per year sent abroad under H:

### 2b. Memo (at most 300 words)

## Part 3: Explain your own numbers

### Q1

Number:
Why (at most 40 words):

### Q2

Number:
Why (at most 40 words):

### Q3

Number:
Why (at most 40 words):

### Q4

Number:
Why (at most 40 words):

### Q5

Number:
Why (at most 40 words):
