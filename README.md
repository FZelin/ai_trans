# ai_trans
ai_trans

##### 1. LLaMA-Factory 安装部署
LLaMA-Factory 的 Github地址：[https://github.com/hiyouga/LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory)
- 克隆仓库
```bash
git clone --depth 1 https://github.com/hiyouga/LLaMA-Factory.git
```
- 修改配置，将 conda 虚拟环境安装到数据盘（更改pkg以及env等资源路径为自己的盘符，方便后期迁移）
```bash
mkdir -p /root/autodl-tmp/conda/pkgs 
conda config --add pkgs_dirs /root/autodl-tmp/conda/pkgs 
mkdir -p /root/autodl-tmp/conda/envs 
conda config --add envs_dirs /root/autodl-tmp/conda/envs
```


- 安装conda

- 检查conda版本
```bash
conda --version
```

- 创建 conda 虚拟环境(必须 3.10 的 python 版本，不然和 LLaMA-Factory 不兼容)
```bash
conda create -n lf python=3.10
```

- 查看已经创建的所有的虚拟环境列表以及路径
```bash
conda env list
```

- 激活虚拟环境
```bash
conda activate lf
```

- 如出现conda init提示，需要输入conda init 并且更新bashrc
```bash
conda init
source ~/.bashrc
``` 

- 在虚拟环境中安装 LLaMA Factory 相关依赖(注：得进入LLaMA Factory文件夹下安装)
```bash
pip install -e ".[torch,metrics]"
```
如报错 bash: pip: command not found ，先执行 conda install pip 即可

- 检验是否安装成功
```bash
llamafactory-cli version
```
- 检查llamafactory-cli安装位置
```bash
which llamafactory-cli
```
- 启动 LLama-Factory 的可视化微调界面 （由 Gradio 驱动）
```bash
llamafactory-cli webui
```

- 创建文件夹统一存放所有模型
```bash
mkdir hugging-face
```
- 修改 HuggingFace 的镜像源 
```bash
export HF_ENDPOINT=https://hf-mirror.com
```
- 修改模型下载的默认位置(这里是一autodl位置为示例)
```bash
export HF_HOME=/root/autodl-tmp/hugging-face
```
 注意：这种配置方式只在当前 shell 会话中有效，如果你希望这个环境变量在每次启动终端时都生效，可以将其添加到你的用户配置文件中（修改 `~/.bashrc` 或 `~/.zshrc`）


- 检查环境变量是否生效
```bash
echo $HF_ENDPOINT
echo $HF_HOME
```

- 安装 HuggingFace 官方下载工具
```text
pip install -U huggingface_hub
```
- 执行下载命令
```bash
huggingface-cli download --resume-download Qwen/QwQ-32B
```


--------------------

unsloth 安装

创建conda 虚拟环境 
```bash
conda create --name unsloth python=3.11
conda init
source ~/.bashrc
conda activate unsloth
```

安装jupyter和jupyter Kernel
```bash
conda install jupyterlab
conda install ipykernel
python -m ipykernel install --user --name unsloth --display-name "Python unsloth"
```

安装Unsloth
```bash
pip install --upgrade --force-reinstall --no-cache-dir unsloth unsloth_zoo
```




---------------------
vllm 安装


创建vllm 虚拟环境
```bash
conda create --name vllm python=3.11
conda init
source ~/.bashrc
conda activate vllm
```

安装vllm
```bash
pip install bitsandbytes>=0.45.3
pip install --upgrade vllm
```
-注：bitsandbytes是为了适配4bit动态量化模型调用，必须引用的库


