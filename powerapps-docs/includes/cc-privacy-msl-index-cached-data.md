---
ms.openlocfilehash: 13a55df026f9114506492f62b236ee8e3f1889cc
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "63319261"
---
Microsoft Social Engagement 将客户搜索配置和数据特选存储在租户分离的数据库（客户数据）中。 然后，客户数据在服务器端缓存到内部应用程序中，以允许常见的检索索引，其唯一目的是最大化解决方案性能。   
 对索引缓存的数据（客户数据）的访问仅由内部应用程序处理，并且不允许用户在内部应用程序中以交互方式访问或修改索引缓存的数据。 订阅许可协议终止后，根据我们的数据保留策略，客户索引缓存的数据将在 180 天后删除。