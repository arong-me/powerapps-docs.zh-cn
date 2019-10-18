---
title: 使用 PowerApps 组件框架工具更新现有代码组件 |Microsoft Docs
description: 使用 PowerApps 组件框架工具更新组件
keywords: PowerApps 组件框架，代码组件，组件框架
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 05e32fb7e098dad3aabf36f2efdaf311c1bea327
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340221"
---
# <a name="update-existing-code-components"></a>更新现有代码组件 

如果你是模型驱动应用的 PowerApps 组件框架专用预览参与者，并且已经生成了代码组件，则需要进行一些小版本的更新，以使其与新的以 ALM 为中心的项目结构兼容。 

若要在现有 PowerApps 组件框架代码组件中使用新的 PowerApps CLI 工具，需要进行一些更改。

> [!NOTE]
> 本主题仅适用于更新模型驱动应用程序的代码组件，因为在对模型驱动应用进行个人预览版时，PowerApps CLI 工具不可用。  

## <a name="creating-an-empty-project"></a>创建空项目

使用 PowerApps CLI 为代码组件创建新的空项目。 详细信息：[使用工具创建组件](create-custom-controls-using-pcf.md)

创建项目后，将代码组件源迁移到新项目：

1. 将组件源文件从源文件复制或替换为**索引。 ts**。
2. 将**ControlManifest**的内容复制或替换为**ControlManifest**文件。
3. 将所有其他外围组件资源（如 CSS、RESX 或 IMG）复制到旧项目的相应子文件夹中。

## <a name="updating-manifest-file"></a>正在更新清单文件

定义代码组件属性的 `ControlManifest.xml` 文件被替换为 `ControlManifest.Input.xml` 文件。 在这两个文件之间，架构的变化应该非常少。

但有几个重要的语义更改：

1. @No__t_0 资源条目现在必须指向代码组件的预编译源文件。 文件名默认为 "**索引"。**

   例如，如果组件源是在名为 `MyControl.ts` 的文件中实现的，则 `ControlManifest.Input.xml` 中 `code` 条目必须指向该文件。 @No__t_0 文件也必须是有效的 TypeScript 文件。 这与在 `code` 条目中指定已编译的 JS 输出文件的旧版清单文件相反。
2. 资源元素的 `path` 属性，如 `code` 或 `css` 现在指的是磁盘上的文件的本地路径。 例如：

    ```XML
   <resources>
    <css path="css/YourControlName" order="1"/>
    </resources>
    ```

上述 `path` 属性表示 `YourControlName.css` 文件与 `ControlManifest.Input.xml` 驻留在磁盘上的当前目录位于 `css` 子文件夹中。

按如下所示更新 ControlManifest 文件：

1. 编辑 `ControlManifest.Input.xml` 中的 `code` 条目到代码组件的预编译源文件（通常为 "索引"）。
2. 编辑资源的任何路径，以正确引用磁盘上文件的相对路径。

## <a name="updating-the-project-files"></a>更新项目文件

如果已使用较旧版本的工具创建了一个组件，并且想要充分利用最新功能，请确保更新项目文件，如下所示：

1. 更新现有项目以使用最新的模块。
 
   - 更新位于 PowerApps component framework 项目文件夹内的 `pcfproj` 中的版本标记，如下所示：

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Pcf" Version="1.*"/>
      ```
   - 更新解决方案项目文件夹中 `cdsproj` 的版本标记，如下所示：

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Solution" Version="1.*"/>
      ```

      > [!NOTE] 
      > 进行上述更改后，运行 `msbuild /t:restore` 命令，将项目更新到正确的版本。


   - 更新位于 PowerApps component framework 项目文件夹内的 `package.json` 文件中的版本标记：

      ```JSON
      "devDependencies":{
       "pcf-scripts": "^1",
       "pcf-start": "^1"
          }
      ```
     > [!NOTE]
     > 进行上述更改后，运行 `npm update` 命令，将项目更新到正确的版本。

2. 如果你以前创建了一个身份验证配置文件，则需要重新创建它。 这是因为新属性已添加到配置文件以支持非公有云。 为此，可以执行以下操作：
 
    - 运行命令 `pac auth clear`。
    - 运行命令 `pac auth create --url <your org url>`。

