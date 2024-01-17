# LMDeploy大模型量化部署实践
## 1. 大模型部署背景
<img width="949" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/89cc5906-a08e-45bf-b873-94f1a51717ea">
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/335d536a-1cf4-4166-9184-585cf44b73c2)

## 2. LMDeploy简介

![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/8484ef6a-bcf7-434c-b189-c97186667f35)

推理性能
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/b8f2409f-525d-4b7c-ba60-ca9807066f12)

### 2.1. 核心功能-量化
为什么要做量化
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/33c0b847-58be-4440-a0ac-dd06b7a29f63)

为什么做weight only的量化（计算的时候还少要反量化成fp16来计算，所以会增加一部分时延，但是访存时延减小得更多）
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/f036e8cd-5cdd-4c69-8fea-7c13a726c356)
