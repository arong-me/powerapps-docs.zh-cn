---
title: "成 Web API 自定义连接器 | Microsoft 文档"
description: "了解如何在 PowerApps 中创建启用了 Azure Active Directory 身份验证的 ASP.NET Web API。"
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
ms.date: 10/26/2016
ms.author: mblythe
ms.openlocfilehash: 4fc9fb1d183ec910d37383be6629aaa67cf3723d
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2018
---
# <a name="build-a-custom-connector-for-a-web-api-in-powerapps"></a>在 PowerApps 中生成 Web API 自定义连接器
本教程介绍了如何开始生成 ASP.NET Web API，在 Azure Web 应用上托管它，启用 Azure Active Directory 身份验证，然后在 PowerApps 中注册 ASP.NET Web API。 注册 API 后，便可以连接它，并在应用中调用它。

## <a name="prerequisites"></a>先决条件
* [Azure 订阅](https://azure.microsoft.com/en-us/free/)。
* [PowerApps 帐户](https://powerapps.microsoft.com)。
* [Visual Studio](https://www.visualstudio.com/vs/) 2013 或更高版本。

## <a name="create-an-aspnet-web-api-and-deploy-it-to-azure"></a>创建 ASP.NET Web API 并将其部署到 Azure
1. 在 Visual Studio 中，依次单击“文件” > “新建项目”，创建新的 C# ASP.NET Web 应用。
   
    ![新建 Web 应用](./media/customapi-web-api-tutorial/newwebapp.png)
2. 选择“Web API”模板。  保持选中“在云中托管”不变。  单击“更改身份验证”。
   
    ![新建 Web 项目的模板](./media/customapi-web-api-tutorial/new-web-api.png)
3. 选中“无身份验证”，然后单击“确定”。
   
    ![无身份验证](./media/customapi-web-api-tutorial/noauth.png)
4. 单击“新建 ASP.NET 项目”对话框中的“确定”。  此时，“配置 Microsoft Azure Web 应用”对话框显示。
   
    ![配置 Microsoft Azure Web 应用](./media/customapi-web-api-tutorial/azure-publishing.png)]
   
    选择你的 Azure 帐户，键入 **Web 应用名称**（或保留默认名称），然后选择你的 Azure **订阅**。  选择或创建**应用服务计划**（订阅中的 Web 应用集合）。  选择或创建一个**资源组**（订阅中的 Azure 资源分组）。  选择应在其中部署 Web 应用的区域。  如果 Web API 需要，请选择或创建一个 Azure **数据库服务器**。  最后，单击“确定”。
5. 生成 Web API。
   
    > [!NOTE]
> 如果尚无可用的 Web API 代码，请尝试学习教程 [ASP.NET Web API 2 (C#) 入门](http://www.asp.net/web-api/overview/getting-started-with-aspnet-web-api/tutorial-your-first-web-api)。
6. 若要连接 Web API 和 PowerApps，我们需要使用描述 API 操作的 [OpenAPI](http://swagger.io/) 文件。  可以使用[联机编辑器](http://editor.swagger.io/)编写你自己的 OpenAPI 文件，但在本教程中，将使用名为 [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle/blob/master/README.md) 的开放源代码工具。  依次单击“工具” > “NuGet 包管理器” > “包管理器控制台”，然后在包管理器控制台中键入命令“`Install-Package Swashbuckle`”，从而在 Visual Studio 项目中安装 Swashbuckle Nuget 包。
   
    ![Install-Package Swashbuckle](./media/customapi-web-api-tutorial/swashbuckle-console.png)
   
    > [!TIP]
> 现在，如果在安装 Swashbuckle 后运行 Web API 应用，可以在 URL `http://<your root URL>/swagger/docs/v1` 处生成 OpenAPI 文件。  `http://<your root URL>/swagger` 处还生成了一个用户界面。
7. 当 Web API 就绪时，将其发布到 Azure。 若要从 Visual Studio 发布，请右键单击解决方案资源管理器中的 Web 项目，单击“发布...”，然后按“发布”对话框中的提示操作。
8. 转到 `https://<azure-webapp-url>/swagger/docs/v1` 检索 OpenAPI JSON。  将内容另存为 JSON 文件。  可能需要将文本复制并粘贴到空的文本文件中，具体视浏览器而定。   
   
    > [!IMPORTANT]
> 包含重复操作 ID 的 OpenAPI 文档无效。 如果使用的是示例 C# 模板，操作 ID `Values_Get` 就会重复两次。 若要修复此问题，可以将一个实例更改为 `Value_Get`，然后重新发布。 也可以从本教程中下载[示例 OpenAPI 文件](http://pwrappssamples.blob.core.windows.net/samples/webAPI.json)。 请务必先删除注释（以 `//` 开头），然后再使用。

## <a name="set-up-azure-active-directory-authentication"></a>设置 Azure Active Directory 身份验证
现在，将在 Azure 中创建两个 Azure Active Directory (AAD) 应用。  有关如何执行此操作的示例，请参阅 [Azure 资源管理器教程](customapi-azure-resource-manager-tutorial.md#enable-authentication-in-azure-active-directory)。

> [!IMPORTANT]
> 两个应用必须位于同一目录中。

### <a name="first-aad-application-securing-the-web-api"></a>第一个 AAD 应用：保护 Web API 安全
第一个 AAD 应用可用于保护 Web API 安全。 将此应用命名为“webAPI”。  按照上面链接的教程步骤（即“在 Azure Active Directory 中启用身份验证”部分下的步骤）操作，使用的值如下：

* 登录 URL：`https://login.windows.net`
* 答复 URL：`https://<your-root-url>/.auth/login/aad/callback`
* 无需使用客户端密钥。
* 无需委托任何权限。

> [!IMPORTANT]
> 请记下应用 ID。  稍后将需要使用。

### <a name="second-aad-application-securing-the-custom-connector-and-delegated-access"></a>第二个 AAD 应用：保护自定义连接器并获取委托访问权限
第二个 AAD 应用可用于保护注册的自定义连接器，并获取对第一个应用保护的 Web API 的委托访问权限。 将此应用命名为“webAPI-customAPI”。

* 登录 URL：`https://login.windows.net`
* 答复 URL：`https://msmanaged-na.consent.azure-apim.net/redirect`
* 添加对 Web API 的委托访问权限。
* 由于稍后将需要使用此应用的应用 ID，因此请记下。
* 生成客户端密钥，并存储在安全位置。 稍后将需要使用此密钥。

## <a name="add-authentication-to-your-azure-web-app"></a>向 Azure Web 应用添加身份验证

1. 登录 [Azure 门户](https://portal.azure.com)，然后找到在第一部分中部署的 Web 应用。

2. 单击“设置”，然后选择“身份验证/授权”。

3. 启用“应用服务身份验证”，然后选择“Azure Active Directory”。  选择下一个边栏选项卡上的“快速”。  

4. 单击“选择现有 AD 应用”，然后选择之前创建的“webAPI”AAD 应用。

现在应能够使用 AAD 对 Web 应用进行身份验证。

## <a name="add-the-custom-connector-to-powerapps"></a>将自定义连接器添加到 PowerApps
1. 将 OpenAPI 文件修改为添加 `securityDefintions` 对象和用于 Web 应用的 AAD 身份验证。 包含“host”属性的 OpenAPI 文件部分应如下所示：

    ```javascript
    // File header should be above here...

    "host": "<your-root-url>",
    "schemes": [
        "https"         //Make sure this is https!
    ],
    "securityDefinitions": {
        "AAD": {
            "type": "oauth2",
            "flow": "implicit",
            "authorizationUrl": "https://login.windows.net/common/oauth2/authorize",
            "scopes": {}
        }
    },

    // The rest of the OpenAPI document follows...
    ```

2. 转到 [PowerApps](https://web.powerapps.com)，然后添加自定义连接器，如[在 PowerApps 中注册并使用自定义连接器](register-custom-api.md)中所述。

3. 上载 OpenAPI 文件后，向导便会立即自动检测你是否在对 Web API 使用 AAD 身份验证。

4. 为自定义连接器配置 AAD 身份验证。  
   
   * 客户端 ID：*webAPI-CustomAPI 的客户端 ID*
   * 密码：*webAPI-CustomAPI 的客户端密钥*
   * 登录 URL：`https://login.windows.net`
   * 资源 URI：*webAPI 的客户端 ID*
5. 单击“创建”，建立与自定义连接器的连接。

## <a name="next-steps"></a>后续步骤
了解 [Azure 资源管理器自定义连接器教程](customapi-azure-resource-manager-tutorial.md)。

