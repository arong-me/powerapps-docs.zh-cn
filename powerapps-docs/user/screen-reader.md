---
title: " 在模型驱动应用中使用屏幕阅读器 | MicrosoftDocs"
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
ms.openlocfilehash: c8ef71753fd743788b52b4f3578f829f153c0898
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543449"
---
# <a name="use-a-screen-reader"></a>使用屏幕阅读器 


通过屏幕阅读器，弱视者、盲人或可能需要额外支持来应对临时情况（如眼部疲劳）的人可以轻松使用模型驱动应用。 讲述人、JAWS 和 NVDA 等常用的屏幕阅读器均受支持。 

- [详细了解如何使用 Microsoft 讲述人](https://support.microsoft.com/help/22798)
- [详细了解如何使用 JAWS](https://www.freedomscientific.com/Products/Blindness/JawsDocumentation)


- [详细了解如何使用 NVDA](https://www.nvaccess.org/get-help/)


## <a name="basic-tasks-using-a-screen-reader"></a>使用屏幕阅读器执行基本任务 

### <a name="open-an-app"></a>打开应用

1.  在导航栏上，使用 Tab 键移动到应用下拉控件，然后按 Enter 打开站点地图   。
2.  按 Tab 键，直到听到要打开的应用程序的名称，例如“销售”  。 按 Enter 打开应用  。

### <a name="use-scan-mode-in-narrator"></a>在“讲述人”中使用扫描模式
使用扫描模式，可以快速使用箭头键和常见键盘快捷方式来导航应用。 在此模式下可快速跳转到标题、链接、标志、窗体字段、控件和表。 按 Caps Lock+空格键可打开和关闭扫描模式  。 更多信息：[使用扫描模式](https://support.microsoft.com/help/22809/windows-10-narrator-using-scan-mode)

### <a name="find-your-way-around-the-app"></a>了解如何使用应用

#### <a name="navigation-bar"></a>导航栏
打开应用时，左侧将显示带有子区域图标的竖线。 可以使用 Tab 键在这些图标上移动，直到听到所需子区域的名称（例如“帐户”），也可以使用站点地图控件  。 例如，按 Tab 键，直到听到“帐户”，然后按 Enter 打开“帐户”视图   。

#### <a name="grids"></a>网格
屏幕阅读器可以更可靠、更一致地导航网格，播报行标题、列标题以及网格中的位置。 首次打开网格时，默认制表位为视图选择器。 

每当从网格外进入网格内的一个单元格时，“讲述人”就会播报该表的名称、行和列的计数，以及光标在表中的位置。

如果光标位于表标题内，请使用 Tab 键或 Shift+Tab 在各标题之间快速导航   。输入标题单元格时，“讲述人”会播报每个标题的名称。 它还会播报单元格的类型（如“列标题”）、列的位置（如“第 1 列，共 6 列”）以及是否对该列进行了排序或选择。 如果在表标题中按 Enter，表将按该列进行排序  。 “讲述人”会播报排序顺序，再按 Enter 即可更改顺序  。

移出表的最后一列时，光标将移到网格的第二行，此时必须使用向上键和向下键才能在非标题单元格之间导航。 如果再按 Tab 键，光标将移到下一个交互式元素，通常是表筛选器列表  。 在非标题行单元格之间移动时，“讲述人”会播报列名称、列的位置以及单元格中的文本。

#### <a name="forms"></a>Forms
使用“讲述人”导航窗体时，可以使用多种导航模式，最常见的模式是标志、标题和窗体字段。 若要更改导航模式，请按 Caps Lock+向上键  。 按住 Caps Lock 键，同时按向上键，循环切换各个模式，直到听到要使用的模式。 然后使用 Caps Lock+向左键/向右键来循环访问各项。 例如，如果要访问“联系人信息”部分中的“姓氏”字段，请执行以下操作：

1.  按住 Caps Lock 键，然后按向上键，直到听到“标志”   。
2.  按住 Caps Lock 键，然后按向右键，直到听到“联系人信息”   。
3.  要更改模式，可按住 Caps Lock 键，然后按向上键，直到听到“窗体字段”   。
4.  使用 Caps Lock+向左/右键导航到“姓氏”字段，直到听到“姓氏”。 讲述人还会播报控件类型、值、状态和字段的任何特殊说明。

还可以使用 Tab 键快速导航到窗体上的交互式元素。 按 Ctrl+Enter 时，某些窗体字段的图标将执行默认操作。 例如，电子邮件窗体字段的信封图标可能会打开电子邮件编辑器。 

#### <a name="dashboardscharts"></a>仪表板/图表
可以使用 Tab 键和 Caps Lock+箭头键来导航仪表板图表。 按 Tab 键可以快速切换到交互式元素，使用 Caps Lock+箭头键可导航非交互式元素，例如标题、标志和项  。


> [!NOTE]
> 必须安装最新的 [Windows 10](https://www.microsoft.com/enable/products/windows10/default.aspx) 更新才能使所有辅助功能都可用于各个图表。

#### <a name="interactive-dashboard-streams"></a>交互式仪表板流
可以使用 Tab 键或 Shift+Tab 键在交互式仪表板流（例如“帐户”仪表板中可找到的流）之间移动，也可以只更改导航模式，直到听到“标题”，然后使用 Tab 键在仪表板流之间快速移动    。

要导航仪表板流的每个元素，请使用向上/向下键。 “讲述人”将读出控件类型和控件标题。

#### <a name="business-process-flows"></a>业务流程
要导航业务流程（例如“潜在客户”窗体顶部发现的流程），可以按 Tab 键在实体之间向前移动，按 Shift+Tab 可向后移动   。 对“左移”或“右移”按钮使用 Enter 键可显示流程中的其他实体    。 “讲述人”会读出实体类型、阶段、状态、标题、元素编号（元素总数）以及当前是否选中该实体。

#### <a name="dialog-boxes"></a>对话框

对话框打开时，“讲述人”会播报标题。 对于包含输入字段的对话框，焦点默认位于“关闭”按钮，这样便可以通过按 Enter 来关闭对话框   。 对于需要用户操作的对话框，焦点位于主要操作按钮上，如“删除”或“确定”   。

使用 Tab 键即可在控件之间导航  。 光标将遍历对话框中的每个元素，按 Esc 可将其关闭  。


