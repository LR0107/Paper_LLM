# Measuring and Improving the Energy Efficiency of Large Language Model Inference

**Mauricio Fadel Argerich; Marta Patiño-Martínez**  
**IEEE Access**  
<https://ieeexplore.ieee.org/document/10549890>

## Background

LLM accuracy improvements come with higher compute and energy demands.  
Inference energy efficiency is less studied than training.  
This work analyzes LLM inference energy use and proposes optimization strategies.

## Method

- EnergyMeter: a tool to measure CPU, GPU, memory, and storage energy during inference.  
- Built on RAPL, NVIDIA-SMI, and eBPF, with negligible overhead.  
- Examines optimizations via model size, architecture, batch size, and quantization.

## Experiments

- **Models:** Pythia, Bloom, LLaMA (various scales)  
- **Hardware:** Intel Core i9, NVIDIA RTX 4090  
- Measures effects of model size, architecture, batch size, and quantization on energy and latency.

## Results

1. **Model size:** energy and latency rise significantly; GPU energy grows linearly.  
2. **Architecture:** more parallel models improve energy efficiency.  
3. **Batch size:** larger batches improve GPU utilization and reduce energy per token.  
4. **Quantization:** reduces memory and energy, but aggressive quantization can increase latency.

## Optimization Strategies

- Choose models that balance accuracy and energy use.  
- Prefer quantized versions.  
- Increase batch size until GPU is fully utilized.
