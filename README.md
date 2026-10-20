# privacy-preserving-fl-iot-ids
Privacy-preserving federated learning for CNN-based IoT intrusion detection. Research showcase (ACM TOSEM 2025). Code not public.
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
