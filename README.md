# Effective Hardware Block Design Modifications for Neural Network Performance on FPGAs

This repository contains the research and implementation for the thesis, "Effective Hardware Block Design Modifications: Impact on Neural Network Performance". The project demonstrates how direct, low-cost modifications to FPGA hardware blocks can significantly improve the accuracy of quantized neural networks (QNNs) with only a minimal increase in resource utilization.

The core methodology involves transitioning a **Binarized Neural Network (BNN)** to a **Ternary Neural Network (TNN)** by applying weight randomization techniques within the Matrix-Vector Activation Unit (MVAU).

---

## Project Overview

Deploying neural networks on FPGAs offers high performance and power efficiency but presents a challenge in balancing model accuracy with limited hardware resources. BNNs are resource-efficient but often suffer from accuracy degradation. This project explores a hardware-centric solution to this trade-off by directly tuning the FPGA design to enhance performance.

### Aims & Objectives
- **Analyze Baseline Performance:** Understand the accuracy and resource utilization of a standard BNN on a given task.
- **Implement Hardware-Level Modifications:** Design and apply direct modification techniques to the MVAU within the FINN framework to introduce weight randomization.
- **Evaluate Effectiveness:** Compare the performance of the modified network against the baseline to prove that FPGA tuning is a cost-effective and rapid optimization strategy.
- **Bridge Software and Hardware:** Link software simulations in Brevitas with hardware synthesis in FINN to create a comprehensive workflow.

---

## Frameworks & Methodology

This project utilizes a dual-framework approach to bridge the gap between high-level software models and low-level hardware implementation.

| Framework | Description | Role in Project |
|---|---|---|
| **Brevitas** | A PyTorch library for quantization-aware training. | Used for training the QNN, establishing a baseline accuracy, and simulating the effects of weight randomization on model performance. |
| **FINN** | [cite_start]A Xilinx framework for deploying QNNs on FPGAs. | ]Used for compiling the dataflow architecture, synthesizing the hardware, and estimating the resource utilization (LUTs, FFs) before and after MVAU modifications. |

---

## Evaluation Metrics

Performance was evaluated based on two key criteria, representing the trade-off between model accuracy and hardware cost.

| Metric | Full Name | Purpose |
|---|---|---|
| **Accuracy** | Model Accuracy | Measures the model's classification performance after training and randomization. |
| **Resource Utilization** | FPGA Resource Usage (LUTs, FFs) | [cite_start]Measures the hardware cost by quantifying the number of Look-Up Tables (LUTs) and Flip-Flops (FFs) consumed by the design. |

---

## Experimental Results

The results confirm that a significant accuracy improvement can be achieved for a minimal hardware cost.

| Metric | Baseline (BNN) | With 10% Randomization (TNN) | Change |
|---|---|---|---|
| **Accuracy** | 73.0%  | **82.1%**  | **+12.5%**  |
| **LUT Usage (Avg.)** | Baseline | Baseline + ~7.1% | **+7.1%**  |
| **FF Usage (Avg.)** | Baseline | Baseline + ~4.325% | **+4.325%**  |

### Key Findings
- **Accuracy Gains:** Introducing ternary weights via randomization provided the model with more expressive power, leading to a substantial **~12.5%** improvement in accuracy.
- **Minimal Resource Cost:** The hardware logic for randomization added an average of only **~7.1%** to LUT utilization and **~4.3%** to FF utilization, demonstrating high efficiency.
- **Feasibility:** The findings validate that targeted, direct hardware tuning is a practical and low-cost method for optimizing neural network deployments on FPGAs.

---
