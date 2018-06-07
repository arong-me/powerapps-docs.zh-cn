---
title: 自定义卡 | Microsoft 文档
description: 在 PowerApps 中更改“详细信息”或“编辑”窗体上的卡片中所显示的默认控件
documentationcenter: ''
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 03/18/2018
ms.author: anneta
ms.openlocfilehash: aa9d5785f1c005da7c22c63bd94cb41e1a643ad3
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "31829296"
---
# <a name="customize-a-card-in-powerapps"></a>在 PowerApps 中自定义卡片
举例来说，通过更改卡控件执行基本的自定义（无需解锁卡）。 例如，通过解锁卡及添加默认情况下该卡无法使用的控件来执行高级自定义。

有关概述，请参阅 [了解数据卡](working-with-cards.md)。

## <a name="prerequisites"></a>先决条件

* 了解如何 [添加和配置控件](add-configure-controls.md)。
* 可查看本主题，了解一些基本概念，也可按照下列主题中所述的流程分步完成操作：

  1. [生成应用](data-platform-create-app.md)。
  2. [自定义库](customize-layout-sharepoint.md)。
  3. [自定义窗体](customize-forms-sharepoint.md)。

## <a name="customize-a-locked-card"></a>自定义锁定的卡
在此过程中，会将[文本输入](controls/control-text-input.md)控件替换为[滑块](controls/control-slider.md)控件，而无需解锁卡。

1. 登录 [PowerApps](http://web.powerapps.com)。

    ![PowerApps 主页](./media/customize-card/sign-in.png)

1. 打开生成和自定义的应用，选择 EditForm1，然后通过选择右侧窗格中的“帐户”打开“数据”窗格。

1. 在字段列表中，选择“员工人数”的向下箭头以打开选项列表，然后选择“编辑滑块”。

    ![数量卡片的下拉选项列表](./media/customize-card/card-selector.png)

    屏幕将体现所做的更改。

    ![带滑块控件的 EditForm1](./media/customize-card/add-slider.png)

## <a name="unlock-and-customize-a-card"></a>解锁和自定义卡
在此过程中，将解锁卡片，然后将[切换](controls/control-toggle.md)控件替换为[复选框](controls/control-check-box.md)控件。

1. 在 EditForm1 中，显示“发送市场营销资料”字段。

    ![显示“发送市场营销资料”字段](./media/customize-card/show-field.png)

2. 选择此卡后，单击或点击右侧窗格顶部附近的“高级”，然后单击或点击锁定图标以解锁卡片。

    ![显示“发送市场营销资料”字段](./media/customize-card/unlock-card.png)

1. 在卡片中，删除“切换”控件，添加“复选框”控件，并将新的控件命名为“chkMktg”。

    ![将切换替换为复选框](./media/customize-card/add-checkbox.png)

1. 选择刚才更新的卡片。

    ![选择卡](./media/customize-card/select-card.png)

1. 在右侧窗格中，确保“高级”选项卡仍然可见，并单击或点击“更多选项”。

    ![更多选项按钮](./media/customize-card/more-options.png)

1. 将卡片的“更新”属性的值更改为此表达式：
<br>`chkMktg.Value`

1. 将卡片的错误消息的“Y”属性的值更改为此表达式：<br>
`chkMktg.Y + chkMktg.Height`

    ![为新卡片选择错误消息](./media/customize-card/select-error.png)

1. 将 chkMktg 的“文本”属性的值更改为“是”。

    该屏幕反映出所做的更改，错误已解决。

    ![错误解决后的最终屏幕](./media/customize-card/final-screen.png)

## <a name="next-steps"></a>后续步骤
现已基本了解如何生成应用并自定义库、窗体和卡片，可以[从头开始构建自己的应用](data-platform-create-app-scratch.md)。
