---
title: " 地图组件 |Microsoft Docs"
description: 使用角度 JS 实现地图组件
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: f4b8702ef39688bdfc5f3ce9a51bf5c8c6e0ff20
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341325"
---
# <a name="implementing-map-component"></a>实现地图组件

此示例组件更改与窗体上的地址字段交互的用户体验。 除了地址的文本值，此组件还能直观地标识地图上的特定地址，而无需导航到另一个选项卡或屏幕。 

> [!div class="mx-imgBorder"]
> ![地图组件](../media/map-control.png "图组件")

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览） 

## <a name="manifest"></a>体现

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSMapControl" version="1.0.0" display-name-key="TS_MapControl_Display_Key" description-key="TS_MapControl_Desc_Key" control-type="standard">
        <property name="controlValue" display-name-key="controlValue_Display_Key" description-key="controlValue_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_MapControl.css" order="1" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>代码 

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSMapControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // HTML IFrame element that will be used to render the map
  private _iFrameElement: HTMLIFrameElement;
  // PowerApps component framework framework delegate which will be assigned to this object which would be called whenever an update happens.
  private _notifyOutputChanged: () => void;
  // reference to ComponentFramework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // API Key used to activate and embed the maps automatically
  // NOTE: You can follow the documentation at https://developers.google.com/maps/documentation/embed/get-api-key to generate your own API Key
  private MAPS_API_KEY: string = "<Replace your Key here>";
  /**
   * Empty constructor.
   */
  constructor() {}
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
    this._notifyOutputChanged = notifyOutputChanged;
    this._context = context;
    this._iFrameElement = document.createElement("iframe");
    this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    this.renderMap(this.buildMapUrl(context.parameters.controlValue.formatted));
    container.appendChild(this._iFrameElement);
  }
  /**
   * Checks if the url is not null and sets the value to the iFrame source to be loaded inside it and then notifies the ControlFramework that the output has changed
   * @param mapUrl : The url for the map that needs to be loaded inside the iFrame.
   */
  public renderMap(mapUrl: string) {
    if (mapUrl) {
      this._iFrameElement.setAttribute("src", mapUrl);
      this._iFrameElement.setAttribute("class", "mapVisibleStyle");
    } else {
      this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    }
    this._notifyOutputChanged();
  }
  /**
   * Converts the string that is passed to a valid url that can be used to render the map for the location
   * @param addressString : any string that can be used to search for a location in maps
   * @returns the HTML encoded url that can be used to load the map if the addressString is non empty string
   */
  public buildMapUrl(addressString: string | undefined): string {
    if (addressString) {
      let url: string =
        "https://www.google.com/maps/embed/v1/place?key=" +
        this.MAPS_API_KEY +
        "&q=" +
        encodeURIComponent(addressString);
      return url;
    }
    return "";
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>) {
    this._context = context;
    this.renderMap(this.buildMapUrl(context.parameters.controlValue.formatted));
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
  public destroy() {}
}
```

## <a name="resources"></a>资源

```css
.SampleNamespace\.TSMapControl .mapVisibleStyle {
  width: 640px;
  height: 420px;
  visibility: visible;
}
.SampleNamespace\.TSMapControl .mapHiddenStyle {
  visibility: hidden;
}
```

在清单文件中，为 `Single line of Text` 类型定义了属性。 我们使用此方法将其绑定到表单上的 "地址" 字段。  

> [!NOTE]
> 可以使用市场中提供的任何地图 API。 在此示例中，我们将演示如何通过 Google Map API 来执行此操作。 需要为组件创建 API 密钥，以访问 Google Map API。 按照说明进行操作（ https://developers.google.com/maps/documentation/embed/get-api-key 生成一个）。

创建可在组件上下文中访问的变量名 `MAPS_API_KEY`。
Google Map API 只允许在 `IFRAME` 中呈现映射。 因此，你需要创建一个 `IFRAME` 元素，该元素将使用我们生成的 URL 呈现地图。 默认情况下，我们要将映射设置为隐藏状态，并且仅当窗体上存在地址值时才显示。

`buildMapUrl` 和 `renderMap` （甚至可以将其合并为一个）会采用地址字符串并将其嵌入到地图 URL，方法是对地址字符串进行编码，然后将 IFRAME 元素的 src 元素分别设置为 URL。 此外，请调用**notifyOutputChanged**方法，以确保通知组件呈现已更改。 
 
```TypeScript
 public renderMap(mapUrl: string) {
    if (mapUrl) {
      this._iFrameElement.setAttribute("src", mapUrl);
      this._iFrameElement.setAttribute("class", "mapVisibleStyle");
    } else {
      this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    }
    this._notifyOutputChanged();
  }
```

请确保在[updateView](../reference/control/updateview.md)函数中调用 `renderMap` 函数，以确保每次更新视图时都刷新控件。 

### <a name="related-topics"></a>相关主题

[下载示例组件](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架清单架构参考](../manifest-schema-reference/index.md)