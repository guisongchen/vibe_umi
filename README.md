# Vibe UMI - Robot Learning Documentation Hub

A comprehensive documentation repository for **Universal Manipulation Interface (UMI)** and its derivatives, covering hardware design, data processing, policy learning, and software implementation.

---

## 📚 Overview

This repository contains technical documentation and analysis for state-of-the-art robot imitation learning interfaces, with focus on:

- **Low-cost, portable data collection systems**
- **Vision-Language-Action (VLA) policy training**
- **In-the-wild robot learning**
- **Active perception for manipulation**

---

## 🗂️ Repository Structure

```
vibe_umi/
├── doc/
│   ├── UMI/                    # Original UMI paper
│   ├── FastUMI/                # FastUMI improvements
│   ├── DexUMI/                 # Dexterous hand version
│   ├── MV-UMI/                 # Multi-view extension
│   └── ActiveUMI/              # Active perception variant
│       ├── ActiveUMI_Introduction.md
│       ├── ActiveUMI_Hardware_Design.md
│       └── ActiveUMI_DataProcessing_and_SoftwareDesign.md
└── README.md                   # This file
```

---

## 🔬 Covered Systems

### 1. UMI (Universal Manipulation Interface)
**Original Paper**: Universal Manipulation Interface: In-The-Wild Robot Teaching Without In-The-Wild Robots

| Aspect | Description |
|--------|-------------|
| **Core Innovation** | Handheld gripper interface for bimanual teleoperation |
| **Hardware** | GoPro + 3D-printed gripper + wrist-mounted |
| **Key Feature** | In-the-wild data collection, in-lab robot training |

**Documentation**:
- [Hardware Design](doc/UMI/UMI_hardware_design.md)
- [Data Processing](doc/UMI/UMI_data_processing.md)
- [Diffusion Policy QA](doc/UMI/UMI_Diffusion_Policy_QA.md)

---

### 2. FastUMI
**Improvement**: Deployment speed and hardware accessibility

| Aspect | Description |
|--------|-------------|
| **Core Innovation** | Quick deployment without robot hardware modifications |
| **Hardware** | GoPro on gripper with clip-on mount |
| **Key Feature** | 30-minute deployment, GoPro + fisheye lens |

**Documentation**:
- [Comparison with UMI](doc/FastUMI/fastumi_vs_umi_comparison.md)

---

### 3. DexUMI
**Extension**: Dexterous hand manipulation

| Aspect | Description |
|--------|-------------|
| **Core Innovation** | Transfer from simple grippers to dexterous hands |
| **Hardware** | Enhanced gripper design with more DOFs |
| **Key Feature** | In-the-wild teleoperation for complex manipulation |

**Documentation**:
- [Summary](doc/DexUMI/DexUMI_Summary.md)
- [Hardware Design](doc/DexUMI/DexUMI_Hardware_Design.md)
- [Software Adaptation](doc/DexUMI/DexUMI_Software_Adaptation.md)

---

### 4. MV-UMI
**Extension**: Multi-view spatial relationships

| Aspect | Description |
|--------|-------------|
| **Core Innovation** | Multiple camera views for better spatial understanding |
| **Key Feature** | Hand-object spatial relationship modeling |

**Documentation**:
- [Spatial Relationship](doc/MV-UMI/MV-UMI-MultiView-Spatial-Relationship.md)
- [Comparisons](doc/MV-UMI/MV-UMI-vs-UMI-FastUMI-Comparison.md)

---

### 5. ActiveUMI ⭐
**Latest Innovation**: Active perception for robot manipulation

| Aspect | Description |
|--------|-------------|
| **Paper** | ActiveUMI: Robotic Manipulation with Active Perception from Robot-Free Human Demonstrations (Oct 2025) |
| **Core Innovation** | Robot actively controls its viewpoint via learned attention |
| **Hardware** | Meta Quest 3s VR + wearable PC |
| **Key Feature** | 70% success rate, 56% generalization to new environments |

