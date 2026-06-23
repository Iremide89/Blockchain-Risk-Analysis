# Blockchain-Risk-Analysis

## Author

Ajibola Abiodun Iremide


## Project Overview

This project applies network analytics and fraud detection techniques to the Elliptic Bitcoin Transaction Dataset to identify high-risk transactions, suspicious transaction patterns, and potential money laundering behaviour within a cryptocurrency network.

The objective was to answer the question:

> Who are the riskiest nodes in the network, and how are they connected?

The analysis combines graph theory, centrality measures, fraud pattern detection, and interactive dashboard development to support compliance monitoring and financial crime investigations.


## Business Problem

Cryptocurrency transaction networks can be used to conceal illicit financial activities through complex transaction flows. Traditional transaction monitoring methods often fail to identify suspicious relationships between transactions.

This project uses network analysis techniques to:

* Identify high-risk transactions
* Detect layering behaviour
* Detect fan-out transaction patterns
* Prioritise suspicious transactions for investigation
* Support compliance and anti-money laundering (AML) monitoring

## Dataset

### Elliptic Bitcoin Transaction Dataset

The dataset contains Bitcoin transaction records classified as:

* Illicit
* Licit
* Unknown

### Network Statistics

| Metric                  | Value          |
| ----------------------- | -------------- |
| Total Transactions      | 203,769        |
| Total Transaction Links | 234,355        |
| Network Type            | Directed Graph |


## Methodology

### 1. Network Construction

* Built a directed transaction graph
* Nodes represent transactions
* Edges represent transaction flows
* Added transaction class labels and time steps

### 2. Subgraph Selection

To improve analytical efficiency:

* Randomly sampled 20,000 nodes
* Computed betweenness centrality
* Selected Top 50 influential nodes
* Extracted an ego network
* Expanded until a meaningful analytical subgraph was obtained

### Final Analytical Subgraph

| Metric | Value |
| ------ | ----- |
| Nodes  | 5,207 |
| Edges  | 6,431 |

### 3. Centrality Analysis

Computed:

* In-Degree Centrality
* Out-Degree Centrality
* Betweenness Centrality
* PageRank

A Composite Risk Score was developed using normalized centrality metrics to identify the highest-risk transactions.

### 4. Fraud Pattern Detection

#### Layering Behaviour

Transactions receiving funds from many sources and redistributing them to multiple destinations.

**Results**
63 Layering Candidates Identified

Top Layering Node:

| Node ID  | Sources | Destinations |
| -------- | ------- | ------------ |
| 38688623 | 98      | 15           |

#### Fan-Out Behaviour

Transactions sending funds to large numbers of destinations.

**Results**

* 160 Fan-Out Candidates Identified

Top Fan-Out Node:

| Node ID | Destinations |
| ------- | ------------ |
| 102570  | 122          |

## Key Findings

### Highest Risk Transactions

| Transaction ID | Risk Score | Class   |
| -------------- | ---------- | ------- |
| 38688623       | 0.619      | Licit   |
| 36364435       | 0.515      | Licit   |
| 225859042      | 0.450      | Unknown |

### Risk Overlap Analysis

* 9 Layering Nodes appeared in the Top 20 Risk Transactions.
* 8 Fan-Out Nodes appeared in the Top 20 Risk Transactions.

These findings suggest that structurally important transactions are more likely to exhibit suspicious behaviour.


## Dashboard

The project includes an interactive fraud monitoring dashboard featuring:

* Interactive Network Graph
* Top 20 Risk Transactions
* Transaction Activity Timeline
* Executive Risk Summary
* Fraud Pattern Analysis
* Network Classification Overview



## Technologies Used

* Python
* Pandas
* NumPy
* NetworkX
* PyVis
* Plotly
* Google Colab

---

## Project Files
Stage7_Fraud_Network_Analysis.ipynb
fraud_dashboard.html
network_component.html
Business_Report.pdf

## Recommendations

### Recommendation 1

Implement enhanced monitoring of transactions exhibiting both layering and fan-out characteristics.

**Owner:** Head of Transaction Monitoring

### Recommendation 2

Conduct targeted investigations of high-risk unknown-class transactions identified through network analysis.

**Owner:** Financial Crime Investigation Team

---

## Data Limitation

A significant proportion of transactions were classified as unknown.

| Class   | Count |
| ------- | ----- |
| Unknown | 3,364 |
| Licit   | 1,802 |
| Illicit | 41    |

As a result, suspicious behaviour was identified primarily through network position and transaction activity rather than confirmed fraud labels.

---

## Repository Structure

```text
Elliptic-Bitcoin-Fraud-Network-Analysis/

├── README.md
├── Stage7_Fraud_Network_Analysis.ipynb
├── fraud_dashboard.html
├── Business_Report.pdf
├── images/
│   ├── dashboard.png
│   └── risk_table.png


## Author

**Ajibola Abiodun Iremide**

Data Analyst | Network Analytics | Fraud Detection | Compliance Analytics
