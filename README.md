# Open-Source Fraud Datasets for Machine Learning

A curated list of publicly available datasets for fraud detection and
anti-money-laundering (AML) research — real-world (anonymized),
synthetic-from-real, simulator-generated, and graph datasets — with
the papers that introduced or benchmarked them.

Part of the [ML / AI Engineer Roadmap](https://github.com/NanaAkwasiAbayieBoateng/ai-ml-engineer-roadmap)
portfolio. A machine-readable version of this list is in
[`datasets.csv`](datasets.csv).

## Real-world data (anonymized / masked)

### ULB–Worldline Credit Card Fraud
The de facto research benchmark. 284,807 European card transactions
over two days (Sept 2013), 492 frauds (0.172%); features are
PCA-masked (V1–V28) plus Time and Amount.

- **Source:** [Kaggle — mlg-ulb/creditcardfraud](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
- **Papers:** Dal Pozzolo et al., *Calibrating Probability with
  Undersampling for Unbalanced Classification* (IEEE CIDM 2015);
  Dal Pozzolo et al., *Learned Lessons in Credit Card Fraud Detection
  from a Practitioner Perspective* (Expert Systems with Applications,
  2014).

### IEEE-CIS Fraud Detection (Vesta)
Real e-commerce transactions from Vesta Corporation: 590,540
transactions, ~3.5% fraud, 394 features plus a linked identity/device
table. Released for the 2019 Kaggle competition.

- **Source:** [Kaggle competition — ieee-fraud-detection](https://www.kaggle.com/c/ieee-fraud-detection/overview)
- **Articles:** NVIDIA technical blog on the winning solution; core
  dataset in Amazon's Fraud Dataset Benchmark (below).

### Elliptic Bitcoin Dataset
Real Bitcoin transactions mapped to licit vs illicit entities:
203,769 transaction nodes, 234,355 payment flows, 166 features;
~2% labelled illicit. Also built into PyTorch Geometric.

- **Source:** Kaggle — "Elliptic Bitcoin Dataset"
- **Paper:** Weber et al., *Anti-Money Laundering in Bitcoin:
  Experimenting with Graph Convolutional Networks for Financial
  Forensics* (KDD 2019 workshop), arXiv:1908.02591.

### BitcoinHeist Ransomware Address Dataset
The full Bitcoin transaction graph (Jan 2009 – Dec 2018) reduced to
daily address snapshots: 2,916,697 rows, six graph features per
address (income, neighbors, weight, length, count, loops), labelled
by ransomware family — 28 families drawn from the Montreal,
Princeton, and Padua studies — or "white".

- **Source:** [UCI Machine Learning Repository — dataset 526](https://archive.ics.uci.edu/dataset/526/bitcoinheist+ransomware+dataset) ·
  Kaggle mirror ("BitcoinHeist Ransomware Dataset")
- **Paper:** Akcora, Li, Gel & Kantarcioglu, *BitcoinHeist:
  Topological Data Analysis for Ransomware Prediction on the Bitcoin
  Blockchain* (IJCAI 2020).

### Ethereum Fraud Accounts
Account-level aggregates over real Ethereum activity: 9,841 accounts
with transaction statistics (amounts sent/received, timing, contract
interactions), 2,179 labelled fraud (22.1%) from known
phishing/scam address lists.

- **Source:** [Kaggle — vagifa/ethereum-frauddetection-dataset](https://www.kaggle.com/datasets/vagifa/ethereum-frauddetection-dataset)
- **Use in research:** a standard small benchmark in Ethereum
  illicit-account detection papers and coursework.

### DGraph-Fin
Real user graph from the Finvolution P2P lending platform:
~3.7M nodes, ~4.3M directed edges, ~1.3% fraud.

- **Source:** DGraph project site (Finvolution)
- **Paper:** Huang et al., *DGraph: A Large-Scale Financial Dataset
  for Graph Anomaly Detection* (NeurIPS 2022 Datasets & Benchmarks).

## Synthetic, generated from real data or calibrated simulators

### BAF — Bank Account Fraud suite (Feedzai)
Six 1M-row datasets of bank account-opening applications,
CTGAN-generated from a real anonymized dataset, with controlled bias
variants, temporal drift, and protected attributes for fairness
testing.

- **Source:** [GitHub — feedzai/bank-account-fraud](https://github.com/feedzai/bank-account-fraud) ·
  [Kaggle mirror](https://www.kaggle.com/datasets/sgpjesus/bank-account-fraud-dataset-neurips-2022)
- **Paper:** Jesus et al., *Turning the Tables: Biased, Imbalanced,
  Dynamic Tabular Datasets for ML Evaluation* (NeurIPS 2022 Datasets
  & Benchmarks), arXiv:2211.13358.

### IBM Transactions for AML ("AMLworld")
Agent-based virtual world modelling the full money-laundering cycle
(placement, layering, integration). Six datasets (HI/LI ×
small/medium/large), up to ~180M transactions, with laundering
patterns labelled many steps removed from their source.

- **Source:** [Kaggle — ealtman2019/ibm-transactions-for-anti-money-laundering-aml](https://www.kaggle.com/datasets/ealtman2019/ibm-transactions-for-anti-money-laundering-aml)
- **Paper:** Altman et al., *Realistic Synthetic Financial
  Transactions for Anti-Money Laundering Models* (NeurIPS 2023
  Datasets & Benchmarks), arXiv:2306.16424.

### AMLSim (IBM)
The earlier open-source multi-agent AML simulator from IBM; the
1M-node / 9M-edge graph experiments in the paper below were generated
with it.

- **Source:** GitHub — IBM AMLSim; example datasets on Kaggle.
- **Paper:** Weber et al., *Scalable Graph Learning for Anti-Money
  Laundering: A First Look* (NeurIPS 2018 workshop), arXiv:1812.00076.

### PaySim
Mobile-money simulator calibrated on real logs from an African
operator: 6,362,620 transactions over 30 simulated days, 8,213
frauds (0.13%), concentrated in TRANSFER and CASH-OUT types. The same
author's BankSim covers bank transactions.

- **Source:** [Kaggle — ealaxi/paysim1](https://www.kaggle.com/datasets/ealaxi/paysim1)
- **Paper:** Lopez-Rojas, Elmir & Axelsson, *PaySim: A Financial
  Mobile Money Simulator for Fraud Detection* (EMSS 2016).

### BankSim
PaySim's sibling from the same author: an agent-based simulator of
bank payments calibrated on aggregated data from a Spanish bank.
The standard published run covers 180 simulated days: 594,643
payments, 7,200 fraudulent (~1.2%), with thieves stealing cards and
spending against merchant categories.

- **Source:** [Kaggle — ealaxi/banksim1](https://www.kaggle.com/datasets/ealaxi/banksim1/data)
- **Paper:** Lopez-Rojas & Axelsson, *BankSim: A Bank Payments
  Simulator for Fraud Detection Research* (EMSS 2014).

### AMLNet
A regulation-aware multi-agent generator aligned to Australia's
AUSTRAC rules: 1,090,173 synthetic transactions over 195 days,
1,745 labelled laundering (~0.16%), spanning placement, layering,
and integration plus structuring typologies. Released on Zenodo
(CC BY 4.0).

- **Source:** [Zenodo — doi:10.5281/zenodo.16736515](https://doi.org/10.5281/zenodo.16736515)
- **Paper:** Huda et al., *AMLNet: A Knowledge-Based Multi-Agent
  Framework to Generate and Detect Realistic Money Laundering
  Transactions* (2025 preprint, arXiv:2509.11595).

### SynthAML
Synthetic AML transactions built with a Danish bank to benchmark
detection methods — one of the few synthetic sets published as a
data descriptor in a Nature Portfolio journal, and used as an
external test set by later generators (e.g. AMLNet above).

- **Source:** Jensen et al., *A Synthetic Data Set to Benchmark
  Anti-Money Laundering Methods*, Scientific Data 10, 661 (2023),
  doi:10.1038/s41597-023-02440-4.

### SAML-D
Synthetic AML transaction-monitoring data: 9,504,852 transactions,
28 typologies (11 normal, 17 suspicious), ~0.104% suspicious.

- **Source:** [Kaggle — berkanoztas/synthetic-transaction-monitoring-dataset-aml](https://www.kaggle.com/datasets/berkanoztas/synthetic-transaction-monitoring-dataset-aml)
- **Paper:** Oztas et al., *Enhancing Anti-Money Laundering:
  Development of a Synthetic Transaction Monitoring Dataset*
  (IEEE ICEBE 2023), doi:10.1109/ICEBE59045.2023.00028.

### IBM Credit Card Transactions (TabFormer data)
24M+ synthetic card transactions from IBM's multi-agent simulation,
minimally obfuscated (real MCCs, amounts, fraud rates), spanning
decades of purchases.

- **Source:** [Kaggle — ealtman2019/credit-card-transactions](https://www.kaggle.com/datasets/ealtman2019/credit-card-transactions) ·
  [GitHub — IBM/TabFormer](https://github.com/IBM/TabFormer)
- **Papers:** Padhi et al., *Tabular Transformers for Modeling
  Multivariate Time Series* (ICASSP 2021); Altman, *Synthesizing
  Credit Card Transactions* (ACM ICAIF 2021).

### Sparkov-generated Credit Card Transactions
Simulated cards and merchants via Brandon Harris's Sparkov
generator: 1,296,675 train + 555,719 test transactions, 1,000
customers × 800 merchants, 2019–2020. Popular because its fields are
raw and interpretable (merchant, category, geography) where ULB and
IEEE-CIS mask theirs.

- **Source:** [Kaggle — kartik2112/fraud-detection](https://www.kaggle.com/datasets/kartik2112/fraud-detection)
  (generator: GitHub — namebrandon/Sparkov_Data_Generation)

### Fraud Detection Handbook simulated dataset
1.8M card transactions (Apr–Sep 2018) with customer/terminal
structure and known fraud scenarios, generated by the simulator
shipped with the book — the best resource here for learning
time-aware validation properly.

- **Source:** [GitHub — Fraud-Detection-Handbook/simulated-data-raw](https://github.com/Fraud-Detection-Handbook/simulated-data-raw)
- **Book:** Le Borgne, Siblini, Lebichot & Bontempi, *Reproducible
  Machine Learning for Credit Card Fraud Detection — Practical
  Handbook* (Université Libre de Bruxelles, 2022).

## Graph / review-fraud extensions

### Elliptic++ and Elliptic2
Elliptic++ extends Elliptic with address-level graphs (~823K
addresses) alongside the transaction graph (Elmougy & Liu, 2023).
Elliptic2 goes further: 122K labelled money-laundering subgraphs
over a 49M-cluster background graph.

- **Paper:** Bellei et al., *The Shape of Money Laundering:
  Subgraph Representation Learning on the Blockchain with the
  Elliptic2 Dataset* (2024), arXiv:2404.19109.

### xFraud (eBay)
Real e-commerce transaction networks from eBay, modelled as
heterogeneous graphs (transactions, addresses, payment tokens) with
up to ten million transactions. Ships with the xFraud detector and
its graph explainer.

- **Source:** [GitHub — eBay/xFraud](https://github.com/eBay/xFraud)
- **Paper:** Rao et al., *xFraud: Explainable Fraud Transaction
  Detection on Heterogeneous Graphs* (PVLDB 15(3), 2022),
  arXiv:2011.12193.

### T-Finance & T-Social
Two anonymized account networks from one online platform, with
expert annotations of anomalous accounts (fraud, money laundering,
online gambling). T-Finance is the transaction network — 39,357
accounts, 21.2M edges, 4.6% anomalous; T-Social is the friendship
network — 5.78M accounts, 73.1M edges, 3.0% anomalous. Both are part
of the GADBench graph-anomaly benchmark.

- **Source:** [GitHub — squareRoot3/Rethinking-Anomaly-Detection](https://github.com/squareRoot3/Rethinking-Anomaly-Detection)
- **Paper:** Tang, Li, Gao & Li, *Rethinking Graph Neural Networks
  for Anomaly Detection* (BWGNN, ICML 2022).

### YelpChi & Amazon review-fraud graphs
The standard GNN fraud benchmarks: YelpChi has 45,954 review nodes
at 14.5% fraud; Amazon (musical instruments) has 11,944 user nodes
at 9.5%. Distributed via DGL / PyTorch Geometric and the CARE-GNN
repository.

- **Paper:** Dou et al., *Enhancing Graph Neural Network-based Fraud
  Detectors against Camouflaged Fraudsters* (CARE-GNN, CIKM 2020);
  also PC-GNN (CIKM 2021) and most graph-fraud papers since.

## Adjacent fraud domains (insurance & healthcare)

### Healthcare Provider Fraud Detection Analysis (CMS Medicare)
US Medicare claims restructured for provider-level classification:
5,410 providers, ~558,000 inpatient/outpatient claims, 138,556
beneficiaries, with a `PotentialFraud` label on 9.4% of providers.
Used by dozens of papers and projects — with a caveat: the label is
per provider (not per claim) and its assignment method is
undocumented, so treat results on it as pipeline practice, not
evidence about real Medicare fraud rates.

- **Source:** Kaggle — "Healthcare Provider Fraud Detection
  Analysis" (rohitrox)

### Vehicle Insurance Claim Fraud (fraud_oracle.csv)
The long-circulating auto-claims teaching dataset: 15,420 claims,
32 mostly-categorical features, 923 labelled fraud (~6%). Its
original source was never documented — fine for modelling practice,
not for claims about real portfolios.

- **Source:** Kaggle — search "fraud_oracle" / "Vehicle Insurance
  Claim Fraud Detection"

## Meta-benchmark

### Amazon Fraud Dataset Benchmark (FDB)
A compilation that loads many of the datasets above (IEEE-CIS,
credit-card fraud, and more) with standardized features and
train/test splits, so models can be compared across datasets with
one API.

- **Source:** [GitHub — amazon-science/fraud-dataset-benchmark](https://github.com/amazon-science/fraud-dataset-benchmark)

## Notes on use

- Kaggle-hosted datasets require a free Kaggle account; competition
  data (IEEE-CIS) additionally requires accepting the competition
  rules on the competition page before the API will download it.
- "Real" here means real transactions with anonymization applied
  (PCA masking, GAN generation, or feature suppression) — always
  check each source's licence and citation request before publishing
  results.
- Fraud rates, sizes, and splits quoted above are from the dataset
  papers and data cards linked for each entry.
