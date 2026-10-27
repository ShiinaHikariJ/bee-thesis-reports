# 公开数据

[← 返回实验汇报](../README.md) · [进度页](../progress.md) · [数据集介绍](../datasets.md)

## web_v1：网络开放许可图片（137 张，2026-10-26）

- **来源**：Wikimedia Commons 和 iNaturalist。
- **许可**：只收允许再分发的许可证，包括 CC0、公有领域、CC BY、CC BY-SA。
- **署名**：每张图的来源页、作者、许可证见 [`web_v1/ATTRIBUTION.csv`](web_v1/ATTRIBUTION.csv)。转载或在论文中展示时，需按 CC BY / BY-SA 要求署名；CC BY-SA 图片的衍生作品需以相同许可发布。

| 文件夹 | 内容 | 张数 |
|---|---|---|
| `F_comb_bees` | 巢脾/蜂框 + 蜜蜂 | 88 |
| `Q_queen_cells` | 王台 | 11 |
| `C_comb_closeup` | 巢房特写，蜜蜂很少或没有 | 38 |

| 许可证 | 张数 |
|---|---|
| CC BY-SA（2.0 / 2.5 / 3.0 / 4.0） | 61 |
| CC BY（2.0 / 3.0 / 4.0） | 47 |
| 公有领域 / CC0 | 29 |

**去重**：
- 网络图之间的近重复 6 张（dHash 汉明距离 ≤ 6），已删除。
- 与训练、测试数据重复的 4 张已删除。重复是因为 Roboflow 数据集本身收录了网络图。

**标注状态：预标注，不是真值。**
- 每张图旁的 labelme JSON 来自 ours 模型，`annotation_status` = `PREANNOTATION_NOT_GROUND_TRUTH`。
- 只含 `bee` 框和 `queen_cell` 框，均为 4 点多边形。
- 巢房点在网络图上尺度未知、很不准，已删除。
- 蜂群密集或野生蜂巢的图漏检较多。
- 人工修正后，这批图将作为网络测试集，只用于测试，不参与训练。

## 未公开的数据及原因

| 数据 | 原因 |
|---|---|
| 自采现场图片 | 作者私有数据 |
| DeepBee 原图及由其派生的巢房补全标注、合成王台图 | 原数据集未写明许可证，正式发表前需向作者确认 |
| Roboflow / hivemind 等公开数据集 | 请从原始来源下载，见[数据集介绍](../datasets.md)；本仓库只提供 hivemind 开发/测试划分（[`results/other/hivemind_split_v1.json`](../results/other/hivemind_split_v1.json)） |
| 复制粘贴蜜蜂、扩散融合等合成图 | 由上述数据派生，体积大（每套约 300MB），可由代码重新生成 |
