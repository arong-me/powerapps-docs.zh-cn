---
title: ModelDrivenFormIntegration 控件属性和操作 | MicrosoftDocs
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
---
# <a name="modeldrivenformintegration-control-properties-and-actions"></a>ModelDrivenFormIntegration 控件属性和操作
模型驱动窗体上嵌入的区域应用包含名为 **ModelDrivenFormIntegration** 的特殊控件。 此控件负责将上下文数据从主机模型驱动的窗体带入嵌入式区域应用。  

本主题介绍 ModelDrivenFormIntegration 控件上提供的属性和操作。

| 属性或操作 | 说明 |
|:--------------|:-------------------------|
|**DataSource** | 应设置为连接到主机模型驱动窗体的父实体的数据源。 <br />在[嵌入新区域应用](embedded-canvas-app-add-classic-designer.md)时自动设置。 |
|**项** | 支持嵌入式区域应用访问主机模型驱动窗体中的记录的只读属性。 <br />举例来说，要获取名称为 accountnumber 且显示名称为 Account Number 的字段的值，您可以使用 ModelDrivenFormIntegration.Item.accountnumber 或 ModelDrivenFormIntegration.Item.'Account Number'。 |
|**OnDataRefresh** | 此属性中的公式在主机模型驱动窗体保存数据时接受评估。 <br />请使用它来刷新连接到主机模型驱动窗体的父实体的数据源，并执行设置或更新变量这样的其他操作。 <br /> 举例来说，将其设置为下面的公式将刷新客户数据源，并将名为 CurrentAccountNumber 的变量设置为当前记录的客户编号字段的值。 <br /> Refresh(Accounts); Set(CurrentAccountNumber, ModelDrivenFormIntegration.Item.'Account Number') |
|**RefreshForm** | 刷新主机模型驱动窗体上的数据。 <br />请参阅[在主机窗体上执行预定义操作](embedded-canvas-app-actions.md#refreshformshowprompt)了解详细信息。 |
|**SaveForm** | 保存主机模型驱动窗体上的数据。 <br />请参阅[在主机窗体上执行预定义操作](embedded-canvas-app-actions.md#saveform)了解详细信息。  |
|**NavigateToMainForm** | 在主机模型驱动窗体上导航到主窗体并显示指定记录。 <br />请参阅[在主机窗体上执行预定义操作](embedded-canvas-app-actions.md#navigatetomainformentityname-mainformname-recordid)了解详细信息。 |
|**NavigateToView** | 在主机模型驱动窗体中导航到视图。 <br />请参阅[在主机窗体上执行预定义操作](embedded-canvas-app-actions.md#navigatetoviewentityname-viewname)了解详细信息。  |
|**OpenQuickCreateForm** | 打开实体的默认快速创建窗体。  <br />请参阅[在主机窗体上执行预定义操作](embedded-canvas-app-actions.md#openquickcreateformentityname)了解详细信息。  |
|**数据** | 框架用于将某些关键数据从主机模型驱动窗体发送到嵌入式区域应用的只读属性。  <br /> 请勿使用此属性。 使用“项目”访问主机模型驱动窗体中的记录。  |

## <a name="see-also"></a>另请参阅
[在模型驱动的窗体上嵌入区域应用](embed-canvas-app-in-form.md) <br />
[在模型驱动窗体上添加嵌入式区域应用](embedded-canvas-app-add-classic-designer.md) <br />
[编辑在模型驱动窗体上嵌入的区域应用](embedded-canvas-app-edit-classic-designer.md) <br />
[自定义在模型驱动窗体上嵌入的区域应用的屏幕尺寸和方向](embedded-canvas-app-customize-screen.md) <br />
[从嵌入的区域应用内在主机窗体上执行预定义操作](embedded-canvas-app-actions.md) <br />
[共享嵌入式区域应用](share-embedded-canvas-app.md) <br />
[嵌入式区域应用使用指南](embedded-canvas-app-guidelines.md) <br />
[迁移使用最新的公共预览版本创建的模型驱动窗体上的嵌入式区域应用](embedded-canvas-app-migrate-from-preview.md) <br />
