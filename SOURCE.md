# 来源记录：CNN+LSTM 时序预测代码

## 原始出处

| 项目 | 内容 |
| ---- | ---- |
| 标题 | 时序预测 |
| 博客 | xqy2006's blog（GitHub Pages） |
| 链接 | https://xqy2006.github.io/article/a4iwsl8j/ |
| 发布时间 | 2025-03-08 |
| 标签 | CNN LSTM python · 4 min · 897 words |

## 内容说明

博客提供了一段 CNN+LSTM 时序预测代码（约 145 行），支持：

- 多特征输入、多步预测
- K 折交叉验证
- 训练损失曲线与预测对比曲线可视化
- 各折模型权重保存（`model-foldN.pt`）与多折集成预测

## 本仓库收录的文件

| 文件 | 说明 |
| ---- | ---- |
| `cnn_lstm.py` | 整理后的可运行代码（仅修复缩进与两处断行，逻辑未改动） |

## 整理说明

原始博客页面因排版原因丢失了 Python 缩进。为便于运行和对照学习，本仓库版本仅做了以下最小修改：

1. 修复全部缩进；
2. 将原文断行的 `folenum = 0 for train_index, test_index in kf.split(X):` 还原为赋值语句 + for 循环两行；
3. 补充文件头中文注释与整理说明（不影响原逻辑）。

除此之外，**未改动任何超参数、变量命名与算法逻辑**，可与原文逐行对照。

## 运行依赖

- Python 3.x
- torch / torchvision / pandas / numpy / scikit-learn / matplotlib

## 数据准备

代码运行需要两个 CSV 文件（博客未提供示例数据）：

- `data.csv`：训练数据，需包含 `feature1` ~ `feature4` 四列，要预测的特征放在第一列；
- `predict.csv`：预测输入数据，同样包含上述特征列。

## 原文遗留细节（保留原样，便于对照）

- 类属性 `self.tranform` 为原文拼写（应为 `transform`），因类内部一致，不影响运行；
- 变量 `total_len` 定义后未使用；
- 训练阶段每个 step 都会弹出 loss 曲线图（原文行为）；
- 最终预测使用最后一个折的 `model` 实例循环加载各折权重（原文逻辑）。
