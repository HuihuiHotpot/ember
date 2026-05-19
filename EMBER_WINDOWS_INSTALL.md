# Ember Windows x64 安装步骤

适用仓库：

```text
https://github.com/HuihuiHotpot/ember
```

## 1. 安装 VS Build Tools 2022

安装 **Visual Studio Build Tools 2022**，勾选：

```text
Desktop development with C++
MSVC v143
Windows 10/11 SDK
```

编译时使用：

```text
x64 Native Tools Command Prompt for VS 2022
```

必须使用 x64 编译环境，因为 Conda、Python、Cantera、SUNDIALS 和最终生成的 `_ember.cp311-win_amd64.pyd` 都是 64 位。

## 2. 克隆仓库

```bat
git clone https://github.com/HuihuiHotpot/ember.git
cd ember
```

## 3. 创建 Conda 环境

直接使用仓库中的 `environment-verified.yaml`：

```bat
mamba env create -n ember-build -f environment-verified.yaml
```

或：

```bat
conda env create -n ember-build -f environment-verified.yaml
```

## 4. 编译并安装

打开 **x64 Native Tools Command Prompt for VS 2022**，然后执行：

```bat
conda activate ember-build
cd /d path\to\ember
scons build
scons install
```

`scons test` 可选；Windows 下可能因为旧 GUI/PySide 或可选测试依赖失败，不作为安装必需步骤。
