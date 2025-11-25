# Arbitrary-Bit Quantized Inference Acceleration for Large Language Models

**Chao Zeng, Songwei Liu, Yusheng Xie**  
**AAAI 2025**  
<https://arxiv.org/abs/2408.08554>

## Background

Low-bit quantization reduces memory and compute cost but often harms accuracy and fails to fully utilize GPU low-precision acceleration.  
**ABQ-LLM** provides an arbitrary-bit quantization framework that improves both speed and accuracy across multiple quantization settings.

## Method

1. **Distribution Correction**  
   Uses dual cosine similarity loss (DLC) to correct quantization-induced distribution shifts in transformer blocks.

2. **Bit Balance Strategy**  
   Balances bit-width effects on weights and activations, significantly improving INT2 accuracy.

3. **Arbitrary Precision Inference Framework**  
   Uses hardware like Binary TensorCore (BTC) to accelerate mixed-precision matmul (e.g., W6A6, W2A8).

## Experiments

- **Models:** LLaMA 7B, 13B  
- **Tasks:** WikiText-2, PIQA, ARC  
- **Hardware:** A100, RTX 3070  
- **Baselines:** GPTQ, AWQ, SmoothQuant  
- **Metrics:** PPL, latency, throughput, memory usage

## Results

1. 1.6× speedup, 2.7× memory reduction, surpassing SmoothQuant  
2. +7.5% INT2 accuracy improvement, leading zero-shot results  
3. W2A8 on LLaMA-7B achieves 1.6× speedup and 2.7× memory savings

## Version 2.0
**Motivation:**
Address the high computational and storage demands of large language models, enhancing the efficiency of low-bit quantized inference.

**Main design:**
Introduce ABQ-LLM, using distribution correction and bit balance strategies to enhance performance, and a quantization framework for efficient inference.




