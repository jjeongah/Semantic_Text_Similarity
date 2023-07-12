# Semantic Text Similarity (STS)

## Project Description

Semantic Text Similarity (STS) is an NLP task that measures the similarity between multiple sentences and provides a linear numerical representation of their similarity.

In this project, we aim to build an AI model that takes two sentences as input and measures how semantically similar they are on a scale of 0 to 5.

#### [Wrap up report](https://www.notion.so/STS-d6489847c32c41bc9737b7fc82639eb8?pvs=4)

<br/>

## Dataset 
| Dataset            | Train                    | Dev | Test |
| ------------------ | ----------------------- | --------------: | -----------: |
| **Number of Sentences**        | 9324      |           550 |       1100 |
| **Ratio**        | 85      |           5 |       10 |

<br/>

### Columns
* **id** (string): Unique ID for each sentence, in the format "dataset-name-version-train/dev/test-number"

* **source** (string): The source of the sentence

    * **petition**: Title data from the Korean National Petition Board

    * **NSMC**: Naver Sentiment Movie Corpus

    * **slack**: Data from Upstage Slack

* **sentence1** (string): The first sentence in the sentence pair

* **sentence2** (string): The second sentence in the sentence pair

* **label**: The similarity score between the sentence pair, ranging from 0 to 5 with one decimal place
    * 5: The two sentences have the same core content, including minor details.

    * 4: The two sentences have equivalent core content, with minor differences in additional details.

    * 3: The two sentences have roughly equivalent core content, but there are noticeable differences in additional details.

    * 2: The two sentences do not have equivalent core content, but share some additional details.

    * 1: The two sentences do not have equivalent core content, but cover similar topics.

    * 0: The two sentences do not have equivalent core content and do not share any common details.

* **binary-label**: Binary label derived from the similarity score, where similarity scores of 2 or below are converted to 0, and scores of 3 or above are converted to 1.

<br/>

## Set up

### 1. Requirements

```bash
$ pip install -r requirements.txt
```

### 2. Prepare the dataset

```bash
Add train.csv, dev.csv, and test.csv to the data/raw_data folder.
```

<br/>

# How to Run

## How to train

```bash
$ sh train.sh
```

<br/>

## How to sweep hyperparameter tuning
```bash
$ sh sweep.sh

# Launch agents
## For Bayesian or random search, you can limit the number of training iterations with LIMIT_NUM.
$ wandb agent --count [LIMIT_NUM] [SWEEPID] 
```

## How to sweep Contrastive Learning
```bash
$ sh cl_sweep.sh

# Launch agents
## For Bayesian or random search, you can limit the number of training iterations with LIMIT_NUM.
$ wandb agent --count [LIMIT_NUM] [SWEEPID] 
```
