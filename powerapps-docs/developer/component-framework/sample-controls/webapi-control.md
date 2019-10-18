---
title: " Web API 组件 |Microsoft Docs"
description: 实现 Web API 组件
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: nkrb
ms.openlocfilehash: 4e893466a5a7404926942b4e297cdc4ecb1affef
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340152"
---
# <a name="implementing-web-api-component"></a>实现 Web API 组件

Web API 组件旨在执行创建、检索、更新和删除操作。 组件呈现四个按钮，单击这些按钮可调用不同的 Web API 操作。 Web API 调用的结果被注入到代码组件底部的 HTML div 元素中。  

> [!div class="mx-imgBorder"]
> ![WEB api 组件](../media/web-api-control.png "web api 组件")

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="manifest"></a>体现

 ```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSWebAPI" version="1.0.0" display-name-key="TS_WebAPI_Display_Key" description-key="TS_WebAPI_Desc_Display_Key" control-type="standard">
        <property name="stringProperty" display-name-key="stringProperty_Display_Key" description-key="stringProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_WebAPI.css" order="2" />
        </resources>
        <feature-usage>
            <uses-feature name="WebAPI" required="true" />
        </feature-usage>
    </control>
</manifest>
```

## <a name="code"></a>代码

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSWebAPI
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // reference to the control container HTMLDivElement
  // This element contains all elements of our custom control example
  private _container: HTMLDivElement;
  // reference to ComponentFramework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // Name of entity to use for example Web API calls performed by this control
  private static _entityName: string = "account";
  // Required field on _entityName of type 'single line of text'
  // Example Web API calls performed by example custom control will set this field for new record creation examples
  private static _requiredAttributeName: string = "name";
  // Value the _requiredAttributeName field will be set to for new created records
  private static _requiredAttributeValue: string =
    "Web API Custom Control (Sample)";
  // Name of currency field on _entityName to populate during record create
  // Example Web API calls performed by example custom control will set and read this field
  private static _currencyAttributeName: string = "revenue";
  // Friendly name of currency field (only used for control UI - no functional impact)
  private static _currencyAttributeNameFriendlyName: string = "annual revenue";
  // Flag if control view has been rendered
  private _controlViewRendered: Boolean;
  // references to button elements rendered by example custom control
  private _createEntity1Button: HTMLButtonElement;
  private _createEntity2Button: HTMLButtonElement;
  private _createEntity3Button: HTMLButtonElement;
  private _deleteRecordButton: HTMLButtonElement;
  private _fetchXmlRefreshButton: HTMLButtonElement;
  private _oDataRefreshButton: HTMLButtonElement;
  // references to div elements rendered by the example custom control
  private _odataStatusContainerDiv: HTMLDivElement;
  private _resultContainerDiv: HTMLDivElement;
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
    this._context = context;
    this._controlViewRendered = false;
    this._container = document.createElement("div");
    this._container.classList.add("TSWebAPI_Container");
    container.appendChild(this._container);
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>): void {
    if (!this._controlViewRendered) {
      this._controlViewRendered = true;
      // Render Web API Examples
      this.renderCreateExample();
      this.renderDeleteExample();
      this.renderFetchXmlRetrieveMultipleExample();
      this.renderODataRetrieveMultipleExample();
      // Render result div to display output of Web API calls
      this.renderResultsDiv();
    }
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
  /**
   * Renders example use of CreateRecord Web API
   */
  private renderCreateExample() {
    // Create header label for Web API sample
    let headerDiv: HTMLDivElement = this.createHTMLDivElement(
      "create_container",
      true,
      "Click to create " + TSWebAPI._entityName + " record"
    );
    this._container.appendChild(headerDiv);
    // Create button 1 to create record with revenue field set to 100
    let value1: string = "100";
    this._createEntity1Button = this.createHTMLButtonElement(
      this.getCreateRecordButtonLabel(value1),
      this.getCreateButtonId(value1),
      value1,
      this.createButtonOnClickHandler.bind(this)
    );
    // Create button 2 to create record with revenue field set to 200
    let value2: string = "200";
    this._createEntity2Button = this.createHTMLButtonElement(
      this.getCreateRecordButtonLabel(value2),
      this.getCreateButtonId(value2),
      value2,
      this.createButtonOnClickHandler.bind(this)
    );
    // Create button 3 to create record with revenue field set to 300
    let value3: string = "300";
    this._createEntity3Button = this.createHTMLButtonElement(
      this.getCreateRecordButtonLabel(value3),
      this.getCreateButtonId(value3),
      value3,
      this.createButtonOnClickHandler.bind(this)
    );
    // Append all button HTML elements to custom control container div
    this._container.appendChild(this._createEntity1Button);
    this._container.appendChild(this._createEntity2Button);
    this._container.appendChild(this._createEntity3Button);
  }
  /**
   * Renders example use of DeleteRecord Web API
   */
  private renderDeleteExample(): void {
    // Create header label for Web API sample
    let headerDiv: HTMLDivElement = this.createHTMLDivElement(
      "delete_container",
      true,
      "Click to delete " + TSWebAPI._entityName + " record"
    );
    // Render button to invoke DeleteRecord Web API call
    this._deleteRecordButton = this.createHTMLButtonElement(
      "Select record to delete",
      "delete_button",
      null,
      this.deleteButtonOnClickHandler.bind(this)
    );
    // Append elements to custom control container div
    this._container.appendChild(headerDiv);
    this._container.appendChild(this._deleteRecordButton);
  }
  /**
   * Renders example use of RetrieveMultiple Web API with OData
   */
  private renderODataRetrieveMultipleExample(): void {
    let containerClassName: string = "odata_status_container";
    // Create header label for Web API sample
    let statusDivHeader: HTMLDivElement = this.createHTMLDivElement(
      containerClassName,
      true,
      "Click to refresh record count"
    );
    this._odataStatusContainerDiv = this.createHTMLDivElement(
      containerClassName,
      false,
      undefined
    );
    // Create button to invoke OData RetrieveMultiple Example
    this._fetchXmlRefreshButton = this.createHTMLButtonElement(
      "Refresh record count",
      "odata_refresh",
      null,
      this.refreshRecordCountButtonOnClickHandler.bind(this)
    );
    // Append HTML elements to custom control container div
    this._container.appendChild(statusDivHeader);
    this._container.appendChild(this._odataStatusContainerDiv);
    this._container.appendChild(this._fetchXmlRefreshButton);
  }
  /**
   * Renders example use of RetrieveMultiple Web API with Fetch XML
   */
  private renderFetchXmlRetrieveMultipleExample(): void {
    let containerName: string = "fetchxml_status_container";
    // Create header label for Web API sample
    let statusDivHeader: HTMLDivElement = this.createHTMLDivElement(
      containerName,
      true,
      "Click to calculate average value of " +
        TSWebAPI._currencyAttributeNameFriendlyName
    );
    let statusDiv: HTMLDivElement = this.createHTMLDivElement(
      containerName,
      false,
      undefined
    );
    // Create button to invoke Fetch XML RetrieveMultiple Web API example
    this._oDataRefreshButton = this.createHTMLButtonElement(
      "Calculate average value of " +
        TSWebAPI._currencyAttributeNameFriendlyName,
      "odata_refresh",
      null,
      this.calculateAverageButtonOnClickHandler.bind(this)
    );
    // Append HTML Elements to custom control container div
    this._container.appendChild(statusDivHeader);
    this._container.appendChild(statusDiv);
    this._container.appendChild(this._oDataRefreshButton);
  }
  /**
   * Renders a 'result container' div element to inject the status of the example Web API calls
   */
  private renderResultsDiv() {
    // Render header label for result container
    let resultDivHeader: HTMLDivElement = this.createHTMLDivElement(
      "result_container",
      true,
      "Result of last action"
    );
    this._container.appendChild(resultDivHeader);
    // Div elements to populate with the result text
    this._resultContainerDiv = this.createHTMLDivElement(
      "result_container",
      false,
      undefined
    );
    this._container.appendChild(this._resultContainerDiv);
    // Init the result container with a notification the control was loaded
    this.updateResultContainerText("Web API sample custom control loaded");
  }
  /**
   * Event Handler for onClick of create record button
   * @param event : click event
   */
  private createButtonOnClickHandler(event: Event): void {
    // Retrieve the value to set the currency field to from the button's attribute
    let currencyAttributeValue: Number = parseInt(
      event.srcElement!.attributes.getNamedItem("buttonvalue")!.value
    );
    // Generate unique record name by appending timestamp to _requiredAttributeValue
    let recordName: string =
      TSWebAPI._requiredAttributeValue + "_" + Date.now();
    // Set the values for the attributes we want to set on the new record
    // If you want to set additional attributes on the new record, add to data dictionary as key/value pair
    var data: any = {};
    data[TSWebAPI._requiredAttributeName] = recordName;
    data[TSWebAPI._currencyAttributeName] = currencyAttributeValue;
    // store reference to 'this' so it can be used in the callback method
    var thisRef = this;
    // Invoke the Web API to creat the new record
    this._context.webAPI.createRecord(TSWebAPI._entityName, data).then(
      function(response: ComponentFramework.Entityreference) {
        // Callback method for successful creation of new record
        // Get the ID of the new record created
        let id: string = response.id;
        // Generate HTML to inject into the result div to showcase the fields and values of the new record created
        let resultHtml: string =
          "Created new " + TSWebAPI._entityName + " record with below values:";
        resultHtml += "<br />";
        resultHtml += "<br />";
        resultHtml += "id: " + id;
        resultHtml += "<br />";
        resultHtml += "<br />";
        resultHtml += TSWebAPI._requiredAttributeName + ": " + recordName;
        resultHtml += "<br />";
        resultHtml += "<br />";
        resultHtml +=
          TSWebAPI._currencyAttributeName + ": " + currencyAttributeValue;
        thisRef.updateResultContainerText(resultHtml);
      },
      function(errorResponse: any) {
        // Error handling code here - record failed to be created
        thisRef.updateResultContainerTextWithErrorResponse(errorResponse);
      }
    );
  }
  /**
   * Event Handler for onClick of delete record button
   * @param event : click event
   */
  private deleteButtonOnClickHandler(): void {
    // Invoke a lookup dialog to allow the user to select an existing record of type _entityName to delete
    var lookUpOptions: any = {
      entityTypes: [TSWebAPI._entityName]
    };
    // store reference to 'this' so it can be used in the callback method
    var thisRef = this;
    var lookUpPromise: any = this._context.utils.lookupObjects(lookUpOptions);
    lookUpPromise.then(
      // Callback method - invoked after user has selected an item from the lookup dialog
      // Data parameter is the item selected in the lookup dialog
      (data: ComponentFramework.Entityreference[]) => {
        if (data && data[0]) {
          // Get the ID and entityType of the record selected by the lookup
          let id: string = data[0].id;
          let entityType: string = data[0].entityType!;
          // Invoke the deleteRecord method of the WebAPI to delete the selected record
          this._context.webAPI.deleteRecord(entityType, id).then(
            function(response: ComponentFramework.Entityreference) {
              // Record was deleted successfully
              let responseId: string = response.id;
              let responseEntityType: string = response.entityType!;
              // Generate HTML to inject into the result div to showcase the deleted record
              thisRef.updateResultContainerText(
                "Deleted " +
                  responseEntityType +
                  " record with ID: " +
                  responseId
              );
            },
            function(errorResponse: any) {
              // Error handling code here
              thisRef.updateResultContainerTextWithErrorResponse(errorResponse);
            }
          );
        }
      },
      (error: any) => {
        // Error handling code here
        thisRef.updateResultContainerTextWithErrorResponse(error);
      }
    );
  }
  /**
   * Event Handler for onClick of calculate average value button
   * @param event : click event
   */
  private calculateAverageButtonOnClickHandler(): void {
    // Build FetchXML to retrieve the average value of _currencyAttributeName field for all _entityName records
    // Add a filter to only aggregate on records that have _currencyAttributeName not set to null
    let fetchXML: string =
      "<fetch distinct='false' mapping='logical' aggregate='true'>";
    fetchXML += "<entity name='" + TSWebAPI._entityName + "'>";
    fetchXML +=
      "<attribute name='" +
      TSWebAPI._currencyAttributeName +
      "' aggregate='avg' alias='average_val' />";
    fetchXML += "<filter>";
    fetchXML +=
      "<condition attribute='" +
      TSWebAPI._currencyAttributeName +
      "' operator='not-null' />";
    fetchXML += "</filter>";
    fetchXML += "</entity>";
    fetchXML += "</fetch>";
    // store reference to 'this' so it can be used in the callback method
    var thisRef = this;
    // Invoke the Web API RetrieveMultipleRecords method to calculate the aggregate value
    this._context.webAPI
      .retrieveMultipleRecords(TSWebAPI._entityName, "?fetchXml=" + fetchXML)
      .then(
        function(response: ComponentFramework.WebApi.RetrieveMultipleResponse) {
          // Retrieve multiple completed successfully -- retrieve the averageValue
          let averageVal: Number = response.entities[0].average_val;
          // Generate HTML to inject into the result div to showcase the result of the RetrieveMultiple Web API call
          let resultHTML: string =
            "Average value of " +
            TSWebAPI._currencyAttributeNameFriendlyName +
            " attribute for all " +
            TSWebAPI._entityName +
            " records: " +
            averageVal;
          thisRef.updateResultContainerText(resultHTML);
        },
        function(errorResponse: any) {
          // Error handling code here
          thisRef.updateResultContainerTextWithErrorResponse(errorResponse);
        }
      );
  }
  /**
   * Event Handler for onClick of calculate record count button
   * @param event : click event
   */
  private refreshRecordCountButtonOnClickHandler(): void {
    // Generate OData query string to retrieve the _currencyAttributeName field for all _entityName records
    // Add a filter to only retrieve records with _requiredAttributeName field which contains _requiredAttributeValue
    let queryString: string =
      "?$select=" +
      TSWebAPI._currencyAttributeName +
      "&$filter=contains(" +
      TSWebAPI._requiredAttributeName +
      ",'" +
      TSWebAPI._requiredAttributeValue +
      "')";
    // store reference to 'this' so it can be used in the callback method
    var thisRef = this;
    // Invoke the Web API Retrieve Multiple call
    this._context.webAPI
      .retrieveMultipleRecords(TSWebAPI._entityName, queryString)
      .then(
        function(response: any) {
          // Retrieve Multiple Web API call completed successfully
          let count1: number = 0;
          let count2: number = 0;
          let count3: number = 0;
          // Loop through each returned record
          for (let entity of response.entities) {
            // Retrieve the value of _currencyAttributeName field
            let value: Number = entity[TSWebAPI._currencyAttributeName];
            // Check the value of _currencyAttributeName field and increment the correct counter
            if (value == 100) {
              count1++;
            } else if (value == 200) {
              count2++;
            } else if (value == 300) {
              count3++;
            }
          }
          // Generate HTML to inject into the fetch xml status div to showcase the results of the OData retrieve example
          let innerHtml: string =
            "Use above buttons to create or delete a record to see count update";
          innerHtml += "<br />";
          innerHtml += "<br />";
          innerHtml +=
            "Count of " +
            TSWebAPI._entityName +
            " records with " +
            TSWebAPI._currencyAttributeName +
            " of 100: " +
            count1;
          innerHtml += "<br />";
          innerHtml +=
            "Count of " +
            TSWebAPI._entityName +
            " records with " +
            TSWebAPI._currencyAttributeName +
            " of 200: " +
            count2;
          innerHtml += "<br />";
          innerHtml +=
            "Count of " +
            TSWebAPI._entityName +
            " records with " +
            TSWebAPI._currencyAttributeName +
            " of 300: " +
            count3;
          // Inject the HTML into the fetch xml status div
          if (thisRef._odataStatusContainerDiv) {
            thisRef._odataStatusContainerDiv.innerHTML = innerHtml;
          }
          // Inject a success message into the result div
          thisRef.updateResultContainerText("Record count refreshed");
        },
        function(errorResponse: any) {
          // Error handling code here
          thisRef.updateResultContainerTextWithErrorResponse(errorResponse);
        }
      );
  }
  /**
   * Helper method to inject HTML into result container div
   * @param statusHTML : HTML to inject into result container
   */
  private updateResultContainerText(statusHTML: string): void {
    if (this._resultContainerDiv) {
      this._resultContainerDiv.innerHTML = statusHTML;
    }
  }
  /**
   * Helper method to inject error string into result container div after failed Web API call
   * @param errorResponse : error object from rejected promise
   */
  private updateResultContainerTextWithErrorResponse(errorResponse: any): void {
    if (this._resultContainerDiv) {
      // Retrieve the error message from the errorResponse and inject into the result div
      let errorHTML: string = "Error with Web API call:";
      errorHTML += "<br />";
      errorHTML += errorResponse.message;
      this._resultContainerDiv.innerHTML = errorHTML;
    }
  }
  /**
   * Helper method to generate Label for Create Buttons
   * @param entityNumber : value to set _currencyAttributeNameFriendlyName field to for this button
   */
  private getCreateRecordButtonLabel(entityNumber: string): string {
    return (
      "Create record with " +
      TSWebAPI._currencyAttributeNameFriendlyName +
      " of " +
      entityNumber
    );
  }
  /**
   * Helper method to generate ID for Create Button
   * @param entityNumber : value to set _currencyAttributeNameFriendlyName field to for this button
   */
  private getCreateButtonId(entityNumber: string): string {
    return "create_button_" + entityNumber;
  }
  /**
   * Helper method to create HTML Button used for CreateRecord Web API Example
   * @param buttonLabel : Label for button
   * @param buttonId : ID for button
   * @param buttonValue : value of button (attribute of button)
   * @param onClickHandler : onClick event handler to invoke for the button
   */
  private createHTMLButtonElement(
    buttonLabel: string,
    buttonId: string,
    buttonValue: string | null,
    onClickHandler: (event?: any) => void
  ): HTMLButtonElement {
    let button: HTMLButtonElement = document.createElement("button");
    button.innerHTML = buttonLabel;
    if (buttonValue) {
      button.setAttribute("buttonvalue", buttonValue);
    }
    button.id = buttonId;
    button.classList.add("SampleControl_WebAPI_ButtonClass");
    button.addEventListener("click", onClickHandler);
    return button;
  }
  /**
   * Helper method to create HTML Div Element
   * @param elementClassName : Class name of div element
   * @param isHeader : True if 'header' div - adds extra class and post-fix to ID for header elements
   * @param innerText : innerText of Div Element
   */
  private createHTMLDivElement(
    elementClassName: string,
    isHeader: boolean,
    innerText?: string
  ): HTMLDivElement {
    let div: HTMLDivElement = document.createElement("div");
    if (isHeader) {
      div.classList.add("SampleControl_WebAPI_Header");
      elementClassName += "_header";
    }
    if (innerText) {
      div.innerText = innerText.toUpperCase();
    }
    div.classList.add(elementClassName);
    return div;
  }
}
```

## <a name="resources"></a>资源

```css
.SampleNamespace\.TSWebAPI {
  font-family: "SegoeUI-Semibold", "Segoe UI Semibold", "Segoe UI Regular",
    "Segoe UI";
  color: #1160b7;
}
.SampleNamespace\.TSWebAPI .TSWebAPI_Container {
  overflow-x: auto;
}
.SampleNamespace\.TSWebAPI .SampleControl_WebAPI_Header {
  color: rgb(51, 51, 51);
  font-size: 1rem;
  padding-top: 20px;
}
.SampleNamespace\.TSWebAPI .result_container {
  padding-bottom: 20px;
}
.SampleNamespace\.TSWebAPI .SampleControl_WebAPI_ButtonClass {
  text-decoration: none;
  display: inline-block;
  font-size: 14px;
  cursor: pointer;
  color: #1160b7;
  background-color: #ffffff;
  border: 1px solid black;
  padding: 5px;
  text-align: center;
  min-width: 300px;
  margin-top: 10px;
  margin-bottom: 5px;
  display: block;
}
```

默认情况下，在示例中，该组件配置为对 `Account` 实体执行创建、检索、更新操作，并在 Web API 示例中设置名称和收入字段。

若要更改任何实体或字段的默认配置，请按如下所示更新以下配置值  

 ```TypeScript
  private static _entityName:string = "account";  
  private static _requiredAttributeName: string = "name";  
  private static _requiredAttributeValue: string = "Web API code component (Sample)";  
  private static _currencyAttributeName: string = "revenue";  
 ```

@No__t_0 方法将呈现三个按钮，这允许你创建一个将 "收入" 字段设置为不同值（100、200、300）的帐户记录。

单击其中一个 "创建" 按钮时，按钮的 `onClick` 事件处理程序将检查所单击按钮的值，然后使用 "Web API 操作" 创建一个帐户记录，并将 "收入" 字段设置为按钮的值。 帐户记录的 "名称" 字段将设置为 `Web API code component (Sample)`，并将随机 `int` 追加到字符串的末尾。 来自 Web API 调用的回调方法将 Web API 调用（成功或失败）的结果注入到自定义控件的结果 div 中。  
 
@No__t_0 方法将呈现一个按钮，单击该按钮可打开查找对话框。 "查找" 对话框允许您选择要删除的帐户记录。 从查找对话框中选择帐户记录后，它将传递到 `deleteRecord` 以从数据库中删除该记录。 来自 Web API 调用的回调方法将 Web API 调用（成功或失败）的结果注入到自定义控件的结果 div 中。  

FetchXML `retrieveMultiple` 方法呈现代码组件中的按钮。 此按钮的 `onClick`，将生成 FetchXML，并将其传递给 `retrieveMultiple` 函数，以便计算所有帐户记录的收入字段的平均值。 来自 Web API 调用的回调方法将 Web API 调用（成功或失败）的结果注入到自定义控件的结果 div 中。  

OData `retrieveMultiple` 方法呈现代码组件中的按钮。 此按钮的 `onClick` 中，将生成 OData 字符串并将其传递给 `retrieveMultiple` 函数，以检索名称字段类似于 "代码组件 Web API （示例）" 的所有帐户记录，这对于此代码组件示例创建的所有帐户记录均为 true。  

成功检索记录后，代码组件包含的逻辑可用于计算多少个帐户记录的收入字段设置为100、200或300，并将此计数显示在代码组件的 odata 状态容器 div 中。  来自 Web API 调用的回调方法将 Web API 调用（成功或失败）的结果注入到自定义控件的结果 div 中。  

### <a name="related-topics"></a>相关主题

[下载示例组件](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架清单架构参考](../manifest-schema-reference/index.md)
