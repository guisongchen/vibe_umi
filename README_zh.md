# Vibe UMI - 机器人学习文档中心

一个关于**通用操作接口（Universal Manipulation Interface, UMI）**及其衍生系统的综合性技术文档库，涵盖硬件设计、数据处理、策略学习和软件实现。

---

## 📚 项目简介

本仓库包含最先进的机器人模仿学习接口的技术文档和分析，重点关注：

- **低成本、便携式数据收集系统**
- **视觉-语言-动作（VLA）策略训练**
- **野外机器人学习（In-the-wild robot learning）**
- **主动感知操作（Active perception for manipulation）**

---

## 🗂️ 仓库结构

```
vibe_umi/
├── doc/
│   ├── UMI/                    # 原始 UMI 论文
│   ├── FastUMI/                # FastUMI 改进版本
│   ├── DexUMI/                 # 灵巧手版本
│   ├── MV-UMI/                 # 多视角扩展版本
│   └── ActiveUMI/              # 主动感知变体
│       ├── ActiveUMI_Introduction.md
│       ├── ActiveUMI_Hardware_Design.md
│       └── ActiveUMI_DataProcessing_and_SoftwareDesign.md
└── README.md                   # 本文件
```

---

## 🔬 涵盖系统

### 1. UMI（通用操作接口）
**原始论文**: Universal Manipulation Interface: In-The-Wild Robot Teaching Without In-The-Wild Robots

| 方面 | 描述 |
|------|------|
| **核心创新** | 手持式夹爪接口，支持双手遥操作 |
| **硬件组成** | GoPro + 3D打印夹爪 + 手腕安装 |
| **关键特性** | 野外数据收集，实验室机器人训练 |

**技术文档**:
- [硬件设计](doc/UMI/UMI_hardware_design.md)
- [数据处理](doc/UMI/UMI_data_processing.md)
- [扩散策略问答](doc/UMI/UMI_Diffusion_Policy_QA.md)

---

### 2. FastUMI
**改进点**: 部署速度和硬件可获取性

| 方面 | 描述 |
|------|------|
| **核心创新** | 无需改装机器人硬件的快速部署 |
| **硬件组成** | 夹爪上的卡扣式GoPro安装 |
| **关键特性** | 30分钟完成部署，GoPro + 鱼眼镜头 |

**技术文档**:
- [与UMI的对比](doc/FastUMI/fastumi_vs_umi_comparison.md)

---

### 3. DexUMI
**扩展**: 灵巧手操作

| 方面 | 描述 |
|------|------|
| **核心创新** | 从简单夹爪到灵巧手的迁移 |
| **硬件组成** | 增强夹爪设计，更多自由度 |
| **关键特性** | 野外遥操作，支持复杂操作任务 |

**技术文档**:
- [技术总结](doc/DexUMI/DexUMI_Summary.md)
- [硬件设计](doc/DexUMI/DexUMI_Hardware_Design.md)
- [软件适配](doc/DexUMI/DexUMI_Software_Adaptation.md)

---

### 4. MV-UMI
**扩展**: 多视角空间关系

| 方面 | 描述 |
|------|------|
| **核心创新** | 多相机视角，更好的空间理解能力 |
| **关键特性** | 手-物体空间关系建模 |

**技术文档**:
- [空间关系](doc/MV-UMI/MV-UMI-MultiView-Spatial-Relationship.md)
- [系统对比](doc/MV-UMI/MV-UMI-vs-UMI-FastUMI-Comparison.md)

---

### 5. ActiveUMI ⭐（重点推荐）
**最新创新**: 主动感知机器人操作

| 方面 | 描述 |
|------|------|
| **论文** | ActiveUMI: Robotic Manipulation with Active Perception from Robot-Free Human Demonstrations (2025年10月) |
| **核心创新** | 机器人通过学习到的注意力主动控制自身视点 |
| **硬件组成** | Meta Quest 3s VR + 可穿戴计算机 |
| **关键特性** | 70%成功率，在新环境中保持56%泛化能力 |

**核心优势**:
- ✅ **主动感知**: 机器人基于学习到的注意力控制头部相机
- ✅ **高精度**: 4.0mm 相对位姿误差（相比UMI的10.1mm）
- ✅ **高效率**: 比传统遥操作快1.5-2倍
- ✅ **强泛化**: 在新物体和新场景中保持56%成功率

