---
title: 从嵌入的区域应用内在主机模型驱动窗体上执行操作 | MicrosoftDocs
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
ms.openlocfilehash: 0f6ec9122582f338ac23143149c6f59ea63e456f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2706095"
---
# <a name="perform-predefined-actions-on-the-host-model-driven-form-from-within-an-embedded-canvas-app"></a>从嵌入的区域应用内在主机模型驱动窗体上执行预定义的操作
嵌入的区域应用提供在主机模型驱动窗体上执行预定义操作的功能。 这些操作让开发者可以导航、刷新、保存主机模型驱动窗体。 使用这些操作，嵌入的区域应用可以充当更重要的模型驱动窗体和模型驱动应用的组成部分。  

**ModelDrivenFormIntegration** 对象现在包括以下新方法以允许开发者在主机模型驱动窗体上执行操作。  
  
### <a name="navigatetomainformentityname-mainformname-recordid"></a>NavigateToMainForm(entityName, mainFormName, recordId)
在主机模型驱动窗体上导航到主窗体并显示指定记录。  
* **entityName** - 指定主窗体的父实体的必需字符串参数。  
* **formName** - 指定要导航到的主窗体名称的必需字符串参数。  
* **recordId** - 必需的字符串参数，指定要在主窗体中显示的记录的 ID。  
 
调用 NavigateToMainForm 方法可能显示以下错误消息。
  
| 错误消息 | 疑难解答指南 |
|:--------------|:-------------------------|
|**找不到实体：*[EntityName]*** | 请检查 *entityName* 参数的值并确保它是有效的实体名称，以及用户有权访问它。 |
|**找不到窗体：*[FormName]*** | 请检查 *mainFormName* 参数的值并确保它是有效的主窗体名称，以及用户有权访问它。 |
|**加载记录时出现问题。** | 请检查 *recordId* 参数的值并确保它是有效的记录 ID，以及用户有权访问它。 |
  
  
### <a name="navigatetoviewentityname-viewname"></a>NavigateToView(entityName, viewName)
在主机模型驱动窗体中导航到视图。  
* **entityName** - 指定视图的父实体的必需字符串参数。  
* **viewName** - 指定要导航到的主窗体名称的必需字符串参数。  
 
调用 NavigateToView 方法可能显示以下错误消息。
  
| 错误消息 | 疑难解答指南 |
|:--------------|:-------------------------|
|**找不到实体：*[EntityName]*** | 请检查 *entityName* 参数的值并确保它是有效的实体名称，以及用户有权访问它。 |
|**找不到视图：*[ViewName]*** | 请检查 *viewName* 参数的值并确保它是有效的视图名称，以及用户有权访问它。 |
  
  
### <a name="openquickcreateformentityname"></a>OpenQuickCreateForm(entityName)  
打开实体的默认快速创建窗体。  
* **entityName** - 指定快速创建窗体的父实体的必需字符串参数。  
 
调用 OpenQuickCreateForm 方法可能显示以下错误消息。
  
| 错误消息 | 疑难解答指南 |
|:--------------|:-------------------------|
|**找不到实体：*[EntityName]*** | 请检查 *entityName* 参数的值并确保它是有效的实体名称，以及用户有权访问它。 |
  
  
### <a name="refreshformshowprompt"></a>RefreshForm(showPrompt)  
刷新主机模型驱动窗体上的数据。  
* **showPrompt** - 必需的布尔参数，指示是否应在保存主机模型驱动窗体上的任何未保存数据前向用户显示确认提示。 值应为“true”或“false”。
 
调用 RefreshForm 方法可能显示以下错误消息。
  
| 错误消息 | 疑难解答指南 |
|:--------------|:-------------------------|
|**请使用“true”或“false”作为参数值。** | 请检查 *showPrompt* 参数的值并确保它为“true”或“false”。 |
  
  
### <a name="saveform"></a>SaveForm()  
保存主机模型驱动窗体上的数据。  


> [!NOTE]
> 如果您在功能变为可用之前创建的嵌入区域应用中未看到用于执行预定义操作的方法的 IntelliSense；保存、关闭并重新打开应用。 

## <a name="see-also"></a>另请参阅
[在模型驱动的窗体上嵌入区域应用](embed-canvas-app-in-form.md) <br />
[在模型驱动窗体上添加嵌入式区域应用](embedded-canvas-app-add-classic-designer.md) <br />
[编辑在模型驱动窗体上嵌入的区域应用](embedded-canvas-app-edit-classic-designer.md) <br />
[自定义在模型驱动窗体上嵌入的区域应用的屏幕尺寸和方向](embedded-canvas-app-customize-screen.md) <br />
[ModelDrivenFormIntegration 控件的属性和操作](embedded-canvas-app-properties-actions.md) <br />
[共享嵌入式区域应用](share-embedded-canvas-app.md) <br />
[嵌入式区域应用使用指南](embedded-canvas-app-guidelines.md) <br />
[迁移使用最新的公共预览版本创建的模型驱动窗体上的嵌入式区域应用](embedded-canvas-app-migrate-from-preview.md) <br />
