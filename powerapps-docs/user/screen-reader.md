---
title: " 在模型驱动的应用中使用屏幕阅读器 |MicrosoftDocs"
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 555a587a3c0eeb599439f713c9a99a7ace6b205a
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "61545111"
---
# <a name="use-a-screen-reader"></a>使用屏幕阅读器 


屏幕阅读器使模型驱动的应用程序可供具有很低或没有视觉方案或需要对临时方案的额外支持的人员 (如眼睛疲劳) 使用。 支持常用的屏幕阅读器, 如讲述人、JAWS 和 NVDA。 

- [了解有关使用 Microsoft 讲述人的详细信息](https://support.microsoft.com/help/22798)
- [了解有关使用 JAWS 的详细信息](http://www.freedomscientific.com/Products/Blindness/JawsDocumentation)


- [了解有关使用 NVDA 的详细信息](https://www.nvaccess.org/get-help/)


## <a name="basic-tasks-using-a-screen-reader"></a>使用屏幕阅读器的基本任务 

### <a name="open-an-app"></a>打开应用

1.  在导航栏上, 使用**Tab**键移动到 "应用程序" 下拉控件, 然后按**enter**打开站点地图。
2.  按**tab**键, 直到听到要打开的应用程序的名称, 例如 "销售"。 按**enter**打开应用。

### <a name="use-scan-mode-in-narrator"></a>在讲述人中使用扫描模式
你可以使用 "扫描模式" 快速使用箭头键和常见键盘快捷键来导航应用。 在此模式下快速跳转到标题、链接、特征点、窗体字段、控件和表。 按**Caps lock + 空格键**打开和关闭扫描模式。 详细信息：[使用扫描模式](https://support.microsoft.com/en-us/help/22809/windows-10-narrator-using-scan-mode)

### <a name="find-your-way-around-the-app"></a>在应用程序中查找

#### <a name="navigation-bar"></a>导航栏
打开应用时, 将在左侧显示带有子区域图标的竖线。 您可以使用 Tab 键在这些图标**上**移动, 直到听到您所需的子区域的名称 (例如 "帐户"), 或者可以使用站点地图控件。 例如, 按**tab**键, 直到听到 "帐户", 然后按**Enter**打开 "帐户" 视图。

#### <a name="grids"></a>置
屏幕阅读器更可靠、一致地浏览网格, 并公布行标题和列标题以及网格中的位置。 首次打开网格时, 默认制表位为视图选择器。 

每当您在网格外的网格内输入一个单元时, 讲述人就会公布该表的名称、行和列的计数, 以及游标在表中的位置。

如果光标位于表头内, 则使用**Tab**键或**Shift + tab**在标题之间快速导航。当你输入标题单元格时, 讲述人会公布每个标头的名称。 它还公布了单元的类型 (例如, "列标题")、列的位置 (例如, "第1列, 共6列") 以及列是否已排序或已选中。 如果在表头中按**enter**键, 则将按该列对表进行排序。 讲述人公布排序顺序, 你可以再次按**enter**来更改顺序。

当移出表中的最后一列时, 光标将移到网格的第二行, 此时必须使用向上键和向下键在非标头单元格之间导航。 如果改为按**tab**键, 则光标将移至下一个交互式元素, 通常为表筛选器列表。 在非标题行单元之间移动时, 讲述人会公布列名称、列的位置以及单元中的文本。

#### <a name="forms"></a>窗体
使用讲述人浏览窗体时, 可以使用多个导航模式, 最常见的模式是特征点、标题和窗体字段。 若要更改导航模式, 请按**Caps lock + 向上键**。 按住箭头锁定键, 同时按向上键以循环切换模式, 直到听到要使用的模式。 然后使用 Caps lock + 向左键和向右键来浏览各个项。 例如, 如果要访问联系人信息部分中的 "姓氏" 字段, 请执行以下操作:

1.  按住**Caps lock**键并按**向上**键, 直到听到 "特征点"。
2.  按住**Caps lock**键, 并按**向右箭头**键, 直到听到 "联系信息"。
3.  按住**Caps lock**键并按**向上**键键, 直到听到 "窗体字段", 以更改模式。
4.  使用 Caps lock + 左/右箭头键导航到 "姓氏" 字段, 直到听到 "Last Name"。 讲述人还公布控件类型、值、状态和字段的任何特殊说明。

你还可以使用 Tab 键快速导航到窗体上的交互式元素。 某些窗体字段的图标将在你按 Ctrl + Enter 时执行默认操作。 例如, 电子邮件窗体字段可能有打开电子邮件编辑器的信封图标。 

#### <a name="dashboardscharts"></a>仪表板/图表
您可以使用 Tab 键和 Caps lock + 箭头键来浏览仪表板图表。 按**tab**键可以快速切换到交互式元素, 并使用 Caps lock + 箭头键来导航非交互式元素, 例如标题、特征点和项。


> [!NOTE]
> 您必须安装最新的[Windows 10](http://www.microsoft.com/enable/products/windows10/default.aspx)更新, 才能获得适用于图表的所有辅助功能。

#### <a name="interactive-dashboard-streams"></a>交互仪表板流
您可以使用**Tab**键或**Shift + tab**键在交互仪表板流之间移动 (例如, 在 "帐户" 仪表板中找到), 或者只更改导航模式, 直到听到 "标题", 然后使用**Tab**键在仪表板流。

若要浏览仪表板流的每个元素, 请使用向上/向下箭头键。 讲述人将读取控件类型和控件标题。

#### <a name="business-process-flows"></a>业务流程
您可以在业务流程中导航, 例如在潜在顾客窗体顶部找到的流程, 按**tab**键向前移动, 并按**Shift + Tab**在实体之间向后移动。 使用在**左侧移动**的**Enter**键或**移动到右侧**按钮, 以显示处理流中的其他实体。 讲述人读取实体类型、阶段、状态、标题、元素编号 (超出元素总数) 以及当前是否选中。

#### <a name="dialog-boxes"></a>对话框

当对话框打开时, 讲述人会公布标题。 对于包含输入字段的对话框, "**关闭**" 按钮具有默认焦点, 允许您通过按**enter**关闭该对话框。 对于需要用户操作的对话框, 焦点位于 "主要操作" 按钮上, 如 "**删除**" 或 **"确定"** 。

您可以通过使用**Tab**键在控件之间进行导航。 光标将循环遍历对话框中的每个元素, 您可以按**Esc**键关闭该对话框。


