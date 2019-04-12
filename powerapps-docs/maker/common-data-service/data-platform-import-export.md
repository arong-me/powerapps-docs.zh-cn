---
title: 从 Common Data Service 导入或导出数据
description: 使用“从 Excel 获取数据”和“导出数据”功能在 Common Data Service 中的实体中批量导入和导出 Excel 或 CSV 文件的数据
author: sabinn-msft
ms.service: powerapps
ms.topic: conceptual
ms.component: cds
ms.date: 05/14/2018
ms.author: sabinn
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="import-or-export-data-from-common-data-service"></a>从 Common Data Service 导入或导出数据

若要批量导入和导出 Microsoft Excel 或 CSV 文件的数据，对更新的 Common Data Service 环境使用“从 Excel 文件获取数据”和“导出数据”功能。

有两种方式可以将文件导入 Excel 或 CSV 文件的实体。

## <a name="option-1-import-by-creating-and-modifying-a-file-template"></a>选项 1：通过创建和修改文件模板导入

每个实体都包含必须存在于输入文件中的必填字段。 建议您创建模板。 首先，从实体导出数据。 使用相同文件（已使用您的数据修改）将数据导入到实体。 此模板节省时间和工作量。 您不必负责每个实体的必填字段。

1. 准备文件模板。

    a. 将实体数据导出到 CVS 文件。 按照**将数据导出到 CSV** 中的步骤操作。  
    b. 定义计划以确保数据是唯一的。 使用**主键**或**备用键**。  
    c. 请参阅下一部分了解在将数据导入到实体前确保数据是唯一数据的相关说明。 

1. 使用您的数据修改文件。

    - 将 Excel 或 CSV 文件中的数据复制到您刚才创建的模板中。

