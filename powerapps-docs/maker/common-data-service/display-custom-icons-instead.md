---
title: 使用 PowerApps 在列表视图中显示自定义图标而不是值 | MicrosoftDocs
description: 了解如何在视图中显示自定义图标图形
ms.custom: ''
ms.date: 06/21/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 592d2ad73b192d7f03c552563c4f91d52f3d201d
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667942"
---
# <a name="display-custom-icons-instead-of-values-in-list-views"></a>在列表视图中显示自定义图标而不是值

<a name="GridIcons"></a>   

 PowerApps 环境管理员和定制者可向视图添加图形，还可使用 JavaScript 建立用于基于列值选择图形的逻辑。 在关系见解中引入了显示列表视图的功能，这些列表视图在某些列中显示图标而不是文本或数值。 
  
> [!NOTE]
>  网格图标仅在 Web 界面显示， 不在 [!INCLUDE[pn_Outlook_short](../../includes/pn-outlook-short.md)] 或移动应用中显示。  
  
### <a name="add-custom-graphics-and-javascript-as-web-resources"></a>添加自定义图形和 JavaScript 作为 Web 资源  
  
1.  创建进行自定义所需的新图形文件。 我们建议图标大小为 16x16 像素（较大图像将按比例缩小）。  
  
2.  编写一个或多个 JavaScript 函数，用于确定要针对哪些值显示哪些图标（通常要自定义的每列都需要一个函数）。 每个函数必须接受行数据对象和语言 (LCID) 代码作为输入，并返回包含图像名称和工具提示文本的数组。 有关示例函数，请参阅本主题后面的[示例 JavaScript 函数](#SampleJavascript)。  
  
3.  以管理员身份登录环境并打开[解决方案资源管理器](../model-driven-apps/advanced-navigation.md#solution-explorer)。  
  
4.  “默认解决方案”弹出窗口随即打开。 在此处导航到“组件” > “Web 资源”。  
  
5.  接下来，上传自定义图形（一次一个），将其作为 Web 资源。 选择工具栏中的“新建”按钮，创建新的 Web 资源。 另一个弹出窗口随即打开，用于帮助你创建资源。 执行以下操作：  
  
    1.  为新资源提供有意义的“名称”。 这是从 JavaScript 代码中引用每个图形时将使用的名称。  
  
    2.  将“类型”设置为保存图形文件时所使用的图形格式（PNG、JPEG 或 GIF）。  
  
    3.  选择“选择文件”以打开文件浏览器窗口。 使用该窗口查找并选择图形文件。  
  
    4.  如果需要，可添加“显示名称”和/或“说明”。  
  
    5.  选择“保存”，然后关闭“Web 资源”窗口。  
  
6.  对每个图形文件重复上述步骤。  
  
7.  接下来，添加 JavaScript 作为最终的 Web 资源。 选择工具栏上的“新建”，创建新的 Web 资源。 另一个弹出窗口随即打开，用于帮助你创建资源。 执行以下操作：  
  
    1.  为新资源提供有意义的“名称”。  
  
    2.  将“类型”设置为“脚本(JScript)”。  
  
    3.  选择“文本编辑器”（“类型”设置旁边），打开文本编辑器窗口。 在此处粘贴 Javascript 代码，然后选择“确定”将其保存。  
  
    4.  如果需要，可添加“显示名称”和/或“说明”。  
  
    5.  选择“保存”，然后关闭“Web 资源”窗口。  
  
8.  在“默认解决方案”弹出窗口仍处于打开状态的情况下，展开“组件” > “实体”树，找到要自定义的实体。  
  
9. 展开实体并选择其“视图”图标。  
  
10. 现在可看到所选实体的视图列表。 从列表中选择一个视图。 然后打开工具栏中的“更多操作”下拉列表，并选择“编辑”。  
  
11. 这将打开一个弹出窗口，其中包含用于编辑所选视图的控件。 该窗口显示视图中的每一列。 选择目标列，然后在“常见任务”框中选择“更改属性”。 “更改列属性”对话框随即打开，在此处进行以下设置：  
  
    - **Web 资源**：指定为保存 Javascript 函数而创建的 Web 资源的名称（选择“浏览”，从列表中进行选择）。  
  
    - **函数名称**：键入为修改所选列和视图而编写的函数的名称。  
  
12. 选择“确定”，关闭“更改列属性”对话框。  
  
13. 选择“保存并关闭”，保存视图。  
  
14. 根据需要对每个实体、视图和列重复这些步骤。  
  
15. 准备就绪后，选择“发布所有自定义项”来发布更改。 然后，关闭“默认解决方案”窗口。  
  
<a name="SampleJavascript"></a>   

### <a name="sample-javascript-function"></a>示例 JavaScript 函数  
 用于显示自定义图标和工具提示的 JavaScript 函数需要以下两个参数：layoutxml 中指定的整行对象和调用用户的区域设置 ID (LCID)。 LCID 参数可用于指定多种语言的工具提示文本。 有关环境支持的语言的详细信息，请参阅[启用语言](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages)和[安装或升级 Dynamics 365 的语言包](https://technet.microsoft.com/library/hh699674.aspx)。 有关可在代码中使用的区域设置 ID (LCID) 值的列表，请参阅 [Microsoft 分配的区域设置 ID](https://go.microsoft.com/fwlink/?linkid=829588)。

  
 假设要为选项集类型的属性（具有一组有限的预定义选项）添加自定义图标，请确保使用选项的整数值而不是标签，以避免本地化问题。  
  
 以下示例代码基于 opportunityratingcode（评级）属性中的三个值之一（1：热、2：温、3：冷）显示图标和工具提示。 该示例代码还演示如何显示本地化的工具提示文本。 要使此示例生效，必须使用 16x16 像素的图像创建三个图像 Web 资源，这些图片的名称如下：new_Hot、new_Warm 和 new_Cold。  
  
```  
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
  
 这会导致在“评级”列中显示带有工具提示的图标，这些图标取决于每行中的值。 结果可能如下所示：  
  
 ![自定义列图形示例](media/custom-column-graphics-example.png "自定义列图形示例")  
 
 ### <a name="see-also"></a>另请参阅
 [创建或编辑视图](../model-driven-apps/create-edit-views.md)
