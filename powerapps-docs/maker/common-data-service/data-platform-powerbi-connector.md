---
title: 创建 PowerBI 报表 | Microsoft Docs
description: 使用面向应用程序的 Common Data Service 连接器从 PowerBI Desktop 连接到您的数据。
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-a-power-bi-report"></a>创建 Power BI 报表
面向应用程序的 Common Data Service 允许您使用 Power BI Desktop 直接连接到您的数据以创建报表并将其发布到 Power BI。 从 Power BI，报表可在仪表板中使用，与其他用户共享并可跨 Power BI 移动应用程序上的平台访问。

![Power BI Desktop](./media/data-platform-cds-powerbi-connector/PBIDesktop.png "Power BI Desktop")

## <a name="prerequisites"></a>必备条件 

若要通过面向应用程序的 Common Data Service 使用 Power BI，您需要执行以下操作：

* 下载并安装 Power BI Desktop，这是在本地计算机上运行的免费应用程序。 您可以在[此处](https://powerbi.microsoft.com/desktop/)下载 Power BI Desktop。
* 具有制造者门户访问权限和实体内的数据读取访问权限的面向应用程序的 Common Data Service 环境。

## <a name="finding-your-common-data-service-for-apps-environment-url"></a>查找您的面向应用程序的 Common Data Service 环境 URL。

1. 打开 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 并选择要连接到的环境，然后单击右上角的**设置齿轮**，然后单击**高级自定义**

    ![面向应用程序的 CDS 环境](./media/data-platform-cds-powerbi-connector/CDSEnv1.png "面向应用程序的 CDS 环境")

2. 单击“开发人员资源”部分下**资源**，其将打开一个新选项卡。

    ![面向应用程序的 CDS 环境](./media/data-platform-cds-powerbi-connector/CDSEnv2.png "面向应用程序的 CDS 环境")

3. 复制新选项卡中该 URL 的根，这是您的环境的唯一 URL。 URL 格式将为 **https://yourenvironmentid.crm.dynamics.com/**，请确保不要复制 URL 的其余部分。 请将信息保留在方便的位置，以便您可以在创建 PowerBI 报表时使用它。

    > [!div class="mx-imgBorder"] 
    > ![面向应用程序的 CDS 环境](./media/data-platform-cds-powerbi-connector/CDSEnv3.png "面向应用程序的 CDS 环境")

## <a name="connecting-to-common-data-service-for-apps-from-power-bi-desktop"></a>从 Power BI Desktop 连接到面向应用程序的 Common Data Service

1. 启动 **Power BI Desktop**，如果是您首次启动，可能会使用欢迎屏幕提示您或将您直接带入一个空白区域 - 不论是哪种情况，均单击**获取数据**并选择**更多**打开可用于 Power BI Desktop 的数据源的完整列表。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport1.png "Power BI Desktop")

2. 从连接器列表单击 **Online Services** 和**面向应用程序的 Common Data Service (Beta)**。 单击**连接**。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport2.png "Power BI Desktop")

3. 将您的**面向应用的 Common Data Service 环境 URL** 复制到**服务器 URL** 字段中，然后单击**确定**。 如果是您首次使用，将提示您使用用于连接到 PowerApps 和面向应用程序的 Common Data Service 的相同凭据登录。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport3.png "Power BI Desktop")

4. 导航器将为您显示您的环境可用的所有实体，并分组到三个文件夹中。 展开**通用数据模型**文件夹。

    * 通用数据模型 - 这些是在所有环境中作为通用数据模型的一部分通用和可用的标准实体。
    * 自定义实体 - 是您在环境中创建或导入的实体。
    * 系统 - 包含您的环境中的所有实体，包括通用数据模型和自定义实体。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport4.png "Power BI Desktop")

5. 选择**客户**实体在右侧窗格中查看数据的预览，然后单击**加载**。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport5.png "Power BI Desktop")

6. 现在您的实体已加载到报表中，您可以开始创建报表，也可以重复此过程添加其他实体。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport6.png "Power BI Desktop")

7. 单击“字段”面板中的**名称**字段向报表区域添加新可视化项。 现在您可以重复此过程并更改可视化项来创建报表。

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport7.png "Power BI Desktop")


## <a name="using-option-sets"></a>使用选项集

选项集用于在实体中向应用程序和流中的用户提供值下拉列表。 在使用 Power BI 连接器时，选项集字段将显示为两列来显示唯一值和显示值。

举例来说，如果您在名为 ApprovalStatus 的实体中有一个选项集，您会看到 Power BI 中的两个字段：

* ApprovalStatus - 这将显示您的选项集中每个项目的唯一整数值，这在应用筛选器以使它们在您未来对显示名称进行更改时不会受影响时提供帮助。
* ApprovalStatus_display - 这将显示项目的友好显示名称，最常用于在表或图表中呈现选项时。

    |ApprovalStatus|ApprovalStatus_Display|
    |---------|---------|
    1|已提交
    2|审核中
    3|已审核
    4|已拒绝

## <a name="navigating-relationships"></a>导航关系

面向应用程序的 Common Data Service 中的关系需要您使用 GUID 字段在 PowerBI desktop 内在两个实体之间创建关系，这是系统生成的唯一标识符，确保关系为其他字段可能不明确或重复的创建记录创建。 可以在[此处](https://docs.microsoft.com/power-bi/desktop-create-and-manage-relationships)了解 Power BI desktop 中管理关系的详细信息。

虽然有些关系可能自动创建，您仍然可以查看并确保在创建报表时建立正确的关系：

* 实体中的查找字段将在相关实体中包含记录的 GUID。
* 相关实体将有格式为 "[EntityName]id" 的字段，其包含 GUID，例如，Accountid 或 MyCustomEntityid
* 使用 PowerBI desktop 管理关系功能，您可以在查找字段之间建立新关系，以及相关实体中的 ID 字段。


## <a name="next-steps"></a>后续步骤
* [管理实体中的字段](data-platform-manage-fields.md)
* [定义实体之间的关系](data-platform-entity-lookup.md)


