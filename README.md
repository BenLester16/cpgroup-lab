# cpgroup-lab
为“土壤生物膜与环境健康”课题组量身打造一站式科研平台，完成网站建设、生物信息学数据分析与文献复现。


RNAseqSimPkg: RNA-seq Simulation, Analysis & Deployment

本项目“RNAseqSimPkg: RNA-seq Simulation, Analysis & Deployment”由高春辉老师课堂（RNA-seq课程）启发，于2025年完成，旨在提供一个集数据模拟、差异表达分析、可视化与富集分析，以及Shiny交互与Plumber API部署于一体的完整R包解决方案。核心思路是通过可重复的模拟流程生成复杂RNA-seq数据，利用DESeq2进行差异分析，并通过Shiny与Plumber实现在线交互与REST服务，极大提高分析的可重现性与易用性。

一、基本信息提取
项目标题：
RNAseqSimPkg: RNA-seq Simulation, Analysis & Deployment

作者与年份：
1.作者：李斌，欧阳皓楠，陈扬，孙孟，刘琪
2.教学来源：高春辉老师“RNA-seq”课堂
3.完成时间：2025年4月

期刊或依托：
1.课程依托：高春辉老师课堂RNA-seq
2.项目类型：R包开发 + Shiny应用 + Plumber API + Docker化 + CI/CD

二、研究背景与目的
·背景：
RNA-seq技术已经成为基因表达研究的主流手段，但其结果往往受实验设计、批次效应、数据处理流程等多种因素影响，导致可重复性不足。尤其在教学与方法演示中，缺少一个从模拟到部署的端到端可复现范例。

·研究问题与假设
1.问题：如何构建一个既能模拟多因素（时间、实验组、批次、复制）RNA-seq数据，又能完成标准差异表达分析、可视化及富集分析的统一框架？
2.假设：通过引入批次效应与多种对比组的模拟，可在教学和研究中更直观地展示RNA-seq分析全流程，并利用Shiny与Plumber实现交互与服务化部署。

·研究目的与动机
1.模拟复杂RNA-seq数据：包括多时间点、多组别和批次效应。
2.运行DESeq2差异表达分析：封装构建DSSeqDataset与results调用。
3.可视化：火山图、PCA及富集分析（GO/KEGG）。
4.交互与部署：提供Shiny前端、Plumber API、Docker镜像与GitHub Actions CI/CD模板，支持教学与生产环境使用。

三、项目内容
·方法与流程
1.数据模拟：
simulate_samples() 生成样本元信息；
generate_counts() 基于负二项分布引入批次、组内变化与大小因子。
2.差异表达分析：
build_deseq_objects() 构建含批次校正的 DESeqDataSet；
get_DEGs() 提取并过滤显著基因。
3.可视化模块：
plot_volcano()、plot_PCA()；
enrich_analysis() 进行GO/KEGG富集并绘制点图。
4.交互与服务：
Shiny App：文件上传、参数选择、图形展示与下载；
Plumber API：/simulate 接口直接返回模拟元信息；
Dockerization：基于 Rocker 镜像，打包Shiny与Plumber服务；
CI/CD：GitHub Actions 测试、构建、Docker镜像发布。

四、数据来源与分析框架
1.源数据：完全模拟产生，无外部依赖；
2.分析框架：R/Bioconductor 生态（DESeq2, clusterProfiler, enrichplot）；
3.优势：端到端可重现，教学示例与生产部署一体化；
4.局限性：模拟数据可能无法涵盖所有真实样本异质性；批次模型简单，仅演示基础校正。

五、讨论与结论
·结果讨论：
1.模拟数据在多种对比下均产生合理的差异基因排序与可视化；
2.PCA图有效展示批次与时间的主要变异；
3.富集分析模块在上调基因集中识别相关通路，验证了模拟设置可产生显著生物学信号。

·研究领域影响
1.教学意义：为RNA-seq方法教学提供了完整流水线示例；
2.实践意义：可快速搭建私有化部署的差异分析服务，支持生物信息平台集成。
·结论与未来方向
1.结论：本项目实现了RNA-seq模拟到部署的全链条可重复流程；
2.局限：需要扩展至更多物种注释、引入真实数据校准；
3.未来：加入单细胞RNA-seq模拟、更多富集方法、多种机器学习模型集成。

·创新点与贡献
1.端到端可重现：从模拟到差异分析、可视化再到在线部署一体化。
2.教学与生产双兼容：既适用于课堂演示，也可用于实际生物信息平台。
3.模块化设计：每一步（模拟、分析、可视化、服务化）皆可单独调用或替换。
4.云原生支持：Docker、CI/CD、Kubernetes 清晰模板，降低部署门槛。

六、个人评价与启示
·评价
1.质量：代码注释完善，步骤清晰，组件解耦良好；
2.方法：使用成熟Bioconductor包，可靠度高；
3.可信度：模拟结果与实际流程高度一致，测试覆盖全面。

·不足与争议
1.模拟模型：目前仅考虑单一批次效应与简单Fold-change，缺少其他噪声模型；
2.扩展性：尚未支持多物种自动注释与下游机器学习。

·建议与启示
1.引入真实数据校准：可将模拟参数与真实RNA-seq数据拟合；
2.增补单细胞模块：扩展到scRNA-seq分析流程；
3.增强分析丰富性：添加时序分析、共表达网络构建等功能。

附：
项目开源地址
GitHub: [https://github.com/username/RNAseqSimPkg](https://github.com/BenLester16/cpgroup-lab)
Docker Hub: https://hub.docker.com/r/username/rnaseqsimpkg
