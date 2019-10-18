---
title: 获取 PowerApps 组件框架的工具 |Microsoft Docs
description: 获取 Microsoft PowerApps CLI，使用 PowerApps 组件框架创建、调试和部署代码组件。
keywords: PowerApps 组件框架，代码组件，组件框架
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
ms.openlocfilehash: 496b7d443775da075dd8da52ac4b0a754121bf28
ms.sourcegitcommit: 4c35aedde46380d5438687ae6f61a3b0cc7e7e2f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2019
ms.locfileid: "72340014"
---
# <a name="get-tooling-for-powerapps-component-framework"></a>获取 PowerApps 组件框架的工具

使用**MICROSOFT POWERAPPS CLI** （命令行接口）通过 PowerApps 组件框架创建、调试和部署代码组件。 PowerApps CLI 使开发人员可以快速创建代码组件。 将来，会将其扩展为包含对其他开发和应用程序生命周期管理（ALM）体验的支持。 

## <a name="what-is-microsoft-powerapps-cli"></a>什么是 Microsoft PowerApps CLI 

Microsoft PowerApps CLI 是一个简单的、单一停止开发人员命令行界面，使开发人员和应用程序开发人员能够创建代码组件。 PowerApps CLI 工具是一个全面的 ALM 故事的第一步，其中企业开发人员和 Isv 可以快速高效地创建、构建、调试和发布其扩展和自定义内容。  

## <a name="install-microsoft-powerapps-cli"></a>安装 Microsoft PowerApps CLI

若要获取 Microsoft PowerApps CLI，请执行以下操作：

1. 安装[Npm](https://www.npmjs.com/get-npm) （随附于 node.js [）或 node.js](https://nodejs.org/en/) （附带 Npm）。 建议 LTS （长期支持）版本 10.15.3 LTS，因为它看起来最稳定。

1. 安装[.NET Framework 4.6.2 开发人员工具包](https://dotnet.microsoft.com/download/dotnet-framework/net462)。 

1. 如果尚未安装 Visual Studio 2017 或更高版本，请遵循以下选项之一：
   - 选项1：安装[Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017)或更高版本。
   - 选项2：安装[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) ，然后安装[Visual Studio Code](https://code.visualstudio.com/Download)。

1. 安装[MICROSOFT POWERAPPS CLI](https://aka.ms/PowerAppsCLI)。
1. 若要利用所有最新功能，请使用以下命令将 PowerApps CLI 工具更新到最新版本：

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - 若要使用 PowerApps CLI 部署代码组件，必须具有具有系统管理员或系统定制员权限的 Common Data Service 环境。
> - 目前，PowerApps CLI 仅在 Windows 10 上受支持。

## <a name="microsoft-powerapps-cli-telemetry"></a>Microsoft PowerApps CLI 遥测

功能团队正在聚合遥测，以了解 PowerApps CLI 工具中最常使用的开发人员功能。 聚合数据使我们能够将重点放在重要的基础上，为客户提供最佳体验。

> [!NOTE]
> 若要禁用遥测集合，请运行命令 `pac telemetry disable`。 若要重新打开遥测数据，请使用命令 `pac telemetry enable`。


## <a name="uninstall-microsoft-powerapps-cli"></a>卸载 Microsoft PowerApps CLI

若要卸载 PowerApps CLI 工具，请从[此处](https://aka.ms/PowerAppsCLI)运行 MSI。 

如果你是个人预览版参与者并具有较早版本的 CLI，请执行以下步骤：

1. 若要了解 PowerApps CLI 的安装位置，请打开命令提示符并键入 `where pac`。
1. 删除 PowerAppsCLI 文件夹。
1. 通过在命令提示符下运行命令 `rundll32 sysdm.cpl,EditEnvironmentVariables` 打开环境变量工具。
1. 双击 `User variable for...` 部分下的 `Path`。
1. 选择包含 PowerAppsCLI 路径的行，然后选择右侧的 "**删除**" 按钮。
1. 选择 **"确定"** 两次。

### <a name="see-also"></a>另请参阅

[使用 TypeScript 实现组件](implementing-controls-using-typescript.md)<br/>
