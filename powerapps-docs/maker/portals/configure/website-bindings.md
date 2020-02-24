---
title: 在门户中创建和管理网站绑定 | MicrosoftDocs
description: 了解如何在门户中创建和管理网站绑定。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/12/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 294e1040f79ed5a25521ae2a861ccd30cdbfaf3e
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977530"
---
# <a name="create-and-manage-website-bindings"></a>创建和管理网站绑定

在门户中，选择网站的默认方法，是通过匹配在该特定门户的 web.config 文件中定义的网站名称来查找网站。 网站绑定提供了在加载门户或选择适当网站的请求路径时使用主机名选择网站的替代方法。 这无需修改每个特定网站版本的单独 web.config 文件。 这将简化各个部署、阶段和生产环境中门户的部署。 此外，这还允许通用门户代码库运行多个网站。

## <a name="manage-website-bindings"></a>管理网站绑定

可在 Power Apps 门户中创建、编辑和删除网站绑定。 

1. 打开[“门户管理”应用](configure-portal.md)。

2. 转到**门户** > **网站绑定**。

3. 若要创建新的网站绑定，请选择**新建**。

4. 若要编辑现有的网站绑定，请选择网站绑定的名称。

5. 在这些字段中输入相应值。

6. 选择**保存并关闭**。

### <a name="website-binding-attributes"></a>网站绑定属性

下面是所有绑定通用的属性。

|​名称|说明|
|-----|----------|
|​名称| 查看记录时识别网站绑定的标题。|
|网站|应由门户选择的[网站](websites.md) 。|
|发布日期|确定允许网站何时可以选择的日期。|
|到期日期|确定允许网站何时停止选择的日期。|
|||

#### <a name="application-settings"></a>应用程序设置

为应用程序级绑定指定这些属性的值。 此绑定映射基于 IIS 网站或应用程序。

|​名称|说明|
|-----|----------|
|网站名称|IIS 网站的名称。|
|虚拟路径|网站下的 IIS 应用程序的名称。|
|||

对于 Azure 网站和云服务，网站名称和虚拟路径值由 **ServiceDefinition.csdef** 文件的 <Site> 和 <VirtualApplication> 节点确定。

```
<ServiceDefinition>
  <WebRole>
    <Sites>
      <Site name=Dynamics Portals>
        <VirtualApplication name=customer-portal/>
```

### <a name="see-also"></a>另请参阅
[创建和管理网站](websites.md)
