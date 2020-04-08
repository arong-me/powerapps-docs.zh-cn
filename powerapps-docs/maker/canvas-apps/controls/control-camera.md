---
title: 照相机控件：参考 | Microsoft 文档
description: 有关照相机控件的信息，包括属性和示例
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/07/2020
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 59c0f85dd71c9dc512e348d6d8ee9686d6945fa1
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80871111"
---
# <a name="camera-control-in-power-apps"></a>Power Apps 中的相机控件

使用户能够在设备上使用相机拍摄照片的控件。

## <a name="description"></a>说明

使用 "**照相机**" 控件来捕获带有设备照相机的照片。  设备必须具有照相机并且用户必须授权应用程序使用相机。 在 web 浏览器中运行时，支持相机控件。

最近捕获的图片通过**Photo**属性提供。 对于此属性，图像可以是：

- **用图像控件查看。** 使用 "[图像](control-image.md)" 控件查看捕获的映像。 有关详细信息，请参阅[示例](#examples)。  
- **临时放入变量或集合。**  使用[Set](../functions/function-set.md)或[Collect](../functions/function-clear-collect-clearcollect.md)函数将图像存储在变量或集合中。  在使用设备的有限内存的同时，使用集合中的多个图像时要格外小心。 使用[SaveData](../functions/function-savedata-loaddata.md)和[LoadData](../functions/function-savedata-loaddata.md)函数将图像移到设备上的本地存储和[脱机方案](../offline-apps.md)。
- **存储在数据库中。**  使用[Patch](../functions/function-patch.md)函数可在数据库中存储图像。
- **作为 base64 编码文本字符串传输。**  使用[JSON](../functions/function-json.md)函数对图像进行 base64 编码。

使用 " **Stream**"、" **StreamRate**" 和 " **OnStream** " 属性可自动捕获计时器上的图像，例如，每分钟移动一张图片以创建一个时间间隔序列。

捕获的媒体由文本字符串 URI 引用。 有关详细信息，请参阅[数据类型文档](../functions/data-types.md#uris-for-images-and-other-media)。

照相机控件生成的图像通常不是相机的完整分辨率。 如果需要完整的分辨率图像，请使用 "[添加图片](control-add-picture.md)" 控件。

## <a name="key-properties"></a>关键属性

**AvailableDevices** –设备上可用相机的表。

表包含两列： 
- 要与**相机**属性一起使用的*Id*号 
- 设备提供的用于标识相机的*名称*。 某些平台可能包括*正面*或*背面*，以帮助找到照相机。

*注意*：并非表中的所有设备都可在应用中使用。  有些特定的驱动程序或应用程序可能专门用于特定目的。  

**照相机**–要使用的照相机的数字 ID。  对于具有多个照相机的设备很有用。  

**OnStream** - 更新 **Stream** 属性时应用的响应方式。

**照片**–用户拍摄照片时捕获的图像。 

**Stream** - 基于 **StreamRate** 属性自动更新的图像。

**StreamRate** - 在 **Stream** 属性上更新图像的频率（以毫秒为单位）。 此值的范围为 100（1/10 秒）到 3,600,000（1 小时）。

## <a name="additional-properties"></a>其他属性

[AccessibleLabel](properties-accessibility.md) – 屏幕阅读器标签。 应描述拍照的用途。

[BorderColor](properties-color-border.md)：控件边框的颜色。

[BorderStyle](properties-color-border.md)：控件边框是“实线”、“虚线”、“点线”还是“无”。

[BorderThickness](properties-color-border.md)：控件边框的粗细。

**Brightness** - 用户在图像中可能感知到的光线强度。

**Contrast** - 用户可区分图像中相似颜色的轻松程度。

[DisplayMode](properties-core.md) –控件是允许用户输入（**Edit**）、仅显示数据（**View**），还是已禁用（**disabled**）。

[FocusedBorderColor](properties-color-border.md) –控件聚焦时控件边框的颜色。

[FocusedBorderThickness](properties-color-border.md) –控件聚焦时控件边框的粗细。

[Height](properties-size-location.md) - 控件上边缘和下边缘之间的距离。

[OnSelect](properties-core.md)：用户点击或单击控件时应用的响应方式。

[TabIndex](properties-accessibility.md) –相对于其他控件的键盘导航顺序。

[Tooltip](properties-core.md)：用户将鼠标悬停在控件上时显示的解释性文本。

[Visible](properties-core.md)：控件显示还是隐藏。

[Width](properties-size-location.md) - 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) –控件左边缘与其父容器或屏幕左边缘之间的距离。

[Y](properties-size-location.md) -控件上边缘和父容器或屏幕上边缘之间的距离。

## <a name="examples"></a>示例

对于这些示例，需要一个带有照相机的设备。 若要测试应用，请使用浏览器可访问的 web cam。 或者，通过保存应用并将其加载到带有照相机的 iOS 或 Android 设备。

### <a name="simple-display-of-a-captured-picture"></a>简单显示拍摄的图片

1. [添加](../add-configure-controls.md)**相机**控件。

1. 在出现提示时，授权应用程序使用设备的照相机。

1. 添加[**图像**](../controls/control-image.md)控件。

1. 将**image**控件的**image**属性设置为以下公式：

    ```powerapps-dot
    Camera1.Photo
    ```

    > [!NOTE]
    > 根据需要替换摄像控件名称*Camera1* 。

1. 按 F5 预览应用程序。

1. 通过选择或点击 "照相机" 控件拍摄图片。 你应会在图像控件中看到结果。

### <a name="add-pictures-to-an-image-gallery-control"></a>向图像库控件添加图片

1. 添加 "**照相机**" 控件，将其命名为**mycamera.photo**，并将其[OnSelect](properties-core.md)属性设置为以下公式：

    ```powerapps-dot
    Collect( MyPix, MyCamera.Photo )
    ```

    有关详细信息，请参阅：

    - [如何添加、命名和配置控件？](../add-configure-controls.md)
    - 阅读有关[收集](../functions/function-clear-collect-clearcollect.md)函数或[其他函数](../formula-reference.md)的详细信息。

1. 按 F5，然后通过选择或点击 " **mycamera.photo**" 拍摄图片。

1. 添加[垂直库](control-gallery.md)控件。 然后调整其[图像](control-image.md)控件、其模板以及**图像库**的大小，以适应屏幕大小。

1. 将 "**图像库**" 控件的[Items](properties-core.md)属性设置为以下公式：
 
    ```powerapps-dot
    MyPix
    ```

1. 将库中**图像**控件的[image](properties-visual.md)属性设置为以下公式：

    ```powerapps-dot   
    ThisItem.Url
    ```

    您拍摄的图片显示在 "**图像库**" 控件中。

1. 接受任意数量的图片，然后按 Esc 返回到默认工作区。

1. 可有可无将 "**图像库**" 控件中**图像**控件的**OnSelect**属性设置为公式：

    ```powerapps-dot
    Remove( MyPix, ThisItem )
    ```

1. 按 F5，然后选择图片将其删除。

使用[SaveData](../functions/function-savedata-loaddata.md)函数将图片保存在本地，或使用[Patch](../functions/function-patch.md)函数更新数据源。

### <a name="change-the-active-camera-from-a-drop-down"></a>从下拉更改活动相机

1. [添加](../add-configure-controls.md)**相机**控件。

1. 在出现提示时，授权应用程序使用设备的照相机。
    
1. [添加](../add-configure-controls.md)[下拉](control-drop-down.md)控件。

1. 将 dropdown 的**Items** prroperty 设置为：

    ```powerapps-dot
    Camera1.AvailableDevices
    ```

    > [!NOTE]
      > 根据需要替换摄像控件名称*Camera1* 。
    
1. 将相机的**相机**属性设置为： 

    ```powerapps-dot
    Dropdown1.Selected.Id
    ```

    > [!NOTE]
      > 根据需要替换下拉控件名称*Dropdown1* 。

1. 按 F5，然后从下拉列表中选择一项以更改相机。

## <a name="accessibility-guidelines"></a>辅助功能准则

相机控件显示 "相机进纸"，还显示为拍摄图片的按钮。 因此，有与按钮类似的辅助功能注意事项。

### <a name="video-alternatives"></a>视频替代项

请考虑为有视觉障碍的用户添加另一种输入形式。 例如，"[添加图片](control-add-picture.md)" 允许用户从其设备上传图像。

### <a name="color-contrast"></a>颜色对比度

[FocusedBorderColor](properties-color-border.md)与外部颜色之间必须有足够的颜色对比度。

### <a name="screen-reader-support"></a>屏幕阅读器支持

["Accessiblelabel"](properties-accessibility.md)必须存在。

### <a name="keyboard-support"></a>键盘支持

- [TabIndex](properties-accessibility.md)必须为零或更大，以便键盘用户可以导航到它。

- 焦点指示器必须清晰可见。 使用[FocusedBorderColor](properties-color-border.md)和[FocusedBorderThickness](properties-color-border.md)更新焦点指示器的可见性。
