---
title: 将数据导入或导出 Common Data Service for Apps
description: 使用“从 Excel 获取数据”和“导出数据”功能，将 Excel 或 CSV 文件中的数据批量导入和导出到 Common Data Service (CDS) for Apps 中的实体
author: sabinn-msft
ms.service: powerapps
ms.topic: conceptual
ms.component: cds
ms.date: 05/14/2018
ms.author: sabinn
ms.openlocfilehash: 7f3e16be5bba1874759e0f9e40dc455f1e29c2bc
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697369"
---
# <a name="import-or-export-data-from-the-common-data-service-for-apps"></a>将数据导入或导出 Common Data Service for Apps

如果希望能够从 Excel 或 CSV 文件批量导入和导出数据，可以使用更新后 Common Data Service (CDS) for Apps 环境中的“从 Excel 文件获取数据”和“导出数据”功能。

有两种方法可以将文件从 Excel 或 CSV 文件导入到实体中

## <a name="option-1-import-by-creating-and-modifying-a-file-template"></a>选项 1：通过创建和修改文件模板导入

每个实体都具有输入文件中必须存在的必填字段。 为了使此方法更完美，建议创建一个模板，方法是先从实体导出数据，然后使用同一个文件（用数据进行了修改）将数据导入到该实体中。 这可节省时间和精力，而不必考虑每个实体的必填字段。

1. 准备文件模板

    - 首先按照“将数据导出到 CSV”下列出的步骤，将实体数据导出到 CSV 文件
    - 使用主键或备用键来定义计划，确保数据的唯一性。
    - 请参阅以下部分，了解如何在将数据导入实体前确保唯一性

1. 用数据修改文件

    - 将 Excel 或 CSV 文件中的数据复制到刚创建的模板中

1. 导入文件
    - 在 [powerapps.com](https://web.powerapps.com/) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“实体”
    - 选择要导入数据的实体
    - 单击顶部的省略号或菜单，选择“获取数据”并单击/点击“从 Excel 中获取数据”

> [!NOTE]
> 要将数据导入多个实体，请在顶部的菜单中选择“获取数据”并单击/点击“从 Excel 中获取数据”。 此时应该能够选择多个实体，并点击“下一步”

![将数据导入“帐户”实体的示例](./media/data-platform-import-export/import-data-to-account.png)

- 这可让你进入“导入数据”屏幕，可以在其中选择通过 Excel 或 CSV 文件导入数据
- 单击或点击“上传”
- 选择文件并按照提示操作，开始上传该文件

![将文件上传到“帐户”实体的示例](./media/data-platform-import-export/upload-account.png)

- 上传文件且“映射状态”为绿色后，在右上角单击“导入”。 如果在映射过程中遇到错误，请参阅以下部分，导航并修复映射错误

![成功“映射状态”和“导入”按钮的示例](./media/data-platform-import-export/success-map-imp.png)

- 导入成功完成后，可看到总的插入数和更新数

![显示插入数和更新数的成功导入示例](./media/data-platform-import-export/success-imp-insert.png)

> [!NOTE]
> 我们使用 Upsert（更新或插入）逻辑来更新记录（如果记录已存在）或者插入新记录。

## <a name="option-2-import-by-bringing-your-own-source-file"></a>选项 2：通过引入自己的源文件导入

如果你是高级用户，并且熟悉针对 Common Data service for Apps 实体的给定实体所需的字段，则可以定义自己的 Excel 或 CSV 源文件，并按照“导入文件”下记录的步骤操作

## <a name="navigating-mapping-errors"></a>导航映射错误

如果遇到映射错误，请在上传文件后，单击“映射状态”，使用以下步骤检查并纠正字段映射错误。

- 使用右下方“显示”下的下拉列表，遍历“未映射的字段”、“出现错误的字段”或“必填字段”

> [!TIP]
> 根据收到的是“警告”还是“错误”，首先通过“字段映射”中的下拉式体验来检查“未映射的字段”或“出现错误的字段”

![由于带有字段映射的警告而导致部分匹配的示例](./media/data-platform-import-export/partial-match.png)

![导航字段映射问题的示例](./media/data-platform-import-export/navigate-mappings.png)

![ 使用字段映射检查和纠正警告的示例](./media/data-platform-import-export/inspect-warnings.png)

- 纠正了所有错误和/或警告后，点击右上角的“保存更改”，应可借此返回“导入数据”屏幕
- “映射状态”列指示“已完成”（绿色）后，单击右上角的“导入”
- 收到“导入成功完成”消息后，可看到总的插入数和更新数

## <a name="ensuring-uniqueness-while-importing-data-into-entity-from-excel-or-csv"></a>在将数据从 Excel 或 CSV 导入实体时确保唯一性

Common Data Service for Apps 实体使用主键唯一地标识 CDS 实体表中的记录。 CDS 实体的主键是全局唯一标识符 (GUID)，并构成记录标识的默认基础。 数据操作（如将数据导入 CDS 实体）将显示默认主键。

示例：“帐户”实体的主键是 accountid

![从“帐户”实体导出文件的示例，accountid 显示为主键](./media/data-platform-import-export/export-pk.png)

有时，在集成来自外部源的数据时，主键可能不合格和/或无法满足需要。 为此，CDS 允许你定义备用键，代替主键唯一地标识记录。

示例：对于“帐户”实体，可以使用基于自然键的标识将“transactioncurrencyid”设置为备用键（例如，使用“美元”而非如上所示的 GUID 值 88c6c893-5b45-e811-a953-000d3a33bcb9 ）。 也可以选择货币符号或货币名称作为键。

![对“货币”实体创建备用键的示例](./media/data-platform-import-export/create-ak.png)

![从“帐户”实体导出文件的示例，“货币名称”显示为自然键](./media/data-platform-import-export/export-nk.png)

指定备用键后，用户仍然可以使用主键作为标识符。 因此，在上面的示例中，第一个文件仍然有效，前提是 GUID 为有效数据。

## <a name="export-data-to-csv"></a>将数据导出到 CSV

可以一次性导出标准实体或自定义实体的数据，并能一次导出多个实体的数据。 如果从多个实体导出数据，则每个实体的数据导出到其各自的 Microsoft CSV 文件中。

1. 在 [powerapps.com](https://web.powerapps.com/) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“实体”
1. 选择要导出数据的实体
1. 单击顶部的省略号或菜单，选择“导出”并单击/点击“数据”

    ![从“帐户”实体中导出数据的示例](./media/data-platform-import-export/export-account.png)

    > [!NOTE]
    > 要从多个实体导出数据，请在顶部菜单中选择“导出”并单击/点击“数据”。 此时应该能够选择多个实体

1. 导出成功完成后，应能够“下载导出数据”，这应该会提供一个指向可下载 CSV 文件的链接

    ![显示成功导出与可下载文件链接的示例导出](./media/data-platform-import-export/export-success.png)

## <a name="unsupported-data-types"></a>不支持的数据类型

当前不支持以下数据类型

- 时区
- 多项选择选项集
- 图像
