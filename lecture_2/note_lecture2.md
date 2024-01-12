# 轻松分钟玩转书生·浦语大模型趣味 Demo
## 实践过程
### 环境准备
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/a130e9f9-edf8-4527-b3e6-1ada202fec64)

进入开发机后，在终端输入bash命令，进入 conda 环境。**之所以要输入bash，是为了重新加载环境变量，确保conda相关配置能够对新开的shell环境生效**
使用以下命令从本地克隆一个已有的 pytorch 2.0.1 的环境
```
bash /root/share/install_conda_env_internlm_base.sh lgx-internlm-demo  # 执行该脚本文件来安装项目实验环境
```
使用如下命令激活conda环境
```
conda activate internlm-demo
```
安装demo运行需要的包：
```
# 升级pip
python -m pip install --upgrade pip

pip install modelscope==1.9.5
pip install transformers==4.35.2
pip install streamlit==1.24.0
pip install sentencepiece==0.1.99
pip install accelerate==0.24.1
```
### 模型下载截图
下载代码：
```
import torch
from modelscope import snapshot_download, AutoModel, AutoTokenizer
import os
model_dir = snapshot_download('Shanghai_AI_Laboratory/internlm-chat-7b', cache_dir='/root/model', revision='v1.0.3')
```
<img width="1425" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/b7a6a9ed-aba3-4ed1-be35-de1ffa0c2a08">

### cli_demo运行
<img width="1057" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/62d77399-1a7a-4ce6-b18b-c15c6de105dc">

### web_demo运行
配置好ssh连接后，先用如下命令运行web_demo.py
```
streamlit run web_demo.py --server.address 127.0.0.1 --server.port 6006
```
再在本地浏览器输入http://127.0.0.1:6006，服务器的程序才会开始加载模型，加载完毕后就可以对话了：
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/16e298cc-2a66-43d4-b6c4-660ed5342a1a">

### Lagent智能体工具调用demo
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/b4460c54-2e60-4e99-901e-d976889b7b42">

