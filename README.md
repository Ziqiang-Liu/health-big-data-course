# 健康大数据实践课程

## 项目环境规范

本项目的所有 Python 代码、Jupyter Notebook 和依赖包，统一使用以下 Conda 环境：

| 项目 | 要求 |
|---|---|
| 环境名称 | class |
| Python 版本 | 3.8.20 |
| 环境路径 | D:\Miniconda3\envs\class |
| Notebook 内核 | class (Python 3.8.20) |

严禁使用系统 Python、其他 Conda 环境、旧版 D:\Miniconda 或 uv 环境运行本项目代码。

## 激活环境

推荐在 Miniconda Prompt 中执行：

    conda activate class

激活后检查当前解释器：

    python --version
    python -c "import sys; print(sys.executable)"

预期结果：

    Python 3.8.20
    D:\Miniconda3\envs\class\python.exe

如果终端无法识别 conda，可以直接使用 Miniconda 的完整路径：

    D:\Miniconda3\Scripts\conda.exe run --name class python --version

## VS Code / Jupyter 设置

打开 Notebook 后，在右上角内核选择器中选择：

    class (Python 3.8.20)

该内核对应的 Python 路径必须是：

    D:\Miniconda3\envs\class\python.exe

如果内核没有显示，在 class 环境中执行：

    conda activate class
    conda install --name class ipykernel --override-channels --channel conda-forge --yes
    python -m ipykernel install --user --name class --display-name "class (Python 3.8.20)"

## 安装依赖的规则

所有依赖必须安装到 class 环境中，禁止直接对系统 Python 或其他环境执行安装命令。

优先使用 Conda 安装：

    conda activate class
    conda install --name class <package-name> --override-channels --channel conda-forge --yes

Conda 中没有所需包时，先激活 class，再使用该环境的 Python 安装：

    conda activate class
    python -m pip install <package-name>

安装后确认 pip 也属于 class 环境：

    python -m pip --version

不要使用以下形式安装项目依赖：

    pip install <package-name>

除非已经确认当前终端处于 class 环境，否则不要执行安装命令。

## 当前已安装的主要包

当前环境已配置：

- Python 3.8.20
- ipykernel 6.29.5
- pandas 2.0.3
- numpy 1.24.4

## 运行前检查

运行 Notebook 或 Python 脚本前，确认：

    import sys

    print(sys.executable)
    assert sys.executable.lower() == r"d:\miniconda3\envs\class\python.exe"

如果断言失败，请先切换到 class (Python 3.8.20) 内核。

## 更新环境记录

当项目新增或删除依赖时，在 class 环境中更新环境记录：

    conda activate class
    conda env export --name class --from-history > environment.yml

更新记录后再运行项目测试，确保所有 Notebook 和脚本仍然可以执行。
