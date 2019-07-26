---
ms.openlocfilehash: f1c11fd086a91db6dc0d0629549166bbba547dee
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67226510"
---
## <a name="mapping-functions-for-dynamics-365-customer-engagement-plan"></a>Dynamics 365 Customer Engagement Plan 的地图功能 
 现场服务和 Project Service Automation 具有依赖于位置的关键功能。 例如，服务帐户的位置（定义服务或任务发生的位置）或资源的开始/结束位置（执行服务或任务的人员）。  为了让系统在地图上显示这些位置或计算点之间的距离，有必要使用地图服务（在本例中为必应地图）。  
  
 以下是必应地图服务的工作流：  
  
|来自 Dynamics 365|必应地图返回|纪录|  
|-----------------------|-----------------------|----------|  
|地址（帐户或资源）|地址的经度和纬度（位置）|这被称为地址的“地理编码”。|  
|一组位置（纬度/经度）|位置之间的距离|可用于查找资源的最佳路径或计算行程时间。|  
|一组位置（纬度/经度）|地图上以别针标明位置的地图视图|用于查看地图视图中的帐户和资源。|  
  
> [!NOTE]
>  除了上面引用的数据之外，没有其他数据发送到必应地图服务。
