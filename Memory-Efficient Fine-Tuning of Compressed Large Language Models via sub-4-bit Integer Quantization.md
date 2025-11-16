# Memory-Efficient Fine-Tuning of Compressed Large Language Models via sub-4-bit Integer Quantization

**Jeonghoon Kim, Jung Hyun Lee, Sungdong Kim**  
**NeurIPS 2023**  
<https://arxiv.org/abs/2305.14152>

## Background

LLM inference and fine-tuning are memory and compute intensive.  
**PEQA** combines PEFT and quantization to reduce memory and speed up inference by only updating quantization scales.

## Method

1. **Separation of Quantization and Fine-Tuning**  
   Freeze quantized weights and only adjust quantization scales, reducing memory and computation.

2. **Task-Specific Adaptation**  
   Fine-tune the quantized model for specific tasks, maintaining accuracy at low-bit precision.

3. **Inference Speedup**  
   Low-bit quantization accelerates inference, especially on GPUs and TPUs.

## Experiments

- **Models:** GPT-Neo, LLaMA  
- **Hardware:** NVIDIA A100, V100, RTX 3080  
- **Datasets:** Wikitext2, Alpaca (instruction fine-tuning)  
- **Baselines:** LoRA, PEFT+PTQ, QAT  
- **Metrics:** Perplexity (PPL), task accuracy, inference speed, memory usage, DRAM consumption

## Results

1. **Inference Speedup:** PEQA (4-bit) is 1.5–2.8× faster than LoRA with 3× less memory usage.  
2. **Accuracy:** PEQA with 3-bit quantization retains accuracy close to full precision.  
3. **Task Adaptation:** PEQA achieves task adaptation similar to LoRA on Alpaca.