1. 导入文件。  
    a. 在 [powerapps.com](https://web.powerapps.com/) 上，展开**数据**部分。 在左侧导航窗格中选择**实体**。  
    b. 选择您要导入数据的实体。  
    c. 选择顶部的省略号或菜单。 选择**获取数据**。 选择**从 Excel 获取数据**。  

    > [!NOTE]
    > 若要将数据导入到多个实体，在顶部菜单上，选择**获取数据**。 选择**从 Excel 获取数据**。 然后可以选择多个实体并选择**下一步**。

    > [!div class="mx-imgBorder"] 
    > ![将数据导入**客户**实体的示例](./media/data-platform-import-export/import-data-to-account.png)

    d. 在**导入数据**屏幕上，选择是否从 Excel 或 CSV 文件导入数据。  
    e. 选择**上载**。  
    f. 选择您的文件。 按照提示上载文件。  

    > [!div class="mx-imgBorder"] 
    > ![将文件上载到**客户**实体的示例](./media/data-platform-import-export/upload-account.png)

    g. 在上载文件后，**映射状态**为绿色，选择右上角的**导入**。 请参阅下一部分了解如何导航以及修复任何映射错误。  

    > [!div class="mx-imgBorder"] 
    > ![成功**映射状态**和**导入**按钮的示例](./media/data-platform-import-export/success-map-imp.png)

    h. 在导入成功完成后，您将看到插入和更新的总数。  

    > [!div class="mx-imgBorder"] 
    > ![显示插入和更新数量的成功导入的示例](./media/data-platform-import-export/success-imp-insert.png)

    > [!NOTE]
    > 使用 Upsert（插入或更新）逻辑更新记录（如果已经存在）或插入新记录。

## <a name="option-2-import-by-bringing-your-own-source-file"></a>选项 2：通过提供您自己的源文件导入

如果您是一个高级用户并且了解 Common Data Service 实体的指定实体的必填字段，请定义您自己的 Excel 或 CSV 源文件。 请按照**导入文件**中的步骤操作。

## <a name="navigate-mapping-errors"></a>导航映射错误

如果您在上载文件后收到映射错误，选择**映射状态**。 请采取以下步骤检查和纠正字段映射错误。

1. 使用右侧的下拉菜单（在**显示**下）浏览**未映射的字段**、**出错的字段**或**必填字段**。

    > [!TIP]
    > 根据您是否收到警告或错误，通过**字段映射**中的下拉菜单检查**未映射的字段**或**出错的字段**。

    > [!div class="mx-imgBorder"] 
    > ![由于字段映射出现警告而部分匹配的示例](./media/data-platform-import-export/partial-match.png)

    > [!div class="mx-imgBorder"] 
    > ![导航字段映射问题的示例](./media/data-platform-import-export/navigate-mappings.png)

    > [!div class="mx-imgBorder"] 
    > ![检查和纠正字段映射警告的示例](./media/data-platform-import-export/inspect-warnings.png)

2. 在解决所有错误和警告后，选择右上角的**保存更改**。 您将返回到**导入数据**屏幕。
3. 当**映射状态**列显示绿色的**已完成**时，选择右上角的**导入**。
4. 当您收到消息**导入已成功完成**时，将显示总插入和更新数。

## <a name="ensure-uniqueness-when-you-import-data-into-an-entity-from-excel-or-csv"></a>确保从 Excel 或 CSV 将数据导入实体时的唯一性

Common Data Service 实体使用主键唯一标识 Common Data Service 实体表中的记录。 Common Data Service 实体的主键是一个全局唯一标识符 (GUID)。 这将建立记录标识的的默认基础。 数据操作（如将数据导入到 Common Data Service 实体）显示默认主键。

示例：  
**客户**实体的主键是 **accountid**。

   > [!div class="mx-imgBorder"] 
   > ![显示 **accountid** 作为主键的**客户**实体的示例导出文件](./media/data-platform-import-export/export-pk.png)

有时，在从外部源集成数据时，主键可能不起作用。 使用 Common Data Service 定义替代主键唯一标识记录的备用键。

示例：  
对于**客户**实体，您可以使用基于自然键的标识将 **transactioncurrencyid** 设置为备用键。 例如，使用**美元**而不是之前显示的 GUID 值 **88c6c893-5b45-e811-a953-000d3a33bcb9** 。 您还可以选择**货币符号**或**货币名称**作为键。

   > [!div class="mx-imgBorder"] 
   > ![在**货币**实体上创建备用键的示例](./media/data-platform-import-export/create-ak.png)

   > [!div class="mx-imgBorder"] 
   > ![显示**货币名称**作为自然键的**客户**实体的示例导出文件](./media/data-platform-import-export/export-nk.png)

在指定备用键后，用户仍然可以使用主键作为标识符。 在前面的示例中，如果 GUID 是有效的数据，第一个文件仍然有效。

## <a name="export-data-to-csv"></a>将数据导出到 CSV

您可以从标准实体或自定义实体进行一次性数据导出。 您可以一次性从多个实体导出数据。 如果从多个实体导出数据，每个实体将导出到其自己的 Microsoft CSV 文件。

1. 在 [powerapps.com](https://web.powerapps.com/) 上，展开**数据**部分。 在左侧导航窗格中选择**实体**。
1. 选择您要从中导出数据的实体。
1. 选择顶部的省略号或菜单。 选择**导出**。 选择**数据**。

    > [!div class="mx-imgBorder"] 
    > ![从**客户**实体导出数据的示例](./media/data-platform-import-export/export-account.png)

    > [!NOTE]
    > 若要从多个实体导出数据，在顶部菜单上，选择**导出**。 选择**数据**。 您可以选择多个实体。

1. 在成功完成导出后，您可以**下载导出的数据**。 此下载将为您提供可下载 CSV 文件的链接。

    > [!div class="mx-imgBorder"] 
    > ![显示包含可下载文件链接的成功导出的示例导出](./media/data-platform-import-export/export-success.png)

## <a name="unsupported-data-types"></a>不支持的数据类型

当前不支持以下数据类型。

- 时区
- 多选选项集
- 图像
