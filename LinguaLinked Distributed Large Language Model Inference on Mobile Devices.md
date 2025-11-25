# LinguaLinked: Distributed Large Language Model Inference on Mobile Devices

**Junchen Zhao, Yurun Song, Simeng Liu, Ian G. Harris, Sangeetha Abdu Jyothi**  
<https://arxiv.org/abs/2312.00388>

## Background

LLMs are too large to run on a single phone, and cloud inference raises privacy, bandwidth, and latency issues. Existing mobile optimizations remain insufficient for full models. **LinguaLinked** enables multiple trusted phones to cooperatively run different model segments.

## Methods

### Model partitioning

- Split the LLM into subgraphs.
- Assign subgraphs based on each device’s compute, memory, and bandwidth.

### Efficient communication

- Devices pass activations in a ring structure.
- Allows direct device-to-device transfer when needed to avoid unnecessary hops.

### Load balancing

- The system monitors device speed and bandwidth.
- If a device slows down, subgraph assignments adapt to remove bottlenecks.

## Experiments

**Devices:** 3× Pixel 7 Pro + 1 low-end phone  
**Models:** BLOOM 1.1B / 1.7B / 3B (full precision & int8)  
**Task:** Wikitext-2 text generation; measure per-token latency  
**Comparison:** naive equal partitioning vs LinguaLinked optimized scheduling

## Results

1. Optimized partitioning: 1.1×–1.6× faster
2. Multithreading: up to 2.6× speedup 
3. Load balancing: ~30% improvement
4. Residual communication: 4–5% lower communication delay

## Version 2.0
**Motivation:**
LinguaLinked enables efficient LLM inference on mobile devices, addressing memory and processing limitations while ensuring data privacy.

**Main Design:**
It uses decentralized task distribution, optimized model assignment, and load balancing to enhance efficiency and minimize latency across mobile devices.

