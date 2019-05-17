---
title: 共享嵌入式区域应用 | MicrosoftDocs
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

# <a name="share-an-embedded-canvas-app"></a>共享嵌入式区域应用
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

本主题说明如何共享已创建的嵌入式区域应用。

在创建并向模型驱动窗体添加了嵌入式区域应用后，您需要采取步骤以确保可以访问模型驱动窗体的所有用户还可以访问区域应用及其使用的数据。 请参阅以下指南：
-   与您组织中的每个人或安全组或特定用户共享您的嵌入式区域应用。 详细信息：[共享应用](../canvas-apps/share-app.md#share-an-app)
-   确保用户具有嵌入式区域应用使用的任何 Common Data Service 实体的相应权限。 详细信息：[管理实体权限](../canvas-apps/share-app.md#manage-entity-permissions)
-   确保用户具有嵌入式区域应用使用的任何云服务（如 SharePoint 或 OneDrive）上数据的相应权限。 共享步骤特定于每个云服务，超出 PowerApps 的范围。

> [!NOTE]
> 目前，不能使用安全角色中的**区域应用**权限为应用用户授予嵌入式或单机区域应用的访问权限。

解决方案也可以识别嵌入式区域应用。 默认情况下，嵌入式区域应用在与主机模型驱动窗体相同的解决方案中创建。 若要将嵌入式区域应用从一个环境移至另一个环境，与任何其他组件一样，将嵌入式区域应用作为解决方案的一部分导出和导入。

## <a name="see-also"></a>另请参阅
[在模型驱动的窗体中嵌入区域应用](embed-canvas-app-in-form.md) <br />
[将当前记录作为数据上下文传递到嵌入式区域应用](pass-current-embedded-canvas-app.md) <br />
[将一列相关记录作为数据上下文传递到嵌入式区域应用](pass-related-embedded-canvas-app.md) <br />
[从嵌入的区域应用内在主机窗体上执行预定义操作](embedded-canvas-app-actions.md) <br />
[嵌入式区域应用使用指南](embedded-canvas-app-guidelines.md)
