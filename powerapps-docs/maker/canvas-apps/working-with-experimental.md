---
title: 了解预览和实验性功能 | Microsoft Docs
description: 测试并开始采用新功能。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/16/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 741cec402c6a5b5ea30700badd265f5e950203e9
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42858466"
---
# <a name="understand-experimental-and-preview-features-in-powerapps"></a>了解 PowerApps 中的实验性和预览功能

对于每个版本，我们都作出更改并添加功能，使 PowerApps 成为适应你需求的最佳工具。 我们推动产品向前发展。  

我们非常重视后向兼容性。 但是，在任何更改或改进中，我们可能会引入意外的副作用，应用可能无法完全按以前的方式运行。

为了平衡改进对现有应用的影响，我们会通过循序渐进的阶段推出较大型的功能。 本文介绍了此过程以及如何控制你对正在开发的功能的使用程度。

## <a name="feature-roll-out-stages"></a>功能推出阶段

功能在成为产品的正式部分之前将经历三个阶段：

1. 实验性：功能正处在开发之中。 尚不能依赖此功能；它可能会经历重大更改。
1. 预览：此功能即将完成并且稳定。 现在开始将现有应用向它迁移。
1. 已交付：此功能已完成。 所有应用都已启用此功能，且无法将其关闭。

在每个阶段，使用该功能的用户数将不断增加，这有助于我们验证该功能满足用户需求，且不会带来意外的副作用。

你的反馈对此过程至关重要。  请在 [PowerApps 社区论坛](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)中发布你的反馈。

功能的每个阶段持续多长时间？ 此值因功能而异。 我们需要考量许多因素，包括使用该功能的应用数、报告的问题数和需要该功能的迫切程度。 功能的某个阶段可能持续数周到数月。

此表可帮助你确定应在何时开始使用某个功能： 

| 阶段 | 应该何时使用它？ | 我是否可以自信地使用它？ | 新应用默认启用该功能吗？ | 
|----|----|----|-----|------|
| 实验性 | 如果你是希望测试该功能的前期采用者，请参阅一些有用信息。 | 不。  实验性功能可能随时从根本上更改或彻底消失。 | 不。 要使用该功能，必须明确选择加入。  |  
| 预览 | 新应用将自动包含此功能。  开始在现有应用中启用和测试，因为它们最终也会启用此功能。 | 可以。 此功能正逐渐成为产品的永久部分之一。  | 可以。 如果遇到问题，可能需要将其关闭。  请报告问题；这是功能处于预览状态的主要原因。 | 
| 已交付：（不再出现在“高级设置”中） | 所有应用都具有此功能。 | 可以。 | 可以。  大多数无法禁用。  |  

预览阶段即将结束时，我们可能会为所有应用启用该功能一次，并且我们将其标记为正在最终验证。  此更改为大多数用户提供试用该功能且仍可将其关闭的最后一次机会。 在此期间的及时反馈至关重要，因为下一阶段将完全交付此功能，并且用户无法将其关闭。  

## <a name="documentation"></a>文档

哪里可以找到有关这些功能的信息？  我们将“预览”功能视为已完成功能，你可以像了解任何其他产品功能一样对其进行了解： 
- [PowerApps 文档](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started)。 我们将提供有关新功能的基础知识：好处、入门方法和参考信息。
- [PowerApps 社区论坛](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)。  其他用户将与你一起探索新功能。 学习他们的经验，并分享你的经验。
- [PowerApps 博客](https://powerapps.microsoft.com/blog/)。  博客文章经常（但不是总是）会介绍一些新功能。

实验性功能不同。  它们是正在开发的功能，我们不将其视为已完成功能。 “应用设置”窗格（见下文）中的简短说明可能是它们唯一的信息。 实验性功能通常不会显示在文档中。 社区论坛可能是相关信息的最佳来源。  在某些情况下，早期的博客文章会对此类功能进行介绍。  如果未找到足够的信息，可在论坛中提问或等待功能进入预览阶段。

## <a name="controlling-which-features-are-enabled"></a>控制启用哪些功能

实验性和预览功能在应用的“高级设置”中列出。  在应用内，选择“文件”菜单并选择“应用设置”，然后选择“高级设置”。 向下滚动到“预览功能”和“实验性功能”部分：

![](media/working-with-experimental/advanced-settings.png)

每项功能都有一个切换开关。  “关”表示该功能处于禁用状态。  将所有开关关闭是运行应用的基准方法，也是最安全的方法。

在某些情况下，更改设置后可能需要关闭并重新打开应用。  功能说明应该会指示何时必须执行此步骤。

在“高级设置”窗格顶部，可以查找完全交付功能的设置，这些功能不是预览或实验性的，你可以完全依赖它们。 

这些设置特定于每个应用，因此更改切换开关会影响当前处于打开状态的应用。 如果创建应用，这些开关将还原为应用的默认设置。
