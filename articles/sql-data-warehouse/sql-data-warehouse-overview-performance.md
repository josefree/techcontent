<properties
   pageTitle="性能和缩放性概述 | Azure"
   description="介绍 SQL 数据仓库的性能与缩放性功能。"
   services="sql-data-warehouse"
   documentationCenter="NA"
   authors="TwoUnder"
   manager="barbkess"
   editor=""/>

<tags
   ms.service="sql-data-warehouse"
   ms.date="03/03/2016"
   wacn.date="04/11/2016"/>

# 性能和缩放性概述
如果将数据仓库放在云中，你就不再需要应付低级硬件问题。此外，你再也不需要为了获得优异的数据仓库性能，而研究处理器类型、需要的内存容量或存储空间类型。相反，SQL 数据仓库会问你：你想要多快的数据处理速度？

SQL 数据仓库是基于云的分布式数据库平台，其设计目的是在对于用于解析查询的资源拥有完整控制权的范围内提供优异的性能。你只需调整分配给数据仓库的数据仓库单位数量，就能在几秒内弹性缩放仓库资源的大小。SQL 数据仓库是一个分布式的向外缩放平台，可让数据仓库以有效且有利的方式处理大量数据卷，同时让你完全控制解决方案的成本。

我们的 SQL 数据仓库目标是：- 可预测的性能与 PB 量级数据的线性缩放性 - 以服务级别协议 (SLA) 作为后盾的所有数据仓库操作都有极佳的稳定性 - 针对关系与非关系数据快速完成从加载数据到提供数据见解的过程


## 数据保护
SQL 数据仓库使用异地冗余 Blob，将所有数据存储在 Azure 存储空间中。将在本地 Azure 区域维护数据的三个同步副本，确保在发生局部故障（例如存储驱动器故障）时能够保证提供透明的数据保护。此外，还会在远程 Azure 区域维护三个异步副本，以确保在发生区域性故障时能够保证提供数据保护（灾难恢复）。将局部和远程区域配对可以保持可接受的同步延迟（例如在中国东部和北部）。

## 数据库还原
SQL 数据仓库使用 Azure 存储空间快照，每 4 小时备份所有数据一次。这些快照免费保留 7 天。这样，在生成最新快照前的 7 天内，最多就有 42 个时间点可用于还原数据。可以使用 PowerShell 或 REST API 从快照还原数据。快照以异步复制到远程 Azure 区域，以便在发生区域性故障时提高恢复能力（灾难恢复）。

## 可靠性
SQL 数据仓库是包含多个组件的分布式系统，其组件数量随着数据仓库单位 (DWU) 的增加而增加。SQL 数据仓库将自动检测并缓解计算故障，但是，操作（例如数据加载或查询）可能会因为单个计算故障而失败。

根据所收集的遥测数据，SQL 数据仓库对典型的数据仓库工作负荷的可靠性预计为 98%。这意味着，在 100 次查询中，平均有 2 次查询可能因系统错误而失败。请注意，查询失败的可能性随着其执行时间而增加（例如，持续 2 小时以上的查询，其失败的可能性远高于持续 10 分钟以下的查询）。

## 性能和缩放性
SQL 数据仓库引入了数据仓库单位 (DWU) 作为许多节点的聚合计算资源（CPU、内存、存储 I/O）的抽象概念。增加 DWU 数量还会增加 SQL 数据仓库实例的聚合计算资源。SQL 数据仓库将操作（例如数据加载或查询）分布到实例中的所有计算基础结构，随着系统相应增加或减少而提高或降低加载与查询的性能。

任一数据仓库都有 2 个基本性能指标：- **加载速率**：每秒可载入数据仓库的记录数量。我们会专门度量可通过 PolyBase 从 Azure Blob 存储导入包含群集列存储索引的表中的记录数量。- **扫描速率**：每秒可从数据仓库依序检索的记录数量。此指标专门度量查询从包含群集列存储索引的表中返回的记录数量。

## 关键性能概念

请参阅以下文章，以帮助了解其他一些关键的性能与缩放性概念：

- [性能和缩放性][]
- [并发模型][]
- [设计表][]
- [为表选择哈希分布键][]
- [用于改善性能的统计信息][]

## 后续步骤
请参阅[开发概述][]一文，以获取有关构建 SQL 数据仓库解决方案的一些指导。

<!--Image references-->

<!--Article references-->

[性能和缩放性]: /documentation/articles/sql-data-warehouse-performance-scale/
[并发模型]: /documentation/articles/sql-data-warehouse-develop-concurrency/
[设计表]: /documentation/articles/sql-data-warehouse-develop-table-design/
[为表选择哈希分布键]: /documentation/articles/sql-data-warehouse-develop-hash-distribution-key/
[用于改善性能的统计信息]: /documentation/articles/sql-data-warehouse-develop-statistics/
[开发概述]: /documentation/articles/sql-data-warehouse-overview-develop/

<!--MSDN references-->

<!--Other web references-->

<!---HONumber=Mooncake_0307_2016-->