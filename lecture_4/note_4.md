# XTuner大模型单卡低成本微调实践

## 1. Finetune简介
<img width="1120" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/91db8903-8a68-422a-9c45-cfdee385b71c">

### 1.1. 指令跟随微调
对话模板
<img width="1014" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/7acbed75-f24d-4fa4-8ef0-d95fd3386331">

不同的开源模型，对话模板可能不一样。预测阶段不需要特定指明角色，一般框架内部会配好对应的角色模板
<img width="1182" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/fc77f2e0-2d96-40ca-8e79-3c99a50e28f6">
<img width="1186" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/a45c56df-ca2e-419a-b0cb-6fce11774572">

只计算system部分的loss
### 1.2. 增量预训练微调
只需要把system和user这两个角色留空
<img width="1139" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/60c2bcdb-b397-4f5f-aab6-77db24789197">

### 1.3. 微调方法
LoRA & QLoRA
<img width="1038" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/04d265d6-892e-434b-910e-bf841f83bc13">

## 2. XTuner

## 3. 8GB显存玩转LLM
<img width="1159" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/e20a465d-e0d9-41bc-ae05-0ef29ceec3a9">

## 4. 动手实践环节
<img width="1142" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/ef73ce2e-7cd0-4f6e-bf20-a1b05897f29f">
<img width="1440" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/2b15c2e2-6568-4711-b827-29c7b663b969">
