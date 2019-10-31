---
title: 在 PowerApps 中创建和使用数据流 | MicrosoftDocs
description: 了解如何在 PowerApps 中创建和使用数据流
ms.custom: ''
ms.date: 08/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-use-dataflows-in-powerapps"></a>在 PowerApps 中创建和使用数据流
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

通过 PowerApps 中提供的高级数据准备，您可以创建一个称为数据流的数据集合，然后可以使用它与来自各个源的业务数据连接、清理数据、转换数据，然后将数据加载到 Common Data Service 或您的组织的 Azure Data Lake Gen2 存储帐户中。

数据流是在 PowerApps 服务的环境中创建和管理的实体（实体类似于表）的集合。 您可以直接在创建数据流的环境中添加和编辑数据流中的实体，以及管理数据刷新计划。

在 PowerApps 门户中创建数据流后，您可以使用 Common Data Service 连接器或 Power BI Desktop 数据流连接器从中获取数据，具体取决于创建数据流时选择的目标。

使用数据流的三个主要步骤：

1.  在 PowerApps 门户中创作数据流。 您选择加载输出数据的目标、从中获取数据的源，以及使用 Microsoft 工具（让操作简单）转换数据的 Power Query 步骤。

2.  计划数据流运行。 Power Platform 数据流应以这种频率刷新数据流将加载和转换的数据。

3.  使用您加载到目标存储的数据。 您可以使用 Azure 数据服务（例如 Azure Data Factory、Azure Databricks 或任何其他支持 Common Data Model 文件夹标准的服务）生成应用、流、Power BI 报表和仪表板，或直接连接到组织湖中数据流的 Common Data Model 文件夹。

以下各节介绍了每个步骤，以便您可以熟悉提供的用于完成每个步骤的工具。 

## <a name="create-a-dataflow"></a>创建数据流
数据流是在一个环境中创建的。 因此，您只能从该环境查看和管理它们。 另外，想要从您的数据流中获取数据的个人必须有权访问您在其中创建数据流的环境。

> [!NOTE]
> 当前不支持在默认环境中创建将数据加载到 Azure Data Lake Storage Gen2 的数据流。

1.  登录到 PowerApps，并验证您所在的环境，在命令栏右侧附近找到环境切换器。

    ![环境切换器](media/environment-switcher.png)

2.  在左侧导航窗格中，选择**数据**旁边的向下箭头。

    ![数据选择](media/data-select.png)

3.  在**数据**列表中，选择**数据流**，然后选择**新建数据流**。

    ![创建数据流](media/create-a-dataflow.png)

4.  在**选择加载目标**页面上，选择要在其中存储实体的目标存储。 数据流可以将实体存储在 Common Data Service 或组织的 Azure Data Lake Storage 帐户中。 选择要加载数据的目标后，为数据流输入**名称**，然后选择**创建**。

    ![选择加载目标](media/select-load-target.png)

     > [!IMPORTANT]
     > 任何数据流只有一个负责人—创建它的人。 只有负责人才可以编辑数据流。 对数据流创建的数据的授权和访问取决于您将数据加载到的目标。 可以通过 Common Data Service 连接器访问加载到 Common Data Service 中的数据，需要访问该数据的人员被授权使用 Common Data Service。
     > 可通过 Power Platform 数据流连接器访问加载到组织的 Azure Data Lake Gen2 存储帐户中的数据，访问该数据需要在其创建环境中具有成员资格。

5. 在**选择数据源**页面上，选择存储实体的数据源，然后选择**创建**。 显示的数据源选择允许您创建数据流实体。 

    ![选择数据源](media/choose-data-source.png)

6. 选择数据源后，系统会提示您提供连接设置，包括连接到数据源时要使用的帐户。

    ![连接到数据源](media/data-source-provide-cred.png)

7. 连接后，选择用于实体的数据。 选择数据和源后，Power Platform 数据流服务随后将重新连接到数据源，以使数据流中的数据保持刷新状态，并以稍后在设置过程中选择的频率进行。


    ![选择数据](media/choose-data.png)

现在，您已经选择了要在实体中使用的数据，可以使用数据流编辑器将数据改编或转换为在数据流中使用所需的格式。

## <a name="use-the-dataflow-editor-to-shape-or-transform-data"></a>使用数据流编辑器来改编或转换数据
您可以使用 Power Query 编辑体验（类似于 Power BI Desktop 中的 Power Query 编辑器）将数据选择调整为最适合您的实体的形式。 要了解有关 Power Query 的详细信息，请参阅 [Power BI Desktop 中的 Query 概述](/power-bi/desktop-query-overview)。

如果要查看该查询编辑器在每个步骤中创建的代码，或者要创建自己的改编代码，可以使用高级编辑器。

![高级编辑器](media/advanced-editor.png)

