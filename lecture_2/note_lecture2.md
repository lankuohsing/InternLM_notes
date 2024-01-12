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
#### 本地配置SSH Key(执行一次即可)并连接ssh（新建立开发机后都要运行一次？似乎不用也行）
在本地机器上打开 Power Shell 终端。在终端中，运行以下命令来生成 SSH 密钥对:
```
ssh-keygen -t rsa
```
查看公钥：
```
cat ~/.ssh/id_rsa.pub
```
将公钥复制到剪贴板中，然后回到 InternStudio 控制台，点击配置 SSH Key:
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/69e702da-1396-44d9-9b43-b8f7f67bee7b)
将刚刚复制的公钥添加进入即可:
![image](https://github.com/lankuohsing/InternLM_notes/assets/12205805/047e402c-037f-4e09-aec9-75ffab1de34b)

本地shell运行(最后的端口号要换成开发机上的ssh链接里面的配置)：
```
ssh -CNg -L 6006:127.0.0.1:6006 root@ssh.intern-ai.org.cn -p 33090
```
配置好ssh连接后，先用如下命令运行web_demo.py
```
streamlit run web_demo.py --server.address 127.0.0.1 --server.port 6006
```
再在本地浏览器输入http://127.0.0.1:6006，服务器的程序才会开始加载模型，加载完毕后就可以对话了：
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/16e298cc-2a66-43d4-b6c4-660ed5342a1a">

### Lagent智能体工具调用demo
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/b4460c54-2e60-4e99-901e-d976889b7b42">
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/5b5e6b8e-4bc4-4e7a-a0d1-373395b2e34a">

### 浦语·灵笔图文理解创作Demo
注意要在本地浏览器输入127.0.0.1:6006而不是从vscode跳转（跳转方式可能会有问题，网业上的按钮点了没反应）
#### 创作图文并茂文章
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/07b96613-022d-417f-a198-01fa565c071d">
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/77d30226-4440-49a0-8728-93f476eaa21d">
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/3107c79a-e537-49ad-b2ec-9d278925ccc6">
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/13188c97-c814-47b6-a96b-6f594c33a3df">
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/2a508654-3f31-45d1-9895-419c458c40a5">
<img width="1419" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/389a0b00-9ff0-4bc3-afaa-4a8d02f1fc2c">

#### 多模态对话
<img width="1271" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/404ad222-6ee9-4f9f-9dc2-ea3bea786229">




