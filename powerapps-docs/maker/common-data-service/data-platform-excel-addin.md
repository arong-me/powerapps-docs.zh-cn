---
title: 在 Excel 中打开实体数据| Microsoft 文档
description: 在 Excel 中打开实体数据，进行交互式查看和编辑。
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: clwesene
ms.openlocfilehash: 8dbf6088104270d9251b70eec9adf0642de2f879
ms.sourcegitcommit: 91a102426f1bc37504142cc756884f3670da5110
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "34445837"
---
# <a name="open-entity-data-in-excel"></a>在 Excel 中打开实体数据
通过在 Microsoft Excel 中打开实体数据，可以使用 Microsoft PowerApps Excel 外接程序快速轻松地查看和编辑数据。 PowerApps Excel 外接程序要求安装 Microsoft Excel 2016。

![Excel 外接程序](./media/data-platform-cds-excel-addin/ExcelAddin.png "PowerApps Excel 外接程序")

## <a name="open-entity-data-in-excel"></a>在 Excel 中打开实体数据
1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“实体”。 显示所有实体。
2. 单击你感兴趣的实体右侧的省略号 (...)。
3. 单击“在 Excel 中打开”，打开生成的工作簿。 此工作簿具有实体的绑定信息、环境的指针和 PowerApps Excel 外接程序的指针。  
4. 在 Excel 中，单击“启用编辑”，允许 PowerApps Excel 外接程序运行。 Excel 外接程序将在 Excel 窗口右侧的窗格中运行。
5. 如果是首次运行 PowerApps Excel 外接程序，请单击“信任此外接程序”，允许 Excel 外接程序运行。
6. 如果系统提示你登录，请单击“登录”， 然后使用 [powerapps.com](https://web.powerapps.com) 上所用的同一凭据进行登录。 Excel 外接程序将使用以前的登录上下文并在可以登录时自动登录。 因此，请验证 Excel 外接程序右上角的用户名称。

Excel 外接程序将自动读取所选实体的数据。 注意，在 Excel 外接程序读取实体数据之前，工作簿中没有任何数据。

## <a name="view-and-refresh-data-in-excel"></a>在 Excel 中查看和刷新数据
当 Excel 外接程序将实体数据读取到工作簿后，可以通过单击 Excel 外接程序中的“刷新”随时更新数据。

## <a name="edit-data-in-excel"></a>在 Excel 中编辑数据
可以根据需要更改实体数据，然后通过单击 Excel 外接程序中的“发布”进行发布。

若要编辑一条记录，请选择工作表中的某个单元格，然后更改单元格的值。

若要添加一条新纪录，请执行以下步骤之一：

* 单击工作表中的任意位置，然后单击 Excel 外接程序中的“新建”。
* 在工作表的最后一行中单击，然后按 Tab 键，直至光标移出该行的最后一列，创建一个新行。
* 单击工作表下方的第一行，开始在单元格中输入数据。 将焦点移出该单元格时，工作表将会展开以包含新行。

若要删除一条记录，请执行以下步骤之一：

* 右键单击要删除的工作表行旁边的行号，然后单击“删除”。
* 右键单击要删除的工作表行，然后依次单击“删除” > “表行”。

## <a name="add-or-remove-columns"></a>添加或删除列
可使用设计器调整自动添加到工作表的列和实体。

1. 单击“选项”按钮（齿轮符号）启用 Excel 外接程序的数据源设计器，然后选择“启用设计”复选框。
2. 单击 Excel 外接程序中的“设计”。 所有数据源均列出。
3. 在数据源旁，单击“编辑”按钮（铅笔符号）。
4. 根据需要，调节“所选字段”字段中的列表：
   * 若要将某个字段从“可用字段”字段添加到“所选字段”字段，请单击该字段，然后单击“添加’。 或者，双击该字段。
   * 若要将某个字段从“所选字段”字段中删除，单击该字段，然后单击“删除”。 或者，双击该字段。
   * 若要更改字段的顺序，在“所选字段”字段中单击该字段，然后单击“向上”或“向下”。
5. 单击“更新”，然后单击“完成”退出设计器，将所做更改应用到数据源。 如果添加了字段（列），则单击“刷新”拉取已更新的数据集。

> [!NOTE]
> 请确保始终在工作簿中包含 ID 和必需字段，否则可能在发布时收到错误。

> [!NOTE]
> 添加查找字段时，请确保添加 ID 和“显示”字段。

## <a name="troubleshooting"></a>故障排除
可以通过一些简单的步骤解决一些问题。

* 并非所有实体都支持编辑和创建新记录，这些实体将在 Excel 中打开，可查看其中数据，但发布功能将被禁用。
* 必须使用外接程序编辑查找字段，以确保引用了正确的记录，不支持通过复制和粘贴更新这些字段或直接向字段中键入内容。


如果遇到此处未描述的问题，请通过[支持页面](https://powerapps.microsoft.com/support/)联系我们。

## <a name="next-steps"></a>后续步骤
* [管理实体中的字段](data-platform-manage-fields.md)
* [定义实体之间的关系](data-platform-entity-lookup.md)
* [使用 Common Data Service for Apps 生成应用](../canvas-apps/data-platform-create-app.md)
* [使用 Common Data Service for Apps 从头创建应用](../canvas-apps/data-platform-create-app-scratch.md)

