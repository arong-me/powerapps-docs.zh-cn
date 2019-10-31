---
title: 在 PowerApps 的列表视图中在值旁边显示自定义图标 | MicrosoftDocs
description: 了解如何在视图中显示自定义图标图形
ms.custom: ''
ms.date: 02/14/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: af866aed-2586-4b6f-bb1c-3519baae3645
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="display-custom-icons-alongside-values-in-list-views"></a>在列表视图中在值旁边显示自定义图标

<a name="GridIcons"></a>   

 PowerApps 环境管理员和定制员可以将图形添加到视图，并使用 JavaScript 建立用于基于列值选择图形的逻辑。 此功能让您可以自定义在文本旁边显示图标或数字值的列表视图。 

> [!div class="mx-imgBorder"] 
> ![](media/icon-in-opportunity-view.png "“等级”列显示图标和文本值的所有商机视图")
  
> [!NOTE]
>  网格图标仅在 Web 界面中显示。 不在 [!INCLUDE[pn_Outlook_short](../../includes/pn-outlook-short.md)] 或移动应用中显示。  
  
### <a name="add-custom-graphics-and-javascript-as-web-resources"></a>将自定义图形和 JavaScript 添加为 Web 资源  
  
1.  创建自定义所需新图形文件。 我们建议图标大小为 16x16 像素（将缩小更大的图像）。  
  
2.  编写一个或多个 JavaScript 函数，用于指定为哪些值显示哪些图标（要自定义的每个列通常需要一个函数）。 每个函数必须接受一个行数据对象和一个语言 (LCID) 代码充当输入，并返回包含图像名称和工具提示文本的任何数组。 有关示例函数，请参阅本主题中后文的[示例 JavaScript 函数](#SampleJavascript)。  
  
3.  作为管理员登录到您的环境并打开解决方案资源管理器。  
  
4.  将打开**默认解决方案**弹出窗口。 此处导航到**组件** > **Web 资源**。  
  
5.  现在您将上传自定义图形充当 Web 资源，一次一个。 选择工具栏中的**新建**按钮创建新 Web 资源。 将再打开一个弹出窗口，帮助您创建资源。 请执行以下操作：  
  
    1.  为新资源提供有意义的**名称**。 这是将用于从 JavaScript 代码引用各图形的名称。  
  
    2.  将**类型**设置为已用于保存您的图形文件的图形格式（PNG、JPEG 或 GIF）。  
  
    3.  选择**选择文件**打开文件浏览器窗口。 将其用于查找并选择图形文件。  
  
    4.  根据需要添加**显示名称**和/或**说明**。  
  
    5.  选择**保存**，然后关闭 **Web 资源**窗口。  
  
6.  为您拥有的每个图形文件重复上一步。  
  
7.  现在您将把您的 JavaScript 添加为最终 Web 资源。 选择工具栏上的**新建**按钮创建新 Web 资源。 将再打开一个弹出窗口，帮助您创建资源。 请执行以下操作：  
  
    1.  为新资源提供有意义的**名称**。  
  
    2.  将**类型**设置为**脚本(JScript)**。  
  
    3.  选择**文本编辑器**（在**类型**设置旁边）打开文本编辑器窗口。 将您的 Javascript 代码粘贴到此处，然后选择**确定**保存。  
  
    4.  根据需要添加**显示名称**和/或**说明**。  
  
    5.  选择**保存**，然后关闭 **Web 资源**窗口。  
  
8.  在**默认解决方案**弹出窗口仍然保持打开状态时，展开**组件** > **实体**树并找到要自定义的实体。  
  
9. 展开您的实体并选择其**视图**图标。  
  
10. 现在将看到您所选实体的视图列表。 从列表中选择视图。 然后打开工具栏中的**其他操作**下拉列表，然后选择**编辑**。  
  
11. 将打开一个弹出窗口，其中包含用于编辑您所选视图的控件。 它显示视图的每个列。 选择目标列，然后选择**普通任务**框中的**更改属性**按钮。 将打开**更改列属性**对话框；请在此处执行以下设置：  
  
    - **Web 资源**：指定创建来存储您的 Javascript 函数的 Web 资源的名称（选择**浏览**从列表中选择）。  
  
    - **函数名称**：键入您编写来修改所选列和视图的函数的名称。  
  
12. 选择**确定**关闭**更改列属性**对话框。  
  
13. 选择**保存并关闭**以保存您的视图。  
  
14. 根据需要为每个实体、视图和列重复这些步骤。  
  
15. 在您准备就绪时，请选择**发布所有自定义项**发布您的更改。 然后，关闭**默认解决方案**窗口。  
  
<a name="SampleJavascript"></a>   

### <a name="sample-javascript-function"></a>示例 JavaScript 函数：  
 用于显示自定义图标和工具提示的 JavaScript 函数需要下面的两个自变量：layoutxml 中指定的完整行对象和调用用户的区域设置 ID (LCID)。 LCID 参数用于指定多种语言的工具提示文本。 有关环境支持的语言的更多信息，请参阅[启用语言](/dynamics365/customer-engagement/admin/enable-languages)和[安装或升级语言包](/dynamics365/customer-engagement/on-premises/install-or-upgrade-language-packs)。 有关可在代码中使用的区域设置 ID (LCID) 值的列表，请参阅 [Microsoft 分派的区域设置 ID](https://go.microsoft.com/fwlink/?linkid=829588)。

  
 假定您将为属性的选项集类型添加自定义图标，该图标有一小组预定义的选项，那么确保使用这些选项的整数值而不是标签，以避免本地化问题。  
  
 以下示例代码根据 opportunityratingcode（等级）属性中的三个值之一（“1: 热”、“2: 暖和”、“3: 冷”）显示图标和工具提示。 此示例代码还演示如何显示已本地化的工具提示文本。 要让此示例工作，必须创建带 16x16 图像且具有以下名称的三个图像 Web 资源：new_Hot、new_Warm 和 new_Cold。  

> [!IMPORTANT]
> 此示例需要商机实体，其在 Dynamics 365 Sales 应用中提供。
  
```javascript
function displayIconTooltip(rowData, userLCID) {      
    var str = JSON.parse(rowData);  
    var coldata = str.opportunityratingcode_Value;  
    var imgName = "";  
    var tooltip = "";  
    switch (parseInt(coldata,10)) { 
        case 1:  
            imgName = "new_Hot";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Hot";  
                    break;  
                default:  
                    tooltip = "Opportunity is Hot";  
                    break;  
            }  
            break;  
        case 2:  
            imgName = "new_Warm";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Warm";  
                    break;  
                default:  
                    tooltip = "Opportunity is Warm";  
                    break;  
            }  
            break;  
        case 3:  
            imgName = "new_Cold";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Cold";  
                    break;  
                default:  
                    tooltip = "Opportunity is Cold";  
                    break;  
            }  
            break;  
        default:  
            imgName = "";  
            tooltip = "";  
            break;  
    }  
    var resultarray = [imgName, tooltip];  
    return resultarray;  
}  
```  
  
 <!-- This results in displaying icons with tooltips in the **Rating** column that depend on the value in each row. The result could look like this:  
  
 ![Custom column graphics example](../customize/media/custom-column-graphics-example.png "Custom column graphics example")  -->
 
 ### <a name="see-also"></a>另请参阅
[了解模型驱动应用程序视图](../model-driven-apps/create-edit-views.md)