## <a name="updating-your-project-with-the-latest-node-modules"></a>用最新的节点模块更新项目

旧项目需要检索最新的 npm 模块，才能利用最新的 CLI 功能。 若要更新之前下载的节点模块，请在开发人员命令提示符处中转到项目目录并运行命令 `npm update`。 

## <a name="using-es6-module-syntax"></a>使用 ES6 模块语法

生成工具需要使用标准 ES6 模块格式导出组件源。 旧组件通常导出为内部模块（也称为命名空间）。 必须按如下所示修改组件源文件，以使其与新的生成工具匹配。

1. 打开用于实现代码组件的源文件（例如，"索引"）。
2. 通过删除模块声明来使用标准 ES6 导出语法。

     早
     ```TypeScript
     module SampleNamespace
     {
    export class TSLinearInputControl implements ComponentFramework.StandardControl<InputsOutputs.IInputBag, InputsOutputs.IOutputBag> {
          <your class implementation>
           }
            }
     
      ```
    晚
    ```TypeScript
     export class YourControlName implements ComponentFramework.StandardControl<IInputs, IOutputs> { 
          <your class implementation>
          }
   ```

## <a name="using-generated-manifest-typing-file"></a>使用生成的清单键入文件

旧项目需要手动创建和编辑 `inputsOutputs.d.ts` 键入文件，此文件通常位于 `private_typing` 子文件夹下。 PowerApps CLI 工具现在会自动在生成时生成此文件。 

代码生成确保组件源代码中使用 `type` 定义与组件清单文件中定义的 `types` 保持同步。

键入文件已重命名为 `ManifestTypes.d.ts`，现在会生成到名为 `generated` 的子文件夹中。 此外，`InputsOutputs.IInputBag` 和 `InputsOutputs.IOutputBag` 类型分别重命名为 `IInputs` 和 `IOutputs`。

使用新的类型化文件：

1. 通过在组件源文件的顶部添加以下行来导入新的 `ManifestTypes.d.ts` 文件：

    从 `./generated/ManifestTypes` 导入 {IInputs，IOutputs}。
2. 将**InputsOutputs**的所有引用重命名为**IInputs**。
3. 将**InputsOutputs**的所有引用重命名为**IOutputs**。
4. 使用命令 `npm run build` 生成项目以生成新的**ManifestTypes 文件。**

## <a name="troubleshooting-and-workarounds"></a>故障排除和解决方法

1. 如果收到询问如何使用 pcf 脚本的1ES 通知，请注意，这些脚本仅用于生成代码组件，但不会被生成的组件捆绑或使用。  
2. 如果以前使用工具版本0.1.817.1 或更早版本创建了代码组件，并希望确保使用最新的生成和调试模块，请对包进行更新，如下所示：
   
    ```JSON
     "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
    ```
3. 用户在生成失败时，`Failed to retrieve information about Microsoft.PowerApps.MSBuild.Pcf from remote source <Feed Url>` 获取授权问题的错误。 下面是此操作的解决方法：

   - 打开 **%APPDATA%\NuGet**中的 NuGet 文件。 此文件中应存在用户从中获取错误的源。 
   - 从 NuGet 文件中删除该源，或生成一个 PAT 令牌并将其添加到 Nuget 文件。 例如：

     ```XML
     <?xml version="1.0" encoding="utf-8"?>  
     <configuration>  
     <packageSources>  
         <add key="CRMSharedFeed" value="https://dynamicscrm.pkgs.visualstudio.com/_packaging/CRMSharedFeed/nuget/v3/index.json" />  
      </packageSources>  
     <packageSourceCredentials>  
      <CRMSharedFeed>  
      <add key="Username" value="anything" />  
      <add key="Password" value="User PAT" />  
    </CRMSharedFeed>  
     </packageSourceCredentials>  
   </configuration>
     ```

### <a name="see-also"></a>另请参阅

[PowerApps 组件框架的限制](limitations.md)<br/>
[PowerApps 组件框架 API 参考](reference/index.md)<br/>
[PowerApps 组件框架概述](overview.md)
