---
title: 将地理位置添加到门户中的托管窗体 | MicrosoftDocs
description: 关于将地理位置添加到托管窗体的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 44619bfdb6d09221a6a23164a9627b4e06ebb0d7
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979422"
---
# <a name="add-geolocation"></a>添加地理位置

*地理位置*是对象的实际地理位置的标识。 地理位置类似于使用定位系统，但更加注重确定一个有意义的位置（例如街道地址），而不仅仅是一组地理坐标来与定位系统进行区分。 地理位置一词也可以指一个特定地点的经纬度坐标。

托管窗体可以进行配置以显示一个地图控件，用于显示地图上的图钉的现有位置或使用户可以指定一个位置。

![窗体中的位置数据。](../media/location-data-form.png "窗体中的位置数据")

如果窗体或地址行字段是可编辑的，且该字段为空，则在加载页面时，它会提示用户并询问用户是否希望共享位置。 如果他们选择共享位置，则地图将使用其当前发现的位置进行更新。 用户可通过拖动调整图钉的位置。 如果用户选择不共享位置，用户可以在提供的字段中手动指定位置，并查询映射服务以查找位置，更新经纬度并相应地重新定位地图上的图钉。

## <a name="add-geolocation"></a>添加地理位置
若要在托管窗体中添加地理位置功能，必须完成以下任务。

### <a name="form-customization"></a>窗体自定义
使用窗体设计器编辑实体窗体并进行以下修改：

1. 创建新节并提供相应的标签，例如**地图**。 本节将包含地图。
2. 将节名称设置为 **section\_map** 或使用 _section\_map_ 结尾的名称，例如，**contoso\_section\_map**。 此名称很重要，因为窗体引擎使用此名称查找节以确定何时呈现地图。 
3. 添加将要存储格式化地址的新字段或现有字段，并将其添加到在上一步中创建的**地图**部分。
4. 创建新节并提供相应的标签，例如**位置**。 本节将包含所选位置的地址字段。
5. 将所需的地址字段添加到在上一步中创建的**位置**部分： 
    - 地址行
    - 市/县
    - 县
    - 省/直辖市/自治区
    - 国家/地区
    - 邮政编码
    - 纬度
    - 经度

生成的窗体应与以下类似。 您可以为这些字段选择不同的显示名称。 您还可以为这些节选择您喜爱的任何布局。

![自定义地理位置窗体。](../media/custom-geolocation-form.png "自定义地理位置窗体")

### <a name="site-settings"></a>站点设置
使用托管窗体地图功能的地理位置需要配置设置才能使用映射服务 REST 端点完成请求。 以下站点设置用于配置位置服务。

|姓名|值|
|---|---|
|Bingmaps/凭据|用于对 Bing 地图 API 请求进行身份验证的唯一密钥。 访问 [www.bingmapsportal.com](https://www.bingmapsportal.com) 以创建 Bing 地图帐户和获取密钥。 必需。|
|Bingmaps/restURL|Bing 地图 REST API 的 URL。 （可选） 如果未指定值，则使用默认值 https://dev.virtualearth.net/REST/v1/Locations。|
| |

### <a name="field-configurations"></a>字段配置
地图控件需要额外配置才能告知它不同位置字段的 ID，从而可以向它们分派值或检索来自它们的值。 配置取决于托管窗体的类型。

- 有关实体窗体，请参阅[实体窗体的地理位置配置](entity-forms.md#geolocation-configuration-for-entity-forms)。

- 有关 Web 窗体，请参阅 [Web 窗体的地理位置配置](web-form-properties.md#geolocation-configuration-for-web-form)。
