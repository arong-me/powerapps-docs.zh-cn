---
title: 创建和更新集合 | Microsoft 文档
description: 创建集合，并在 PowerApps 中向现有集合添加列
documentationcenter: ''
author: lonu
manager: kfile
editor: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 11/30/2015
ms.author: lonu
ms.openlocfilehash: 01065fd1a12b3d55e8726582cead3d86a6e6a8ad
ms.sourcegitcommit: 45fac73f04aa03b5796ae6833d777f4757e67945
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="create-and-update-a-collection-in-your-app"></a>创建和更新应用中的集合
集合用于存储可在应用中使用的数据。 集合是一组类似的项。 例如，你会创建“MyImages”集合来存储公司出售的所有产品的图像。 在 PowerApps 内，可以添加“MyImages”集合，然后创建一个应用来显示这些产品的所有图片。 再比如，可以创建“PriceList”集合，列出所有产品及其价格。

可以在 PowerApps 中创建和使用集合。 现在就开始吧。

### <a name="prerequisites"></a>先决条件
* [注册](../signup-for-powerapps.md) PowerApps，然后使用注册所用的同一凭据[登录](https://web.powerapps.com)。
* 在 PowerApps 中创建一个应用，或打开一个现有应用。
* 了解如何在 PowerApps 中 [配置控件](add-configure-controls.md)。
* 本文中的步骤过程使用 [PriceList.zip](http://pwrappssamples.blob.core.windows.net/samples/PriceList.zip) 文件作为示例输入数据。 此 zip 文件中包含可以转换成 Excel 的 XML 文件。 在其他情况下，PowerApps 会自动读取 .zip 文件中的文件，并成功导入这些文件。 可以下载和使用此示例数据，也可以导入你自己的数据。

## <a name="create-a-single-column-collection"></a>创建单列集合
下面的步骤展示了如何使用 Collect 函数在应用内创建集合，以及如何向集合添加项。

1. 打开应用。
2. 在“插入”选项卡上，依次选择“文本”和“文本输入”：  
   ![][1]  
3. 选择左上角的“Text1”，然后将此控件重命名为“Destination”：  
   ![][2]  
4. 选择“插入”选项卡上的“按钮”，向设计器添加按钮控件。 下拉列表中列出了“[OnSelect](controls/properties-core.md)”属性。 将此属性设为以下函数：  
   
    ```Collect(Destinations, Destination!Text)```
   
    具体设置应如下所示：  
    ![][3]  
5. 选择按钮文本，然后输入“添加”：  
   ![][5]  
6. 选择“添加”按钮，然后将其移到文本控件下方。 可以将它移到任何位置：  
   ![][6]  

在上面的步骤过程中，你使用 Collect 函数创建了“Destinations”集合。 此外，还添加了按钮控件，当用户选择此按钮时，可以向集合添加新项。 现在，预览一下所创建的内容：

1. 选择“预览”：  
   ![][7]  
2. 在框中键入城市名称，然后选择“添加”按钮。
3. 输入其他一些城市名称，每次输入都要选择“添加”按钮。
4. 按 **Esc** 键，关闭“预览”窗口。
5. 查看“Destinations”集合和你输入的文本值。 选择“文件”选项卡上的“集合”。 你输入的文本已列出：  
   ![][8]

#### <a name="extra-credit"></a>加分做法
现在，让我们将“Destinations”集合绑定到列表框：

1. 返回到设计器。
2. 在“插入”选项卡上，依次选择“控件”和“列表框”：  
   ![][22]  
3. 将列表框移到显眼位置上。 将其“[Items](controls/properties-core.md)”属性设为以下表达式：  
   ```Destinations!Value```  <br/>
   
    执行此操作后，列表框中会自动填充你之前在“Destinations”集合中输入的项：  
   ![][4]  

预览所做的更改：![][7]。 在列表框中，可以看到所输入的不同城市。 在文本输入控件中，输入新的城市名称，然后选择“添加”按钮。 列表框会自动更新为列出你输入的新城市。

## <a name="create-a-multi-column-collection"></a>创建多列集合
下面的步骤展示了如何使用 Collect 函数在应用内创建集合，以及如何向集合添加多行。

1. 在“开始”选项卡上，打开一个新屏幕。
2. 在“插入”选项卡上，依次选择“文本”和“文本输入”。
3. 将文本控件重命名为“City”：  
   ![][9]  
4. 插入另一个文本输入控件，并将其命名为“States”。
5. 将“City”和“States”文本控件移到能够同时容纳这两个控件的位置上：  
   ![][10]  
   
    > [!NOTE]
> 可以将“文本输入”替换为“城市”或“州/省/自治区/直辖市”，如上图所示。  
6. 选择“插入”选项卡上的“按钮”。 将其“[OnSelect](controls/properties-core.md)”属性设为以下函数：  
   ```Collect(Destinations, {Cities:City!Text, States:States!Text})```  
   
    具体设置应如下所示：  
    ![][11]  
   
    > [!NOTE]
> 可以使用同一函数向此集合添加其他列。 例如，可以再添加一个“Country”文本输入控件，从而添加“Countries”列：
   
    `Collect(Destinations, {Cities:City!Text, States:States!Text}, {Countries:Country!Text})`
7. 将按钮控件重命名为“AddCityStateButton”，然后将其“[Text](controls/properties-core.md)”属性设为“Add City and State”：  
   ![][12]  

在上面的步骤过程中，你向“Destinations”集合添加了“Cities”和“States”列。 按钮控件用于向集合添加新的文本项。 现在，预览一下所创建的内容：

1. 选择“预览”：  
   ![][7]  
2. 在“城市”和“州/省/自治区/直辖市”框中键入一些文本，然后选择“添加城市和州/省/自治区/直辖市”按钮。
3. 添加其他一些城市和州/省/自治区/直辖市。
4. 按 **Esc** 键，关闭“预览”窗口。
5. 若要查看添加到“Destinations”集合中的项，请依次选择“文件”选项卡和“集合”：  
   ![][13]

## <a name="add-columns-to-a-collection"></a>向集合添加列
本演练分成几个部分。 完成后，你将了解如何将数据导入集合、如何创建库来显示价格列表中的数据，以及如何使用滑块控件来确定产品数量。

### <a name="import-the-price-list-and-create-the-collection"></a>导入价格列表并创建集合
1. 下载“[PriceList](http://pwrappssamples.blob.core.windows.net/samples/PriceList.zip)”zip 文件。
2. 在“开始”选项卡上，添加一个新屏幕。
3. 在“插入”选项卡上，选择“控件”，然后选择“导入”：  
   ![][14]  
4. 选择“操作”选项卡上的“OnSelect”。 输入以下函数：  
   
    ```Collect(PriceList, Import1!Data)```  
5. 预览应用。 依次选择“导入数据”按钮、PriceList.zip 文件和“打开”。
6. 关闭“预览”窗口。
7. 依次选择“文件”选项卡和“集合”。 你导入的 PriceList 项已列出：  
   ![][15]

### <a name="add-the-gallery-to-show-the-collection-items"></a>添加库来显示集合项
1. 返回到设计器。
2. 在“插入”选项卡上，选择“库”，向下滚动到“自定义库”，然后选择“纵向”：    
   ![][16]  
3. 将库重命名为“PriceGallery”，然后将其“Items”属性设为“[PriceList](controls/properties-core.md)”：  
   ![][18]  
4. 将 PriceList 库移到“导入数据”控件下方。 选择库边框，然后单击并拖动边框，将库的大小重设为可显示三个方形。
5. 在库中，选择第一个方形，然后添加三个标签（依次选择“插入”选项卡和“标签”）。
6. 重设标签大小，并在第一个方形顶端附近将标签排成一行。 库如下所示：  
   ![][19]
7. 将每个标签的“[Text](controls/properties-core.md)”属性设为以下表达式：  
   
   | 标签 | 将“Text”属性设为 |
   | --- | --- |
   | Label1 |``ThisItem!Name`` |
   | Label2 |``Text(ThisItem!Price, "$#")`` |
   | Label3 |``ThisItem!Maker`` |
   
    执行此操作后，标签会自动更新为显示“PriceList”集合内的名称、价格和制造商值。
8. 重设标签和库的大小，去掉任何多余空间。 屏幕如下所示：  
   ![][17]

### <a name="add-the-quantity-slider-and-update-the-collection"></a>添加数量滑块并更新集合
1. 在“插入”菜单上，依次选择“控件”和“滑块”。 将滑块重命名为“OrderQty”，然后将其移到库下方。
2. 添加一个按钮，将其“[Text](controls/properties-core.md)”属性设为“Add”，然后将其移到“OrderQty”滑块下方。 应用如下所示：  
   ![][20]
3. 将“添加”按钮的“[OnSelect](controls/properties-core.md)”属性设为以下表达式：  
   
    ```Collect(OrderList, {Name:PriceGallery!Selected!Name, Qty:OrderQty!Value, Cost:OrderQty!Value*LookUp(PriceList, PriceGallery!Selected!Name in Name, Price)});SaveData(OrderList, "orderfile")```  
   
    > [!NOTE]
> 稍后在此过程中选择这个按钮时，将创建并保存“OrderList”集合。 此集合中包含你在库中输入的产品名称、使用滑块选择的产品数量，以及通过将产品数量与价格相乘计算得出的总成本。
4. 选择“屏幕”选项卡，然后将其“[OnVisible](controls/control-screen.md)”属性设为以下表达式：  
   
    ```If(IsEmpty(PriceList), LoadData(PriceList, "pricefile"));If(IsEmpty(OrderList), LoadData(OrderList, "orderfile"))```

现在，预览一下所创建的内容：

1. 打开“预览”。
2. 选择库中的一个产品，将滑块移到所需的数量，然后选择“添加”按钮。  
   
   > [!IMPORTANT]
   > 选择的产品不会通过突出显示来指明你已选择它。 我们在创建库时没有添加此功能。 知道单击产品即可选择就行了。  
   > 
   > 
3. 重复执行上述步骤，添加更多产品。 按 **ESC** 键，关闭“预览”窗口。
4. 选择“文件”选项卡上的”集合”，显示你创建的“OrderList”集合的预览版：  
   ![][21]

> [!TIP]
> 若要删除订单列表中的所有项，请添加一个按钮，将其 **[Text](controls/properties-core.md)** 属性设为 **Clear**，并将其 **[OnSelect](controls/properties-core.md)** 属性设为以下表达式：  
> ```Clear(OrderList);SaveData(OrderList, "orderfile")```  
> 若要一次删除一项，打开库中的“OrderList”集合，然后将库中标签的“[OnSelect](controls/properties-core.md)”属性设为以下表达式：  
> ```Remove(OrderList, ThisItem);SaveData(OrderList, "orderfile")```
> 
> 

## <a name="tips-and-tricks"></a>提示和技巧
* 可以随时选择“预览”按钮 (![][7]) 来预览图表及其所含数据。
* 设计应用时，可以重设控件大小，然后单击并拖动它们来进行移动。

## <a name="what-you-learned"></a>已了解的内容
在本主题中，你已执行以下操作：

* 使用 Collect() 函数在应用内创建了集合。
* 添加了按钮控件，当用户选择此按钮时，可以向集合添加新项。
* 使用列表框将项添加到了集合中。
* 添加了滑块控件，以更新集合项。

[1]: ./media/create-update-collection/insertmenu-inputtext.png
[2]: ./media/create-update-collection/renametext.png
[3]: ./media/create-update-collection/buttononselect.png
[4]: ./media/create-update-collection/listboxpreview.png
[5]: ./media/create-update-collection/buttontext.png
[6]: ./media/create-update-collection/buttonundertext.png
[7]: ./media/create-update-collection/preview.png
[8]: ./media/create-update-collection/existingcollections.png
[9]: ./media/create-update-collection/renametext-city.png
[10]: ./media/create-update-collection/citystate.png
[11]: ./media/create-update-collection/buttononselectcitystate.png
[12]: ./media/create-update-collection/buttononcitystate.png
[13]: ./media/create-update-collection/existingcollectionscitystate.png
[14]: ./media/create-update-collection/import.png
[15]: ./media/create-update-collection/pricelistcollection.png
[16]: ./media/create-update-collection/portrait.png
[17]: ./media/create-update-collection/resizedgallery.png
[18]: ./media/create-update-collection/galleryitems.png
[19]: ./media/create-update-collection/gallerylabels.png
[20]: ./media/create-update-collection/slider.png
[21]: ./media/create-update-collection/existingcollectionsorderlist.png
[22]: ./media/create-update-collection/listbox.png
