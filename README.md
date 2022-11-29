# answer-selection
New datasets for Answer Sentence Selection.

# Why?

Common datasets for Answer Sentence Selection (AS2) like WikiQA and TREC-QA are very small (a few thousand QA pairs) and are not challenging anymore. Some systems achiveve MAP > 92% on both datasets.

A recent large-scale dataset ([ASNQ](https://github.com/alexa/wqa_tanda)) shows that more data are needed to reach SOTA performance.
Inspired by how ASNQ was build starting from [Google's NQ](https://ai.google.com/research/NaturalQuestions/), we release 5 large-scale dataset for AS2 derived from [NewsQA](https://www.microsoft.com/en-us/research/project/newsqa-dataset/), [TriviaQA](https://nlp.cs.washington.edu/triviaqa/), [SearchQA](https://arxiv.org/abs/1704.05179) and [HotpotQA](https://hotpotqa.github.io).

We named those new dataset `NewsAS2`, `TriviaAS2`, `SearchAS2` and `HotpotAS2`.

**NOTICE**: in all datasets, the original validation set has been split in both dev and test to have non-hidden labels.


# How to

The dataset are available from the [Huggingface](https://huggingface.co) datasets repository.

First, install the `datasets` library with `pip install datasets --upgrade`.

Then, dowload the datasets with:
```python

from datasets import load_dataset

news_as2 = load_dataset('lucadiliello/news_as2')
trivia_as2 = load_dataset('lucadiliello/trivia_as2')
search_as2 = load_dataset('lucadiliello/search_as2')
hotpot_as2 = load_dataset('lucadiliello/hotpot_as2')

```

## Statistics

<table>
    <thead>
        <tr>
            <th rowspan=2>Dataset</th>
            <th colspan=2>Training set</th>
            <th colspan=2>Validation set</th>
            <th colspan=2>Test set</th>
        </tr>
        <tr>
            <th># Q</th>
            <th># QA pairs</th>
            <th># Q</th>
            <th># QA pairs</th>
            <th># Q</th>
            <th># QA pairs</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>NewsAS2</td>
            <td>71561</td><td>1840533</td><td>2102</td><td>51844</td><td>2083</td><td>51472</td>
        </tr>
        <tr>
            <td>TriviaAS2</td>
            <td>61688</td><td>1843349</td><td>3933</td><td>117012</td><td>3852</td><td>114853</td>
        </tr>
        <tr>
            <td>SearchAS2</td>
            <td>117220</td><td>3281909</td><td>8509</td><td>236360</td><td>8470</td><td>236792</td>
        </tr>
        <tr>
            <td>HotpotAS2</td>
            <td>72921</td><td>489238</td><td>2989</td><td>25295</td><td>2912</td><td>24846</td>
        </tr>
    </tbody>
</table>



## Baselines performance

- Best checkpoint selection on the MAP of the development set.
- 5 different runs with different random seeds.
- Standard deviation of results in round brackets.

### `NewsAS2`

| Model        | MAP        | MRR        | P@1        |
| ------------ | ---------- | ---------- | ---------- |
| RoBERTa Base | 82.4 (0.2) | 85.2 (0.3) | 76.4 (0.6) |
| ELECTRA Base | 82.0 (0.2)	| 84.8 (0.2) | 76.0 (0.2) |

### `TriviaAS2`

| Model        | MAP        | MRR        | P@1        |
| ------------ | ---------- | ---------- | ---------- |
| RoBERTa Base | 76.9 (0.6)	| 82.2 (0.5) | 73.1 (0.5) |
| ELECTRA Base | 73.3 (0.7)	| 79.1 (1.1) | 68.9 (1.3) |

### `SearchAS2`

| Model        | MAP        | MRR        | P@1        |
| ------------ | ---------- | ---------- | ---------- |
| RoBERTa Base | 84.1 (0.2)	| 88.1 (0.3) | 82.1 (0.5) |
| ELECTRA Base | 83.0 (0.1)	| 87.3 (0.2) | 80.3 (0.4) |

### `HotpotAS2`

| Model        | MAP        | MRR        | P@1        |
| ------------ | ---------- | ---------- | ---------- |
| RoBERTa Base | 92.6 (0.2) | 93.5 (0.2) | 90.4 (0.3) |
| ELECTRA Base | 92.9 (0.1)	| 93.5 (0.1) | 89.5 (0.1) |

