---
title: 控件状态 API |Microsoft Docs
description: ''
keywords: PowerAppsPowerApps 组件框架
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a77bf37-8ea0-4fe3-9fe7-2769387167c3
ms.openlocfilehash: 57982a4e9a4ee50954eb7b5f12e75a8ca43544ef
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340520"
---
# <a name="implementing-control-state-api-component"></a>实现控制状态 API 组件

PowerApps 组件框架允许在同一会话中跨组件的多个呈现保持组件的状态。 它使您能够生成组件，这些组件可在用户浏览到组件时在整个用户会话中维护用户状态。

例如，如果代码组件是用户可以滚动的长列表，则可以使用 **_SetControlState_** 功能来记住用户在离开窗体时要查看的列表中的点。 然后，你可以在组件初始化中添加逻辑以检查存储状态，并在用户之前读取的位置呈现组件的列表。

> [!div class="mx-imgBorder"] 
> ![控件状态 api](../media/control-state-api.png "控制状态 api")

## <a name="available-for"></a>适用于

模型驱动应用和画布应用（实验性预览）

## <a name="manifest"></a>体现

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="JSAngularJSFlipControl" version="1.0.0" display-name-key="JS_AngularJSFlipControl_Display_Key" description-key="JS_AngularJSFlipControl_Desc_Key" control-type="standard">
        <property name="flipModel" display-name-key="flipModel_Display_Key" description-key="flipModel_Desc_Key" of-type="TwoOptions" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="5" />
            <css path="css/bootstrap-associated.css" order="1" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>代码

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
// Key used to store the selected color into the context object to persist across navigations
const PERSISTED_SELECTED_COLOR_KEY_NAME = "selectedColor";
// Key used to store the selected color into the context object to persist across navigations
const PERSISTED_SELECTED_Label_KEY_NAME = "selectedLabel";
export class TSControlStateAPI
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Flag if control view has been rendered
  private _controlViewRendered: Boolean;
  // reference to the control container HTMLDivElement
  // This element contains all elements of our custom control example
  private _container: HTMLDivElement;
  // Div element to show the current selected color
  private _selectedColorElement: HTMLDivElement;
  // Control context object
  private _context: ComponentFramework.Context<IInputs>;
  // The color selected from the previous navigation
  private _persistedSelectedColor: string;
  // The label selected from the previous navigation
  private _persistedSelectedLabel: string;
  // Data type used to store the various information as part of the state object.
  private _stateDictionary: ComponentFramework.Dictionary = {};
  // references to HTML Button Elements rendered on the control
  private _buttonRed: HTMLButtonElement;
  private _buttonBlue: HTMLButtonElement;
  private _buttonGreen: HTMLButtonElement;
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
  ): void {
    this._controlViewRendered = false;
    this._container = document.createElement("div");
    this._context = context;
    this._container.classList.add("ControlState_Container");
    container.appendChild(this._container);
    // Check if state was persisted from the last time the control was loaded.
    if (state) {
      // If you are storing a collection of key value pairs as part of the state object, maintain a local copy of it so that it can be used to
      // add, update or remove keys during the control life cycle.
      this._stateDictionary = state;
      // Retrieve persisted state and set values into variables so state can be used during control rendering.
      this._persistedSelectedColor = state[PERSISTED_SELECTED_COLOR_KEY_NAME];
      this._persistedSelectedLabel = state[PERSISTED_SELECTED_Label_KEY_NAME];
    }
    // State not persisted in control -- set variable to default values
    if (!this._persistedSelectedColor) {
      this._persistedSelectedColor = "transparent";
    }
    // State not persisted in control -- set variable to default values
    if (!this._persistedSelectedLabel) {
      this._persistedSelectedLabel = "none";
    }
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>): void {
    if (!this._controlViewRendered) {
      // Render header label
      let chooseColorLabel: HTMLElement = this.renderLabelDivElement(
        "Select a Color"
      );
      this._container.appendChild(chooseColorLabel);
      // Render 3 color buttons
      this._buttonGreen = this.renderButtonElement("Green", "#80ff80");
      this._container.appendChild(this._buttonGreen);
      this._buttonBlue = this.renderButtonElement("Blue", "#add8e6");
      this._container.appendChild(this._buttonBlue);
      this._buttonRed = this.renderButtonElement("Red", "#ff8080");
      this._container.appendChild(this._buttonRed);
      // Render label for 'selected color' area
      let selectedColorLabel: HTMLElement = this.renderLabelDivElement(
        "Selected Color"
      );
      this._container.appendChild(selectedColorLabel);
      // Render 'selected color' display area
      this.renderSelectedColorElement();
      this.updateSelectedColorElement(
        this._selectedColorElement,
        this._persistedSelectedLabel,
        this._persistedSelectedColor
      );
      // Mark the control view as rendered so we do not re-render next time this method is invoked
      this._controlViewRendered = true;
    }
  }
  /**
   * Creates an HTML Div Element with the provided label
   *
   * @param labelText : label for the div
   */
  private renderLabelDivElement(labelText: string): HTMLDivElement {
    let div: HTMLDivElement = document.createElement("div");
    div.innerText = labelText;
    div.classList.add("ControlState_DivLabelClass");
    return div;
  }
  /**
   * Renders a button element that the user can click to select a color
   *
   * @param label : label for the button (color name)
   * @param color : Hex code for the color
   */
  private renderButtonElement(label: string, color: string): HTMLButtonElement {
    let button: HTMLButtonElement = document.createElement("button");
    button.innerHTML = label;
    button.setAttribute("value", label);
    button.setAttribute("buttonColor", color);
    button.classList.add("ControlState_ButtonClass");
    button.addEventListener("click", event =>
      this.onButtonClick(event, this._selectedColorElement)
    );
    return button;
  }
  /**
   * This method updates the selected color element to reflect the last color the user selected.
   * The label and background color will be updated to reflect the selected color.
   *
   * @param selectedColorElement element to make the changes to
   * @param label new label for the selectedColorElement
   * @param backgroundColor new background color for the selectedColorElement
   */
  private updateSelectedColorElement(
    selectedColorElement: HTMLDivElement,
    label: string,
    backgroundColor: string
  ) {
    selectedColorElement.innerText = label;
    this._selectedColorElement.style.backgroundColor = backgroundColor;
  }
  /**
   * Renders a div Element that will contain information regarding the last color the user selected
   */
  private renderSelectedColorElement() {
    this._selectedColorElement = document.createElement("div");
    this._selectedColorElement.classList.add(
      "ControlState_SelectedColorElement"
    );
    this._container.appendChild(this._selectedColorElement);
  }
  /**
   * Onclick event handler for click of a color button
   * This method checks the button that was clicked (red / blue / green) and updates the selected color element
   * with the selected color as the element label and background
   *
   * @param event Click Event
   * @param selectedColorElement The HTML Div Element that the results should be injected into
   */
  private onButtonClick(event: Event, selectedColorElement: HTMLDivElement) {
    const eventTarget: Element = event.srcElement as Element;
    if (event.srcElement) {
      // Get the label and the selected color attributes from the div element that was clicked
      let label: string = event.srcElement.attributes.getNamedItem("value")!
        .value;
      let selectedColor: string = event.srcElement!.attributes.getNamedItem(
        "buttonColor"
      )!.value;
      // Update the selected color div element with the results
      this.updateSelectedColorElement(
        selectedColorElement,
        label,
        selectedColor
      );
      // store the label and selected color into the local state dictionary that will be passed onto the framework.
      this._stateDictionary[PERSISTED_SELECTED_Label_KEY_NAME] = label;
      this._stateDictionary[PERSISTED_SELECTED_COLOR_KEY_NAME] = selectedColor;
      // Store the state dictionary object into the setControlState interface method to allow the
      // selected data to persist within the user session
      // In scenarios where you don't need a collection of key value pairs but just one key value pair to be stored, just pass that object to the setControlState method.
      this._context.mode.setControlState(this._stateDictionary);
    }
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    return {};
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. canceling any pending remote calls, removing listeners, etc.
   */
  public destroy(): void {}
}
```

## <a name="resources"></a>资源

```css
.SampleNamespace\.TSControlStateAPI {
  font-family: "SegoeUI-Semibold", "Segoe UI Semibold", "Segoe UI Regular",
    "Segoe UI";
}
.SampleNamespace\.TSControlStateAPI .ControlState_Container {
  overflow-x: auto;
}
.SampleNamespace\.TSControlStateAPI .ControlState_ButtonClass {
  text-decoration: none;
  display: inline-block;
  font-size: 14px;
  cursor: pointer;
  color: #1160b7;
  background-color: #ffffff;
  border: 1px solid black;
  padding: 5px;
  text-align: center;
  min-width: 200px;
  margin-top: 10px;
  margin-bottom: 10px;
  display: block;
}
.SampleNamespace\.TSControlStateAPI .ControlState_SelectedColorElement {
  width: 200px;
  height: 40px;
  margin-bottom: 25px;
  text-align: center;
  padding: auto;
  font-size: 24px;
  color: rgb(51, 51, 51);
}
.SampleNamespace\.TSControlStateAPI .ControlState_DivLabelClass {
  width: 200px;
  height: 40px;
  text-align: center;
  padding: auto;
  font-size: 24px;
  color: rgb(51, 51, 51);
}

```

### <a name="related-topics"></a>相关主题

[下载示例组件](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架清单架构参考](../manifest-schema-reference/index.md)