**Key Advantages**:
- ✅ **Active Perception**: Robot controls head camera based on learned attention
- ✅ **High Precision**: 4.0mm RPE (vs 10.1mm for UMI)
- ✅ **Efficient**: 1.5-2× faster than traditional teleoperation
- ✅ **Generalizable**: 56% success on novel objects and scenes

**Documentation**:
- [Introduction](doc/ActiveUMI/ActiveUMI_Introduction.md) - Overview and core contributions
- [Hardware Design](doc/ActiveUMI/ActiveUMI_Hardware_Design.md) - VR system, calibration, sensors
- [Data & Software](doc/ActiveUMI/ActiveUMI_DataProcessing_and_SoftwareDesign.md) - Pipeline, policy learning, deployment

---

## 🏗️ System Comparison

| System | Camera Setup | Active Perception | Precision (RPE) | In-the-Wild | Cost |
|--------|-------------|-------------------|-----------------|-------------|------|
| **UMI** | Wrist-mounted | ❌ | 10.1mm | ✅ | Low |
| **FastUMI** | Wrist-mounted + clip-on | ❌ | ~10mm | ✅ | Low |
| **DexUMI** | Wrist-mounted | ❌ | ~10mm | ✅ | Medium |
| **MV-UMI** | Multi-view wrist | ❌ | ~10mm | ✅ | Medium |
| **ActiveUMI** | Wrist × 2 + Head × 1 | ✅ **Yes** | **4.0mm** | ✅ | **Low** |

---

## 🎯 Key Technical Insights

### Active Perception
The breakthrough insight from ActiveUMI:
> *"Learning how to look is as important as learning what to do."*

By recording human head movements (attention) during demonstration, the robot learns to:
- **Overcome occlusions** by moving its viewpoint
- **Acquire task-critical information** on demand
- **Handle long-horizon tasks** requiring precision

### Data Efficiency
ActiveUMI demonstrates high sample efficiency:
- **1% teleoperated data + 99% ActiveUMI data** → 95% success rate
- Pure ActiveUMI data → 80% success rate
- Reduces cost of developing robot foundation models

### Hardware Evolution
```
UMI (2023)          →  GoPro + 3D-printed gripper
    ↓
FastUMI (2024)      →  Clip-on mount, faster deployment
    ↓
DexUMI (2024)       →  Dexterous hand support
    ↓
MV-UMI (2024)       →  Multi-view cameras
    ↓
ActiveUMI (2025)    →  VR-based, active perception
```

---

## 🚀 Quick Start

### For Researchers
1. **Understand the basics**: Start with [UMI hardware design](doc/UMI/UMI_hardware_design.md)
2. **Explore active perception**: Read [ActiveUMI introduction](doc/ActiveUMI/ActiveUMI_Introduction.md)
3. **Implement hardware**: Follow [ActiveUMI hardware guide](doc/ActiveUMI/ActiveUMI_Hardware_Design.md)

### For Engineers
1. **Data pipeline**: Check [data processing docs](doc/ActiveUMI/ActiveUMI_DataProcessing_and_SoftwareDesign.md)
2. **Policy training**: Review VLA model integration and mixed training strategies
3. **Deployment**: See inference pipeline and software architecture

---

## 📖 Citation

If you use this documentation for your research, please cite the original papers:

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

## 🤝 Contributing

This is a documentation repository. To contribute:
1. Fork the repository
2. Add or improve documentation
3. Submit a pull request

---

## 📄 License

This documentation is provided for educational and research purposes. Please refer to individual paper licenses for specific implementations.

---

## 🔗 Resources

- **ActiveUMI Project Page**: https://activeumi.github.io
- **UMI Project Page**: https://umi-gripper.github.io
- **π₀ Model**: https://github.com/physical-intelligence/pi0

---

*Last Updated: March 2026*

*Maintained by: vibe_umi contributors*
