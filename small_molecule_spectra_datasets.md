# 小分子光谱数据集整理（IR / Raman / UV-Vis / NMR / MS）

更新日期：2026-04-21  
整理范围：优先收录**小分子**相关、可公开访问、适合检索/下载/建模的数据库或数据集。  
说明：这里的“数据集”同时包含公开数据库、谱图库和论文附带数据集。部分资源会跨多个谱学模态；为避免重复，我先给出多模态核心库，再按单一模态细分。

补充说明：上一版更偏向“公开数据库/实验资源/可直接检索的谱图库”，因此把 `QM9S`、`QMe14S`、`QM9NMR` 这类**量化计算 benchmark 家族**写轻了。严格来说，它们是小分子光谱机器学习里非常重要的一条主线，这一版已补入。

## 1. 先看结论：最值得优先整理的核心资源

如果你的目标是先搭一个“小分子多谱学数据底座”，建议优先从下面几类开始：

| 优先级 | 资源 | 适合场景 | 主要模态 |
| --- | --- | --- | --- |
| 高 | SDBS | 经典有机小分子基准库，跨 IR / Raman / NMR / MS | IR, Raman, 1H NMR, 13C NMR, EI-MS |
| 高 | NIST Chemistry WebBook | 小分子物性与光谱联合查询，IR/MS/UV-Vis 很实用 | IR, MS, UV-Vis |
| 高 | nmrshiftdb2 | 开放式有机小分子 NMR 数据与预测 | 1H NMR, 13C NMR, 其他核种 |
| 高 | MassBank | 开放、FAIR 的小分子 MS/MS 参考库 | MS/MS |
| 高 | MoNA | 聚合型超大规模小分子质谱资源 | MS/MS, GC-MS |
| 高 | HMDB | 代谢物方向最重要的小分子 NMR/MS 资源之一 | NMR, MS/MS, GC-MS |
| 高 | QM9S | 小分子计算光谱 benchmark，适合结构到谱图学习 | IR, Raman, UV-Vis |
| 高 | QMe14S | 比 QM9S 更广的元素和官能团覆盖 | IR, Raman, NMR |
| 高 | QM9NMR | 大规模小分子 NMR shielding benchmark | NMR |
| 中高 | ChEMBL IR/Raman 扩展集 | 适合机器学习的大规模计算光谱数据 | IR, Raman |
| 中高 | ORNL_AISD-Ex / GDB-9-Ex | 超大规模 UV-Vis 计算数据 | UV-Vis |
| 中 | GNPS Public Libraries | 天然产物、药物、小分子社区型 MS/MS 库 | MS/MS |
| 中 | API Raman dataset (2025) | 药物开发流程里的实验 Raman 小数据集 | Raman |
| 中 | UV/Vis comparative dataset (2019) | 文献抽取的实验 UV-Vis 峰位和消光系数 | UV-Vis |

## 2. 多模态核心数据库

### 2.1 SDBS

- 名称：Spectral Database for Organic Compounds (SDBS)
- 机构：AIST / NMIJ（日本）
- 小分子相关性：很高，核心对象就是有机小分子
- 模态：EI-MS、FT-IR、`1H NMR`、`13C NMR`、Laser Raman、ESR
- 规模：AIST 介绍页给出的历史统计为约 `34,600` 个化合物；约 `25,000` 个 MS、`54,100` 个 FT-IR、`15,900` 个 `1H NMR`、`14,200` 个 `13C NMR`、`3,500` 个 Raman 谱图
- 特点：
  - 经典、稳定、结构化程度高
  - 同一化合物下可同时看到多种谱图
  - 很适合作为小分子谱学“种子库”
- 局限：
  - 页面较老，批量化下载体验一般
  - 规模虽经典，但不属于最新超大规模资源
