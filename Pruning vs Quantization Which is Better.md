# Pruning vs Quantization: Which is Better?

**Andrey Kuzmin, Markus Nagel, Mart van Baalen**  
**NeurIPS 2023**  
<https://arxiv.org/abs/2307.02973>

## Background

Pruning and quantization are key model compression methods, but their comparative behavior—especially in accuracy and hardware efficiency—is not well studied.  
This work systematically compares the two across models, tasks, and compression ratios.

## Method

1. **Theoretical SNR Analysis**  
   Models pruning vs. quantization error and predicts which is smaller under different compression levels.

2. **Large-Scale Empirical Study**  
   Tests INT8/INT4/INT2 quantization vs. various pruning ratios with equal compression.  
   Measures actual layer output error.

## Experiments

- **Models:** ResNet-18/50, MobileNetV2/V3, ViT, DeepLabV3, EfficientDet, OPT-350m  
- **Tasks:** ImageNet, Pascal VOC, MS COCO, WikiText-103  
- **Baselines:** QAT, magnitude pruning  
- **Metrics:** accuracy (Top-1/mIoU/mAP), perplexity, latency, memory, hardware efficiency

## Results

1. Quantization usually beats pruning in accuracy and error.  
2. Pruning only wins at extreme compression, but performance becomes unusably low.  
3. Best results from quantization + light pruning.  
4. Quantization is more hardware-friendly due to efficient low-bit integer operations.
