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


For B:
recall@1 = 18/60 = 0.3

recall@3 = (18+20) / 60 = 0.63 

recall@5 = (18+20+5) / 60 = 0.716



| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|----------|----------|----------|---|
| A | 0.5      | 0.66     | 0.73     |0.5946 |
| B | 0.3      | 0.63     | 0.716    |0.4651 |

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

95 % Wilson interval for hits out of n, with p = hits ÷ n and z = 1.96: centre = (p + z² ÷ 2n) ÷ (1 + z² ÷ n), half-width = z × √(p(1 − p) ÷ n + z² ÷ 4n²) ÷ (1 + z² ÷ n); interval = centre ± half-width.

| candidate | recall@k | lower  | upper  |
|---|----------|--------|--------|
| A, k=3 | 0.66     | 0.5406 | 0.7727 |
| A, k=5 | 0.73     | 0.6099 | 0.8287 |
| B, k=3 | 0.63     | 0.5068 | 0.7438 |
| B, k=5 | 0.716    | 0.5923 | 0.8149 |

### 1c. Annual model cost in USD

According to the DATA.md file:
- Requests per day: **10,500**, in the traffic shares above.
- System prompt: **194** tokens in every request.
- Price: **$2** per million input tokens, **$10** per million output tokens.
- Annual budget for this service (model calls only): **$32,700**.

To calculate annual cost of each candidate (the cost should not be higher than $32.700):

For A, k=3:
EN: 194 + 43 + 3 * 260 = 1017 
RU: 194+ 74 + 3 * 447 = 1609
KK: 194+ 163 + 3 * 985 = 3312

EN: (1017 * 2 + 138 * 10)/1 000 000 = 0,003414
RU: (1609 * 2 + 237 * 10)/1 000 000 = 0,005588
KK: (3312 * 2 + 523 * 10)/1 000 000 = 0,011854

0,23 * 0,003414 + 0,41 * 0,005588 + 0,36 * 0,011854 = 0,007344 $ (for 1 request)

0,007344 * 10 500 * 365 = 28,144.88 (for 1 year)


For A, k=5:
EN: 194 + 43 + 5 * 260 = 1540
RU: 194 + 74 + 5 * 447 = 2503
KK: 194 + 163 + 5 * 985 = 5282

EN: (1540 * 2 + 138 * 10)/1 000 000 = 0,00446 
RU: (2503 * 2 + 237 * 10)/1 000 000 = 0,007376
KK: (5282 * 2 + 523 * 10)/1 000 000 = 0,015794

0,23 * 0,00446 + 0,41 * 0,007376 + 0,36 * 0,015794 = 0,0097358
0,0097358 * 10 500 * 365 = 37,312.4535

The same mechanism for B, k=3 and B, k = 5.

| candidate | annual cost  |
|---|--------------|
| A, k=3 | $28,144.88   |
| A, k=5 | $37,312.4535 |
| B, k=3 | $18,422.60   |
| B, k=5 | $21,103.35   |

### 1d. Decision (at most 150 words)

Chosen candidate: The most suitable candidate is B,k=5 because its price is one of the lowest in this table, but at the same time it has second highest total recall. Only A,k=5 has more than it but due to the high cost that goes beyond the limits of $32,700, it cannot be used. 

The recall for B,5 by language is:
EN: 14/20 = 0.70
RU: 16/20 = 0.80
KK: 13/20 = 0.65

(Decision, using your intervals and the budget. Give the recall of your choice for EN, RU and KK separately.)

### 1e. Next measurement (at most 60 words)
Add about 200 test questions in Kazakh and recalculate the recall for B.5 and A.3. Currently, the KK interval for B.5 has a width of approximately 0.4. If the recall for B.5 in Kazakh remains below 0.7, while the recall for A.3 proves to be significantly higher, I will switch to A.3 or increase the 'k' value specifically for the Kazakh language.


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
