# Datasets

This project reproduces HTTP2vec on the **CSIC 2010 HTTP** dataset only.

## CSIC 2010

The dataset consists of three plain-text files of raw HTTP requests:

| File                       | Content                  | Count  | Used for                          |
| -------------------------- | ------------------------ | ------ | --------------------------------- |
| `normalTrafficTraining.txt`| normal requests          | 36,000 | tokenizer + RoBERTa MLM training  |
| `normalTrafficTest.txt`    | normal requests          | 36,000 | inference / classification (label 0) |
| `anomalousTrafficTest.txt` | anomalous (attack) requests | 25,065 | inference / classification (label 1) |

These counts match Table 1 of the paper.

## How to obtain it

1. Official source (Spanish Research National Council, CSIC):
   https://www.tic.itefi.csic.es/dataset/
2. Place the three `.txt` files directly in this folder:

```
data/raw/normalTrafficTraining.txt
data/raw/normalTrafficTest.txt
data/raw/anomalousTrafficTest.txt
```

Alternatively run the helper (downloads only over HTTPS, verifies the files land in `data/raw/`):

```
python scripts/download_data.py --dest data/raw
```

If the automatic download fails (the upstream host occasionally changes), download
the files manually from the official page and drop them into `data/raw/`.

## Notes

- Raw data files are intentionally **not** committed; keep them local.
- The requests contain real attack payloads (SQL injection, XSS, CRLF, etc.).
  They are always handled as opaque text and are never executed or rendered.
