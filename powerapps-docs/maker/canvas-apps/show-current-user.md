---
title: 在画布应用中显示有关当前用户的详细信息 | Microsoft Docs
description: 在 Power Apps 中，在画布应用中显示已登录用户的名称和电子邮件地址
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f77ec80cfaf579c836277f0e29d3b84b325a0462
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674596"
---
# <a name="show-information-about-a-power-apps-user-in-a-canvas-app"></a>在画布应用中显示有关 Power Apps 用户的信息

在 "Power Apps" 中，显示与登录到画布应用的用户关联的完整名称、电子邮件地址和图片。 例如，可以使用此信息来自动填充窗体。

例如，可以使用此功能：

* 为参加培训的用户、活动志愿者、展台签到等创建签到“表”。
* 在人力资源应用中显示全名。
* 联系支持人员时，自动输入电子邮件地址。

基本上可在自动填充窗体或标签的任意情景中使用此功能，用户会因此而获益

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="show-user-details"></a>显示用户详细信息

1. 在“插入”选项卡上，单击或点击“媒体”，然后单击或点击“图像”。
   
   ![][2]
2. 将 **[Image](controls/properties-visual.md)** 属性设为下面的公式：
   <br>**User().Image**
   
    ![][3]
3. 在“插入”选项卡上，依次单击或点击“文本”和“标签”：  
   
    ![][4]
4. 将 **[Text](controls/properties-core.md)** 属性设为下面的公式：
   <br>**User().FullName**
   
   ![][6]
   
   执行此操作时，标签会自动填充为全名。 移动标签，使其位于图像控件下方，如下所示：
   
   ![][5]
5. 添加另一个标签，然后将其 **[Text](controls/properties-core.md)** 属性设置为以下公式：
   <br>**User().Email**  
   
    ![][8]
   
    执行此操作时，标签会自动填充为电子邮件地址。 移动标签，使其位于第一个标签下方，如下所示：  
   
    ![][7]

[2]: ./media/show-current-user/add-image.png
[3]: ./media/show-current-user/imageproperty.png
[4]: ./media/show-current-user/insertlabel.png
[5]: ./media/show-current-user/label.png
[6]: ./media/show-current-user/textproperty.png
[7]: ./media/show-current-user/secondlabel.png
[8]: ./media/show-current-user/email.png
[9]: ./media/show-current-user/preview.png
