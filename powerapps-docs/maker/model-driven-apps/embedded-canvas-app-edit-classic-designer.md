---
title: 编辑在模型驱动窗体上嵌入的区域应用 | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3c93c6696efc39e4f2354418ad1743fca3ebea95
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873033"
---
# <a name="edit-a-canvas-app-embedded-on-a-model-driven-form"></a>编辑在模型驱动窗体上嵌入的区域应用
本主题介绍如何编辑在模型驱动窗体上嵌入的区域应用。

## <a name="edit-the-canvas-app-directly"></a>直接编辑区域应用
您可以编辑在模型驱动窗体上嵌入的区域应用，与编辑任何其他区域应用一样。 有关编辑区域应用的步骤，请参阅：[编辑区域应用](../canvas-apps/edit-app.md)

## <a name="edit-the-canvas-app-via-the-host-model-driven-form"></a>通过主机模型驱动窗体编辑区域应用
替代选项是通过主机模型驱动窗体编辑嵌入式区域应用。

假设您要编辑在客户实体的名为 Account Main Form 的窗体上嵌入的区域应用。 为此，请按照以下步骤操作： 

1.  登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
2.  [编辑客户实体的名为 Account Main Form 的窗体](create-and-edit-forms.md)。 
3.  在命令栏中，选择**切换到经典**在经典窗体设计器中打开窗体。
4.  在经典窗体设计器中，选择自定义以显示嵌入式区域应用的字段。
5.  选择字段后，在**主页**选项卡上的**编辑**组中，选择**更改属性**。
6.  在**字段属性**对话框中，选择**控件**选项卡。
7.  在**字段属性**对话框中，在控件列表中，选择**区域应用**。
8.  在控件列表下的部分，选择**自定义**编辑区域应用。 这会在 Power Apps Studio 中在新选项卡上打开要编辑的区域应用。
       > [!NOTE]
       > 如果打开 Power Apps Studio 被 Web 浏览器弹出窗口阻止程序阻止，您必须启用 make.powerapps.com 网站或暂时禁用弹出窗口阻止程序，然后再次选择**自定义**。
9. 在完成更改时，选择**文件**选项卡，然后选择**保存**。
10. 若要让您的更改对最终用户可用，选择**发布**，然后选择**发布此版本**。

## <a name="see-also"></a>另请参阅
[在模型驱动的窗体上嵌入区域应用](embed-canvas-app-in-form.md) <br />
[在模型驱动窗体上添加嵌入式区域应用](embedded-canvas-app-add-classic-designer.md) <br />
[自定义在模型驱动窗体上嵌入的区域应用的屏幕尺寸和方向](embedded-canvas-app-customize-screen.md) <br />
[从嵌入的区域应用内在主机窗体上执行预定义操作](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegration 控件的属性和操作](embedded-canvas-app-properties-actions.md) <br />
[共享嵌入式区域应用](share-embedded-canvas-app.md) <br />
[嵌入式区域应用使用指南](embedded-canvas-app-guidelines.md) <br />
[迁移使用最新的公共预览版本创建的模型驱动窗体上的嵌入式区域应用](embedded-canvas-app-migrate-from-preview.md) <br />
