# Automated Design for Hardware-aware Graph Neural Networks on Edge Devices

**Xiuwen Li; Weiwei Fang; Liang Qian; Haoyuan Li; Yanming Chen; Neal N. Xiong**  
<https://ieeexplore.ieee.org/document/11077755>

## Background

Graph Neural Networks (GNNs) are widely used in social networks, transportation, and IoT applications. However, when deployed on edge devices (Jetson Nano, mobile CPUs, embedded GPUs), they often suffer from:

- high latency  
- high energy consumption  
- memory pressure / OOM  
- strong sensitivity to hardware and task configurations  

Most existing NAS methods only optimize accuracy, resulting in architectures that remain slow on edge devices.  
This work explores: **Can NAS optimize both accuracy and latency to find the best GNN architecture for each edge device?**

## Method

**HWGNAS** is a hardware-aware NAS framework. Its key components include:

### Hardware-aware search space

Based on GraphNAS with six operation categories, covering attention, aggregation, activation, number of heads, hidden size, etc.  
Two-layer architectures produce over **167 million** possible combinations.

### Surrogate predictors

Two lightweight predictors replace full training and deployment:

- **AP:** predicts accuracy  
- **LP:** predicts inference latency on the target device  

### RL-based search (PPO)

A reward function combines accuracy and latency:

- Higher accuracy → higher reward  
- Lower latency → higher reward  

**Workflow:**  
Generate architecture → predict accuracy/latency → update policy → iterate → select optimal GNN

## Experiments

**Datasets:** Cora, Citeseer, SIoT  
**Hardware:** RTX 3090, i5-7300HQ, Jetson Nano  
**Baselines:** GCN, GAT, GIN, GraphNAS, EGNAS, HGNAS  
**Metrics:** accuracy, model size, inference latency, search time

## Results

1. **Inference speedup:** up to 73.4× on Jetson Nano (vs EGNAS)  
2. **Higher accuracy:** +8–11% over manually designed GNNs  
3. **Smaller models:** up to 99.5% reduction in size  
4. **Faster search:** 16.5%–75% reduction in search time  
