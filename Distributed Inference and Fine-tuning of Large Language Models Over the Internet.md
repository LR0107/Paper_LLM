# Distributed Inference and Fine-tuning of Large Language Models Over the Internet

**Alexander Borzunov, Max Ryabinin, Artem Chumachenko**  
**NeurIPS 2023**  
<https://arxiv.org/abs/2312.08361>

## Background

Large LLMs (50B–176B) require expensive multi-GPU servers for inference and fine-tuning.  
RAM/SSD offloading is too slow for interactive use (seconds per request).  
This work explores using distributed, low-cost, globally available GPUs to run large models collaboratively.

## Method: PETALS

A decentralized, fault-tolerant system for distributed LLM inference and fine-tuning.

### Fault-tolerant distributed inference

- Model split by layers across multiple GPUs (pipeline).  
- Dual-cache: servers store KV cache; client stores input activations.  
- Fast recovery when nodes drop—no full regeneration.

### Decentralized load balancing

- Each node selects layer ranges based on compute and bandwidth.  
- Nodes can join/leave anytime; system rebalances automatically.

### Client-side trainable parameters

- Supports LoRA and prompt tuning.  
- Servers run forward/backward compute; client holds trainable weights.

## Experiments

- **Models:** BLOOM-7B, 70B, 176B  
- **Hardware:** mixed GPUs (T4, A100, 3090, 2080Ti)  
- **Networks:** 1Gbps / 100Mbps, low/high latency  
- **Baselines:** RAM offloading, local NVLink pipelines  
- **Metrics:** per-token speed, forward throughput

## Results

1. **>10× faster** than offloading  
2. Robust under high latency and high drop rates  
3. Outperforms offloading in real intercontinental settings  
4. Load balancing achieves 90–100% of optimal throughput

## Version 2.0
**Motivation:**
This paper proposes a distributed method to run large language models efficiently using multiple internet-connected devices, reducing hardware needs.

**Main Design:**
The system utilizes a distributed architecture and fault-tolerant algorithms to optimize inference, ensuring high performance even with unstable devices and networks.



