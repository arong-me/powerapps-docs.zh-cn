---
title: 有关活动和时间轴留言板的常见问题 | Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 08859f70e047d1c53379e8a79f56997d6beedc58
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456990"
---
# <a name="frequently-asked-questions-about-activities-and-the-timeline-wall"></a>有关活动和时间轴留言板的常见问题  

## <a name="is-a-title-required-when-adding-a-new-note"></a>添加新注释时需要标题吗？

不。 向活动添加注释时，会将标题字段标记为强制字段，但不是必需的。 这是旧版 Web 客户端中的一个已知问题。

## <a name="for-an-appointment-when-i-choose-the-option-to-save-as-draft-it-doesnt-show-that-the-appointment-has-been-saved-as-a-draft"></a>当我对约会选择“保存为草稿”选项时，它不会显示该约会已保存为草稿。

在旧版 Web 客户端中将约会保存为草稿时，标题不会显示“[草稿]”来表示约会已保存为草稿。

## <a name="can-i-add-activities-to-read-only-records"></a>可以向只读记录添加活动吗？

可以。 可以向只读实体（例如注释、电话呼叫、任务等等）添加活动。 

## <a name="are-html-tags-supported-in-notes"></a>注释是否支持 HTML 标记？

不。 为任何记录或实体创建注释活动时，不支持 HTML 标记。 例如, 如果将添加`<TAG> </TAG>`到便笺字段, 则它将显示为。 `<TAG_XXX="XX"> </TAG>`

## <a name="how-can-i-improve-performance-on-timeline-wall"></a>如何提高时间轴留言板性能？

通过优化由特定实体记录返回的数据量，可以提高时间轴留言板的性能。 

1.  将实体窗体配置为仅显示正在使用的活动。  这可以在窗体级别完成，只显示有用的活动。  例如，如果不为案例使用任务，可以在案例窗体上配置时间轴留言板，使其不显示任务。
2.  减少时间轴留言板显示的默认记录的数量。  默认情况下，将其设置为返回 10，如果超过 10，会导致性能问题。  建议不要超过默认值。 

## <a name="activity-wall-is-not-supported-in-print-preview"></a>打印预览不支持活动留言板。

在 Dynamics 365 中选择“打印预览”选项时，“时间轴留言板”不会显示在可用列表中。 用户将看到“注释”，但它不会显示任务或电子邮件。





