# SEER-GBM-Survival-Analysis
基于SEER数据库的脑胶质母细胞瘤预后因素分析及预测模型构建

## 项目简介

基于美国SEER数据库，分析2004-2019年脑胶质母细胞瘤(GBM)患者的
预后因素，并构建Cox比例风险预测模型。

## 数据来源

- **数据库**: SEER Research Data, 17 Registries, Nov 2025 Sub (2000-2023)
- **筛选条件**:
  - 原发部位: C71.0-C71.9 (Brain)
  - 组织学: 9440/3 (Glioblastoma NOS), 9441/3 (Giant cell), 9445/3 (IDH-mutant)
  - 诊断年份: 2004-2019
- **样本量**: 39,796例 (清洗后)

## 分析方法

| 步骤 | 方法 | 工具 |
|------|------|------|
| 数据清洗 | 缺失值处理、变量编码 | pandas |
| 描述性分析 | 基线特征表、分布图 | matplotlib/seaborn |
| 生存分析 | Kaplan-Meier曲线、Log-rank检验 | lifelines |
| 预测模型 | Cox比例风险回归 | lifelines |
| 模型评估 | ROC曲线、校准曲线、DCA | scikit-learn/lifelines |
| 可视化 | 列线图 (Nomogram) | matplotlib |

## 项目结构

├── data.csv # 原始SEER数据

├── cleaned_data.csv # 清洗后数据

├── data_clean.ipynb # 数据清洗

├── descriptive_analysis.ipynb # 描述性分析 + Table 1

├── survival_analysis.ipynb # KM曲线 + Log-rank检验

├── prediction_model.ipynb # Cox回归 + ROC + DCA + 列线图

├── fig1_sex.tiff ~ fig16_nomogram.tiff # 结果图

└── table1.csv # 基线特征表

## 主要结果

- Cox模型一致性指数 (C-index): 0.71
- 独立预后因素: 年龄、手术、放疗、化疗、分期
- 1年/3年/5年 AUC: 见ROC曲线

## 环境依赖

Python >= 3.8

pandas

numpy

matplotlib

seaborn

lifelines

scikit-learn

## 参考文献

1. SEER Program: https://seer.cancer.gov
2. lifelines documentation: https://lifelines.readthedocs.io

## License

MIT License

## ⚠️ Limitations

- Race and Sex were not included as covariates in the Cox model
- Age and Stage were treated as ordinal variables
- Grade was excluded due to 74.5% missing data
