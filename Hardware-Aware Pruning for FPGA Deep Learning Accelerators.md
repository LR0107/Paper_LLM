# Hardware-Aware Pruning for FPGA Deep Learning Accelerators

**Jef Plochaet; Toon Goedemé**

https://ieeexplore.ieee.org/document/10209061

**CVPR 2023**

## Background

FPGAs for embedded deep learning have limited compute and memory bandwidth.  
Conventional pruning (e.g., L2-norm) ignores residual-connection constraints and FPGA hardware structure, so parameter reduction does not always lead to real speedup.  
The goal is a pruning method that is **residual-aware** and **FPGA-aware** to reduce true inference latency.

## Method

### Residual-aware pruning

- Treat channels in each residual block as groups.  
- Use the group’s maximum L2-norm as importance.  
- Remove entire groups to preserve residual consistency.

### Hardware-Aware Pruning (HAP)

- Align pruned channel counts to FPGA systolic-array widths (e.g., CO = 32).  
- Ensures pruning reduces actual hardware compute blocks.

### Workflow

compute importance → initial pruning → hardware alignment (HAP) → finetuning → repeat

## Experiments

- **Model:** DeepLabV3+ (Xception)  
- **Task:** polyp segmentation  
- **Hardware:** nearbAI FPGA (Arria-10)  
- **Baselines:** L2 pruning, no-residual pruning, no-HAP pruning

## Results

1. 1.87× speedup  
2. 5× compression with minimal accuracy loss  
3. Residual pruning and HAP each add 10–16% additional speedup