**技术文档**:
- [技术简介](doc/ActiveUMI/ActiveUMI_Introduction.md) - 概述和核心贡献
- [硬件设计](doc/ActiveUMI/ActiveUMI_Hardware_Design.md) - VR系统、校准、传感器
- [数据处理与软件](doc/ActiveUMI/ActiveUMI_DataProcessing_and_SoftwareDesign.md) - 数据流、策略学习、部署

---

## 🏗️ 系统对比

| 系统 | 相机配置 | 主动感知 | 精度 (RPE) | 野外采集 | 成本 |
|------|-------------|-------------------|-----------------|-------------|------|
| **UMI** | 手腕安装 | ❌ | 10.1mm | ✅ | 低 |
| **FastUMI** | 手腕安装 + 卡扣式 | ❌ | ~10mm | ✅ | 低 |
| **DexUMI** | 手腕安装 | ❌ | ~10mm | ✅ | 中 |
| **MV-UMI** | 多视角手腕安装 | ❌ | ~10mm | ✅ | 中 |
| **ActiveUMI** | 手腕×2 + 头部×1 | ✅ **是** | **4.0mm** | ✅ | **低** |

---

## 🎯 核心技术洞察

### 主动感知（Active Perception）
ActiveUMI的突破洞见：
> *"学习如何观察（how to look）与学习做什么（what to do）同样重要。"*

通过记录人类演示时的头部运动（注意力），机器人学会：
- **通过移动视点克服遮挡**
- **按需获取任务关键信息**
- **处理需要高精度的长时程任务**

### 数据效率
ActiveUMI展示了高样本效率：
- **1%遥操作数据 + 99% ActiveUMI数据** → 95%成功率
- 纯ActiveUMI数据 → 80%成功率
- 大幅降低开发机器人基础模型的成本

### 硬件演进
```
UMI (2023)          →  GoPro + 3D打印夹爪
    ↓
FastUMI (2024)      →  卡扣式安装，快速部署
    ↓
DexUMI (2024)       →  支持灵巧手
    ↓
MV-UMI (2024)       →  多视角相机
    ↓
ActiveUMI (2025)    →  VR-based，主动感知
```

---

## 🚀 快速开始

### 研究人员
1. **了解基础**: 从 [UMI硬件设计](doc/UMI/UMI_hardware_design.md) 开始
2. **探索主动感知**: 阅读 [ActiveUMI技术简介](doc/ActiveUMI/ActiveUMI_Introduction.md)
3. **实现硬件**: 跟随 [ActiveUMI硬件指南](doc/ActiveUMI/ActiveUMI_Hardware_Design.md)

### 工程师
1. **数据流**: 查看 [数据处理文档](doc/ActiveUMI/ActiveUMI_DataProcessing_and_SoftwareDesign.md)
2. **策略训练**: 了解VLA模型集成和混合训练策略
3. **部署**: 参考推理流水线和软件架构

---

## 📖 引用

如果您在研究中使用了本文档，请引用原始论文：

**ActiveUMI**:
```bibtex
@article{zeng2025activeumi,
  title={ActiveUMI: Robotic Manipulation with Active Perception from Robot-Free Human Demonstrations},
  author={Zeng, Qiyuan and Li, Chengmeng and St. John, Jude and Zhou, Zhongyi and Wen, Junjie and Feng, Guorui and Zhu, Yichen and Xu, Yi},
  journal={arXiv preprint arXiv:2510.01607},
  year={2025}
}
```

**UMI**:
```bibtex
@article{chi2024universal,
  title={Universal Manipulation Interface: In-The-Wild Robot Teaching Without In-The-Wild Robots},
  author={Chi, Cheng and Xu, Zhenjia and Pan, Chuer and Cousineau, Eric and Burchfiel, Benjamin and Feng, Siyuan and Tedrake, Russ and Song, Shuran},
  journal={arXiv preprint arXiv:2402.10329},
  year={2024}
}
```

---

## 🤝 贡献

这是一个文档仓库。如需贡献：
1. Fork 本仓库
2. 添加或改进文档
3. 提交 Pull Request

---

## 📄 许可

本文档仅供教育和研究目的使用。具体实现请遵守原始论文的许可协议。

---

## 🔗 资源链接

- **ActiveUMI 项目主页**: https://activeumi.github.io
- **UMI 项目主页**: https://umi-gripper.github.io
- **π₀ 模型**: https://github.com/physical-intelligence/pi0

---

## 🌐 语言切换

- [English Version](README.md)
- 中文版本（当前）

---

*最后更新: 2026年3月*

*维护者: vibe_umi 贡献者*
