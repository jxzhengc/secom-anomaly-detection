# 基于 SECOM 数据集的半导体制造过程异常检测

## 项目背景
半导体制造过程数据维度高、良率极高（极度不平衡），传统单变量 SPC 控制图难以捕捉多变量复杂异常模式。
本项目基于 UCI SECOM 公开数据集，构建了一套**可解释的多变量异常检测流程**。

## 数据集
- 1567 个样本，590 个传感器特征
- 标签：良品（-1）、不良品（1）
- 良品率约 93%，极度不平衡

## 我的工作
1. **数据预处理**：处理约 4 万个缺失值，删除常量列，特征维度从 590 降至 400+
2. **特征工程**：方差过滤 + 随机森林特征重要性，提取 Top 30 关键传感器特征
3. **模型构建与优化**：
   - Isolation Forest 无监督基线：召回率 29%
   - Gradient Boosting 有监督模型：Accuracy 0.93 但召回率仅 16%（不平衡陷阱）
   - **阈值调优**：将不良品召回率从 16% 提升至 39%，符合半导体行业“漏报代价 > 误报代价”的业务逻辑
4. **模型可解释性（SHAP）**：利用 SHAP 瀑布图进行根因分析，定位导致异常的关键传感器，将机器学习结果转化为工艺工程师可执行的排查线索

## 关键技术栈
Python、Pandas、Scikit-learn、Matplotlib、SHAP、Jupyter Notebook

## 项目成果可视化
<img width="1012" height="427" alt="image" src="https://github.com/user-attachments/assets/14f019c9-7976-4a06-a7ef-0cd36a4624a9" />
<img width="1101" height="465" alt="image" src="https://github.com/user-attachments/assets/5cbc4c7f-d6b7-4994-81cd-ece21d1187b1" />
<img width="545" height="456" alt="image" src="https://github.com/user-attachments/assets/7b49afbd-54e1-4d9b-b262-f07866fe7b01" />
<img width="914" height="597" alt="屏幕截图 2026-09-21 144438" src="https://github.com/user-attachments/assets/0e531ed9-48d7-4f16-9bf6-0009c78f8217" />


