# DexUMI: Using Human Hand as the Universal Manipulation Interface for Dexterous Manipulation

**论文来源**: arXiv:2505.21864v3 (CoRL 2025)
**项目网站**: https://dex-umi.github.io/

---

## 核心问题

**如何将人类灵巧操作技能高效地转移到各种机器人手上，同时最小化"具身差异"（Embodiment Gap）的影响。**

---

## 问题背景

### 1. 具身差异（Embodiment Gap）
人类手与机器人手在以下方面存在显著差异：
- 运动学结构（Kinematic structures）
- 接触表面形状（Contact surface shape）
- 可用触觉信息（Available tactile information）
- 视觉外观（Visual appearance）

### 2. 现有方法的局限性
- **遥操作（Teleoperation）**：存在空间观察不匹配、缺乏直接触觉反馈的问题
- **人类手部视频学习**：需要额外的真实世界机器人数据或依赖仿真学习

---

## 解决方案: DexUMI 框架

DexUMI 是一个数据收集和策略学习框架，包含两个核心适应层：

### 1. 硬件适应（Hardware Adaptation）
设计**可穿戴手部外骨骼（Wearable Hand Exoskeleton）**，实现：

| 特性 | 说明 |
|------|------|
| 直观的演示 | 用户可以直接接触物体，获得直接触觉反馈 |
| 动作映射 | 外骨骼约束人类手部动作以匹配目标机器人的运动学 |
| 精确关节捕捉 | 通过编码器直接读取关节角度，而非视觉追踪 |
| 触觉信息匹配 | 在指尖安装与目标机器人手相同的触觉传感器 |

**优化目标**：通过双层优化框架，同时考虑：
- 指尖工作空间的相似性（最大化）
- 可穿戴性约束（确保人类手部舒适操作）

### 2. 软件适应（Software Adaptation）
通过数据处理流程弥合视觉差距：

1. **分割（Segment）**：使用 SAM2 分割视频中的人类手和外骨骼
2. **修复（Inpaint）**：使用 ProPainter 修复被移除区域的背景
3. **录制机器人动作**：在机器人手上重放录制的关节动作并录制视频
4. **合成（Compose）**：将修复后的背景与机器人手视频合成，保持正确的遮挡关系

---

## 实验评估

### 测试的机器人手
- **Inspire Hand**：12-DoF（6个主动自由度）欠驱动手
- **XHand**：12-DoF 全驱动手

### 测试任务
1. **Cube Pick and Place** - 基础抓取精度
2. **Egg Carton Opening** - 多指协调
3. **Tea Picking with Tool** - 使用工具的接触丰富操作
4. **Kitchen** - 长时程任务（关旋钮、移动锅、撒盐等）

### 主要结果

| 指标 | 结果 |
|------|------|
| 平均任务成功率 | **86%** |
| 数据收集效率提升 | **3.2x** （相比传统遥操作） |

### 关键发现
- **相对手指轨迹**比绝对轨迹更鲁棒
- **触觉反馈**在具有清晰力分布的任务中显著提高性能
- **软件适应**（图像修复）对于策略学习至关重要

---

## 局限性与未来工作

### 硬件适应
- 每款机器人手需要专门的外骨骼设计
- 可穿戴性受限于3D打印材料强度
- 触觉传感器在高压下会漂移

### 软件适应
- 目前仍需要真实机器人硬件来获取机器人手图像
- 修复质量受限于光照条件
- 相机位置固定，不支持移动相机

### 机器人手硬件
- 现有商业手部在精度方面存在限制
- 机器人手与人类手的大小差异可能影响可穿戴性

---

## 与 UMI 的关系

DexUMI 扩展了 UMI（Universal Manipulation Interface）的概念：
- UMI 主要关注夹爪（gripper）操作
- DexUMI 针对**多指灵巧手（dexterous hands）**的操作
- 两者都强调使用人类作为自然的操作接口

---

## 关键词

Dexterous Manipulation, Learning from Human, Imitation Learning, Exoskeleton, Embodiment Gap
