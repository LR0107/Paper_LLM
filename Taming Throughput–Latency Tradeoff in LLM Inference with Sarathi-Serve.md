# Taming Throughput–Latency Tradeoff in LLM Inference with Sarathi-Serve

**Amey Agrawal, USENIX OSDI 2024**  
<https://www.usenix.org/system/files/osdi24-agrawal.pdf>

## Background

LLM inference has two phases: prefill (high parallelism, high latency) and decode (light computation, inefficient).  
Batching improves throughput, but mixing these phases creates a throughput–latency tradeoff.

## Method

### Chunked-Prefills

Splits long prefill requests into smaller chunks processed over multiple iterations to prevent prefill from blocking decode.

### Stall-Free Batching

Allows new requests to join batches without pausing ongoing decode tasks, eliminating stalls present in traditional schedulers.

### Workflow

Prefill chunking → iterative processing → token-by-token decode → stall-free concurrent scheduling.

## Experiments

- **Hardware:** A100 (1 GPU), Yi-34B (2 GPUs), LLaMA2-70B (8 GPUs)  
- **Models:** Mistral-7B, Yi-34B, LLaMA2-70B, Falcon-180B  
- **Baselines:** vLLM, Orca

## Results

1. **Throughput:**  
   - 3.7× over vLLM on Yi-34B  
   - 2.6× on Mistral-7B  
   - Up to 5.6× with pipeline parallelism on large models  
2. **Latency:**  
   Lower P99 TBT via stall-free batching; reduced high-latency outliers.  
3. **Pipeline Efficiency:**  
   Fewer pipeline bubbles, improving throughput on large-model deployments.

## Version 2.0
**Motivation:**
Optimize the throughput-latency balance in large language model (LLM) inference.
**Main Design:**
Sarathi-Serve introduces chunked-prefills to split prefill tasks into smaller chunks, and stall-free scheduling to allow new requests to join ongoing batches without interrupting decodes.

