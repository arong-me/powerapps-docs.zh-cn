---
title: 在门户中将地理位置添加到托管窗体 |MicrosoftDocs
description: 有关将地理位置添加到托管窗体的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a3c583658a5593d8e6c5f6c139a5c967e9581626
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553546"
---
# <a name="add-geolocation"></a>添加地理位置

*地理*位置是对象的实际地理位置的标识。 地理位置与定位系统的使用紧密相关，但重点在于确定有意义的位置（例如街道地址）而不只是一组地理坐标。 "地理位置" 一词也可以表示特定位置的纬度和经度坐标。

可以将托管窗体配置为显示地图控件，以将现有位置显示为地图上的 pin，或提供用户指定位置的功能。

![表单中的位置数据。](../media/location-data-form.png "表单中的位置数据")

如果 "窗体" 或 "地址行" 字段是可编辑的并且此字段为空，则在加载页面时，将提示用户是否想要共享其位置。 如果他们选择共享其位置，则将用当前检测到的位置更新地图。 用户可以通过拖动来优化 pin 的位置。 如果用户选择不共享其位置，则他们可以在提供的字段中手动指定位置，并将查询映射服务以查找位置、更新纬度和经度，并相应地重定位地图上的 pin。

## <a name="add-geolocation"></a>添加地理位置
若要将地理位置功能添加到托管窗体，必须完成以下任务。

### <a name="form-customization"></a>表单自定义
使用窗体设计器编辑实体窗体，并进行以下修改：

1. 创建一个新的节，并提供适当的标签，例如**Map**。 此部分将包含映射。
2. 将节的名称设置为 " **\_映射" 部分**或以 " _\_映射_" 部分结尾的名称，例如**contoso\_节\_map**。 此名称很重要，因为窗体引擎查找具有此名称的部分来确定何时呈现地图。 
3. 添加新的或现有的字段以存储格式化地址，并将其添加到在上一步中创建的**地图**部分。
4. 创建一个新的节，并提供相应的标签，例如 "**位置**"。 此部分将包含所选位置的地址字段。
5. 将所需的地址字段添加到在上一步中创建的**Location**部分： 
    - 地址行
    - 梵蒂冈
    - 指
    - 省/市/自治区
    - 国家/地区
    - 邮政编码
    - 纬度
    - 精度

生成的窗体应类似于以下内容。 您可以为这些字段选择不同的显示名称。 你还可以选择按你喜欢的方式对这些部分进行布局。

![自定义地理位置窗体。](../media/custom-geolocation-form.png "自定义地理位置窗体")

### <a name="site-settings"></a>站点设置
托管窗体上带有地图功能的地理位置需要配置设置才能完成映射服务 REST 终结点的请求。 以下站点设置用于配置位置服务。

|名称|Value|
|---|---|
|Bingmaps/凭据|用于对 Bing 地图 API 请求进行身份验证的唯一键。 请访问[www.bingmapsportal.com](https://www.bingmapsportal.com)创建 Bing 地图帐户并获取密钥。 必填。|
|Bingmaps/restURL|必应地图 REST API 的 URL。 可选。 如果未指定值，则使用默认 https://dev.virtualearth.net/REST/v1/Locations 。|
| |

### <a name="field-configurations"></a>字段配置
Map 控件需要其他配置来告诉它各种位置字段的 Id 是什么，因此它可以为它们赋值或从中检索值。 此配置取决于托管窗体的类型。

- 有关实体窗体，请参阅[实体窗体的地理位置配置](entity-forms.md#geolocation-configuration-for-entity-forms)。

- 对于 web 窗体，请参阅[web 窗体的地理位置配置](web-form-properties.md#geolocation-configuration-for-web-form)。
