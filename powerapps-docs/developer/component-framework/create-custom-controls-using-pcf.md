---
title: 创建并生成代码组件 |Microsoft Docs
description: 开始使用 PowerApps 组件框架工具创建组件
keywords: PowerApps 组件框架，代码组件，组件框架
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 9a02b64321564b0a09e6b53223f13748358d76cf
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025782"
---
# <a name="create-and-build-a-code-component"></a>创建并生成代码组件

本主题演示如何使用 PowerApps CLI 创建和部署代码组件。 确保已安装[MICROSOFT POWERAPPS CLI](https://aka.ms/PowerAppsCLI)。

## <a name="create-a-new-component"></a>创建新组件

若要开始，请在安装 PowerApps CLI 后打开**VS 2017 开发人员命令提示**。

1. 在 VS 2017 的开发人员命令提示中，使用命令 `mkdir <Specify the folder name>`在本地计算机上创建一个新文件夹，例如*C:\Users\your name\Documents\My_code_Component* 。
2. 使用命令 `cd <specify your new folder path>` 中转到新创建的文件夹。
3. 通过使用命令传递某些基本参数来创建新的组件项目：

    `pac pcf init --namespace <specify your namespace here> --name <Name of the code component> --template <component type>`
 
   > [!NOTE]
   > 当前，PowerApps CLI 支持两种类型的组件：用于模型驱动应用的**字段**和**数据集**。  对于画布应用，此试验预览版仅支持**字段**类型。

4. 若要检索所有必需的项目依赖项，请运行命令 `npm install`。
5. 在所选的任何开发人员环境中 `C:\Users\<your name>\Documents\<My_code_Component>` 打开项目文件夹，并开始编写代码组件。 最快的入门方法是，一旦进入 `C:\Users\<your name>\Documents\<My_code_Component>` 目录，就可以从命令提示符运行 `code .`。 此命令在 Visual Studio Code 中打开组件项目。
6. 实现组件所需的项目，如清单、组件逻辑和样式，然后生成组件项目。 更多信息：[实现示例组件](implementing-controls-using-typescript.md)

## <a name="build-your-component"></a>构建组件

若要生成组件项目，请打开包含 Visual Studio Code 中 `package.json` 的项目文件夹，并使用 "（Ctrl + Shift-B）" 命令，然后选择 "生成" 选项。 或者，您可以使用 VS 2017 窗口的开发人员命令提示中的 "`npm run build`" 命令快速生成组件。

> [!TIP]
> 若要在生成操作期间或之后调试组件，请参阅[调试代码组件](debugging-custom-controls.md)。

在 TypeScript 中实现组件逻辑后，需要将所有代码组件元素捆绑到一个解决方案文件中，以便可以将解决方案导入到 Common Data Service 中。 详细信息：[打包代码组件](import-custom-controls.md)

## <a name="known-configuration-issues-and-workarounds"></a>已知配置问题和解决方法

**Msbuild 错误 MSB4036：**

1. 项目文件中的任务名称与任务类的名称相同。
2. 任务类为公共类并实现 ITask 接口。
3. 该任务是通过项目文件中的 *\<UsingTask >* 正确声明的，或者位于路径目录中的 *. tasks 文件中。

**分辨率**

1. 打开 Visual Studio 安装程序。 
1. 对于 Visual Studio 2017，选择 "**修改**"。 
1. 选择**各个组件**。
1. 在 "代码工具" 下，选中 " **NuGet 目标 & 生成任务**"。

**发布者前缀**

如果组件是使用低于0.4.3 的 PowerApps CLI 工具版本创建的，则在尝试将解决方案文件重新导入到 Common Data Service 时，将遇到错误。 引发该错误的原因是，新导入的组件名称现在追加了发布者前缀，以确保其唯一性并避免冲突。

**解决方法**：

- 从 Common Data Service 删除包含相关组件的解决方案。 如果已在窗体或网格上配置了该组件，则需要首先将其删除，因为组件解决方案依赖于配置。  
- 导入新的解决方案，其中包含由最新 CLI 版本生成的组件的更新。
- 现在可以在窗体或网格中配置新导入的组件。  


<!--2. When the components are created with the publisher prefix in mixed or upper case using the new CLI tooling version, it throws an error while importing the solution. This happens because the updated tooling version (0.4.3 and newer) now enforces the platform standard for lower case publisher prefix.

   **Workaround**:

    Update the solution and customizations to ensure that the associated prefix is modified to lower case and import the new solution into Common Data Service.-->


### <a name="see-also"></a>另请参阅

[调试代码组件](debugging-custom-controls.md)<br/>
[打包代码组件](import-custom-controls.md)<br/>
[向字段或实体添加代码组件](add-custom-controls-to-a-field-or-entity.md)<br/>
[更新现有代码组件](updating-existing-controls.md)<br/>
[PowerApps 组件框架 API 参考](reference/index.md)<br/>
[PowerApps 组件框架概述](overview.md)
