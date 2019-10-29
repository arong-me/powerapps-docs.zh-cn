---
title: 使用 TypeScript 实现代码组件 |MicrosoftDocs
description: 如何使用 TypeScript 实现代码组件
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 669bf03d7869d6fd625288a65a305a3a458cfde4
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025761"
---
# <a name="implement-components-using-typescript"></a>使用 TypeScript 实现组件

本主题将指导你完成使用 PowerApps CLI 在 TypeScript 中创建新代码组件的过程。 在本教程中，我们将构建一个示例线性代码组件，使用户能够使用视觉对象滑块来更改数值，而不是在字段中键入值。 

生成代码组件所需的项目为：

1. [创建新的组件项目](#creating-a-new-component-project)
2. [实现清单](#implementing-manifest)
3. [使用 TypeScript 实现组件逻辑](#implementing-component-logic)
4. [将样式添加到代码组件](#adding-style-to-the-code-component)
5. [打包代码组件](#packaging-your-code-components)

## <a name="creating-a-new-component-project"></a>创建新的组件项目

创建新项目：

1. 打开**VS 2017**窗口的开发人员命令提示。
1. 使用以下命令为项目创建一个新文件夹： 
    ```CLI
    mkdir LinearComponent
    ```

1. 使用命令 `cd LinearComponent`进入组件文件夹。 
   
1. 通过使用命令传递基本参数来创建新的组件项目。

   ```CLI
    pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
    ``` 

1. 使用命令 `npm install` 安装项目生成工具。 
1. 在所选的开发人员环境中 `C:\Users\<your name>\Documents\<My_code_Component>` 打开项目文件夹，并开始使用代码组件开发。 最快的启动方法是在 `C:\Users\<your name>\Documents\<My_code_Component>` 目录中运行 `code .` 从命令提示符运行。 此命令在 Visual Studio Code 中打开组件项目。

## <a name="implementing-manifest"></a>实现清单

清单是一个 XML 文件，其中包含代码组件的元数据。 它还定义代码组件的行为。 在本教程中，将在 `<Your component Name>` 子文件夹下创建此清单文件。 当您在 Visual Studio Code 中打开 `ControlManifest.Input.xml` 文件时，您会注意到，预定义了清单文件的某些属性。 详细信息：[清单](manifest-schema-reference/manifest.md)。

对预定义的清单文件进行更改，如下所示：

1. [控制](manifest-schema-reference/control.md)节点定义代码组件的命名空间、版本和显示名称。 现在，按如下所示定义[控制](manifest-schema-reference/control.md)节点的每个属性：

   - **命名空间**：代码组件的命名空间。 
   - **构造函数**：代码组件的构造函数。
   - **版本**：组件的版本。 更新组件时，需要更新版本以查看运行时中的最新更改。
   - **显示名称-键**： UI 上显示的代码组件的名称。
   - **说明-名称键**： UI 上显示的代码组件的说明。
   - **控件类型**：代码组件类型。 仅支持*标准*类型的代码组件。

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNameSpace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
     ```

2. [属性](manifest-schema-reference/property.md)节点定义代码组件的属性，例如定义字段的数据类型。 属性节点指定为 `control` 元素下的子元素。 定义[属性](manifest-schema-reference/property.md)节点，如下所示：

   - **名称**：属性的名称。
   - **显示名称-键**：显示在 UI 上的属性的名称。
   - **description-name-key**： UI 上显示的属性的说明。 
   - **类型组**：当要拥有两个以上的数据类型字段时，使用[类型组](manifest-schema-reference/type-group.md)。 将[类型组](manifest-schema-reference/type-group.md)元素作为同级添加到清单中的 `property` 元素。 `of-type-group` 指定组件的值，并且可以包含整数、货币、浮点或小数值。
   - **用法**：有两个属性： "*绑定*" 和 "*输入*"。 绑定属性仅绑定到字段的值。 输入属性可以绑定到字段，也可以是允许静态值。
   - **必需**：定义属性是否是必需的。

     ```XML
      <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
      ```
3. "[资源](manifest-schema-reference/resources.md)" 节点定义代码组件的可视化。 它包含生成代码组件的可视化和样式的所有资源。 在 resources 元素下，[代码](manifest-schema-reference/code.md)被指定为子元素。 按如下所示定义[资源](manifest-schema-reference/resources.md)：

   - **代码**：引用所有资源文件所在的路径。
 
      ```XML
      <resources>
        <code path="index.ts" order="1" />
        <css path="css/TS_LinearInputComponent.css" order="1" />
        </resources>
        ```
      总体清单文件应如下所示： 

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNamespace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
        <type-group name="numbers">
          <type>Whole.None</type>
          <type>Currency</type>
          <type>FP</type>
          <type>Decimal</type>
         </type-group>
        <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
       <resources>
         <code path="index.ts" order="1" />
         <css path="css/TS_LinearInputComponent.css" order="1" />
       </resources>
      </control>
     </manifest>
     ```

4. 保存对 `ControlManifest.Input.xml` 文件所做的更改。
5. 现在，在 `TSLinearInputComponent` 文件夹内创建一个新文件夹，并将其命名为**css**。
6. 创建一个用于[将样式添加到代码组件的](#adding-style-to-the-code-component)CSS 文件。
7. 使用命令 `npm run build` 生成组件项目。
8. 生成在 `TSLinearInputComponent/generated` 文件夹下生成更新的 TypeScript 类型声明文件。

## <a name="implementing-component-logic"></a>实现组件逻辑

实现清单文件后的下一步是使用 TypeScript 实现组件逻辑。 组件逻辑应在 `index.ts` 文件中实现。 当您在 Visual Studio Code 中打开 `index.ts` 文件时，您会注意到，这四个基本类是预定义的。 现在，让我们实现代码组件的逻辑。 

1. 打开所选代码编辑器中的 `index.ts` 文件。
2. 用以下代码更新 `TSLinearInputComponent` 类：

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputComponent
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the component
  private _value: number;
  // PowerApps component framework delegate which will be assigned to this object which would be called whenever any update happens.
  private _notifyOutputChanged: () => void;
  // label element created as part of this component
  private labelElement: HTMLLabelElement;
  // input element that is used to create the range slider
  private inputElement: HTMLInputElement;
  // reference to the component container HTMLDivElement
  // This element contains all elements of our code component example
  private _container: HTMLDivElement;
  // reference to PowerApps component framework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // Event Handler 'refreshData' reference
  private _refreshData: EventListenerOrEventListenerObject;

  constructor() {}

  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this._context = context;
    this._container = document.createElement("div");
    this._notifyOutputChanged = notifyOutputChanged;
    this._refreshData = this.refreshData.bind(this);
    // creating HTML elements for the input type range and binding it to the function which refreshes the component data
    this.inputElement = document.createElement("input");
    this.inputElement.setAttribute("type", "range");
    this.inputElement.addEventListener("input", this._refreshData);
    //setting the max and min values for the component.
    this.inputElement.setAttribute("min", "1");
    this.inputElement.setAttribute("max", "1000");
    this.inputElement.setAttribute("class", "linearslider");
    this.inputElement.setAttribute("id", "linearrangeinput");
    // creating a HTML label element that shows the value that is set on the linear range component
    this.labelElement = document.createElement("label");
    this.labelElement.setAttribute("class", "TS_LinearRangeLabel");
    this.labelElement.setAttribute("id", "lrclabel");
    // retrieving the latest value from the component and setting it to the HTML elements.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this.inputElement.setAttribute(
      "value",
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "0"
    );
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "0";
    // appending the HTML elements to the component's HTML container element.
    this._container.appendChild(this.inputElement);
    this._container.appendChild(this.labelElement);
    container.appendChild(this._container);
  }

  /**
   * Updates the values to the internal value variable we are storing and also updates the html label that displays the value
   * @param context : The "Input Properties" containing the parameters, component metadata and interface functions
   */

  public refreshData(evt: Event): void {
    this._value = (this.inputElement.value as any) as number;
    this.labelElement.innerHTML = this.inputElement.value;
    this._notifyOutputChanged();
  }

  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // storing the latest context from the control.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this._context = context;
    this.inputElement.setAttribute(
      "value",
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : ""
    );
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "";
  }

  public getOutputs(): IOutputs {
    return {
      sliderValue: this._value
    };
  }

  public destroy() {
    this.inputElement.removeEventListener("input", this._refreshData);
  }
}

```

3. 使用命令 `npm run build` 重新生成项目。 
 
4. 该组件将编译到 `out/controls/TSLinearInputComponent` 文件夹中。 生成项目包括：

   - node.js –捆绑的组件源代码。 
   - ControlManifest-上载到 Common Data Service 组织的实际组件清单文件。

## <a name="adding-style-to-the-code-component"></a>将样式添加到代码组件

开发人员和应用程序开发人员可以定义其样式，以直观地使用 CSS 表示其代码组件。 CSS 允许开发人员描述代码组件的表示形式，包括样式、颜色、布局和字体。 线性输入组件的[init](reference/control/init.md)方法会创建一个输入元素，并将类属性设置为 `linearslider`。 `linearslider` 类的样式在单独的 `CSS` 文件中定义。 其他组件资源（如 `CSS` 文件）可以与代码组件一起提供，以支持进一步的自定义。

1. 在 "`TSLinearInputComponent`" 文件夹下创建新的 `css` 子文件夹。 
2. 在 `css` 子文件夹内创建新的 `TS_LinearInputComponent.css` 文件。 
3. 将以下样式内容添加到 `TS_LinearInputComponent.css` 文件：

    ```CSS
    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider {
      margin: 1px 0;
      background: transparent;
      -webkit-appearance: none;
      width: 100%;
      padding: 0;
      height: 24px;
      -webkit-tap-highlight-color: transparent
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider:focus {
      outline: none;
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-runnable-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
    }
    ```

5. 保存 `TS_LinearInputComponent.css` 文件。
6. 编辑 `ControlManifest.Input.xml` 文件，将 `CSS` 资源文件包含在资源元素中。
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputComponent.css" order="1"/> 
    </resources> 
     ```
7. 使用以下命令重新生成项目： 
   ```CLI
   npm run build
   ```
8. 检查 **/out/controls/TSLinearInputComponent**下的生成输出，并观察**TS_LinearInputComponent**文件现在包含在已编译的生成项目中。 

## <a name="debugging-your-code-component"></a>调试代码组件

完成代码组件逻辑的实现后，运行以下命令以启动调试进程。 详细信息：[调试代码组件](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-code-components"></a>打包代码组件

按照以下步骤创建和导入[解决方案](https://docs.microsoft.com/powerapps/maker/common-data-service/solutions-overview)文件：

1. 在**LinearComponent**文件夹中创建新的文件夹**解决方案**，并导航到该文件夹。 
2. 使用以下命令在**LinearComponent**文件夹中创建一个新的解决方案项目：
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > [发布服务器名称](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher)和[发布服务器前缀](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix)值必须对您的环境是唯一的。
 
3. 创建新的解决方案项目后，需要引用创建的组件所在的位置。 可以使用以下命令添加引用：

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. 若要从解决方案项目生成 zip 文件，需要将 `cd` 到解决方案项目目录中，并使用以下命令生成项目： 

    ```CLI
     msbuild /t:restore
    ```

5. 同样，请运行以下命令 msbuild：
    ```CLI
     msbuild
    ```

    > [!NOTE]
    > 请确保选中 " **NuGet 目标 & 生成任务**"。 若要启用它：
    > - 打开**Visual Studio 安装程序**。
    > - 对于 Visual Studio 2017，选择 "**修改**"。
    > - 选择**各个组件**。
    > - 在 "**代码工具**" 下，选中 " **NuGet 目标 & 生成任务**"。

6. 生成的解决方案 zip 文件位于 `Solution\bin\debug` 文件夹中。
7. Zip 文件准备就绪后，请使用 web 门户手动[将解决方案导入 Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) ，或查看使用 PowerApps CLI 命令导入到你的组织和[部署](import-custom-controls.md#deploying-code-components)部分进行[身份验证](import-custom-controls.md#authenticating-to-your-organization)。

## <a name="adding-code-components-in-model-driven-apps"></a>在模型驱动应用中添加代码组件

若要添加代码组件（如线性输入组件），请按照主题[将组件添加到字段和实体](add-custom-controls-to-a-field-or-entity.md)中所述的步骤进行操作。

## <a name="adding-code-components-to-a-canvas-app"></a>向画布应用添加代码组件

若要将代码组件添加到画布应用，请按照主题[将代码组件添加到画布应用](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)中的步骤操作。

### <a name="see-also"></a>另请参阅

[下载示例组件](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[更新现有 PowerApps 组件框架组件](updating-existing-controls.md)<br/>
[PowerApps 组件框架 API 参考](reference/index.md)<br/>
[PowerApps 组件框架概述](overview.md)
