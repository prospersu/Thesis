# Effective Hardware Block Design Modifications for Neural Network Performance on FPGAs

[cite_start]This repository contains the research and implementation for the thesis, "Effective Hardware Block Design Modifications: Impact on Neural Network Performance"[cite: 3]. The project demonstrates how direct, low-cost modifications to FPGA hardware blocks can significantly improve the accuracy of quantized neural networks (QNNs) with only a minimal increase in resource utilization.

[cite_start]The core methodology involves transitioning a **Binarized Neural Network (BNN)** to a **Ternary Neural Network (TNN)** by applying weight randomization techniques within the Matrix-Vector Activation Unit (MVAU)[cite: 31, 128].

---

## 📖 Project Overview

[cite_start]Deploying neural networks on FPGAs offers high performance and power efficiency but presents a challenge in balancing model accuracy with limited hardware resources[cite: 124]. [cite_start]BNNs are resource-efficient but often suffer from accuracy degradation[cite: 126]. This project explores a hardware-centric solution to this trade-off by directly tuning the FPGA design to enhance performance.

### 🎯 Aims & Objectives
- [cite_start]**Analyze Baseline Performance:** Understand the accuracy and resource utilization of a standard BNN on a given task[cite: 138].
- [cite_start]**Implement Hardware-Level Modifications:** Design and apply direct modification techniques to the MVAU within the FINN framework to introduce weight randomization[cite: 33, 139].
- [cite_start]**Evaluate Effectiveness:** Compare the performance of the modified network against the baseline to prove that FPGA tuning is a cost-effective and rapid optimization strategy[cite: 140].
- [cite_start]**Bridge Software and Hardware:** Link software simulations in Brevitas with hardware synthesis in FINN to create a comprehensive workflow[cite: 34].

---

## 🛠️ Frameworks & Methodology

[cite_start]This project utilizes a dual-framework approach to bridge the gap between high-level software models and low-level hardware implementation[cite: 34].

| Framework | Description | Role in Project |
|---|---|---|
| **Brevitas** | [cite_start]A PyTorch library for quantization-aware training[cite: 343]. | [cite_start]Used for training the QNN, establishing a baseline accuracy, and simulating the effects of weight randomization on model performance[cite: 32, 437]. |
| **FINN** | [cite_start]A Xilinx framework for deploying QNNs on FPGAs[cite: 317]. | [cite_start]Used for compiling the dataflow architecture, synthesizing the hardware, and estimating the resource utilization (LUTs, FFs) before and after MVAU modifications[cite: 33, 501, 502]. |

---

## 📊 Evaluation Metrics

Performance was evaluated based on two key criteria, representing the trade-off between model accuracy and hardware cost.

| Metric | Full Name | Purpose |
|---|---|---|
| **Accuracy** | Model Accuracy | [cite_start]Measures the model's classification performance after training and randomization[cite: 702]. |
| **Resource Utilization** | FPGA Resource Usage (LUTs, FFs) | [cite_start]Measures the hardware cost by quantifying the number of Look-Up Tables (LUTs) and Flip-Flops (FFs) consumed by the design[cite: 702, 848]. |

---

## 📈 Experimental Results

The results confirm that a significant accuracy improvement can be achieved for a minimal hardware cost.

| Metric | Baseline (BNN) | With 10% Randomization (TNN) | Change |
|---|---|---|---|
| **Accuracy** | [cite_start]73.0% [cite: 752] | [cite_start]**82.1%** [cite: 804] | [cite_start]**+12.5%** [cite: 805] |
| **LUT Usage (Avg.)** | Baseline | Baseline + ~7.1% | [cite_start]**+7.1%** [cite: 885, 909] |
| **FF Usage (Avg.)** | Baseline | Baseline + ~4.325% | [cite_start]**+4.325%** [cite: 889, 909] |

### Key Findings
- [cite_start]**Accuracy Gains:** Introducing ternary weights via randomization provided the model with more expressive power, leading to a substantial **~12.5%** improvement in accuracy[cite: 805, 920].
- [cite_start]**Minimal Resource Cost:** The hardware logic for randomization added an average of only **~7.1%** to LUT utilization and **~4.3%** to FF utilization, demonstrating high efficiency[cite: 896].
- [cite_start]**Feasibility:** The findings validate that targeted, direct hardware tuning is a practical and low-cost method for optimizing neural network deployments on FPGAs[cite: 918].

---
