# LADDER: Enabling Efficient Low-Precision Deep Learning Computing through Hardware-aware Tensor Transformation

**Lei Wang**  
**Usenix 2024**  
<https://www.usenix.org/conference/osdi24/presentation/wang-lei>

## Background

Deep learning relies on low-bit (INT8/4/2/1, NF4, FP8) and mixed precision to reduce costs, but GPUs natively support only a few data types, limiting performance.  
**LADDER** provides a system that efficiently executes arbitrary low-bit precision formats without hardware modification.

## Method

1. **tType**: Unified description for any 1–16 bit format (INT1/2/4/8, NF4, FP8, MXFP8) with type conversion mechanism.  
2. **tTile**: Splits tensors into tiles, aligns, and transforms them into hardware-friendly layouts using four primitives: slice, pad, map, convert.  
3. **Hardware-aware Scheduling**: Optimizes conversion locations, tile layouts, and operator fusion based on GPU access patterns for high bandwidth utilization.

**Workflow**:  
tType → slice tiles → align & transform → hardware-aware scheduling → efficient kernel generation.

## Experiments

- **Hardware**: NVIDIA A100/V100/A6000, AMD MI250  
- **Models**: LLaMA/BLOOM, ResNet/ShuffleNet/ViT, Conformer  
- **Precision**: FP16, FP8, INT8/4/2/1, NF4, MXFP8  
- **Comparisons**: TensorRT, Welder, CUTLASS, vLLM, Inductor  
- **Metrics**: Inference latency, GPU throughput, memory usage

## Results

1. **Speedup**: INT4/W4A16 is 2.0–2.3× faster than vLLM; INT1/INT2 achieves 10–14× speedup.  
2. **Memory Savings**: LLaMA-2 INT1/INT2 reduces GPU memory usage by 70–85%.  
3. **Cross-Platform**: Achieves near-cuBLAS/CUTLASS bandwidth utilization on A100/V100/A6000, MI250.  
4. **Fast Compilation**: **100×** faster than AMOS, 10× faster than TensorIR.
