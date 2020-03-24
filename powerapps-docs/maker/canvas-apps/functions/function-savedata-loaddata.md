---
title: SaveData 和 LoadData 函数 | Microsoft 文档
description: Power Apps 中的 SaveData 和 LoadData 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c90f0be8d1f8f62afd3fdec1701b98b434f74387
ms.sourcegitcommit: 1b29cd1fa1492037ef04188dd857a911edeb4985
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80122826"
---
# <a name="savedata-and-loaddata-functions-in-power-apps"></a>Power Apps 中的 SaveData 和 LoadData 函数
从本地设备保存和重新加载[集合](../working-with-data-sources.md#collections)。

## <a name="description"></a>说明
**SaveData** 函数会存储某个集合，以便在将来通过另一个名称来使用。  

**LoadData**函数通过以前使用**SaveData**保存的名称重新加载集合。 不能使用此函数加载另一个源的集合。  

使用这些函数可通过以下方式提高应用程序启动性能：

- 在第一次运行时在 **[app.config](../controls/control-screen.md#additional-properties)** 公式中缓存数据。
- 下次运行时重新加载本地缓存。

你还可以使用这些函数向应用添加[简单的脱机功能](../offline-apps.md)。

在以下情况中，不能在浏览器中使用这些函数：

- 在 Power Apps Studio 中创作应用程序。
- 在 web 播放器中运行应用。 

若要测试你的应用，请在 iPhone 或 Android 设备上的 Power Apps Mobile 中运行它。

这些函数在内存中集合操作时受可用应用内存量的限制。 可用内存可能因以下因素而异： 

- 设备和操作系统。
- Power Apps 播放机使用的内存。
- 具有屏幕和控件的应用的复杂性。 

在应用程序类型上测试应用程序，该应用程序在存储大数据时希望应用程序能够运行。 预计有 30 MB 到 70 MB 的可用内存。

这些函数依赖于通过 **[收集](function-clear-collect-clearcollect.md)** 或 **[ClearCollect](function-clear-collect-clearcollect.md)** 隐式定义的集合。 无需调用**Collect**或**ClearCollect**将数据加载到集合中来定义它。 在以前的**SaveData**中使用**LoadData**时，通常会出现这种情况。  所有所需的都是在公式中存在这些函数以隐式定义集合的结构。  有关详细信息，请参阅[创建和删除变量](../working-with-variables.md#create-and-remove-variables)。

加载的数据将追加到集合中。 如果要从空集合开始，请在调用**LoadData**之前使用 **[Clear](function-clear-collect-clearcollect.md)** 函数。

设备的内置应用沙盒功能用于将保存的数据与其他应用隔离。 

设备还可以加密数据;或者，可以使用移动设备管理工具，如[Microsoft Intune](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune)。

## <a name="syntax"></a>语法
**SaveData**( *Collection*, *Name* )<br>**LoadData**( *Collection*, *Name* [, *IgnoreNonexistentFile* ])

* *Collection* - 必需。  要存储或加载的集合。
* *Name* - 必需。  存储的名称。 该名称必须相同才能保存和加载相同的数据集。 命名空间不与其他应用或用户共享。
* *IgnoreNonexistentFile* - 可选。 一个布尔值，指示在文件不存在时要执行的操作。  使用*false* （默认值）可返回错误，使用*true*可禁止显示错误。   

## <a name="examples"></a>示例

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **SaveData （LocalCache，"MyCache"）** | 将**LocalCache**集合保存到名为 "MyCache" 的用户设备上，适用于稍后要检索的**LoadData** 。 | 数据保存到本地设备。 |
| **LoadData （LocalCache，"MyCache"）** | 将名为 "MyCache" 的用户设备中的**LocalCache**集合加载到以前，并调用**SaveData**。  | 将从本地设备中加载数据。 |   

### <a name="simple-offline-example"></a>简单的脱机示例

以下简单示例在脱机时捕获并存储日常项目的名称和图片。  它将信息存储在设备的本地存储区中供以后使用。 这允许关闭应用，或者在不丢失数据的情况下重新启动设备。  

你必须有一个设备来处理此示例，因为它使用在 web 浏览器中不会运行的**LoadData**和**SaveData**函数。

1. 使用平板电脑布局创建一个空画布应用。  有关更多详细信息，请阅读[从模板创建应用](../get-started-test-drive.md)，并选择 "**空白应用**" 下的 " **Tablet 布局**"。  

1. 添加 "[**文本输入**](../controls/control-text-input.md)" 控件和 "[**照相机**](../controls/control-camera.md)" 控件，并按如下所示大致排列它们：
    > [!div class="mx-imgBorder"]  
    > ![添加到空白屏幕上的文本输入和相机控件](media/function-savedata-loaddata/simple-text-camera.png)

1. 添加[**按钮**](../controls/control-button.md)控件。

2. 双击按钮控件，将按钮文本更改为 "**添加项**" （或修改 " **text** " 属性）。

3. 将 "button" 控件的 " **OnSelect** " 属性设置为此公式，此公式将向集合添加项：
    ```powerapps-dot
    Collect( MyItems, { Item: TextInput1.Text, Picture: Camera1.Photo } )
    ```
    > [!div class="mx-imgBorder"] 
    > ![使用文本 "Add Item" 和 OnSelect 属性集添加的按钮控件](media/function-savedata-loaddata/simple-additem.png)

1. 添加另一个**按钮**控件。

2. 双击按钮控件，更改按钮文本以**保存数据**（或修改**text**属性）。

3. 将按钮控件的 " **OnSelect** " 属性设置为此公式，以便将集合保存到本地设备：
    ```powerapps-dot
    SaveData( MyItems, "LocalSavedItems" )
    ```
    > [!div class="mx-imgBorder"] 
    > ![使用文本 "Save Data" 和 OnSelect 属性集添加的按钮控件](media/function-savedata-loaddata/simple-savedata.png)

    测试按钮非常有吸引力，因为它不会影响任何内容。 但在 web 浏览器中创作时，只会看到错误。 请先保存该应用，然后在设备上打开，然后再执行后续步骤来测试此公式：

1. 添加第三个**按钮**控件。

2. 双击按钮控件，更改按钮文本以**加载数据**（或修改**text**属性）。

3. 将按钮控件的 " **OnSelect** " 属性设置为此公式，以便从本地设备加载集合：
    ```powerapps-dot
    LoadData( MyItems, "LocalSavedItems" )
    ``` 
    > [!div class="mx-imgBorder"] 
    > ![用文本 "Load Data" 和 OnSelect 属性集添加的按钮控件](media/function-savedata-loaddata/simple-loaddata.png)

1. 添加具有垂直布局的[**库**](../controls/control-gallery.md)控件，其中包括图片和文本区域： 
    > [!div class="mx-imgBorder"] 
    > ![库各种选择，将 "垂直" 选有图像和文本区域](media/function-savedata-loaddata/simple-gallery-add.png)

1. 出现提示时，选择**MyItems**集合作为此库的数据源。  这会设置**库**控件的**Items**属性： 
    > [!div class="mx-imgBorder"] 
    > ![库选择 "数据源"](media/function-savedata-loaddata/simple-gallery-collection.png) 库模板中的 "图像" 控件应将其 " **image** " 属性默认为 " **ThisItem** "，并且 "标签" 控件应将其 "**文本**" 属性设置为 " **ThisItem**"。  如果在以下步骤中添加项后，请检查这些公式。在库中看不到任何内容。 

1. 将控件置于其他控件的右侧： 
    > [!div class="mx-imgBorder"] 
    > ![库重新定位在屏幕的右侧](media/function-savedata-loaddata/simple-gallery-placed.png)

1. 保存您的应用程序。  如果是第一次保存，则无需发布。 如果不是第一次，请在保存后发布应用。

1. 在手机或平板电脑等设备上打开应用。  **SaveData**和**LoadData**不能在 Studio 或 web 浏览器中使用。  刷新应用列表如果你没有立即看到应用，可能需要几秒钟时间，应用才会显示在你的设备上。  注销并重新登录到你的帐户也会有所帮助。
    > [!div class="mx-imgBorder"] 
    > ![应用运行时未添加任何项](media/function-savedata-loaddata/simple-mobile.png) 应用下载后，可以断开与网络的连接并脱机运行应用。

1. 输入名称，并拍照一项。

2. 选择 "**添加项**" 按钮。  重复多次添加项以加载集合。
    > [!div class="mx-imgBorder"] 
    > 添加了三项的 ![应用](media/function-savedata-loaddata/simple-mobile-with3.png) 

1. 选择 "**保存数据**" 按钮。  这会将集合中的数据保存到本地设备。

1. 关闭应用。  内存中的集合将丢失，包括所有项名称和图片，但它们仍会出现在设备的存储中。

1. 重新启动应用。  内存中的集合将再次在库中显示为空。
    > [!div class="mx-imgBorder"] 
    > ![应用再次运行，但未添加任何项](media/function-savedata-loaddata/simple-mobile.png) 

1. 选择 "**加载数据**" 按钮。  该集合将从设备上存储的数据重新填充，并且你的项将返回到库中。  该集合在此按钮调用**LoadData**函数之前为空;从存储加载数据之前，无需调用**Collect**或**ClearCollect** 。
    > [!div class="mx-imgBorder"] 
    > 在调用 LoadData 函数后，运行了三个项目的 ![应用](media/function-savedata-loaddata/simple-mobile-load1.png) 

1. 再次选择 "**加载数据**" 按钮。  存储的数据将追加到集合的末尾，并且滚动条将出现在库中。  如果要替换而不是追加，请在调用**LoadData**函数之前，先使用**clear**函数清除该集合。
    > [!div class="mx-imgBorder"] 
    > 在调用 LoadData 函数两次后，运行的 ![应用会还原六个项](media/function-savedata-loaddata/simple-mobile-load2.png) 
 
### <a name="more-advanced-offline-example"></a>更高级的脱机示例

有关详细示例，请参阅有关[简单脱机功能](../offline-apps.md)的文章。







