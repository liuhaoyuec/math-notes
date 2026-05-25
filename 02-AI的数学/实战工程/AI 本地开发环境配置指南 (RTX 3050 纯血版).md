# 🗂️ Obsidian 笔记：AI 本地开发环境配置指南 (RTX 3050 纯血版)

**🏷️ 标签:** #AI环境配置 #PyTorch #Miniconda #避坑指南 
**📅 日期:** 2026-04-15

---

## 1. 🧠 宏观认知图谱 (我们在装什么？)
AI 环境配置的核心逻辑是**“俄罗斯套娃”与“绝对隔离”**。绝不能在 Windows 默认环境下装包，否则极易产生依赖冲突。

- 💻 **物理硬件:** RTX 3050 显卡 (提供算力)
  - 🔌 **驱动层:** NVIDIA 驱动 + CUDA 12.8 (算力调度通道)
    - 🛡️ **隔离墙:** Miniconda (切断与系统其他 Python 软件的联系)
      - 📦 **沙盒环境:** `ai_base` (独立的文件夹)
        - 🐍 **基础语言:** Python 3.10 (最稳定版本)
        - ⚙️ **核心计算库:** PyTorch (强制注入包含 CUDA 12.4 的完整版)

---

## 2. 🚀 标准操作 S.O.P (按顺序执行)

### 步骤 0：硬件自检 (查看显卡底牌)
在任意终端执行，查看当前显卡支持的最高 CUDA 版本（`CUDA Version`）。
```bash
nvidia-smi
```
> **💡 规则：** 后续下载的 PyTorch-CUDA 版本，必须 **≤** 这里显示的 CUDA Version。

### 步骤 1：建立隔离沙盒 (Miniconda)
打开 `Anaconda Prompt`，执行以下命令创建并进入沙盒：
```bash
# 1. 创建名为 ai_base 的环境，并锁定 Python 3.10 版本
conda create -n ai_base python=3.10 -y

# 2. 激活并进入该沙盒
conda activate ai_base
```

### 步骤 2：暴力注入满血版 PyTorch (极其重要)
⚠️ **绝对不要使用国内镜像源（如清华源）下载 PyTorch！** 国内镜像源默认只提供 CPU 阉割版。必须在开启**魔法代理（全局模式/TUN模式）**的情况下，使用 `pip` 从官方直接拉取 2.5GB 完整版：
```bash
# --index-url 强制从官方获取，cu124 代表包含 CUDA 12.4 底层库
pip install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu124](https://download.pytorch.org/whl/cu124)
```

### 步骤 3：点火自检测试 (验证环境)
在 `ai_base` 环境下，依次输入并回车：
```python
python
import torch
print(torch.cuda.is_available()) # 必须输出 True 才算成功！
exit()
```

---

## 3. 💣 黄金避坑准则 (Troubleshooting)

**🔴 踩坑症状：** 测试 `torch.cuda.is_available()` 依然返回 `False`。

**🔍 诊断原因：** 典型的**“全局环境污染”**。因为之前电脑里 `C:\Users\...\AppData\Roaming\Python` 目录中残留过旧的 CPU 版 PyTorch。`pip` 安装时直接关联了旧文件（引狼入室）。

**🛠️ 破解方案：**
先卸载假货，再添加 `--ignore-installed` 参数，强制无视所有历史残留，在当前沙盒内重新下载：
```bash
# 1. 斩草除根
pip uninstall torch torchvision torchaudio -y

# 2. 强行覆写安装
pip install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu124](https://download.pytorch.org/whl/cu124) --ignore-installed
```