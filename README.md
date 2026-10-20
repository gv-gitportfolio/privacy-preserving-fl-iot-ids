# Privacy-Preserving Federated Learning for IoT Intrusion Detection

**Federated Learning · Deep Learning · Cybersecurity · Privacy-Preserving AI**

[![DOI](https://img.shields.io/badge/DOI-10.1145%2F3695998-blue)](https://doi.org/10.1145/3695998)
[![Journal](https://img.shields.io/badge/ACM%20TOSEM-2025-green)](https://dl.acm.org/doi/full/10.1145/3695998)

A research showcase for our peer-reviewed study on privacy-preserving federated learning with a 1D CNN for intrusion detection in IoT networks.

## Publication

**Toward Enhancing Privacy Preservation of a Federated Learning CNN Intrusion Detection System in IoT: Method and Empirical Study**
D. Torre, A. Chennamaneni, J. Jo, G. Vyas, B. Sabrsula
*ACM Transactions on Software Engineering and Methodology*, Vol. 34, Issue 2, Article 53, January 2025
[Read the paper](https://dl.acm.org/doi/full/10.1145/3695998)

## My Contribution

- **Data preprocessing** for three of the seven datasets: **CIC IoMT 2024, RT-IoT 2022, and EdgeIIoT** (cleaning inconsistent values, handling missing data, removing empty columns, label encoding, Min-Max normalization)
- **Evaluation:** produced the classification metrics (accuracy, precision, recall, F1-score) for these three datasets
- **Writing:** contributed to sections of the paper draft

## Overview

Centralized intrusion detection can expose sensitive IoT traffic data. This work uses federated learning, where clients train local models and share only protected model parameters with a central server. Three privacy techniques are integrated:

- **Differential Privacy (DP):** adds calibrated noise to limit information leakage.
- **Diffie–Hellman Key Exchange:** establishes shared secrets for secure communication.
- **Homomorphic Encryption (HE):** enables supported computation on encrypted model parameters.

The study evaluates detection performance, federated learning execution time, privacy-related overhead, and comparisons with other AI-based intrusion detection systems.

## Experimental Setup

- **Model:** 1D CNN (input layer, Conv1D, max pooling, flatten, 128-unit ReLU dense layer, dropout, batch normalization, softmax output); Adam optimizer, categorical cross-entropy loss
- **Federation:** 4 clients, 1 central server, up to 10 iterations per client
- **Partitioning:** random sampling into 40 subsets (4 clients × 10 iterations); each subset split 75% train / 25% test
- **Design testing:** 5% of each dataset used during initial CNN development
- **Sampling:** no under- or over-sampling, to avoid overfitting and poor generalization
- **Metrics:** accuracy, precision, recall, F1-score, client computation time (CCT), time to receive federated data (TFD), local accuracy, federated accuracy

## Datasets

| Dataset | Approx. size | Preprocessing notes |
| --- | --- | --- |
| TON-IoT | 461,040 records | Used the `Train_Test_Network` set; label encoding |
| IoT-23 | 325.3M | Fixed string values, dropped empty columns; excluded Heartbeat, FileDownload, Mirai (few samples) |
| BoT-IoT | 73M | Converted hex/string port values, filled missing values, dropped empty columns |
| CIC IoT 2023 | 46.7M | Pre-processed CSVs; excluded Web-based and Brute-force attacks (few samples) |
| **CIC IoMT 2024** ★ | 9M | Label encoding, missing values filled, empty columns removed, Min-Max scaling |
| **RT-IoT 2022** ★ | 1.5M | Hex converted to integers, strings replaced, empty columns removed, label encoding, Min-Max scaling |
| **EdgeIIoT** ★ | 2.5M | Data cleansing, missing values filled, empty columns removed, column renaming, label encoding, Min-Max scaling |

★ = datasets I preprocessed and evaluated. Sizes are approximate source-dataset figures from the paper. Datasets are hosted by their providers and are not included here.

## Key Results

Average performance across the seven datasets (abstract):

| Metric | Result |
| --- | --- |
| Accuracy | 97.31% |
| Precision | 95.59% |
| Recall | 92.43% |
| F1-score | 92.69% |

- **Privacy cost:** enabling all three techniques added about **10%** computation time, with negligible change in local and federated accuracy.
- **Comparison:** competitive or superior accuracy against previously published AI-based IDS approaches on the same datasets.

### Accuracy by Dataset

From the paper's comparative evaluation section:

| Dataset | Accuracy |
| --- | --- |
| TON-IoT | 99.63% |
| IoT-23 | 99.99% |
| BoT-IoT | 100.00% |
| CIC IoT 2023 | 93.96% |
| **CIC IoMT 2024** ★ | 95.63% |
| **RT-IoT 2022** ★ | 99.47% |
| **EdgeIIoT** ★ | 89.12% |

*That section reports an overall average accuracy of 96.83% (F1 92.45%), while the abstract reports 97.31% (F1 92.69%). See the paper for the authoritative figures.*

### Dataset-Specific Findings

- **TON-IoT:** strong overall; weaker recall and F1 for the scarce MITM class.
- **IoT-23:** high accuracy; weaker detection of Command and Control attacks.
- **BoT-IoT:** excellent accuracy; some difficulty separating similar DoS and DDoS traffic.
- **CIC IoT 2023:** performance varies across attack classes.
- **CIC IoMT 2024 ★:** strong performance for several classes, with challenges for some denial-of-service attacks.
- **RT-IoT 2022 ★:** strong reported accuracy, with some reduction in recall for spoofing attacks.
- **EdgeIIoT ★:** strong performance on several classes, with MITM detection remaining a challenge.

High overall accuracy does not imply equally strong detection of every attack class, so per-class metrics matter.

## Figures

<!-- ![Framework](figures/framework.png) -->
<!-- ![CNN architecture](figures/cnn-architecture.png) -->
<!-- ![Results](figures/results.png) -->

*Figures reproduced from the published paper.*

## Implementation Environment

| Component | Specification |
| --- | --- |
| Language / IDE | Python 3.9.12, Jupyter Notebook |
| Libraries | TensorFlow 2.11.0, Keras 2.11.0, Scikit-learn 1.0.2, NumPy 1.23.5, Pandas 1.5.2 |
| System | Windows 10 Pro, Intel Core i7 (2.3 GHz), 64 GB RAM, NVIDIA GeForce RTX 2080 |
| Code size | About 2,895 lines across 20 Python files |

## Limitations

- Federated learning does not by itself prevent all information leakage through model updates.
- DP guarantees depend on the noise mechanism and configuration.
- Diffie–Hellman needs authentication and proper key management; HE does not remove risks tied to key ownership.
- Overall accuracy can hide weak detection of individual attack classes.

## Code Availability

This work was part of a federally funded university project, and the source code is not included in this repository. To request access or further information, please contact [University / Lab name] at [official contact].

## Citation

Torre, D., Chennamaneni, A., Jo, J., Vyas, G., & Sabrsula, B. (2025). Toward Enhancing Privacy Preservation of a Federated Learning CNN Intrusion Detection System in IoT: Method and Empirical Study. *ACM Transactions on Software Engineering and Methodology*, 34(2), Article 53. https://doi.org/10.1145/3695998

## Acknowledgment

Supported in part by the Air Force Research Laboratory (AFRL) and the Department of Homeland Security (DHS) Science and Technology Directorate under award FA8750-19-C-0077.

## Contact

[Your Name] · [LinkedIn] · [Email]




# Privacy-Preserving Federated Learning for IoT Intrusion Detection

**Federated Learning · Deep Learning · Cybersecurity · Privacy-Preserving AI**

[![DOI](https://img.shields.io/badge/DOI-10.1145%2F3695998-blue)](https://doi.org/10.1145/3695998)
[![Journal](https://img.shields.io/badge/ACM%20TOSEM-2025-green)](https://dl.acm.org/doi/full/10.1145/3695998)

A research showcase for our peer-reviewed study on privacy-preserving federated learning with a 1D CNN for intrusion detection in IoT networks.

## Publication

**Toward Enhancing Privacy Preservation of a Federated Learning CNN Intrusion Detection System in IoT: Method and Empirical Study**
D. Torre, A. Chennamaneni, J. Jo, G. Vyas, B. Sabrsula
*ACM Transactions on Software Engineering and Methodology*, Vol. 34, Issue 2, Article 53, January 2025
[Read the paper](https://dl.acm.org/doi/full/10.1145/3695998)

## My Role

[1–2 lines on your actual contribution, e.g., "Contributed to model development and experimental evaluation."]

## Overview

Centralized intrusion detection can expose sensitive IoT traffic data. This work uses federated learning, where clients train local models and share only protected model parameters with a central server. Three privacy techniques are integrated:

- **Differential Privacy (DP):** adds noise to limit information leakage.
- **Diffie–Hellman Key Exchange:** establishes shared keys for secure communication.
- **Homomorphic Encryption (HE):** enables computation on encrypted model parameters.

## Setup

- **Model:** 1D CNN (Conv1D, max pooling, 128-unit dense layer, softmax; Adam optimizer)
- **Federation:** 4 clients, 1 central server, up to 10 iterations per client
- **Data split:** 75% training / 25% testing per partition; no under- or over-sampling
- **Datasets (7):** TON-IoT, IoT-23, BoT-IoT, CIC IoT 2023, CIC IoMT 2024, RT-IoT 2022, EdgeIIoT
- **Stack:** Python 3.9, TensorFlow/Keras 2.11, Scikit-learn, NumPy, Pandas

## Key Results

Average performance across the seven datasets, as reported in the paper:

| Metric | Result |
| --- | --- |
| Accuracy | 97.31% |
| Precision | 95.59% |
| Recall | 92.43% |
| F1-score | 92.69% |

- **Privacy cost:** enabling all three techniques added about **10%** computation time, with negligible change in local and federated accuracy.
- **Class-level challenges:** limited samples for attacks such as MITM and C&C, and similarity between DoS and DDoS traffic, reduced detection for some classes.
- **Comparison:** competitive or superior accuracy against previously published AI-based IDS approaches on the same datasets.

## Figures

<!-- ![Framework](figures/framework.png) -->
<!-- ![CNN architecture](figures/cnn-architecture.png) -->

*Figures reproduced from the published paper.*

## Code Availability

This work was part of a federally funded university project, and the source code is not included in this repository. To request access or further information, please contact [University / Lab name] at [official contact].

## Citation

Torre, D., Chennamaneni, A., Jo, J., Vyas, G., & Sabrsula, B. (2025). Toward Enhancing Privacy Preservation of a Federated Learning CNN Intrusion Detection System in IoT: Method and Empirical Study. *ACM TOSEM*, 34(2), Article 53. https://doi.org/10.1145/3695998

## Acknowledgment

Supported in part by the Air Force Research Laboratory (AFRL) and the Department of Homeland Security (DHS) Science and Technology Directorate under award FA8750-19-C-0077.

## Contact

[Your Name] · [LinkedIn] · [Email]
