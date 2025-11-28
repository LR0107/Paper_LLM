# ZeroQuant: Efficient and Affordable Post-Training Quantization for Large-Scale Transformers

**Zhewei Yao, Reza Yazdani Aminabadi, Minjia Zhang — NeurIPS 2022**  
<https://arxiv.org/abs/2206.01861>

## Background

Large Transformer models face inference bottlenecks in memory and compute.  
Existing quantization often leads to accuracy drops and added latency, especially at scale.  
ZeroQuant provides efficient INT8 and INT4/INT8 PTQ for large models.

## Method

### Hardware-Friendly Quantization

- Group-wise weight quantization  
- Token-wise activation quantization

### Layer-wise Knowledge Distillation (LKD)

- Distills each layer without original training data  
- Avoids costly full-model distillation

### Optimized Inference Backend

- Kernel fusion to reduce bandwidth overhead  
- Faster quantize/dequantize operations

## Experiments

- **Models:** BERT, GPT-J 6B, GPT-NeoX 20B  
- **Tasks:** GLUE, GPT-3 zero-shot (19 tasks + Wikitext-2)  
- **Hardware:** A100, V100, RTX 3080, TPU  
- **Baselines:** PTQ, QAT

## Results

1. 5.19× inference speedup, 3× memory reduction  
2. Accuracy close to FP16  
3. On GPT-NeoX-20B: **5.2×** speedup and lower GPU requirements

## Version 2.0
**Motivation:**
Compress large Transformers efficiently without retraining or access to training data.

**Main Design:**
Use fine-grained INT8/INT4 quantization plus lightweight layer-by-layer distillation and fused kernels to cut memory and latency with minimal accuracy loss.
