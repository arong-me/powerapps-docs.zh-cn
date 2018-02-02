---
title: "将 Azure Active Directory 用于自定义连接器 | Microsoft 文档"
description: "了解如何使用 Azure Active Directory 身份验证为 Azure 资源管理器创建自定义连接器。"
services: 
suite: powerapps
documentationcenter: 
author: mgblythe
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/03/2017
ms.author: mblythe
ms.openlocfilehash: b3df99a335947b0472b9230090e6a49fcea0f799
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2018
---
# <a name="use-azure-active-directory-with-a-custom-connector-in-powerapps"></a>在 PowerApps 中将 Azure Active Directory 用于自定义连接器
可以通过 Azure 资源管理器 (ARM) 在 Azure 上管理解决方案的组件，例如数据库、虚拟机和 Web 应用。 本教程介绍了如何启用 Azure Active Directory 身份验证，将一个 ARM API 注册为自定义连接器，然后在 PowerApps 中连接它。 如果要直接在应用中管理 Azure 资源，这就十分有用。 有关 ARM 的详细信息，请参阅 [Azure 资源管理器概述](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)。

## <a name="prerequisites"></a>先决条件
* [Azure 订阅](https://azure.microsoft.com/free/)。
* [PowerApps 帐户](https://powerapps.microsoft.com)。
* 本教程使用的[示例 OpenAPI 文件](http://pwrappssamples.blob.core.windows.net/samples/AzureResourceManager.json)。

## <a name="enable-authentication-in-azure-active-directory"></a>在 Azure Active Directory 中启用身份验证
首先，我们需要创建一个 Azure Active Directory (AAD) 应用，用于在调用 ARM API 终结点时执行身份验证。

1. 登录 [Azure 门户](https://portal.azure.com)。  如果有多个 Azure Active Directory 租户，请查看右上角的用户名，以确保登录的是正确目录。
   
    ![用户名](./media/customapi-azure-resource-manager-tutorial/current-user.png)
2. 单击左侧菜单上的“更多服务”。  在“筛选器”文本框中，键入“Azure Active Directory”，然后单击“Azure Active Directory”。
   
    ![Azure Active Directory](./media/customapi-azure-resource-manager-tutorial/azureaad.png)
   
    此时，“Azure Active Directory”边栏选项卡会打开。   
3. 在“Azure Active Directory”边栏选项卡上的菜单中，单击“应用注册”。
   
    ![应用注册](./media/customapi-azure-resource-manager-tutorial/azureapplication.png)
4. 在已注册应用的列表中，单击“添加”。
   
    ![“添加”按钮](./media/customapi-azure-resource-manager-tutorial/add-app-btn.png)   
5. 键入应用名称，保持选择“Web 应用/API”不变，然后键入 `https://login.windows.net` 作为“登录 URL”。  单击“创建”。  
   
    ![新建应用的窗体](./media/customapi-azure-resource-manager-tutorial/newapplication.png)
6. 单击列表中的新应用。
   
    ![列表中的新应用](./media/customapi-azure-resource-manager-tutorial/newapplication2.png)
   
    此时，“已注册应用”边栏选项卡会打开。  记下“应用 ID”。  稍后将需要使用。
7. “设置”边栏选项卡应该也会打开。  如果没有，请单击“设置”按钮。
   
    ![“设置”按钮](./media/customapi-azure-resource-manager-tutorial/settings-btn.png)
8. 单击“设置”边栏选项卡中的“答复 URL”。 在 URL 列表中，添加 `https://msmanaged-na.consent.azure-apim.net/redirect`，然后单击“保存”。
   
    ![答复 URL](./media/customapi-azure-resource-manager-tutorial/reply-urls.png)
9. 返回到“设置”边栏选项卡，然后单击“所需权限”。  单击“所需权限”边栏选项卡中的“添加”。
   
    ![所需权限](./media/customapi-azure-resource-manager-tutorial/permissions.png)
   
    此时，“添加 API 访问权限”边栏选项卡会打开。
10. 单击“选择 API”。 在打开的边栏选项卡中，依次单击“Azure 服务管理 API”选项和“选择”。
    
    ![选择 API](./media/customapi-azure-resource-manager-tutorial/permissions2.png)
11. 单击“选择权限”。  在“委托的权限”下，依次单击“以组织用户的身份访问 Azure 服务管理”和“选择”。
    
    ![委托的权限](./media/customapi-azure-resource-manager-tutorial/permissions3.png)
12. 单击“添加 API 访问权限”边栏选项卡中的“完成”。
13. 返回到“设置”边栏选项卡，单击“密钥”。  在“密钥”边栏选项卡中，键入密钥说明，选择一个有效期，然后单击“保存”。  此时，新密钥会显示。  记下密钥值，因为我们稍后还需要使用。  现在可以关闭 Azure 门户了。
    
    ![创建密钥](./media/customapi-azure-resource-manager-tutorial/configurekeys.png)

## <a name="add-the-connection-in-powerapps"></a>在 PowerApps 中添加连接
至此，我们已配置 AAD 应用，让我们来添加自定义连接器。

1. 在 [powerapps.com](https://web.powerapps.com) 的左侧菜单中，单击“连接”。 依次选择省略号（“...”）和右上角的“管理自定义连接器”。
   
     > [!TIP]
> 如果在移动浏览器中找不到自定义连接器的管理位置，可能是在左上角的菜单下方。
   
    ![创建自定义连接器](./media/customapi-azure-resource-manager-tutorial/managecustomapi.png)  
2. 选择“创建自定义连接器”。
   
    ![自定义连接器属性](./media/customapi-azure-resource-manager-tutorial/newcustomapi.png)
3. 键入连接的名称，然后上载[“示例 ARM OpenAPI 文件”](http://pwrappssamples.blob.core.windows.net/samples/AzureResourceManager.json)。  单击“继续”。  
   
    ![连接新的 API 终结点](./media/customapi-azure-resource-manager-tutorial/createcustom.png)
4. 在下一个屏幕上，由于 OpenAPI 文件使用我们的 AAD 应用进行身份验证，因此我们需要为 PowerApps 提供一些有关我们应用的信息。  在“客户端 ID”下，键入之前记下的 AAD **应用 ID**。  在“客户端密码”下，键入**密钥**。  最后，在“资源 URL”下，键入“`https://management.core.windows.net/`”。
   
    > [!IMPORTANT]
> 请务必原封不动地键入之前记下的资源 URL，其中包括尾部反斜杠。
   
    ![OAuth 设置](./media/customapi-azure-resource-manager-tutorial/oauthsettings.png)
5. 现在，自定义连接器已注册，可以在 PowerApps 或 Microsoft Flow 中使用了。
   
    ![添加的自定义连接器](./media/customapi-azure-resource-manager-tutorial/createdcustomapi.png)
   
    > [!NOTE]
> 示例 OpenAPI 未定义全套的 ARM 操作，目前只包含[列出所有订阅](https://msdn.microsoft.com/library/azure/dn790531.aspx)操作。  可以使用[联机 OpenAPI 编辑器](http://editor.swagger.io/)编辑此 OpenAPI 文件或创建另一个 OpenAPI 文件。 此过程可用于访问任何使用 AAD 进行身份验证的 RESTful API。

## <a name="next-steps"></a>后续步骤
若要详细了解如何创建应用，请参阅[在数据的基础之上创建应用](get-started-create-from-data.md)。

若要详细了解如何在应用中使用流，请参阅[在应用中启动流](using-logic-flows.md)。

若要就自定义连接器进行提问或发表评论，请[加入我们的社区](https://aka.ms/powerapps-community)。

