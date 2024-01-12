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
<img width="1425" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/b7a6a9ed-aba3-4ed1-be35-de1ffa0c2a08">

### cli_demo运行
<img width="1057" alt="image" src="https://github.com/lankuohsing/InternLM_notes/assets/12205805/62d77399-1a7a-4ce6-b18b-c15c6de105dc">
