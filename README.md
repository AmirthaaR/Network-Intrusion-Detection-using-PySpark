# Network Intrusion Detection using PySpark

## Overview
A big-data machine learning project that classifies network traffic as **BENIGN** or **DDoS** using Apache Spark's MLlib. The project demonstrates distributed data processing, data cleaning, model training, feature importance analysis, and classification evaluation.

## Objectives
- Process network traffic data using PySpark.
- Clean missing and infinite numeric values.
- Build a binary network traffic classifier.
- Compare Random Forest with Logistic Regression.
- Evaluate predictions using accuracy, precision, recall, F1-score, and a confusion matrix.
- Explore the most influential traffic features.

## Dataset
- **Dataset:** CIC-IDS2017
- **Selected file:** Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv
- **Original records:** 225,745
- **Input features:** 78
- **Target:** BENIGN or DDoS

Dataset source: [CIC-IDS2017 — Canadian Institute for Cybersecurity](https://www.unb.ca/cic/datasets/ids-2017.html)

## Technologies
- Python
- Apache Spark / PySpark
- Spark MLlib
- Pandas
- Google Colab

## Methodology
1. Load the network traffic CSV into a Spark DataFrame.
2. Inspect the schema and class distribution.
3. Clean column names and handle missing and infinite numeric values.
4. Convert class labels into numeric labels.
5. Split the data into training and test sets.
6. Train a Random Forest classifier using Spark MLlib.
7. Train Logistic Regression as a baseline.
8. Evaluate model predictions and inspect the confusion matrix.
9. Analyze Random Forest feature importance.
10. Repeat evaluation after removing exact duplicate feature records.

## Results

| Model / evaluation | Accuracy | F1-score |
|---|---:|---:|
| Logistic Regression baseline | 98.44% | 98.44% |
| Random Forest — deduplicated dataset | 99.98% | 99.98% |

For the deduplicated Random Forest test split, 44,562 records were evaluated:
- Correct predictions: 44,561
- Incorrect predictions: 8

*Note: Verify these counts against the saved notebook output before publishing. The reported confusion matrix totals 44,562 records, with 8 errors.*

## Feature Importance
The leading features in the initial Random Forest model included:
- Fwd_Packet_Length_Max
- Total_Length_of_Fwd_Packets
- Avg_Fwd_Segment_Size
- Fwd_Packet_Length_Mean
- Init_Win_bytes_forward

Feature importance indicates model reliance, not causation.

## Limitations
- Evaluation uses a single DDoS-focused file from CIC-IDS2017.
- Random train/test splitting may place highly similar traffic records in both sets.
- Deduplication reduces exact duplicate records but does not eliminate near-duplicate traffic or establish generalization to new networks.
- Results should not be interpreted as production-ready intrusion detection performance.

## How to Run
1. Open the notebook in Google Colab.
2. Install PySpark if it is not already available.
3. Download the dataset from the official CIC-IDS2017 source or its dataset mirror.
4. Upload the CSV to the notebook environment.
5. Run the notebook cells in order.

## Future Improvements
- Evaluate on a separate capture or day.
- Compare additional intrusion classes.
- Tune model parameters using a validation set.
- Track training time and inference performance.
- Investigate feature scaling and feature-selection strategies.

## Author
Developed as a practical big-data machine learning project using PySpark and Spark MLlib.
