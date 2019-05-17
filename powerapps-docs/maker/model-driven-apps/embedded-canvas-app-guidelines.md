---
title: 嵌入式区域应用使用指南 | MicrosoftDocs
ms.custom: ''
ms.date: 01/07/2019
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
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="guidelines-on-working-with-embedded-canvas-apps"></a>嵌入式区域应用使用指南
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

本主题提供有关使用嵌入式区域应用的指南，以及有助于诊断可能遇到的任何问题的提示。

-   只有统一接口模型驱动的应用才支持嵌入式区域应用。
-   只能在每个窗体上启用一个嵌入式区域应用。 
     - 可以向窗体添加多个嵌入式区域应用，但是一次只能启用一个。
     - 如果尝试在一个模型驱动的窗体上启用多个嵌入式区域应用，将显示消息“一个窗体中只能启用一个区域应用程序。”
     - 若要启用或禁用嵌入式区域应用，请参阅[启用嵌入式区域应用](#enable-an-embedded-canvas-app)和[禁用嵌入式区域应用](#disable-an-embedded-canvas-app)。
-   只能通过主机模型驱动的窗体创建、编辑和使用嵌入式区域应用。
     - 不能直接在模型驱动的窗体上下文外部创建嵌入式区域应用。
     - 同样，不支持在模型驱动的窗体上下文外部打开嵌入式区域应用进行编辑或使用。

     > [!NOTE]
     > 尽管可能可以在模型驱动的应用外部打开嵌入式区域应用，但是不支持这样的行为。

-   使用子网格控件向模型驱动的窗体添加嵌入式区域应用时，请注意以下事项。
     - 运行时发送到嵌入式区域应用的数据（字段和值）由子网格控件属性的**数据源**部分中指定为**默认值**的视图决定。 如果需要，请仅使用视图中包含的嵌入式区域应用内的字段或将其添加到视图。 视图中不包含的所有字段都将在运行时显示为空值。 
     - 创作期间不使用视图的筛选条件。 因此，不会筛选创作嵌入式区域应用时显示的数据，这些数据只是您可访问的前面一些记录的列表。 运行时将按照预期应用视图的筛选条件，并且仅显示相关数据。
-   使用字段控件向模型驱动的窗体添加嵌入式区域应用时，请始终使用一定有值的必填字段。 如果字段无值，则不会刷新嵌入式区域应用来响应主机模型驱动的窗体上的任何数据变化。
-   发布模型驱动的窗体也不会发布嵌入式区域应用。
     - 嵌入式区域应用需要独立于主机模型驱动的窗体发布。 详细信息：[发布应用](../canvas-apps/save-publish-app.md#publish-an-app)。
-   如果 Web 浏览器弹出窗口阻止程序已锁定通过区域应用控件属性中的**自定义**按钮打开 PowerApps Studio 创建或编辑嵌入式区域应用，则必须启用 web.powerapps.com 站点或暂时禁用该弹出窗口阻止程序，然后再次选择**自定义**。
-   创建新记录时不显示嵌入式区域应用，因为需要向其传递记录上下文。
-   ModelDrivenFormIntegration.Data 对象为只读对象。 
     - 若要回写数据，必须使用 Common Data Service 连接器。 详细信息：[Common Data Service](/connectors/commondataservice/)
-   ModelDrivenFormIntegration.Data 对象是一列记录。 
     - 即使当前记录作为仅包含一个记录的列表通过 ModelDrivenFormIntegration.Data 传递到嵌入式区域应用也是如此。
     - 若要直接引用记录，可使用 [First 函数](../canvas-apps/functions/function-first-last.md)。 示例：First(ModelDrivenFormIntegration.Data).Name
-   请尽量避免手动更改区域应用控件属性中的应用 ID。
     - 将自动为您生成和填写区域应用的应用 ID。 
     - 如果出于某个原因的确需要手动编辑，则需确保所用任何应用 ID 与*嵌入式*区域应用对象，而不是与单机区域应用对应。 
     - 创建嵌入式区域应用的数据上下文必须也是要发送模型驱动的窗体的数据上下文。
     - 更新应用 ID 之后，选择**自定义**在 PowerApps Studio 中打开它并建立与新应用之间的连接。
     - 在应用中进行小更改将其进入未保存状态，然后保存并发布应用。
- 使用嵌入式区域应用查看模型驱动的窗体时，如果显示错误消息“抱歉，找不到该应用”，请确保嵌入式区域应用与模型驱动的窗体在同一个解决方案中。
- 使用嵌入式区域应用查看模型驱动的窗体时，如果显示错误消息“您似乎无权访问此应用。 请让其其负责人为您共享”，则请确保作者已与您共享了此嵌入式区域应用。 详细信息：[共享嵌入式区域应用](share-embedded-canvas-app.md)。

## <a name="enable-an-embedded-canvas-app"></a>启用嵌入式区域应用
1. 选择自定义为显示为嵌入式区域应用的字段或子网格控件。
2. 在**字段属性**（如果选择子网格则为**设置属性**）对话框中，选择**控件**选项卡。
3. 在控件列表中，选择**区域应用**，然后选择 **Web** 选项。
4. 选择**确定**。

## <a name="disable-an-embedded-canvas-app"></a>禁用嵌入式区域应用
1. 选择自定义为显示为嵌入式区域应用的字段或子网格控件。
2. 在**字段属性**（如果选择子网格则为**设置属性**）对话框中，选择**控件**选项卡。
3. 在控件列表中，选择默认控件，然后选择 **Web** 选项。
4. 选择**确定**。

## <a name="known-issues-and-limitations-with-embedded-canvas-apps"></a>嵌入式区域应用的已知问题和限制
- 只有 **Web** 客户端类型才支持使用区域应用自定义控件。 目前不支持**手机**和**平板电脑**客户端类型。 详细信息：[使用自定义控件实现模型驱动应用程序的数据可视化](use-custom-controls-data-visualizations.md)
- 创建新记录时，即使在保存了记录之后，也不显示窗体上的嵌入式区域应用。 
-    ModelDrivenFormIntegration.Data 对象目前不支持“显示窗体”和“编辑窗体”控件。
- 不能使用安全角色中的**区域应用**权限为应用用户授予嵌入式或单机区域应用的访问权限。 有关共享嵌入式区域应用的详细信息，请参阅：[共享嵌入式区域应用](share-embedded-canvas-app.md)。
- 如果回写正在主机模型驱动的窗体中显示的相同数据，窗体将继续显示原来的数据，直到刷新。 这样做的简单方法是使用 [RefreshForm](embedded-canvas-app-actions.md) 方法。
- 如果您在功能变为可用之前创建的嵌入区域应用中未看到[用于执行预定义操作的方法](embedded-canvas-app-actions.md)的 IntelliSense；保存、关闭并重新打开应用。 

## <a name="see-also"></a>另请参阅
[在模型驱动的窗体中嵌入区域应用](embed-canvas-app-in-form.md) <br />
[将当前记录作为数据上下文传递到嵌入式区域应用](pass-current-embedded-canvas-app.md) <br />
[将一列相关记录作为数据上下文传递到嵌入式区域应用](pass-related-embedded-canvas-app.md) <br />
[从嵌入的区域应用内在主机窗体上执行预定义操作](embedded-canvas-app-actions.md) <br />
[共享嵌入式区域应用](share-embedded-canvas-app.md)
