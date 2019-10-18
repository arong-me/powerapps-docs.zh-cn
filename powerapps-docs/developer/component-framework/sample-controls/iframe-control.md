---
title: " IFRAME 组件 |Microsoft Docs"
description: 实现 IFRAME 组件
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: d10b03c478f238df02ee7e1309c0e39e758ce4c9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340451"
---
# <a name="implementing-a-iframe-component"></a>实现 IFRAME 组件

此示例说明如何将代码组件绑定到窗体上的不同字段，并将这些字段的值用作组件的输入属性。  

> [!div class="mx-imgBorder"]
> ![Iframe 组件](../media/iframe-control.png "iframe 组件")

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览） 

## <a name="manifest"></a>体现

```XML
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSIFrameControl" version="1.0.0" display-name-key="TS_IFrameControl_Display_Key" description-key="TS_IFrameControl_Desc_Key" control-type="standard">
        <property name="stringProperty" display-name-key="stringProperty_Display_Key" description-key="stringProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <property name="latitudeValue" display-name-key="Bing_Maps_Latitude_Value" description-key="latitude" of-type="FP" usage="bound" required="true" />
        <property name="longitudeValue" display-name-key="Bing_Maps_Longitude_Value" description-key="longitude" of-type="FP" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_IFrameControl.css" order="2" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>代码

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSIFrameControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // reference to Bing Map IFrame HTMLElement
  private _bingMapIFrame: HTMLElement;
  // reference to the control container HTMLDivElement
  // This element contains all elements of our custom control example
  private _container: HTMLDivElement;
  // Flag if control view has been rendered
  private _controlViewRendered: Boolean;
  /**
   * Used to initialize the control instance. Controls can kick off remote server calls and other initialization actions here.
   * Data-set values are not initialized here, use updateView.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to property names defined in the manifest, as well as utility functions.
   * @param notifyOutputChanged A callback method to alert the framework that the control has new outputs ready to be retrieved asynchronously.
   * @param state A piece of data that persists in one session for a single user. Can be set at any point in a controls life cycle by calling 'setControlState' in the Mode interface.
   * @param container If control is marked control-type='standard', it receives an empty div element within which it can render its content.
   */
  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this._container = container;
    this._controlViewRendered = false;
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>) {
    if (!this._controlViewRendered) {
      this._controlViewRendered = true;
      this.renderBingMapIFrame();
    }
    let latitude: number = context.parameters.latitudeValue.raw;
    let longitude: number = context.parameters.longitudeValue.raw;
    this.updateBingMapURL(latitude, longitude);
  }
  /**
   * Render IFrame HTML Element that hosts the Bing Map and appends the IFrame to the control container
   */
  private renderBingMapIFrame(): void {
    this._bingMapIFrame = this.createIFrameElement();
    this._container.appendChild(this._bingMapIFrame);
  }
  /**
   * Updates the URL of the Bing Map IFrame to display the updated lat/long coordinates
   * @param latitude : latitude of center point of Bing map
   * @param longitude : longitude of center point of Bing map
   */
  private updateBingMapURL(latitude: number, longitude: number): void {
    // Bing Map API:
    // https://msdn.microsoft.com/library/dn217138.aspx
    // Provide bing map query string parameters to format and style map view
    let bingMapUrlPrefix = "https://www.bing.com/maps/embed?h=400&w=300&cp=";
    let bingMapUrlPostfix = "&lvl=12&typ=d&sty=o&src=SHELL&FORM=MBEDV8";
    // Build the entire URL with the user provided latitude and longitude
    let iFrameSrc: string =
      bingMapUrlPrefix + latitude + "~" + longitude + bingMapUrlPostfix;
    // Update the IFrame to point to the updated URL
    this._bingMapIFrame.setAttribute("src", iFrameSrc);
  }
  /**
   * Helper method to create an IFrame HTML Element
   */
  private createIFrameElement(): HTMLElement {
    let iFrameElement: HTMLElement = document.createElement("iframe");
    iFrameElement.setAttribute("class", "TS_SampleControl_IFrame");
    return iFrameElement;
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    // no-op: method not leveraged by this example custom control
    return {};
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. canceling any pending remote calls, removing listeners, etc.
   */
  public destroy() {
    // no-op: method not leveraged by this example custom control
  }
}
```

## <a name="resources"></a>资源

```css
.SampleNamespace\.TSIFrameControl .TS_SampleControl_IFrame
{
    width: 300px;
    height: 400px;
}
```

> [!NOTE]
> PowerApps 组件框架尚不支持复合字段，因此不能将此组件绑定到现成的纬度和经度地址字段。 需要将代码组件绑定到另一个浮点字段。

此示例组件呈现显示 `Bing Maps URL` 的 `IFRAME`。 组件绑定到窗体上的两个浮点字段，它们作为参数传递给组件并注入到 `IFRAME URL` 中，以将必应地图更新为所提供输入的纬度和经度。  

更新 `Manifest` 文件以包含绑定到窗体上的两个附加字段。  
此更改通知 PowerApps 组件框架，这些绑定字段需要在初始化期间传递到组件，并且在更新其中一个值时。
  
```xml

<property name="latitudeValue" display-name-key="Bing_Maps_Latitude_Value" description-key="latitude" of-type="FP" usage="bound" required="true" />  
<property name="longitudeValue" display-name-key="Bing_Maps_Longitude_Value" description-key="longitude" of-type="FP" usage="bound" required="true" />  
```

其他绑定属性可能是必需的。 当组件绑定到窗体时，将在组件配置过程中强制执行此过程。 这可以通过设置组件清单中属性节点的 `required` 属性进行配置。 如果您不希望将组件属性绑定到某个字段，请将值设置为 "false"。 
 
需要更新 `ControlFramework.d.ts`，将两个字段添加到 `IInputs` 接口。 这是 PowerApps 组件框架传递字段值的格式。 将这些值添加到 `IInputs` 接口后，你的 TypeScript 文件便可引用这些值并成功编译。  

```TypeScript
    export interface IInputs 
    { latitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
        longitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
    }  
 ```

初始呈现将生成一个 `IFRAME` 元素，并将其追加到 controls 容器。 此 `IFRAME` 用于显示**Bing 地图**。 @No__t_0 的 url 设置为 `Bing Map URL`，并在 url 中包含绑定字段（latitudeValue 和 longitudeValue），以便在提供的位置将地图居中。 

只要在窗体上更新其中一个字段，就会调用[updateView](../reference/control/updateview.md)方法。 此方法更新**必应地图**IFRAME 的 url，以使用传递给该组件的新纬度值和经度值。 若要在运行时查看此组件，请将组件绑定到窗体上的字段，如任何其他代码组件。

### <a name="related-topics"></a>相关主题

[下载示例组件](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[PowerApps 组件框架清单架构参考](../manifest-schema-reference/index.md)<br />
[PowerApps 组件框架 API 参考](../reference/index.md)<br />
[PowerApps 组件框架概述](../overview.md)
