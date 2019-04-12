---
title: 在 Excel 中打开实体数据 | Microsoft Docs
description: 在 Excel 中打开实体数据以进行交互式查看和编辑。
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
# <a name="open-entity-data-in-excel"></a>在 Excel 中打开实体数据
通过在 Microsoft Excel 中打开实体数据，可以使用 Microsoft PowerApps Excel 加载项快速轻松地查看和编辑数据。 PowerApps Excel 加载项需要 Microsoft Excel 2016。

![Excel 加载项](./media/data-platform-cds-excel-addin/ExcelAddin.png "PowerApps Excel 加载项")

## <a name="open-entity-data-in-excel"></a>在 Excel 中打开实体数据
1. 在 [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**实体**。 将显示所有实体。
2. 单击您感兴趣的实体右侧的省略号 (...)。
3. 单击**在 Excel 中打开**，然后打开生成的工作簿。 此工作簿具有实体的绑定信息、您的环境的指针，以及 PowerApps Excel 加载项的指针。  
4. 在 Excel 中，单击**启用编辑**启用要运行的 PowerApps Excel 加载项。 Excel 加载项在 Excel 窗口右侧的窗格中运行。
5. 如果是第一次运行 PowerApps Excel 加载项，请单击**信任此加载项**以允许 Excel 加载项运行。
6. 如果提示您登录，单击**登录**，然后使用您在 [powerapps.com](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上使用的相同凭据登录。 Excel 加载项将使用之前的登录上下文并会让您自动登录（如果可以）。 因此，请确认 Excel 加载项右上角的用户名称。

Excel 加载项自动读取所选实体的数据。 请注意，在 Excel 加载项将数据读取到工作簿中前，工作簿中没有数据。

## <a name="view-and-refresh-data-in-excel"></a>在 Excel 中查看和刷新数据
在 Excel 加载项将实体数据读入工作簿后，您可以通过单击 Excel 加载项中的**刷新**随时更新数据。

## <a name="edit-data-in-excel"></a>在 Excel 中编辑数据
您可以根据需要更改实体数据，然后单击 Excel 加载项中的**发布**重新发布它。

若要编辑记录，选择工作表中的单元格，然后更改单元格值。

若要添加新记录，请执行以下步骤之一：

* 单击工作表中的任意位置，然后在 Excel 加载项中单击**新建**。
* 单击工作表的最后一行，然后按 Tab 键，直到光标移出该行的最后一列，新行创建。
* 单击工作表紧下面的行并开始在单元格中输入数据。 在将焦点从该单元格移出时，工作表将扩展以包括新行。

若要删除记录，请执行以下步骤之一：

* 右键单击要删除的工作表行旁边的行号，然后单击**删除**。
* 右键单击要删除的工作表行，然后单击**删除** > **表行**。

## <a name="add-or-remove-columns"></a>添加或移除列
您可以使用设计器调整自动添加到工作表中的列和实体。

1. 通过单击**选项**按钮（齿轮符号），然后选择**启用设计**复选框启用 Excel 加载项的数据源设计器。
2. 单击 Excel 加载项中的**设计**。 将列出所有数据源。
3. 在数据源旁边，单击**编辑**按钮（铅笔符号）。
4. 根据需要调整**选定字段**字段中的列表：
   * 若要从**可用字段**字段将字段添加到**选定字段**字段，单击该字段，然后单击**添加**。 或者，双击该字段。
   * 若要从**选定字段**字段删除字段，单击该字段，然后单击**删除**。 或者，双击该字段。
   * 若要更改字段顺序，单击**选定字段**字段中的字段，然后单击**向上**或**向下**。
5. 通过单击**更新**将更改应用到数据源，然后单击**完成**退出设计器。 如果您已添加了字段（列），单击**刷新**提取一组更新的数据。

> [!NOTE]
> 请确保始终在工作簿中包含 ID 和必填字段，因为在发布时您可能收到错误。

> [!NOTE]
> 当添加查找字段时，应确保添加 ID 和显示字段。

## <a name="troubleshooting"></a>疑难解答
存在一些可以通过几个简单步骤解决的问题。

* 并非所有实体都支持新记录的编辑和创建，这些实体将在 Excel 中打开并允许您查看数据，但发布将被禁用。
* 查找字段必须使用加载项进行编辑，以确保引用正确的记录，不支持通过复制和粘贴或直接在字段中键入更新这些字段。


如果您遇到此处未提到的问题，请通过[支持页面](https://powerapps.microsoft.com/support/)联系我们。

## <a name="next-steps"></a>后续步骤
* [管理实体中的字段](data-platform-manage-fields.md)
* [定义实体之间的关系](data-platform-entity-lookup.md)
* [使用 Common Data Service 生成应用程序](../canvas-apps/data-platform-create-app.md)
* [使用 Common Data Service 从头创建应用程序](../canvas-apps/data-platform-create-app-scratch.md)

