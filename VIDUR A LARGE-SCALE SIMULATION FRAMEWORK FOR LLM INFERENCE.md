# VIDUR: A LARGE-SCALE SIMULATION FRAMEWORK FOR LLM INFERENCE

**Amey Agrawal, Nitin Kedia, Jayashree Mohan**  
https://arxiv.org/abs/2405.05465

## Research Background

Deploying LLM inference requires tuning multiple configurations (e.g., parallel strategies, schedulers, batch size, GPU SKU), with high real-world testing costs (e.g., LLaMA-70B search takes tens of thousands of GPU hours). A low-cost, high-accuracy LLM inference simulator is needed to replace real experiments.

## Research Method

1. **Operator-level Profiling**  
   Measure real-time costs of key operators (e.g., attention, MLP, communication) for a few input sizes, then use a random forest model (RF) to predict times for all operators.
2. **Runtime Estimator**  
   Simulate the actual LLM inference process iteratively to predict latency for each iteration.
3. **Simulating Real Scheduler**  
   Use Vidur to simulate schedulers (e.g., vLLM, Orca, Sarathi) and predict end-to-end latency and throughput.
4. **Vidur-Search**  
   Automatically search for the optimal deployment configuration (QPS/$ optimal).  
   **Workflow:** Real measurements → Model-based prediction → Iterative inference simulation → Scheduler simulation → Optimal configuration search.

## Input

- **Model specifications:** Architecture, layers, parameters
- **Deployment configurations:** Parallelization, scheduling strategy, batch size, GPU type
- **Workload characteristics:** Token count, batch input/output length

## Output

- **Latency:** First token generation time (TTFT), token-to-token time (TBT)
- **Throughput:** Requests per second (QPS)
- **Cluster-level metrics:** GPU usage, memory usage
- **Method:** Random Forest (error rate < 9%)

## Experimental Design

- **Models:** LLaMA2-7B/70B, Qwen-72B, InternLM-20B
- **Hardware:** A100, H100
- **Workloads:** Chat-1M, Arxiv-4K, BWB
- **Metrics:** TTFT, TBT, end-to-end latency, MFU, KV cache usage, QPS per dollar

## Experimental Results

- Latency error < 9%, even under high load.
- Search cost reduced by 20,000× (from tens of thousands of GPU hours to 1 hour on CPU).
- Optimal configurations vary greatly between workloads; blind migration may lead to 2× cost waste.
- Vidur's configurations significantly improve QPS/$ and throughput.

**Note:** Primarily focused on GPU.
