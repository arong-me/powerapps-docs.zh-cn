---
title: 创建 PowerBI 报表 | Microsoft Docs
description: 使用 Common Data Service for Apps 连接器从 PowerBI Desktop 连接到数据。
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: clwesene
ms.openlocfilehash: d8323eb103751a1be78aeea0093b9d6651ddc3e2
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34445836"
---
# <a name="create-a-power-bi-report"></a>创建 Power BI 报表
通过 Common Data Service for Apps，可使用 Power BI Desktop 直接连接到数据，然后创建报表并发布到 Power BI。 在 Power BI 中，可在仪表板中使用报表，与其他用户共享报表，还可在 Power BI 移动应用上跨平台访问报表。

![Power BI Desktop](./media/data-platform-cds-powerbi-connector/PBIDesktop.png "Power BI Desktop")

## <a name="prerequisites"></a>先决条件

若要将 Power BI 与 Common Data Service for Apps 配合使用，需要具备以下条件：

* 下载并安装 Power BI Desktop - 可在本地计算机上运行的免费应用程序。 可从[此处](https://powerbi.microsoft.com/desktop/)下载 Power BI Desktop。
* 具有创建者权限（用于访问门户）和读取权限（用于访问实体内的数据）的 Common Data Service for Apps 环境。

## <a name="finding-your-common-data-service-for-apps-environment-url"></a>查找 Common Data Service for Apps 环境 URL

1. 打开 [PowerApps](https://web.powerapps.com)，选择要连接到的环境，单击右上角的设置齿轮，然后单击“高级自定义”

    ![CDS for Apps 环境](./media/data-platform-cds-powerbi-connector/CDSEnv1.png "CDS for Apps 环境")

2. 单击开发人员资源部分下的“资源”，这将打开一个新选项卡。

    ![CDS for Apps 环境](./media/data-platform-cds-powerbi-connector/CDSEnv2.png "CDS for Apps 环境")

3. 复制新选项卡中 URL 的根，这是该环境的唯一 URL。 该 URL 的格式为 https://yourenvironmentid.crm.dynamics.com/，请确保不要复制 URL 的其余部分。 将其置于方便使用的位置，以便可在创建 PowerBI 报表时随时使用。

    ![CDS for Apps 环境](./media/data-platform-cds-powerbi-connector/CDSEnv3.png "CDS for Apps 环境")

## <a name="connecting-to-common-data-service-for-apps-from-power-bi-desktop"></a>从 Power BI Desktop 连接到 Common Data Service for Apps

1. 启动 Power BI Desktop，如果是首次启动，可能会出现欢迎屏幕，或直接进入空白画布，无论哪种情况，请单击“获取数据”并选择“更多”，打开 Power BI Desktop 中可用的完整数据源列表。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport1.png "Power BI Desktop")

2. 单击连接器列表中的“Online Services”和“Common Data Service for Apps (Beta)”。 单击“连接”。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport2.png "Power BI Desktop")

3. 将 Common Data Service for Apps 环境 URL 粘贴到“服务器 URL”字段中，单击“确定”。 如果是第一次执行此操作，系统将提示使用连接到 PowerApps 和 Common Data Service for Apps 所用的相同凭据进行登录。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport3.png "Power BI Desktop")

4. 导航器将显示可用于环境的所有实体（归入三个文件夹）。 展开“常见数据模型”文件夹。

    * 常见数据模型 - 这些是常用的标准实体，可作为常见数据模型的一部分在所有环境中使用。
    * 自定义实体 - 已在环境中创建或导入的实体。
    * 系统 - 包含环境中的所有实体，包括常见数据模型和自定义实体。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport4.png "Power BI Desktop")

5. 在右侧窗格，选择“帐户”实体以查看数据预览，单击“加载”。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport5.png "Power BI Desktop")

6. 实体现已加载到报表中，可以开始生成报表或重复此过程以添加其他实体。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport6.png "Power BI Desktop")

7. 在“字段”面板上，单击“名称”字段，向报表画布中添加一个新的可视化效果。 现可通过重复此过程和更改可视化效果来构建报表。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport7.png "Power BI Desktop")


## <a name="using-option-sets"></a>使用“选项”集

在实体中使用选项集，可在应用或流中为用户提供值的下拉列表。 使用 Power BI 连接器时，选项集字段将呈现为两列，分别显示唯一值和显示值。

例如，如果实体上有名为 ApprovalStatus 的选项集，则 Power BI 中将显示两个字段：

* ApprovalStatus - 此字段针对选项集中的每一项显示一个唯一整数值。应用筛选器时，此字段可帮助确保未来更改显示名称时不会对筛选器造成影响。
* ApprovalStatus_display - 此字段显示项的友好显示名称，最常用于在表格或图表中呈现选项的情况。

    |ApproalStatus|ApprovalStatus_Display|
    |---------|---------|
    1|已提交
    2|正在评审
    3|Approved
    4|已拒绝

## <a name="navigating-relationships"></a>关系导航

Common Data Service for Apps 中的“关系”功能要求使用 GUID 字段在 PowerBI Desktop 中的两个实体之间创建关系，这是系统生成的唯一标识符，可确保为可能与其他字段存在歧义或重复的创建记录创建关系。 有关管理 Power BI Desktop 中的关系的详细信息，请参阅[此处](https://docs.microsoft.com/power-bi/desktop-create-and-manage-relationships)。

可能会自动生成某些关系，可在创建报表时查看并确保创建了正确的关系：

* 实体上的查找字段将包含相关实体中的记录的 GUID。
* 相关实体中将具有格式为“[EntityName]id”的字段，其中包含 GUID，例如 Accountid 或 MyCustomEntityid
* 使用 PowerBI Desktop 管理关系功能，可在查找字段与相关实体上的 ID 字段之间创建一个新关系。


## <a name="next-steps"></a>后续步骤
* [管理实体中的字段](data-platform-manage-fields.md)
* [定义实体之间的关系](data-platform-entity-lookup.md)