## <a name="dataflows-and-the-common-data-model"></a>数据流和 Common Data Model 
数据流实体包括新工具，可轻松将您的业务数据映射到 Common Data Model，通过 Microsoft 和第三方数据加以扩充，并简化对机器学习的访问。 可以利用这些新功能为您的业务数据提供明智且可行的见解。 在下面介绍的编辑查询步骤中完成所有转换后，您可以将数据源表中的列映射到 Common Data Model 所定义的标准实体字段。 标准实体具有由 Common Data Model 定义的已知架构。

有关此方法以及 Common Data Model 的详细信息，请参阅 [Common Data Model](/powerapps/common-data-model/overview)。

要在数据流中利用 Common Data Model，请在**编辑查询**对话框中选择**映射到标准**转换。 在出现的**映射实体**屏幕中，选择要映射的标准实体。

![映射到标准实体](media/map-to-standard-entity.png)

当您将源列映射到标准字段时，将发生以下情况：

1.  源列采用标准字段名称（如果名称不同，则该列将重命名）。 

2.  源列获取标准字段数据类型。 

为了保留 Common Data Model 标准实体，所有未映射的标准字段均会获得 *Null* 值。

所有未映射的源列均保持原样，以确保映射结果是具有自定义字段的标准实体。

完成选择并完成实体及其数据设置后，即可以进行下一步，即选择数据流的刷新频率。

## <a name="set-the-refresh-frequency"></a>设置刷新频率
定义实体后，您将需要为每个连接的数据源计划刷新频率。

1. 数据流使用数据刷新过程来使数据保持最新。 在 **Power Platform 数据流创作工具**中，您可以选择手动刷新或按您选择的计划间隔自动刷新数据流。 要计划自动刷新，请选择**自动刷新**。

   ![自动刷新](media/refresh-automatically.png)

2. 以 UTC 时间输入数据流的刷新频率、开始日期和时间。

3. 选择**创建**。
<!-- 
## Connect to your dataflow in Power BI Desktop
Once you’ve created your dataflow and you have scheduled the refresh frequency
for each data source that will populate the model, you’re ready for the final task, which is connecting to your dataflow from within Power BI Desktop.

To connect to the dataflow, in Power BI Desktop select **Get Data** > **Power Platform** > **Power Platform dataflows** > **Connect**.

![Connect to the dataflow](media/get-data.png)

Navigate to the environment where you saved your dataflow, select
the dataflow, and then select the entities that you created from the list.

You can also use the search bar, near the top of the window, to quickly find the
name of your dataflow or entities from among many dataflow entities.

When you select the entity and then select the **Load** button, the entities
appear in the **Fields** pane in Power BI Desktop, and appear and behave just
like tables from any other dataset. -->

## <a name="using-dataflows-stored-in-azure-data-lake-storage-gen2"></a>使用 Azure Data Lake Storage Gen2 中存储的数据流
一些组织可能希望使用自己的存储来创建和管理数据流。 如果您按照要求正确设置存储帐户，则可以将数据流与 Azure Data Lake Storage Gen2 集成。 详细信息：[连接 Azure Data Lake Storage Gen2 以存储数据流](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2) 

## <a name="troubleshooting-data-connections"></a>数据连接疑难解答
有时可能会出现连接到数据流的数据源时出现问题的情况。 本节提供发生问题时的疑难解答提示。

-   **Salesforce 连接器**。 对具有数据流的 Salesforce 使用试用帐户会导致连接失败，而不会提供任何信息。 要解决此问题，请使用生产 Salesforce 帐户或开发人员帐户进行测试。

-   **SharePoint 连接器。** 请确保提供 SharePoint 站点的根地址，没有任何子文件夹或文档。 例如，使用类似于 *https://microsoft.sharepoint.com/teams/ObjectModel* 这样的链接。


-   **JSON 文件连接器。** 目前，您只能使用基本身份验证连接到 JSON 文件。 例如，类似于 *https://XXXXX.blob.core.windows.net/path/file.json?sv=2019-01-01&si=something&sr=c&sig=123456abcdefg* 的 URL 当前不受支持。

-   **Azure SQL 数据仓库。** 数据流当前不支持 Azure SQL 数据仓库的 Azure Active Directory 身份验证。 请在这种情况下使用基本身份验证。

## <a name="next-steps"></a>后续步骤
以下文章对于了解使用数据流的其他信息和场景很有用：

-   [在 Common Data Service 中向实体添加数据](data-platform-cds-newentity-pq.md)

-   [结合本地部署数据源使用数据流](using-dataflows-with-on-premises-data.md)

-   [连接 Azure Data Lake Storage Gen2 以存储数据流](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)

有关 Common Data Model 的详细信息：

-   [Common Data Model - 概述](/powerapps/common-data-model/overview)

-   [在 GitHub 上了解有关 Common Data Model 架构和实体的详细信息](https://github.com/Microsoft/CDM)