- 链接：
  - 主页：[SDBS Introduction](https://sdbs.db.aist.go.jp/Htmls/Introduction_eng.html)
  - 入口：[SDBS](https://sdbs.db.aist.go.jp/)

### 2.2 NIST Chemistry WebBook

- 名称：NIST Chemistry WebBook, SRD 69
- 机构：NIST
- 小分子相关性：很高，覆盖大量有机和小无机分子
- 模态：IR、MS、UV/Vis、vibrational/electronic levels 等
- 规模：NIST 首页显示约 `16,000+` IR、`33,000+` mass spectra、`1,600+` UV/Vis spectra
- 特点：
  - 小分子检索非常方便
  - 光谱与热化学、离子能等信息联动
  - 非常适合做化合物级别交叉核对
- 局限：
  - 不是面向机器学习批量下载设计的现代数据仓库
  - Raman / NMR 不在其核心覆盖范围内
- 链接：
  - 主页：[NIST Chemistry WebBook](https://webbook.nist.gov/)
  - 化学入口：[NIST Chemistry WebBook Chemistry](https://webbook.nist.gov/chemistry/)

### 2.3 HMDB

- 名称：Human Metabolome Database (HMDB)
- 机构：HMDB / Wishart Lab 等
- 小分子相关性：很高，尤其适合代谢物、内源性小分子、生物医学相关小分子
- 模态：MS/MS、`1H/13C NMR`、GC/MS
- 规模：HMDB 页面给出约 `5,700+` 化合物有实验 MS/MS，`1,300+` 化合物有实验 `1H/13C NMR`，`780+` 化合物有 GC/MS；另有约 `3,100` 个预测 NMR
- 特点：
  - 生物相关小分子覆盖好
  - 结构、代谢通路、光谱信息耦合紧密
  - 对代谢组学任务很重要
- 局限：
  - 不适合泛化成“所有有机小分子”数据库
  - 偏代谢物，不是通用化学空间的完整代表
- 链接：
  - 说明页：[HMDB databases](https://hmdb.ca/w/databases)

## 2.4 计算 benchmark 家族

这一组和上面的 SDBS / NIST / HMDB 不太一样。它们不一定是“实验参考数据库”，但在小分子光谱机器学习里非常关键，尤其适合做 benchmark、预训练和结构到谱图的监督学习。

### 2.4.1 QM9S

- 名称：QM9Spectra (QM9S)
- 类型：**计算数据集**
- 小分子相关性：很高，基于 QM9 的小有机分子
- 模态：IR、Raman、UV-Vis
- 规模：`133,885` 个分子
- 计算层级：公开说明里给出几何优化与性质计算基于 `B3LYP/def-TZVP`
- 特点：
  - 目前最常被引用的小分子计算光谱 benchmark 之一
  - 同时覆盖 IR / Raman / UV-Vis
  - 提供优化结构和谱图，适合图网络和多模态建模
- 局限：
  - 化学空间仍继承 QM9 的限制，元素主要集中在 `C/H/N/O/F`
  - 不包含更广的官能团和重元素化学空间
- 链接：
  - 数据集：[figshare QM9S](https://figshare.com/articles/dataset/QM9S_dataset/24235333)
  - 论文背景：[Nature Computational Science 2023](https://www.nature.com/articles/s43588-023-00550-y)

### 2.4.2 QMe14S

- 名称：QMe14S
- 类型：**计算数据集**
- 小分子相关性：很高
- 模态：IR、Raman、NMR
- 规模：`186,102` 个小有机分子
- 覆盖范围：`14` 个元素、`47` 类官能团
- 计算层级：`B3LYP/TZVP`
- 特点：
  - 可以看作 QM9S 的扩展和增强版
  - 元素和官能团覆盖显著更广
  - 文章明确说明其在光谱模拟任务上优于基于 QM9S 训练的模型
- 局限：
  - 仍是计算谱，不等同于实验谱
  - 当前社区普及度还在快速上升中，但已经非常值得纳入主清单
- 链接：
  - 论文：[JPC Letters 2025](https://pubs.acs.org/doi/10.1021/acs.jpclett.5c00839)

### 2.4.3 QM9NMR

- 名称：QM9NMR
- 类型：**计算数据集**
- 小分子相关性：高，覆盖 QM9 化学空间
- 模态：NMR shielding
- 规模：`130,831` 个 QM9 分子
- 内容：gas phase 与多种隐式溶剂条件下的原子级 shielding 参数，以及 raw output 文件
- 特点：
  - 对 NMR 机器学习是非常重要的标准资源
  - 原子级标签细，适合做 node-level 或 atom-wise 学习
  - 可与 QM9 结构空间直接联动
- 局限：
  - 更偏 shielding benchmark，而不是完整实验 NMR 谱图数据库
  - 化学空间同样受 QM9 限制
- 链接：
  - 主页：[QM9NMR](https://moldis-group.github.io/qm9nmr/)

## 3. IR 数据集

### 3.1 SDBS FT-IR

- 类型：实验谱图
- 适合：经典有机小分子检索、结构确认、教学与规则总结
- 备注：如果你准备做“多谱图联合建模”，SDBS 是很好的 IR 起点

### 3.2 NIST Chemistry WebBook IR

- 类型：实验谱图
- 适合：按化合物精确查谱、与物性联合验证
- 备注：对常见小分子覆盖尤其方便

### 3.3 ChEMBL IR/Raman 扩展集（2025）

- 名称：A Dataset of Raman and Infrared Spectra as an Extension to the ChEMBL
- 类型：**计算数据集**
- 小分子相关性：高，来源于 ChEMBL 中抽取的小分子
- 模态：IR + Raman
- 规模：论文说明当前已从 ChEMBL 抽取约 `220,000` 个分子，包含优化几何、振动频率、IR 强度、Raman 强度和能量
- 特点：
  - 规模大
  - 非常适合深度学习/预训练/多任务学习
  - IR 与 Raman 同源生成，便于做跨模态建模
- 局限：
  - 计算谱，不是实验谱
  - 与实验仪器噪声、基线、分辨率不完全一致
- 链接：
  - 论文：[Scientific Data 2025](https://www.nature.com/articles/s41597-025-05289-x)

### 3.4 QM9S

- 类型：计算数据集
- 小分子相关性：高
- 模态：IR
- 规模：`133,885` 个分子
- 特点：
  - 是 IR 机器学习里非常常见的 benchmark 源
  - 可和 Raman / UV-Vis 联合建模

### 3.5 QMe14S

- 类型：计算数据集
- 小分子相关性：高
- 模态：IR
- 规模：`186,102` 个分子
- 特点：
  - 比 QM9S 化学空间更宽
  - 更适合作为下一代结构到 IR 的训练集

## 4. Raman 数据集

### 4.1 SDBS Raman

- 类型：实验谱图
- 小分子相关性：高
- 规模：AIST 介绍页历史统计约 `3,500` 个 Raman 谱
- 特点：和 IR / NMR / MS 能做同分子联查
- 局限：规模不算大

### 4.2 API Raman dataset（2025）

- 名称：Open-source Raman spectra of chemical compounds for active pharmaceutical ingredient development
- 类型：**实验数据集**
- 小分子相关性：高，聚焦 API 开发中常见有机溶剂和试剂
- 模态：Raman
- 规模：`3,510` 个样本，覆盖 `32` 个化合物
- 特点：
  - 完全实验数据
  - 适合做预处理、分类、批间变化分析、方法学验证
  - CSV 形式，落地简单
- 局限：
  - 化学空间比较小
  - 更适合药化/工艺开发场景，不适合作为通用分子库
- 链接：
  - 论文：[Scientific Data 2025](https://www.nature.com/articles/s41597-025-04848-6)

### 4.3 ChEMBL IR/Raman 扩展集（2025）

- 类型：计算数据集
- 适合：大规模分子表示学习、从结构到 Raman/IR 的预测任务
- 备注：如果你希望先做“数量优先”的 Raman 建模，这个资源比实验 Raman 库更容易起量

### 4.4 QM9S

- 类型：计算数据集
- 小分子相关性：高
- 模态：Raman
- 规模：`133,885` 个分子
- 特点：是 Raman 谱图预测里常见的标准 benchmark 之一

### 4.5 QMe14S

- 类型：计算数据集
- 小分子相关性：高
- 模态：Raman
- 规模：`186,102` 个分子
- 特点：在化学空间覆盖上比 QM9S 更强

## 5. UV-Vis 数据集

### 5.1 NIST Chemistry WebBook UV/Vis

- 类型：实验谱图
- 小分子相关性：高
- 规模：NIST 首页给出约 `1,600+` UV/Vis spectra
- 特点：适合查常见小分子基准谱
- 局限：规模偏小，不适合单独作为大模型训练主库

### 5.2 Comparative dataset of experimental and computational attributes of UV/vis absorption spectra（2019）

- 类型：实验 + 计算混合数据
- 小分子相关性：高，以有机分子为主
- 规模：约 `18,309` 条实验记录；`8,488` 个唯一化合物；其中 `5,380` 个化合物带有实验与计算配对数据
- 内容：`λmax`、消光系数 `ε`，以及计算得到的相关光谱属性
- 特点：
  - 对做性质预测、峰位回归、文献抽取验证很有价值
  - 有实验-计算配对，适合误差校正
- 局限：
  - 更接近“光谱特征表”而不是完整连续光谱曲线
- 链接：
  - 论文：[Scientific Data 2019](https://www.nature.com/articles/s41597-019-0306-0)

### 5.3 GDB-9-Ex / ORNL_AISD-Ex（2023）

- 名称：Two excited-state datasets for quantum chemical UV-vis spectra of organic molecules
- 类型：**计算数据集**
- 小分子相关性：很高，都是有机小分子
- 规模：
  - `GDB-9-Ex`：`96,766` 个分子
  - `ORNL_AISD-Ex`：`10,502,904` 个分子
- 特点：
  - 目前公开 UV-Vis 计算数据里非常有代表性的超大规模资源
  - 很适合预训练、生成模型、谱图预测和化学空间覆盖研究
- 局限：
  - 计算谱，不是实验谱
  - 使用 TD-DFTB，精度与高等级量化方法/实验仍有差距
- 链接：
  - 论文：[Scientific Data 2023](https://www.nature.com/articles/s41597-023-02408-4)

### 5.4 QM9S

- 类型：计算数据集
- 小分子相关性：高
- 模态：UV-Vis
- 规模：`133,885` 个分子
- 特点：
  - 是结构到 UV-Vis 学习的紧凑 benchmark
  - 相比 ORNL_AISD-Ex，规模小很多，但更适合快速实验和方法比较
- 局限：化学空间明显窄于更大的有机数据库

## 6. NMR 数据集

### 6.1 nmrshiftdb2

- 名称：nmrshiftdb2
- 类型：开放数据库
- 小分子相关性：很高，明确面向有机结构和小分子 NMR
- 模态：`1H NMR`、`13C NMR`，以及其他核种
- 规模：当前页面显示约 `271,816` 个结构；测得谱图约 `70,027`；计算谱约 `396,583`
- 特点：
  - 开放、可搜索、可预测
  - 对结构-化学位移建模非常友好
  - 有 fully assigned spectra、raw data、peak lists
- 局限：
  - 数据质量依赖社区提交与审核流程
  - 不同化合物的实验条件异质性较强
- 链接：
  - 主页：[nmrshiftdb2](https://nmrshiftdb.nmr.uni-koeln.de/nmrshiftdb/)

### 6.2 SDBS NMR

- 类型：实验谱图
- 模态：`1H NMR`、`13C NMR`
- 规模：历史统计约 `15,900` 个 `1H NMR`、`14,200` 个 `13C NMR`
- 特点：
  - 经典、干净、适合核对
  - 和 IR/MS/Raman 在同库内联动
- 局限：总体规模小于 nmrshiftdb2

### 6.3 HMDB NMR

- 类型：实验 + 预测
- 小分子相关性：高，但主要是代谢物
- 模态：`1H`、`13C`、部分 2D NMR 峰表
- 规模：HMDB 页面说明约 `1,300+` 个实验 `1H/13C NMR`，约 `3,100` 个预测 NMR
- 特点：
  - 代谢物方向非常实用
  - 结构、生物背景和光谱可一起用
- 局限：不覆盖通用小分子化学空间

### 6.4 BMRB 小分子板块

- 名称：BMRB metabolomics / small molecules
- 类型：开放数据库
- 小分子相关性：中高，偏生物相关小分子、代谢物、肽类小分子
- 模态：1D/2D NMR peak lists、raw spectra、FIDs 等
- 规模：BMRB 代谢物说明页提到其 metabolomics 数据库包含 `1,200+` 个分子级别的 1D/2D 峰表、原始谱和 FID
- 特点：
  - 原始 NMR 数据价值高
  - 对谱峰指认和方法学研究特别有帮助
- 局限：
  - 有一部分条目更偏生物相关小分子而非一般有机化合物
- 链接：
  - 小分子入口：[BMRB small molecules](https://bmrb.io/data_library/small_molecules.shtml)
  - 代谢物说明：[BMRB metabolomics standards](https://bmrb.io/metabolomics/metabolomics_standards.php)

### 6.5 QM9NMR

- 类型：计算数据集
- 小分子相关性：高
- 模态：NMR shielding
- 规模：`130,831` 个分子
- 特点：
  - 大规模、原子级别标签
  - 很适合做 NMR 机器学习 benchmark
  - 含 gas phase 和多种溶剂条件
- 局限：更偏 shielding，不是传统实验谱图库

### 6.6 QMe14S

- 类型：计算数据集
- 小分子相关性：高
- 模态：NMR
- 规模：`186,102` 个分子
- 特点：
  - 把 NMR 纳入了更宽化学空间的多谱学 benchmark
  - 对多模态联合学习很有价值
- 局限：当前最核心价值仍然是 benchmark 与模拟学习，而非实验参考

## 7. MS 数据集

### 7.1 MassBank

- 名称：MassBank
- 类型：开放、FAIR 的参考谱数据库
- 小分子相关性：很高，重点就是代谢物、脂质、药物、农药、污染物等小分子
- 模态：MS, MS/MS
- 规模：2025 年 NAR 文章给出约 `119,845` 条谱图，覆盖 `18,529` 个化合物，来自 `53` 个贡献方
- 特点：
  - 开放标准好
  - 元数据详细
  - 适合做高质量参考库
- 局限：
  - 比 MoNA 这类聚合库小
  - 需要面对多来源仪器条件差异
- 链接：
  - 官方站：[MassBank](https://massbank.eu/MassBank/)
  - 资源介绍：[NAR 2025 article](https://academic.oup.com/nar/advance-article-abstract/doi/10.1093/nar/gkaf1193/8321203)

### 7.2 MoNA

- 名称：MassBank of North America (MoNA)
- 类型：聚合型数据库
- 小分子相关性：很高
- 模态：MS/MS、GC-MS 等
- 规模：MANA 数据库页写明，MoNA 提供 `651K+` compounds 的免费 MS/MS 和 GC-MS 光谱，总计 `2M+` spectra
- 特点：
  - 体量非常大
  - 聚合了 MassBank.jp、MassBank.eu、GNPS、HMDB 等多源数据
  - 很适合作为大规模检索和训练集来源
- 局限：
  - 聚合库去重、标准化、来源一致性需要自己再做
  - 部分记录质量差异较大
- 链接：
  - 主页：[MoNA](https://mona.fiehnlab.ucdavis.edu/)
  - 说明参考：[MANA databases](https://www.metabolomicsna.org/mana-databases)

### 7.3 GNPS Public Spectral Libraries

- 名称：GNPS Public Spectral Libraries
- 类型：社区型公共谱图库
- 小分子相关性：高，尤其天然产物、药物、小分子参考标准
- 模态：MS/MS
- 特点：
  - 社区活跃，天然产物生态非常强
  - 可直接和分子网络、库检索工作流打通
  - 页面中可见多个小分子子库，如 FDA、小分子库、植物化学物、农药等
- 局限：
  - 更像“子库集合”
  - 标准化程度不如单一中心化数据库
- 链接：
  - 库入口：[GNPS Spectral Libraries](https://gnps.ucsd.edu/ProteoSAFe/libraries.jsp)

### 7.4 HMDB MS/MS

- 类型：实验 MS/MS + 代谢物数据库
- 小分子相关性：很高，特别适合生物代谢物识别
- 规模：HMDB 页面给出 `5,700+` 个化合物有实验 MS/MS
- 特点：
  - 代谢组学任务极其常用
  - 化合物上下文信息丰富
- 局限：偏生物代谢物空间

### 7.5 NIST Chemistry WebBook MS

- 类型：实验质谱
- 小分子相关性：高
- 规模：NIST 首页给出 `33,000+` mass spectra
- 特点：
  - 基准性强
  - 对经典有机小分子非常实用
- 局限：与现代 LC-MS/MS 社区库相比，工作流联动性稍弱

### 7.6 SDBS EI-MS

- 类型：实验 EI-MS
- 小分子相关性：高
- 规模：历史统计约 `25,000` 个 MS
- 特点：可与同一化合物的 NMR / IR / Raman 联查

## 8. 按任务选择数据集

| 任务 | 最推荐资源 |
| --- | --- |
| 小分子多谱学联合整理 | SDBS + NIST WebBook + HMDB |
| 做 NMR 结构-位移预测 | nmrshiftdb2 + SDBS |
| 做 MS/MS 检索或分子识别 | MassBank + MoNA + GNPS + HMDB |
| 做 Raman/IR 深度学习 | ChEMBL IR/Raman 扩展集 + SDBS |
| 做小分子多谱学 benchmark | QM9S + QMe14S |
| 做实验 Raman 小样本方法学 | API Raman dataset |
| 做 UV-Vis 大规模建模 | ORNL_AISD-Ex / GDB-9-Ex |
| 做 NMR 计算 benchmark | QM9NMR + QMe14S + nmrshiftdb2 |
| 做 UV-Vis 实验峰位任务 | UV/Vis comparative dataset + NIST |
| 做代谢物方向多模态任务 | HMDB + BMRB + MassBank |

## 9. 建议的后续整理方式

如果你下一步要把它真正变成“可用数据资产”，建议按下面字段继续标准化：

| 字段 | 建议内容 |
| --- | --- |
| dataset_name | 数据集名称 |
| modality | IR / Raman / UV-Vis / 1H NMR / 13C NMR / MS / MS2 |
| molecule_scope | organic small molecules / metabolites / drugs / natural products |
| data_type | experimental / computed / mixed |
| access | web / download / API / bulk |
| record_unit | compound-level / spectrum-level / peak-list-level |
| scale | compounds / spectra / records |
| identifiers | SMILES / InChI / InChIKey / CAS / HMDB ID / accession |
| metadata | solvent / instrument / ion mode / collision energy / resolution / temperature |
| license | open / restricted / mixed |
| raw_or_processed | raw / peak list / processed spectrum |
| notes | 质量、局限、是否适合 ML |

## 10. 我建议你先落地的“小分子第一版清单”

如果目标是先做一版真正能用的主表，我建议第一版只收这 10 个：

1. SDBS
2. NIST Chemistry WebBook
3. nmrshiftdb2
4. HMDB
5. BMRB small molecules / metabolomics
6. QM9S
7. QMe14S
8. QM9NMR
9. MassBank
10. MoNA
11. GNPS Public Spectral Libraries
12. ChEMBL IR/Raman 扩展集
13. ORNL_AISD-Ex / GDB-9-Ex

这样可以先把“小分子实验谱 + 计算谱 + 多模态 + benchmark 家族 + 大规模 MS”五个方向都覆盖住。

## 11. 参考链接

1. SDBS: [https://sdbs.db.aist.go.jp/Htmls/Introduction_eng.html](https://sdbs.db.aist.go.jp/Htmls/Introduction_eng.html)
2. SDBS 入口: [https://sdbs.db.aist.go.jp/](https://sdbs.db.aist.go.jp/)
3. NIST Chemistry WebBook: [https://webbook.nist.gov/](https://webbook.nist.gov/)
4. NIST Chemistry WebBook Chemistry: [https://webbook.nist.gov/chemistry/](https://webbook.nist.gov/chemistry/)
5. nmrshiftdb2: [https://nmrshiftdb.nmr.uni-koeln.de/nmrshiftdb/](https://nmrshiftdb.nmr.uni-koeln.de/nmrshiftdb/)
6. HMDB databases: [https://hmdb.ca/w/databases](https://hmdb.ca/w/databases)
7. BMRB small molecules: [https://bmrb.io/data_library/small_molecules.shtml](https://bmrb.io/data_library/small_molecules.shtml)
8. BMRB metabolomics standards: [https://bmrb.io/metabolomics/metabolomics_standards.php](https://bmrb.io/metabolomics/metabolomics_standards.php)
9. MassBank: [https://massbank.eu/MassBank/](https://massbank.eu/MassBank/)
10. MassBank NAR 2025: [https://academic.oup.com/nar/advance-article-abstract/doi/10.1093/nar/gkaf1193/8321203](https://academic.oup.com/nar/advance-article-abstract/doi/10.1093/nar/gkaf1193/8321203)
11. MoNA: [https://mona.fiehnlab.ucdavis.edu/](https://mona.fiehnlab.ucdavis.edu/)
12. MANA databases: [https://www.metabolomicsna.org/mana-databases](https://www.metabolomicsna.org/mana-databases)
13. GNPS Libraries: [https://gnps.ucsd.edu/ProteoSAFe/libraries.jsp](https://gnps.ucsd.edu/ProteoSAFe/libraries.jsp)
14. ChEMBL IR/Raman dataset: [https://www.nature.com/articles/s41597-025-05289-x](https://www.nature.com/articles/s41597-025-05289-x)
15. QM9S dataset: [https://figshare.com/articles/dataset/QM9S_dataset/24235333](https://figshare.com/articles/dataset/QM9S_dataset/24235333)
16. QM9S background paper: [https://www.nature.com/articles/s43588-023-00550-y](https://www.nature.com/articles/s43588-023-00550-y)
17. QMe14S paper: [https://pubs.acs.org/doi/10.1021/acs.jpclett.5c00839](https://pubs.acs.org/doi/10.1021/acs.jpclett.5c00839)
18. QM9NMR: [https://moldis-group.github.io/qm9nmr/](https://moldis-group.github.io/qm9nmr/)
19. API Raman dataset: [https://www.nature.com/articles/s41597-025-04848-6](https://www.nature.com/articles/s41597-025-04848-6)
20. UV/Vis comparative dataset: [https://www.nature.com/articles/s41597-019-0306-0](https://www.nature.com/articles/s41597-019-0306-0)
21. UV-Vis excited-state datasets: [https://www.nature.com/articles/s41597-023-02408-4](https://www.nature.com/articles/s41597-023-02408-4)

## 12. 备注

- 这里优先保留了**公开可访问**且**小分子相关性高**的资源。
- 商业资源如 Reaxys、Wiley KnowItAll、SpectraBase 这次没有作为主清单展开。
- 部分数据库规模会持续变化，以上数字以我在 `2026-04-21` 整理时检索到的官方页面或论文描述为准。
