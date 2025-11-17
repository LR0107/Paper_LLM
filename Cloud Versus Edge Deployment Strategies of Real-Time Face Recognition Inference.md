# Cloud Versus Edge Deployment Strategies of Real-Time Face Recognition Inference

**Anis Koubaa, Adel Ammar, Anas Kanhouch**  
<https://ieeexplore.ieee.org/document/9350171>

## Background

Real-time face recognition requires heavy computation on high-resolution video.  
Cloud offers strong compute but suffers from latency, bandwidth cost, and privacy issues.  
Edge devices offer low latency and better privacy but have limited compute.  
This work compares cloud GPUs and Jetson edge devices running MTCNN + FaceNet.

## Deployment Strategies

### Cloud-Based

- Full frames sent to cloud for MTCNN + FaceNet  
- Pros: strong compute, large models  
- Cons: high latency, bandwidth, privacy concerns

### Edge-Based

- Jetson Nano/TX2/NX/AGX run detection + recognition locally  
- Pros: low latency, good privacy, low bandwidth  
- Cons: limited compute

### Hybrid

- Edge does detection; cloud does recognition  
- Pros: balanced bandwidth and latency  
- Cons: partial network and privacy exposure

## Experiments

- **Cloud GPUs:** GTX1080, RTX2070, RTX2080Ti, RTX8000  
- **Edge:** Jetson Nano, TX2, Xavier NX, Xavier AGX  
- **Models:** MTCNN + FaceNet  
- **Frameworks:** TensorFlow, TensorRT, TFLite  
- **Metrics:** FPS, latency, power, memory, resolution (480p/720p/1080p)  
- **Total:** 294 experiments

## Results

1. **TensorRT** gives the fastest real-time performance  
2. **Edge deployment** best for low latency and privacy  
3. **Cloud** best when compute needs are high and network is strong  
4. **Hybrid** is the most balanced under low bandwidth or weak edge devices
