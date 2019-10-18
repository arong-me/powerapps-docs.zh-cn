---
title: 导入组件 |Microsoft Docs
description: 本主题介绍如何导入代码组件
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
ms.openlocfilehash: 3042202fd1790d117c2a503bd6e69eaaea15c08a
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346799"
---
# <a name="package-a-code-component"></a>打包代码组件

本主题介绍如何将代码组件导入 Common Data Service。 使用 PowerApps CLI 实现代码组件后，下一步是将所有代码组件元素捆绑到一个解决方案文件中，并将解决方案文件导入到 Common Data Service 中，以便可以在运行时查看代码组件。

若要创建和导入解决方案文件：

1. 使用命令 `mkdir Solutions` 创建新的文件夹，并为其命名**解决方案**（或所选的任何名称）。 使用命令 `cd Solutions` 导航到目录。

2. 使用命令 `pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>` 创建新的解决方案项目。 解决方案项目用于将代码组件绑定到用于导入到 Common Data Service 的解决方案 zip 文件。

   > [!NOTE]
   > @No__t_0 和 `publisher-prefix` 值必须对您的环境是唯一的。
 
3. 创建新的解决方案项目后，请将**解决方案**文件夹引用到创建的示例组件所在的位置。 可以使用如下所示的命令添加引用。 此引用将通知解决方案项目应在生成过程中添加哪些代码组件。 您可以在单个解决方案项目中添加对多个组件的引用。

   ```CLI   
    pac solution add-reference --path <path to your PowerApps component framework project>
   ```

3. 若要从解决方案项目生成 zip 文件，请进入解决方案项目目录，并使用命令 `msbuild /t:build /restore` 生成项目。 此命令通过将*NuGet*依赖项拉出作为还原的一部分来使用*MSBuild*生成解决方案项目。 仅在生成解决方案项目时首次使用 `/restore`。 对于每个版本，都可以运行命令 `msbuild`。


    > [!NOTE]
    > - 如果 msbuild 15.9. * 不在路径中，则打开 VS 2017 开发人员命令提示以运行 `msbuild` 命令。
    > - 在*调试*配置中构建解决方案生成非托管解决方案包。 托管解决方案包是通过在*发布*配置中构建解决方案生成的。 可以通过在 `cdsproj` 文件中指定 `SolutionPackageType` 属性来重写这些设置。
    > - 可以将 msbuild 配置设置为 "`Release`" 以发出生产生成。 示例： `msbuild /p:configuration=Release`
    > - 如果在解决方案上运行 `msbuild` 命令时遇到错误，指出*项目名称不明确*，请确保解决方案名称和项目名称不相同。

4. 生成成功后，生成的解决方案文件位于 `\bin\debug\` 文件夹内。
5. 使用 web 门户手动将[解决方案导入到 Common Data Service 中](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-upgrade-solution)，或参阅使用 PowerApps CLI 命令进行身份验证，以导入[到你的组织](#authenticating-to-your-organization)和[部署](#deploying-code-components)部分。

## <a name="authenticating-to-your-organization"></a>向组织进行身份验证

你可以直接从 PowerApps CLI 部署代码组件，方法是向 Common Data Service 组织进行身份验证，然后推送更新的组件。 使用以下步骤来创建身份验证配置文件、连接到 Common Data Service 并推送已更新的组件。 
 
1. 使用以下命令创建身份验证配置文件： 
 
    ```CLI
    pac auth create --url <your Common Data Service org’s url> 
    ```
 
2. 如果你以前创建了一个身份验证配置文件，则可以使用以下命令查看所有现有配置文件： 

   ```CLI
    pac auth list 
   ```
 
3. 若要在前面创建的身份验证配置文件之间进行切换，请使用以下命令： 
   
   ```CLI
    Pac auth select --index <index of the active profile>
    ``` 

4. 若要获取有关组织的基本信息，请使用以下命令。 将使用默认身份验证配置文件建立连接。 

    ```CLI
    pac org who 
    ```
 
5. 若要删除特定身份验证配置文件，请使用命令 `pac auth delete --index < index of the profile >`。 
6. 如果要从本地计算机中清除所有身份验证配置文件，请使用命令 `pac auth clear`。 此操作是不可逆的，因为它将从本地计算机中完全删除 `authprofile.json` 文件和令牌缓存文件。 

## <a name="deploying-code-components"></a>部署代码组件 

成功创建身份验证配置文件后，可以开始使用所有最新更改将代码组件推送到 Common Data Service 实例。 @No__t_0 功能可以加快内部开发人员周期开发，因为它会绕过代码组件版本控制要求，并且不需要您生成解决方案（cdsproj）来导入代码组件。 若要使用 `push` 功能，请执行以下操作：

1. 确保已创建有效的身份验证配置文件。
2. 导航到在其中创建代码组件项目的根目录。
3. 运行 `pac pcf push --publisher-prefix <your publisher prefix>` 命令。

   > [!NOTE]
   > 与 `push` 命令一起使用的发布服务器前缀应与将在其中包含组件的解决方案的发布者前缀匹配。

## <a name="how-to-remove-components-from-a-solution"></a>如何从解决方案中删除组件

如果要从解决方案文件中删除代码组件：

1.  编辑解决方案项目目录中的 `cdsproj` 文件，并删除对该组件的引用。 下面是组件引用的一个示例：

   ```XML
   <ItemGroup>
       <Projectreference Include="..\pcf_component\pcf_component.pcfproj">
         <Project>0481bd83-ffb0-4b70-b526-e0b3dd63e7ef</Project>
         <Name>pcf_component </Name>
         <Targets>Build</Targets>
         <referenceOutputAssembly>false</referenceOutputAssembly>
         <OutputItemType>Content</OutputItemType>
         <CopyToOutputDirectory>Always</CopyToOutputDirectory>
       </Projectreference>
   </ItemGroup>
   ```

2. 使用以下命令执行重新生成（或清理）：
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>另请参阅

[将代码组件添加到模型驱动应用中的字段或实体](add-custom-controls-to-a-field-or-entity.md)<br/>
[将组件添加到画布应用](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[PowerApps 组件框架 API 参考](reference/index.md)<br/>
[PowerApps 组件框架概述](overview.md)
