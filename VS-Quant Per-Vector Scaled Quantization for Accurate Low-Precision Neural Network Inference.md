# VS-Quant: Per-Vector Scaled Quantization for Accurate Low-Precision Neural Network Inference

**Steve Dai, Rangharajan Venkatesan**  
<https://arxiv.org/abs/2102.04503>

## Background

Coarse-grained quantization (per-layer/per-channel) causes large quantization errors when data distributions vary, leading to accuracy loss.  
**VS-Quant** reduces this error by quantizing each vector independently.

## Method

1. **Per-Vector Scaling**  
   Each small vector uses its own scale factor, improving low-bit accuracy.

2. **Two-Level Scaling**  
   
   - Integer scale: applied per vector  
   - Floating-point scale: applied per layer  
     Reduces energy and area overhead.

3. **Hardware-Friendly Computation**  
   Vector MAC units align well with the quantization scheme.

**Workflow:** per-vector quantization → two-level scaling → hardware-optimized execution.

## Experiments

- **Models:** ResNet-50, BERT-base/large  
- **Datasets:** ImageNet, SQuAD  
- **Hardware:** NVIDIA A100/V100; custom accelerator  
- **Metrics:** accuracy, energy/area efficiency, latency, resource usage

## Results

1. Near–full precision accuracy with 4-bit weights + 8-bit activations 
2. 69% energy reduction, 36% area savings, faster inference  
3. Significant memory compression and improved hardware efficiency

## Version 2.0
**Motivation:**
Reduce quantization error more effectively than per-channel methods.

**Main Design:**
Use per-vector scaling with a lightweight two-level scale to achieve low-bit quantization with higher accuracy and small hardware cost.

