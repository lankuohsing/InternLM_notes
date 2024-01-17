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

如何做weight only的量化
有一些重要参数不量化
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/0a7e694e-3163-494d-8dfc-eac2a9b855c9)

### 2.2. 核心功能-推力引擎TurboMind
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/73b0b229-59ae-497f-9ce1-751e0816b134)

持续批处理（decoder才比较常用）
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/8e22a0ce-db06-4116-be26-9bf888023fdd)

有状态的推理
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/fd19e481-7ffc-486e-bb07-6bd443cdba01)

Blocked k/v cache
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/44758c9f-37e5-420d-a1de-03fcbc318552)

高性能的cuda kernel
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/0f5ef432-1ebd-43db-a307-f355c7ee3a03)

### 2.3. 核心功能-推理服务api server

## 3. 动手实践环节-安装、部署、量化
