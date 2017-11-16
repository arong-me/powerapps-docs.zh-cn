---
title: "在 Excel 中打开实体数据| Microsoft 文档"
description: "在 Excel 中打开实体数据，进行交互式查看和编辑。"
services: powerapps
documentationcenter: na
author: chrisgarty
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: 2a72bfa21c8d4cb7eab0a3cb2292a61d5c036696
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="open-entity-data-in-excel"></a>在 Excel 中打开实体数据
通过在 Microsoft Excel 中打开实体数据，可以使用 Microsoft PowerApps Excel 外接程序快速轻松地查看和编辑数据。 PowerApps Excel 外接程序要求安装 Microsoft Excel 2016。

**注意**：如果 Microsoft Azure Active Directory (Azure AD) 租户配置为使用 Active Directory 联合身份验证服务 (ADFS)，则必须确保已应用 2016 年 5 月更新，以便 Excel 外接程序可以正确地登录。

## <a name="open-entity-data-in-excel"></a>在 Excel 中打开实体数据
1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“Common Data Service” 部分，然后单击或点击左侧导航窗格中的“实体”。 显示所有实体。
2. 单击你感兴趣的实体右侧的省略号 (...)。
3. 单击“在 Excel 中打开”，打开生成的工作簿。 此工作簿具有实体、环境指针和 PowerApps Excel 外接程序指针的绑定信息。  
4. 在 Excel 中，单击“启用编辑”，允许 PowerApps Excel 外接程序运行。 Excel 外接程序将在 Excel 窗口右侧的窗格中运行。
5. 如果是首次运行 PowerApps Excel 外接程序，请单击“信任此外接程序”，允许 Excel 外接程序运行。
6. 如果系统提示你登录，请单击“登录”， 然后使用 [powerapps.com](https://web.powerapps.com) 上所用的同一凭据进行登录。Excel 外接程序将使用以前的登录上下文并在可以登录时自动登录。 因此，请验证 Excel 外接程序右上角的用户名称。

Excel 外接程序将自动读取所选实体的数据。 注意，在 Excel 外接程序读取实体数据之前，工作簿中没有任何数据。

## <a name="view-and-refresh-entity-data-in-excel"></a>在 Excel 中查看和刷新的实体数据
当 Excel 外接程序将实体数据读取到工作簿后，可以通过单击 Excel 外接程序中的“刷新”随时更新数据。

## <a name="edit-entity-data-in-excel"></a>在 Excel 中编辑实体数据
可以根据需要更改实体数据，然后通过单击 Excel 外接程序中的“发布”进行发布。

若要编辑一条记录，请选择工作表中的某个单元格，然后更改单元格的值。

若要添加一条新纪录，请执行以下步骤之一：

* 单击工作表中的任意位置，然后单击 Excel 外接程序中的“新建”。
* 在工作表的最后一行中单击，然后按 Tab 键，直至光标移出该行的最后一列，创建一个新行。
* 立即单击工作表下方的行，并开始在单元格中输入数据。 将焦点移出该单元格时，工作表将会展开以包含新行。

若要删除一条记录，请执行以下步骤之一：

* 右键单击要删除的工作表行旁边的行号，然后单击“删除”。
* 右键单击要删除的工作表行，然后依次单击“删除” > “表行”。

## <a name="add-or-remove-columns"></a>添加或删除列
可以使用设计器调节自动添加到工作表的列。

1. 单击“选项”按钮（齿轮符号）启用 Excel 外接程序的数据源设计器，然后选择“启用设计”复选框。
2. 单击 Excel 外接程序中的“设计”。 所有数据源均列出。
3. 在数据源旁，单击“编辑”按钮（铅笔符号）。
4. 根据需要，调节“所选字段”字段中的列表：
   * 若要将某个字段从“可用字段”字段添加到“所选字段”字段，请单击该字段，然后单击“添加’。 或者，双击该字段。
   * 若要将某个字段从“所选字段”字段中删除，单击该字段，然后单击“删除”。 或者，双击该字段。
   * 若要更改字段的顺序，在“所选字段”字段中单击该字段，然后单击“向上”或“向下”。
5. 单击“更新”，然后单击“完成”退出设计器，将所做更改应用到数据源。 如果添加了字段（列），则单击“刷新”拉取已更新的数据集。

## <a name="troubleshooting"></a>故障排除
可以通过一些简单的步骤解决一些问题。

* 如果 Excel 外接程序加载元数据时收到“已禁止”消息，则登录到 Excel 外接程序的帐户无权使用目标 Common Data Service 数据库。 要解决此问题，请确认 Excel 外接程序右上角显示的用户名正确无误。 如有需要，单击 Excel 外接程序右上角的用户名，注销，然后重新登录。
* 如果在登录过程中打开一个空白网页，则帐户需要执行 AD FS，但运行外接程序的 Excel 版本暂不足以加载登录对话框。 根据需要，更新正在使用的 Excel 版本。 若要更新 Excel 版本，请使用 [Office 部署工具](https://technet.microsoft.com/library/jj219422.aspx)[ 从延期频道移至当前频道](https://technet.microsoft.com/library/mt455210.aspx)。

如果遇到此处未描述的问题，请通过[支持页面](https://powerapps.microsoft.com/support/)联系我们。

## <a name="next-steps"></a>后续步骤
* [管理实体中的字段](data-platform-manage-fields.md)
* [定义实体之间的关系](data-platform-entity-lookup.md)
* [使用 Common Data Service 数据库生成应用](data-platform-create-app.md)
* [使用 Common Data Service 数据库从头开始创建应用](data-platform-create-app-scratch.md)

