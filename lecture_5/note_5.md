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
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/47492e95-be20-4c62-bfcd-0d3a192a9264)

### 3.1. 模型转换

启动本地模型
```
lmdeploy chat turbomind /share/temp/model_repos/internlm-chat-7b/  --model-name internlm-chat-7b
```
Tensor并行之列并行
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/f50a28dd-39d3-4ca7-862d-06c00d530595)

Tensor并行之行并行
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/c622a382-d38a-4f0b-b056-164e0dbfad60)


#### 3.1.1. 离线转换
```
# 转换模型（FastTransformer格式） TurboMind
lmdeploy convert internlm-chat-7b /path/to/internlm-chat-7b
```

### 3.2. TurboMind 推理+命令行本地对话
```
# Turbomind + Bash Local Chat
lmdeploy chat turbomind ./workspace
```
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/df7d8f53-e833-47ba-9263-6181043c6198)
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/23dbb507-384c-4900-92bc-cac8b6feda9d)

### 3.3. TurboMind推理+API服务
```
lmdeploy serve api_server ./workspace \
    --server_name 0.0.0.0 \
    --server_port 23333 \
    --instance_num 64 \
    --tp 1
```
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/52c36a8a-5a09-4065-975e-d971adac907d)
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/3ea94235-1cc1-416e-a1e0-ee9ae2345caa)
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/7746c624-7305-42b8-9f73-6180bf21e508)
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/1d06f432-0956-4b35-b3f4-14bbf912cc8c)
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/168c7063-6d1f-4565-a53b-0403b8f8e369)

### 3.4. 网页demo演示
#### 3.4.1. TurboMind 服务作为后端
```
# Gradio+ApiServer。必须先开启 Server，此时 Gradio 为 Client
lmdeploy serve gradio http://0.0.0.0:23333 \
	--server_name 0.0.0.0 \
	--server_port 6006 \
	--restful_api True
```

#### 3.4.2. TurboMind 推理作为后端
```
# Gradio+Turbomind(local)
lmdeploy serve gradio ./workspace
```
<img width="1250" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/5d8b1cbc-233d-4b4f-8113-b4ae96bbc4bc">

