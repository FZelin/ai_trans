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
