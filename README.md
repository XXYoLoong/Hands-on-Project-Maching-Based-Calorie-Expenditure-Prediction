# Hands-on Project: Machine Learning Based Calorie Expenditure Prediction

本仓库为“第8周 模型实战”课程作业项目：基于机器学习的卡路里消耗预测。项目使用 `Exercise.csv.xlsx` 与 `Calories.csv.xlsx` 两个数据文件，通过用户年龄、性别、身高、体重、运动时长、心率、体温等特征预测运动过程中的卡路里消耗量。

## 1. 项目目标

在运动健康场景中，用户希望根据自身身体信息与运动状态估算卡路里消耗。本项目将卡路里消耗预测建模为典型回归问题，完成数据读取、数据合并、特征编码、模型训练、误差计算、模型对比与结果分析。

## 2. 数据说明

| 文件 | 说明 |
| --- | --- |
| `data/Exercise.csv.xlsx` | 用户基本信息与运动记录 |
| `data/Calories.csv.xlsx` | 用户对应的卡路里消耗 |

`Exercise.csv.xlsx` 包含 `User_ID`、`Gender`、`Age`、`Height`、`Weight`、`Duration`、`Heart_Rate`、`Body_Temp`。  
`Calories.csv.xlsx` 包含 `User_ID`、`Calories`。  
两个数据表通过 `User_ID` 字段进行合并。

## 3. 模型选择

本项目选择三种回归模型：

1. **Linear Regression**：线性回归，作为基线模型。
2. **Random Forest Regressor**：随机森林回归，适合处理非线性特征关系。
3. **Gradient Boosting Regressor**：梯度提升回归，具有较强的拟合能力。

## 4. 实验结果

| Model | Train RMSE | Test RMSE | Train MAE | Test MAE | Train R² | Test R² |
| --- | --- | --- | --- | --- | --- | --- |
| Linear Regression | 11.27 | 11.49 | 8.31 | 8.44 | 0.9672 | 0.9673 |
| Random Forest Regressor | 1.07 | 2.65 | 0.65 | 1.69 | 0.9997 | 0.9983 |
| Gradient Boosting Regressor | 3.48 | 3.61 | 2.49 | 2.61 | 0.9969 | 0.9968 |

综合测试集 RMSE、MAE 和 R² 指标，随机森林回归模型表现最好。其测试集 RMSE 最低，R² 最高，说明该模型能够较好捕捉运动时长、心率、年龄等特征与卡路里消耗之间的非线性关系。

## 5. 项目结构

```text
.
├── calorie_prediction.py
├── requirements.txt
├── README.md
├── data/
│   ├── Exercise.csv.xlsx
│   └── Calories.csv.xlsx
├── results/
│   └── model_results.xlsx
├── figures/
│   ├── predicted_vs_actual.png
│   ├── model_comparison.png
│   └── feature_importance.png
└── report/
    └── 卡路里预测项目报告.docx
```

## 6. 运行方法

安装依赖：

```bash
pip install -r requirements.txt
```

运行模型训练：

```bash
python calorie_prediction.py --exercise data/Exercise.csv.xlsx --calories data/Calories.csv.xlsx --output results
```

运行后会输出：

- `results/model_results.xlsx`：三种模型的训练误差与测试误差。
- `results/predicted_vs_actual.png`：最优模型真实值与预测值对比图。
- `results/model_comparison.png`：模型测试集 RMSE 对比图。
- `results/feature_importance.png`：随机森林特征重要性图。

## 7. 版权与开源协议

Copyright 2026 Jiacheng Ni

Licensed under the Apache License, Version 2.0.  
See the [LICENSE](LICENSE) file for details.
