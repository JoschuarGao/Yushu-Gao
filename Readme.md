# Optimal Graph Splitting and Merging of OpenStreetMap Road Networks  
# 基于OpenStreetMap路网的最优图划分与合并研究

### for Highly Parallel HD-Mapping for Deep Learning in Autonomous Driving  
### 面向自动驾驶高精地图并行制作与深度学习的图划分系统设计

This repository contains the code and documentation for my Master's thesis at KIT (Institute for Measurement and Control Systems - MRT).  
本仓库为我在卡尔斯鲁厄理工学院（KIT）MRT研究所硕士论文的代码与文档汇总。

---

##  Project Overview / 项目简介

HD-mapping for autonomous driving requires splitting large city-scale road networks into manageable, well-balanced subgraphs.  
为实现自动驾驶中的高精地图构建，需要将城市级路网图划分为若干结构合理、易于标注与并行处理的子图。

This project explores optimal graph partitioning methods (Balanced Minimum Cut Problem, Multilevel Partitioning),  
并使用多级图划分算法、平衡最小割方法等，对 OpenStreetMap 路网数据进行处理。

Key considerations include:
- Road type, number of lanes, road length
- Edge weight design (customizable)
- Partition quality evaluation: cut weight, balance, connectivity

核心技术点包括：
- 考虑道路类型、车道数、道路长度等要素的加权设计
- 分区划分质量评估：割边数量、总权重、分区平衡与连通性

---

##  Project Structure / 项目结构

```bash
thesis_template_latex-master/       # LaTeX 论文模板文件夹
Main/                               # 主体章节（.tex）
src/                                # 源码（图加载、权重设计、划分等）
  ├── KaHIP.py                      # 分区主程序
  ├── optimize_weights.py           # 参数优化器（Optuna）
  ├── road_type_weights.json        # 道路类型权重设定
  ├── lane_weight_version.json      # 车道数权重设定
cached_maps/                        # 地图缓存
results/                            # CSV 结果输出
figures/                            # 可视化图像输出


##  Project Structure / 项目结构
 Flexible weight design: road type, lanes, length

 Partitioning with KaMinPar (via METIS export)

 Evaluation: cut edges, weight sum, imbalance

 Visual output: maps with edge weights and partitions

 Optuna-based hyperparameter tuning

中文要点：

可自定义的边权计算方式（α·道路类型 + β·车道数 + γ·长度）

使用 KaMinPar 进行图划分

输出可视化图与分区评估指标

使用 Optuna 自动寻找最优权重组合

## Quick Start / 快速开始
python KaHIP.py --place "Karlsruhe, Germany" --version version_1
python optimize_weights.py --city Berlin
