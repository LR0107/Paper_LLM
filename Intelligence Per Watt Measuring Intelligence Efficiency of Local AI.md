# **Intelligence Per Watt:Measuring Intelligence Efficiency of Local AI**

 
**Jon Saad-Falcon, Avanika Narayan 
https://arxiv.org/pdf/2511.07885**



This paper introduces **Intelligence Per Watt (IPW)** as a new metric for measuring the energy efficiency of large language model (LLM) inference when executed on local models and accelerators.

## **Background**

- The growing demand for LLM inference puts pressure on centralized cloud computing resources.
- Local models and accelerators provide a way to offload some inference workloads, improving energy efficiency.
- IPW is proposed as a unified metric to evaluate local inference efficiency.

## **Method**

- IPW is measured as the ratio of task accuracy to power consumption.
- Experiments were conducted on 1 million real-world query tasks using various local and cloud models, and different hardware accelerators.
- A smart routing strategy was proposed to allocate tasks to the most suitable model and hardware configuration for optimization.

## **Experiment**

- **Dataset:** 1 million queries covering conversational and inference tasks.
- **Model Selection:** 20+ local LLMs with fewer than 20 billion parameters, such as QWEN3, LLAMA3.1, and GPT-OSS, compared with cloud models like GPT-5 and Claude.
- **Hardware Selection:** 8 hardware accelerators, including local (e.g., Apple M4 Max, AMD Ryzen AI) and cloud (e.g., NVIDIA H100, A100) models.
- **Evaluation Metrics:** IPW and Energy Per Joule (APJ) were used to measure inference efficiency.

## **Results**

- Local models answered 88.7% of queries, with strong performance in creative tasks.
- Local inference IPW improved 5.3x from 2023 to 2025, with query coverage rising from 23.2% to 71.3%.
- The smart routing system reduced energy consumption, computing power, and costs in hybrid local-cloud systems, saving up to 60-80% of resources.
