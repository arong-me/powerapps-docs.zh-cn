---
title: 在模型驱动的窗体上嵌入区域应用 | MicrosoftDocs
ms.custom: ''
ms.date: 12/10/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="embed-a-canvas-app-on-a-model-driven-form"></a>在模型驱动的窗体上嵌入区域应用

制作者可使用区域应用和低码 WYSIWYG 区域应用设计器轻松设计和创建自定义布局。 制作者还可以使用区域应用在窗体中显示来自超过200 个数据源的数据。

> [!NOTE]
> 此功能现在还在预览中。 <br />
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

通过嵌入式区域应用，制作者可以在模型驱动的窗体上利用区域应用。 可使用嵌入式区域应用在窗体上轻松创建丰富的视觉区域，以及在来自 Common Data Service 的数据旁边显示各种来源的数据。

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-canvas-app-in-form.png "模型驱动的应用窗体中的嵌入式区域应用")

区域应用嵌入模型驱动的窗体中的方式与添加其他自定义控件的方式相同。 嵌入式区域应用中包含丰富的数据集成功能，可以将上下文数据从主机模型驱动的窗体导入到嵌入式区域应用。

在模型驱动的窗体中嵌入区域应用的步骤基于希望主机模型驱动的窗体向嵌入式区域应用提供的数据上下文。
-   将当前记录作为数据上下文传递。 详细信息：[使用嵌入式区域应用将当前记录作为数据上下文传递](pass-current-embedded-canvas-app.md)
-   将一列与当前记录有关的记录作为数据上下文传递。 详细信息：[使用嵌入式区域应用将相关记录列表作为数据上下文传递](pass-related-embedded-canvas-app.md) 

<!-- After you have added an embedded canvas app to your model-driven form, learn how to share your embedded canvas app with other users (LINK TO ARTICLE #4).  -->

<!-- For things to keep in mind when working with embedded canvas apps and to help troubleshoot any issues you might encounter, see (LINK TO ARTICLE #5). -->

## <a name="see-also"></a>另请参阅
[PowerApps 中的区域应用是什么？](../canvas-apps/getting-started.md) <br />
[在 PowerApps 中添加和配置区域应用控件](../canvas-apps/add-configure-controls.md) <br />
[适用于 PowerApps 的区域应用连接器概述](../canvas-apps/connections-list.md) 
