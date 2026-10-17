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

Overall accuracy = sum of n_correct / sum of n_docs 
For H: 163/180 = 0.9056

For L: 148/180 = 0.8222 

Weakest cell (language, condition)

For each cell i of pipeline P:

accuracy_i = n_correct_i ÷ n_docs_i

weakest cell = the cell with min(accuracy_i)

H: KK, degraded, 21 ÷ 30
L: KK, degraded, 21 ÷ 30

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|------------------|----------------------|-------------|---|---|---|
| H | 0.9056           | KK, degraded | 21/30 = 0.7 |0.5212 |0.8334 |29 105.10 |
| L | 0.8222           | KK, degraded | 21/30 = 0.7 |0.5212 |0.8334 |10 800 |

Personal-data pages per year sent abroad under H:

### 2b. Memo (at most 300 words)
Recommendation: Pipeline L

### Who gets the worst results?

Pipeline H has higher overall accuracy than L (0.9056 vs. 0.8222), but this does not mean it works better for everyone. Both pipelines perform worst on Kazakh invoices with poor-quality scans: they correctly process 21 out of 30 invoices (70%). The 95% confidence interval is [0.52; 0.83] for both pipelines, so H does not improve results for this group. 
Pipeline L also has lower accuracy on poor-quality Russian (0.77) and English (0.80) scans. However, each group has only 30 invoices, so I cannot be completely sure about these differences.

### Personal data

About 28% of pages contain a person's name and IIN. Under pipeline H, around 613,200 pages per year would leave Kazakhstan. There are three important questions about personal data: Where is it sent? Who stores it? How long is it kept?
With H, the scans are sent to a foreign data centre, and I do not know how long the provider keeps them. With L, the scans stay on our server in Kazakhstan, and the bank controls how long they are stored.
Before using H, I would need to check how the provider stores data, whether it uses the data to train its models, and whether sending the data abroad follows Kazakhstan's Law No. 94-V. A statement from the provider alone does not prove that everything meets legal requirements.

### How to protect personal data

For pipeline L, I would allow access only to approved staff, automatically delete scans after 30 days, and check access logs every month. If we use H, the contract must clearly state that the provider cannot store the scans or use them for training. I would also hide parts of the IIN before sending the scans and check a sample of processed pages every month.

### Final choice

I would choose pipeline L. It costs $10,800 per year, compared with $29,105 for H, and keeps personal data inside Kazakhstan.
The main disadvantage is that L makes more extraction mistakes, especially on poor-quality scans. To reduce this problem, I would send low-confidence results and poor-quality Kazakh scans for manual review. I would also test the pipeline on more invoices to get a clearer picture of its accuracy.

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
