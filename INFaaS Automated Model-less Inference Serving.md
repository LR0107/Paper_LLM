# INFaaS: Automated Model-less Inference Serving

**Francisco Romero, Qian Li, Neeraja J. Yadwadkar, Christos Kozyrakis (Stanford University)**  
**Best Paper Award**  
<https://www.usenix.org/conference/atc21/presentation/romero>

## Background

Cloud models have many variants (hardware, frameworks, batch sizes), with up to 1000× performance difference.  
Developers must manually pick variants, making it hard to meet latency, throughput, and cost goals.  
**INFaaS** automatically selects the best variant and hardware per request.

## Method

### Variant Generation & Profiling

- Generates many variants (CPU/GPU/Inferentia, TensorRT/TVM/Neuron, batch sizes, quantization).  
- Profiles each variant offline for latency, throughput, loading time, memory, accuracy.  
- Stores all measurements in a metadata database.

### Dynamic Variant Selection

- Filters variants based on user SLOs (latency, accuracy).  
- Considers loaded vs. unloaded variants (loading + inference).  
- Picks the fastest or most cost-efficient option.  
- Decision time: 2–3 ms. Only table lookup without predicting.

### Autoscaling

- **Vertical:** switch CPU → GPU → Inferentia; run multiple variants on bursts.  
- **Horizontal:** add/remove machines based on load.

**Workflow:**  
Model registration → Variant generation → Offline profiling → Online selection → Autoscaling

#### Experiments

**Platform:** AWS (CPU/GPU/Inferentia)  
**Models:** 175 variants, 22 models  
**Baselines:** Clipper+, SageMaker+  
**Workloads:** Twitter traces, 10–1000 QPS, multi-model mixes

## Results

1. **Throughput:** 1.3× higher  
2. **SLO stability:** 1.6×–2.5× fewer violations  
3. **Cost:** up to 21.6× lower (avg 8.5×)  
4. **Utilization:** GPU up to 58.6% (vs 10–20%)

## Notes

- Profiling only measures latency, loading time, and memory—no training or large datasets required.  
- Only one machine per hardware type is needed for profiling (cloud-based).  
- Cost-efficiency = minimal completion time (loading + inference) + lowest hardware cost.

## Version 2.0
**Motivation:**
Eliminate manual model-variant and hardware selection for each inference query.

**Main Design:**
Provide a model-less API and automatically pick and scale the best model-variant and hardware per query using profiling and joint vertical/horizontal autoscaling.

