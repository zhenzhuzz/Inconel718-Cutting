# Inconel718-Cutting
Thermomechanical cutting simulation of nickel-based superalloy Inconel 718 using Abaqus and CuttingSim, analyzing effects of tool geometry, cutting speed, and friction on forces, temperature fields, and chip morphology.

# 镍基高温合金 Inconel718 热力耦合切削仿真

**作者:** 朱镇  
**单位:** 清华大学深圳国际研究生院  
**工具:** Abaqus, CuttingSim  
**语言:** 中文

---

## 📜 项目概述

本仓库包含两个关于 **镍基高温合金 Inconel718 (GH4169)** 切削过程的**热-力耦合有限元仿真**课程项目。  
两次研究的建模思路相似，但研究重点不同：

1. **项目一（2023年1月）**：使用 Abaqus 建立 Johnson–Cook 塑性与损伤模型的全热-力耦合切削仿真。  
2. **项目二（2023年6月）**：基于 CuttingSim 进行刀具圆角、切削速度、摩擦系数等参数化研究，并与文献仿真及实验结果对比。

---

## 🔬 背景

Inconel718 是一种典型的镍基高温合金，主要特性：
- 在高温（约 850 ℃）下仍保持高强度和高刚度  
- 极佳的耐腐蚀性能  
- 加工性差：低导热率、加工硬化、易产生积屑瘤

应用场景：航空发动机涡轮叶片、燃烧室等高温部件。  

由于加工性差，对切削力、温度场及切屑形成的准确预测非常重要，因此需要 **高精度有限元模拟** 来优化工艺参数与刀具设计。

---

## 📂 仓库结构

Inconel718-CuttingSim  
│  
├── project1_Abaqus/ # 2023年1月项目文件  
│ ├── CAD_models/ # 几何与网格  
│ ├── Material_data/ # Inconel718 及刀具材料属性  
│ ├── Abaqus_input/ # Abaqus .inp 输入文件  
│ ├── Results/ # 力、温度、切屑形貌结果  
│ └── Report/ # 最终报告 PDF  
│  
├── project2_CuttingSim/ # 2023年6月项目文件  
│ ├── CuttingSim_inputs/ # 参数化配置文件  
│ ├── Data/ # 仿真输出数据（csv/txt）  
│ ├── Plots/ # 绘图与对比曲线  
│ └── Report/ # 最终报告 PDF  
│  
└── README.md

---


## 🧩 建模方法

### 项目一 – Abaqus 热-力耦合模型
- **热模型**：热力学第一定律，考虑温度相关的 \( c_p \)、\(\lambda\)、\(\alpha\)  
- **力学模型**：弹-塑性，Johnson–Cook 塑性本构  
- **损伤模型**：Johnson–Cook 损伤准则实现切屑分离  
- **接触模型**：库仑摩擦（\(\mu = 0.5\)），热接触完全导通  
- **研究变量**：切削速度 \( V_c = 20, 40, 80\ \text{m/min} \)

### 项目二 – CuttingSim 参数化研究
- **研究变量**：
  - 刀具圆角 \( r = 10, 20, 30\ \mu\text{m} \)
  - 切削速度 \( V_c = 20, 40, 80\ \text{m/min} \)
  - 摩擦系数 \( \mu = 0, 0.5 \)
- **输出量**：
  - 切削力（CF）
  - 进给力（FF）
  - 切屑厚度与形貌
- **对比**：我的仿真结果 vs. 文献仿真结果 vs. 实验结果

---

## 📊 仿真结果与对比

### 项目一（Abaqus）
- 切削力与进给力随速度变化趋势  
- 切削区温度场分布  
- 切屑形貌与厚度  

**示例结果**：  
![切削力随速度变化占位图](images/project1_force_vs_speed.png)  
![温度场分布占位图](images/project1_temperature.png)  
![切屑形貌GIF占位图](images/project1_chip.gif)

---

### 项目二（CuttingSim）
- 不同刀具圆角与切削速度下的力变化趋势  
- 切屑厚度变化规律  
- 与参考数据的吻合程度分析  

**示例结果**：  
![力与刀具圆角关系占位图](images/project2_force_radius.png)  
![切屑厚度对比占位图](images/project2_chip_thickness.png)  
![切屑形貌GIF占位图](images/project2_chip.gif)

---

## 📚 参考文献

1. Rinaldi S, Imbrogno S, Rotella G, et al. *Physics based modeling of machining Inconel 718 to predict surface integrity modification*. Procedia CIRP, 2019, 82: 350–355.  
2. Bedzra R. *Finite element simulation of two dimensional orthogonal cutting process and comparison with experiments*. RWTH Aachen University, 2013.

---

## 🚀 运行方法

### 项目一（Abaqus）
1. 在 Abaqus CAE 中加载 `.inp` 文件  
2. 从 `Material_data/` 中导入材料属性  
3. 运行热-力耦合温度-位移分析  
4. 在 Abaqus Viewer 中进行后处理  

### 项目二（CuttingSim）
1. 打开 CuttingSim 软件  
2. 加载 `CuttingSim_inputs/` 中的参数文件  
3. 运行仿真并保存输出结果  
4. 使用 `Plots/` 中的脚本进行绘图对比  

---

## 📌 注意事项
- 所有材料参数均为温度依赖型，取自文献数据  
- 仿真与实验的差异主要来自模型简化与边界条件假设  
- 本 README 中所有图片为占位符，需替换为实际结果


