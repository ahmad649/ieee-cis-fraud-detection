# IEEE-CIS Fraud Detection Dataset

This project uses the IEEE-CIS Fraud Detection dataset from Kaggle.

## Download Instructions

1. Create or sign in to your Kaggle account.

2. Visit the dataset page:

   https://www.kaggle.com/competitions/ieee-fraud-detection

3. Download the competition files.

4. Extract the downloaded archive.

5. Place the following files inside the `data/` directory:

```
data/
├── train_transaction.csv
├── train_identity.csv
├── test_transaction.csv
├── test_identity.csv
└── sample_submission.csv
```

## Expected Directory Structure

```
project-root/
├── data/
│   ├── train_transaction.csv
│   ├── train_identity.csv
│   ├── test_transaction.csv
│   ├── test_identity.csv
│   └── sample_submission.csv
├── notebook/
├── report/
└── README.md
```

## Notes

The dataset is not included in this repository because of Kaggle's competition data distribution policies and file size limitations.

After downloading the dataset and placing the files in `data/`, update the notebook paths if necessary:

```python
base_path = "../data/"

transaction_train = pd.read_csv(base_path + "train_transaction.csv")
identity_train = pd.read_csv(base_path + "train_identity.csv")
```
