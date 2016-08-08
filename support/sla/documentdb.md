<properties
	pageTitle=""
    description=""
    services=""
    documentationCenter=""
    authors=""
    manager=""
    editor=""
    tags=""/>

<tags ms.service="legal" ms.date="08/2016" wacn.date="08/2016" wacn.lang="cn"/>

> [AZURE.LANGUAGE]
- [中文](/support/sla/documentdb/)
- [English](/support/sla/documentdb-en/)
# DocumentDB 的服务级别协议

我们保证在不少于 99.99% 的时间内成功地处理针对 DocumentDB 资源执行操作的请求。

##SLA 详细信息 

某个帐单月份的“**平均错误率**”是指此帐单月份中每个小时的错误率总和除以此帐单月份内的总小时数。

“**数据库帐户**”是指包含一个或多个数据库的 DocumentDB 帐户。

“**错误率**”的计算方式如下：一个指定 Azure 订购中的所有资源在指定的一小时时间间隔内产生的失败请求总数除以总请求数。如果在指定的一小时时间间隔内的总请求数为零，则该时间间隔的错误率为 0%。

“**排除的请求数**”是指总请求数中导致 HTTP 4xx 状态代码（HTTP 408 状态代码除外）的请求数。

“**失败的请求数**”是指在帐户创建和删除后的 5 分钟内、性能/优惠水平更新后的 3 分钟内或者进行所有其他操作后的 5 秒钟内，在总请求数中返回错误代码或 HTTP 408 状态代码或未能返回成功代码的所有请求数。

“**资源**”是指与数据库帐户关联的一组 URI 可寻址实体。

“**总请求数**”是指在一个帐单月份中指定 Azure 订阅中的一小时时间间隔内尝试针对资源发出的执行操作的所有请求数（排除的请求数除外）。

DocumentDB 服务的“**每月正常服务时间百分比**”通过以下方式计算：100% 减去指定 Azure 订购在一个帐单月份中的平均错误率。一个帐单月份的“平均错误率”为该帐单月份中每个小时的错误率总和除以帐单月份内的总小时数。每月正常服务时间百分比计算公式如下所示：

	每月正常服务时间百分比 = 100% - 平均错误率

服务费抵扣：

每月正常服务时间百分比	| 服务费抵扣  
---|---  
< 99.99% | 10%  
< 99% |	25%
