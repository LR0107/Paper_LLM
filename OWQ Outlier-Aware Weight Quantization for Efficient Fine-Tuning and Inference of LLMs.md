# OWQ: Outlier-Aware Weight Quantization for Efficient Fine-Tuning and Inference of LLMs

**Changhun Lee et al., AAAI 2024**  
<https://arxiv.org/abs/2306.02272>

## Background

3-bit quantization greatly reduces LLM memory but causes accuracy loss.  
Existing methods (e.g., OPTQ) overlook activation outliers, which distort quantization.  
OWQ improves low-bit stability and supports efficient fine-tuning.

## Method

### OWQ (Outlier-Aware Weight Quantization)

- **Weak column identification:** detect weight columns highly affected by activation outliers; keep them in FP16.  
- **3-bit quantization:** apply optimized 3-bit quantization to remaining columns.

### WCT (Weak Column Tuning)

- During fine-tuning, freeze low-bit weights and update only weak columns to reduce compute and memory.

**Workflow:** identify weak columns → 3-bit quantize others → fine-tune weak columns.

## Experiments

- **Models:** OPT, LLaMA (7B–175B)  
- **Hardware:** A100 80GB, RTX 3090  
- **Tasks:** WikiText-2 PPL, MMLU, ARC  
- **Baselines:** OPTQ, QLoRA, LoRA

## Results

1. **3.01-bit OWQ** approaches 4-bit OPTQ accuracy  
2. 3-bit OWQ outperforms OPTQ 3-bit by 2–4%  
3. WCT fine-tuning beats QLoRA with lower memory usage


