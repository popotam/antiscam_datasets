# antiscam_datasets

## Datasets

* reddit_2014-02-19 - upvoted comments from top rated topic on Reddit
* reddit_2015-06-23 - upvoted comments from top rated topic on Reddit
* reddit_2016-06-21 - upvoted comments from top rated topic on Reddit
* quora_2016-06-21 - top answers from top questions on top topics on Quora
* spam_trap_2014-02-06 - spam comments collected by honeypot farm of WordPress instances

## Files

Each dataset consists of the following files:

* **{dataset}.json.gz** - a compressed file with a list of newline separated JSON documents. This is considered RAW data.
* **{dataset}.labels.csv.gz** - a compressed CSV file with document labels (0=not_spam, 1=spam)
* **{dataset}.datetimes.csv.gz** - a compressed CSV file with document creation time in ISO format
* **{dataset}.features.csv.gz** - a compressed CSV file with feature vectors for each document
* **{dataset}.features.normalized.csv.gz** - a compressed CSV file with normalized feature vectors for each document
* **{dataset}.normalization.csv.gz** - a compressed CSV file with description of each normalization
* **README.md** - a description of a dataset

## Normalization

**{dataset}.features.normalized.csv.gz** files are normalized using the following pseudo code (Python3):

```python

def normalize(value, normalization):
    if normalization.stddev == 0.0:
        return 0.0
    if normalization.is_log:
        value = math.log1p(value)
    return (value - normalization.avg) / normalization.stddev
    
```

where normalization attributes are defined as columns in the CSV file:

| name | is_log | avg | stddev |
| ---- | ------ | --- | ------ |
| name of a feature | should value be logarithmized {True\|False} | average value of a feature | standard deviation of a feature |

Note that Python's math.log1p adds 1.0 before logarithmizing.
