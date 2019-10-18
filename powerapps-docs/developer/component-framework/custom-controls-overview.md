---
title: 什么是代码组件？ |MicrosoftDocs
description: 使用 PowerApps 组件框架来创建代码组件，以便为用户提供更好的用户体验，使用户能够查看和处理窗体、视图和仪表板中的数据。
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 135481cd-4583-4e49-8f58-02f32a9b054a
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 08a2043dfb92634837c367e664306d9c100632d6
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346960"
---
# <a name="what-are-code-components"></a>什么是代码组件

代码组件是一种解决方案组件，这意味着它们可以包含在解决方案文件中并安装在不同的环境中。 详细信息：[使用解决方案打包和分发扩展](https://docs.microsoft.com/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)。

您可以通过将代码组件包含在解决方案中，然后将其导入到 Common Data Service 来添加它们。 一旦组件处于 Common Data Service 中，系统管理员和系统定制员就可以配置字段、subgrids、视图和仪表板 subgrids，将其用于替代默认组件。 你还可以在画布应用中添加这些代码组件。 

代码组件由三个元素组成：

1. [体现](#manifest)
2. [组件实现库](#component-implementation-library)
3. [Resources](#resources)

## <a name="manifest"></a>体现

manifest 是定义组件的元数据文件。 它是一个 XML 文档，用于描述：

- 组件的名称。
- 可以配置的数据类型，可以是字段或数据集。
- 添加组件时可以在应用程序中配置的任何属性。
- 组件需要的资源文件的列表。 
- 组件实现库中的 TypeScript 函数的名称，该函数返回应用所需组件接口的对象。

当用户配置代码组件时，清单文件中的数据将筛选出可用组件，以便只有上下文的有效组件可用于配置。 组件在清单文件中定义的属性将呈现为配置字段，以便配置组件的用户可以指定这些值。 然后，这些属性值在运行时可用于组件。 详细信息：[清单架构参考](manifest-schema-reference/index.md)

## <a name="component-implementation-library"></a>组件实现库

使用 PowerApps 组件框架开发代码组件时，实现组件库是关键步骤之一。 开发人员可以使用 TypeScript 来实现组件库。 每个代码组件都必须有一个包含函数定义的库，该函数将返回一个对象，该对象实现代码组件接口中所述的方法。 

对象实现以下方法：

- [init](reference/control/init.md) （必需）
- [updateView](reference/control/updateview.md) （必需）
- [getOutputs](reference/control/getoutputs.md) （可选）
- [销毁](reference/control/destroy.md)（必需）

这些方法控制代码组件的生命周期。

### <a name="page-load"></a>页面加载

加载页面时，应用程序需要一个对象才能正常工作。 通过使用清单文件中的数据，该代码通过调用来获取对象：

```js
var obj =  new <"namespace on manifest">.<"constructor on manifest">();
```

如果清单中的命名空间和构造函数值分别 `SampleNameSpace` 和 `LinearInputComponent`，则用于实例化对象的代码如下所示：

```js
var controlObj = new SampleNameSpace.LinearInputComponent();
```

当该页准备就绪时，它通过使用一组参数调用[init](reference/control/init.md)方法来初始化该组件。

```js
controlObj.init(context,notifyOutputChanged,state,container);
```

|参数|描述|
|---|---|
|快捷| 包含有关如何配置组件的所有信息以及可在组件中使用的所有参数以及[PowerApps 组件框架 api](reference/index.md)。 例如，可以使用 `context.parameters.<"property name from manifest">` 访问输入属性。|
|notifyOutputChanged |只要代码组件具有可异步检索的新输出，就会提醒框架。|
|状态|包含当前会话中以前的页面加载的组件数据（如果组件之前使用[setControlState](reference/mode/setcontrolstate.md)方法显式存储了该组件）。|
|容器|一个 HTML div 元素，开发人员和应用程序开发人员可以在其中追加定义组件的 UI 的 HTML 元素。|

### <a name="user-changes-data"></a>用户更改数据

加载页面时，组件将显示数据，直到用户与组件交互以更改数据。 出现这种情况时，必须调用[init](reference/control/init.md)方法中作为*notifyOutputChanged*参数传入的方法。 使用此方法时，平台会通过调用[getOutputs](reference/control/getoutputs.md)方法做出响应。 [GetOutputs](reference/control/getoutputs.md)方法返回的值包含用户所做的更改。 对于字段组件，这通常是组件的新值。

### <a name="app-changes-data"></a>应用更改数据

如果平台更改了数据，则会调用该组件的[updateView](reference/control/updateview.md)方法，并将新的上下文对象作为参数传递。 应该实现此方法以更新组件中显示的值。

### <a name="page-close"></a>页面关闭

每当用户离开页面时，代码组件就会丢失范围，并清除在该页面中为对象分配的所有内存。 但是，根据浏览器实现机制，某些方法可能会保留并消耗内存。 通常，这些事件处理程序是事件处理程序。 如果用户想要存储此信息，则他们应该实现[setControlState](reference/mode/setcontrolstate.md)方法，以便在同一会话中下一次提供信息。

开发人员应实现[销毁](reference/control/destroy.md)方法，此方法在页面关闭时被调用，以删除任何清理代码，如事件处理程序。

## <a name="resources"></a>资源

每个代码组件都应有一个资源文件来构造其可视化。 可以在清单中定义资源文件。 清单文件中的资源节点是指组件实现其可视化效果所需的资源。 详细信息： [resources 元素](manifest-schema-reference/resources.md)

### <a name="related-topics"></a>相关主题

[创建并生成代码组件](create-custom-controls-using-pcf.md)
