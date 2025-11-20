# VIDUR: A Large-Scale Simulation Framework for LLM Inference

**Amey Agrawal, Nitin Kedia, Jayashree Mohan**  
<https://arxiv.org/abs/2405.05465>

## Background

LLM inference deployment requires tuning many parameters (parallelism, scheduler, batch size, GPU type), and real testing is extremely expensive (e.g., tens of thousands of GPU hours for LLaMA-70B).  
Vidur provides a low-cost, high-accuracy simulator to replace real experiments.

## Method

1. **Operator-level Profiling**  
   Measure key operator runtimes (attention, MLP, communication) at a few input sizes; interpolate with a random forest model.

2. **Runtime Estimator**  
   Simulate the inference loop iteration by iteration to predict latency.

3. **Scheduler Simulation**  
   Model vLLM, Orca, Sarathi to predict end-to-end latency and throughput.

4. **Vidur-Search**  
   Automatically search for optimal deployment configurations ( QPS/$).

**Workflow:** profiling → model prediction → per-iteration simulation → scheduler simulation → config search.

## Experiments

- **Models:** LLaMA2-7B/70B, Qwen-72B, InternLM-20B  
- **Hardware:** A100, H100  
- **Workloads:** Chat-1M, Arxiv-4K, BWB  
- **Metrics:** TTFT, TBT, latency, MFU, KV-cache usage, QPS/$

## Results

1. Latency prediction error < 9%  
2. Search cost reduced by 20,000× (GPU weeks → 1 CPU hour)  
3. Optimal configs vary widely; naive transfer can waste 2× cost  
4. Significant improvements in QPS/$ and throughput
