---
title: 嵌入式区域应用使用指南 | MicrosoftDocs
ms.custom: ''
ms.date: 08/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
author: RichdiMSFT
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1b74b1a9e7cd86240d361fadd2590a704f707176
ms.sourcegitcommit: 564b939577aae9fbedb2186bea3d4740d32e7473
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2020
ms.locfileid: "3043572"
---
# <a name="guidelines-on-working-with-embedded-canvas-apps"></a>嵌入式区域应用使用指南
本主题提供有关使用嵌入式区域应用的指南，以及有助于诊断可能遇到的任何问题的提示。

-   只有统一接口模型驱动的应用才支持嵌入式区域应用。
-   只能在每个窗体上启用一个嵌入式区域应用。 
     - 可以向窗体添加多个嵌入式区域应用，但是一次只能启用一个。
     - 如果尝试在一个模型驱动的窗体上启用多个嵌入式区域应用，将显示消息“一个窗体中只能启用一个区域应用程序。”
     - 若要启用或禁用嵌入式区域应用，请参阅[启用嵌入式区域应用](#enable-an-embedded-canvas-app)和[禁用嵌入式区域应用](#disable-an-embedded-canvas-app)。
-   向模型驱动的窗体添加嵌入式区域应用时，请始终使用一定有值的必填字段。 如果字段无值，则不会刷新嵌入式区域应用来响应主机模型驱动的窗体上的任何数据变化。
-   发布模型驱动的窗体也不会发布嵌入式区域应用。
     - 嵌入式区域应用需要独立于主机模型驱动的窗体发布。 详细信息：[发布应用](../canvas-apps/save-publish-app.md#publish-an-app)。
-   如果 Web 浏览器弹出窗口阻止程序已锁定通过区域应用控件属性中的**自定义**按钮打开 Power Apps Studio 创建或编辑嵌入式区域应用，则必须启用 make.powerapps.com 站点或暂时禁用该弹出窗口阻止程序，然后再次选择**自定义**。
-   创建新记录时不显示嵌入式区域应用，因为需要向其传递记录上下文。
-   ModelDrivenFormIntegration.Item 对象为只读对象。 
     - 若要回写数据，必须使用 Common Data Service 连接器。 更多信息：[Common Data Service](/connectors/commondataservice/)
-   只能通过主机模型驱动的窗体创建嵌入式区域应用。 
    - 在模型驱动窗体上作为嵌入式应用添加现有的区域应用当前不受支持。
    - 使用应用 ID 在模型驱动窗体中嵌入现有区域应用的支持将在以后的更新中提供。
- 使用嵌入式区域应用查看模型驱动的窗体时，如果显示错误消息“抱歉，找不到该应用”，请确保嵌入式区域应用与模型驱动的窗体在同一个解决方案中。
- 使用嵌入式区域应用查看模型驱动的窗体时，如果显示错误消息“您似乎无权访问此应用。 请让其其负责人为您共享”，则请确保作者已与您共享了此嵌入式区域应用。 详细信息：[共享嵌入式区域应用](share-embedded-canvas-app.md)。
- 在子网格控件上添加区域应用不再可用。
    - 在预览版中，开发者能够在子网格控件上添加区域应用。 现在，可以将区域应用嵌入在模型驱动的窗体中，将在模型驱动窗体上添加嵌入式区域应用简化到字段。 
    - 这使开发者更轻松，因为他们不必事先决定是作为数据上下文传递当前（主窗体）记录还是传递与当前（主窗体）记录相关的记录列表。 
    - 开发者总是从一个字段开始，可以访问当前（主窗体）记录或与当前（主窗体）记录相关的记录列表。
    - 要访问区域应用中的相关记录列表，开发者可以将 Common Data Service 连接器和[筛选器](../canvas-apps/functions/function-filter-lookup.md)功能与区域应用中启用的[改进数据源体验和 Common Data Service 视图](https://powerapps.microsoft.com/blog/improved-data-source-selection-and-common-data-service-views/)功能结合使用。  
    例如，要访问*联系人*实体的*可用联系人*视图，开发者可以使用 *Filter(Contacts, 'Contacts (Views)'.'Active Contacts')*。
    - 使用子网格控件的现有区域应用将继续运行。 但是，我们建议您迁移这些应用来改用字段。 详细信息：请参阅[迁移使用与当前（主窗体）记录相关的记录列表的模型驱动窗体上的嵌入式区域应用](embedded-canvas-app-migrate-from-preview.md#migrating-embedded-canvas-apps-on-model-driven-forms-that-use-a-list-of-records-related-to-the-current-main-form-record)了解详细信息。

## <a name="enable-an-embedded-canvas-app"></a>启用嵌入式区域应用
1. 选择自定义为显示为嵌入式区域应用的字段。
2. 在**字段属性**对话框中，选择**控件**选项卡。
3. 在控件列表中，选择**区域应用**，然后选择 **Web** 选项。
4. 选择**确定**。

## <a name="disable-an-embedded-canvas-app"></a>禁用嵌入式区域应用
1. 选择自定义为显示为嵌入式区域应用的字段。
2. 在**字段属性**对话框中，选择**控件**选项卡。
3. 在控件列表中，选择默认控件，然后选择 **Web** 选项。
4. 选择**确定**。

## <a name="known-issues-and-limitations-with-embedded-canvas-apps"></a>嵌入式区域应用的已知问题和限制
- 只有 **Web** 客户端类型才支持使用区域应用自定义控件。 目前不支持**手机**和**平板电脑**客户端类型。
- ModelDrivenFormIntegration 控件不为相关实体的字段提供值。 
  - 例如，当 ModelDrivenFormIntegration 控件连接到“客户”实体时，使用 *ModelDrivenFormIntegration.Item.’Primary Contact’.’Full Name’* 将不会返回值。 
  - 要访问相关实体的字段，开发者可以使用此处列出的两种表达式之一：
    - *LookUp(Accounts, Account = GUID(First(ModelDrivenFormIntegration.Data).ItemId)).'Primary Contact'.'Full Name'*  
      - *ItemId* 在创作时为空，但在运行时将具有值。
    - *LookUp(Accounts, Account = ModelDrivenFormIntegration.Item.Account).'Primary Contact'.'Full Name'*（此表达式更易于读取，但前一个表达式的效果会稍好一些。）
- 不能使用安全角色中的**区域应用**权限为应用用户授予嵌入式或单机区域应用的访问权限。 有关共享嵌入式区域应用的详细信息，请参阅：[共享嵌入式区域应用](share-embedded-canvas-app.md)。
- 如果回写正在主机模型驱动的窗体中显示的相同数据，窗体将继续显示原来的数据，直到刷新。 这样做的简单方法是使用 [RefreshForm](embedded-canvas-app-actions.md#refreshformshowprompt) 方法。

## <a name="see-also"></a>另请参阅
[在模型驱动的窗体上嵌入区域应用](embed-canvas-app-in-form.md) <br />
[在模型驱动窗体上添加嵌入式区域应用](embedded-canvas-app-add-classic-designer.md) <br />
[编辑在模型驱动窗体上嵌入的区域应用](embedded-canvas-app-edit-classic-designer.md) <br />
[自定义在模型驱动窗体上嵌入的区域应用的屏幕尺寸和方向](embedded-canvas-app-customize-screen.md) <br />
[从嵌入的区域应用内在主机窗体上执行预定义操作](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegration 控件的属性和操作](embedded-canvas-app-properties-actions.md) <br />
[共享嵌入式区域应用](share-embedded-canvas-app.md) <br />
[迁移使用最新的公共预览版本创建的模型驱动窗体上的嵌入式区域应用](embedded-canvas-app-migrate-from-preview.md) <br />
