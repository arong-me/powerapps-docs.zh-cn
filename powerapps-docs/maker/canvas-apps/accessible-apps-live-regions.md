---
title: 宣布与中的活动区域的动态更改画布应用 |Microsoft Docs
description: 如何使用活动区域来通知屏幕阅读器的动态更改中的画布应用
author: tahoon-ms
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.date: 10/22/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9a886b1c585f4fc07efc29bc1166ce4aca5586b5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61549941"
---
# <a name="announce-dynamic-changes-with-live-regions-for-canvas-apps"></a>宣布推出的画布应用的活动区域的动态更改

动态更改会造成视觉障碍的挑战。 通过屏幕读取器访问应用程序用户侧重于应用程序的一部分。 如果这些用户不会意识到这一点，在其他位置，发生变化。

可以通过添加实时屏幕读取器跟踪的区域来解决此问题。如果在活动区域中发生更改的内容，屏幕阅读器将公布所做的更改。

活动区域的基础机制[aria live 区域](https://www.w3.org/TR/wai-aria-1.1/#dfn-live-region)，因此适用相同的准则。

## <a name="example-uses-of-live-regions"></a>例如，可使用活动区域

活动区域可用于这些事件发生时通知用户：

* 在窗体中出现验证错误。
* 由按钮触发的操作是成功的。 例如，用户可能选择按钮以将项添加到一个集合，而活动区域无法显示消息"项已添加"。
* 在用户选择了不同的选项卡。
* 后台计时器刷新新闻源。

## <a name="create-and-configure-a-live-region"></a>创建和配置活动区域

你可以仅配置**[标签](controls/control-text-box.md)** 控件作为活动的区域。 其**Live**属性确定是哪种类型的活动区域。

* **关闭**:活动的区域。 屏幕阅读器不公布的更改。
* **礼貌**:完成后，屏幕阅读器读出更改说到。 使用此值不需要立即关注的非关键通知。
* **坚持**:屏幕阅读器中断本身以立即宣布的改变。 使用此函数需要立即关注的重要通知。

如果活动区域的文本内容发生更改，屏幕阅读器将公布的整个文本内容，而不仅仅是更改的部分。 如果的值**[文本](controls/properties-core.md)** 属性设置为空字符串 **""**，屏幕读取器不会公布的任何内容。

若要重复执行一条消息，请清除文本内容的值设置**[文本](controls/properties-core.md)** 属性设置为空字符串 **""** 然后将值设置为该消息。

## <a name="best-practices"></a>最佳做法

* 始终设置**[Visible](controls/properties-core.md)** 为 true。 某些屏幕阅读器不检测活动区域的消失，并且重新出现。
* 避免更改的值 **[Live](controls/properties-accessibility.md)**。 某些屏幕读取器不检测实时非实时区域后，反之亦然。
* 放置活动的区域中的逻辑位置在应用中，即使它不可见。 请确保它的内容之前和之后它有意义的元素的上下文中。 用户可访问活动区域随时通过使用屏幕阅读器，常规导航不只是发生了更改。

## <a name="next-steps"></a>后续步骤

了解如何[仅对屏幕读取器中显示的内容](accessible-apps-content-visibility.md)如果活动区域应从视力正常用户隐藏。