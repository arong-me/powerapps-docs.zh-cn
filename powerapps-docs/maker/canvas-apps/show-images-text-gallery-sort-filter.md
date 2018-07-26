---
title: 在库中显示数据，并对数据进行排序和筛选 | Microsoft 文档
description: 使用库显示图像和文本。 在 PowerApps 中对图像进行排序和筛选。
author: lonu
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/02/2015
ms.author: lonu
ms.openlocfilehash: 51a93009f187b31cd0d3159f97c78ff5bd60ae33
ms.sourcegitcommit: 0e9af8cace2bdc04750f4c5a70a3c4af8e3d2292
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2018
ms.locfileid: "39195533"
---
# <a name="show-sort-and-filter-data-in-a-powerapps-gallery"></a>在 PowerApps 库中显示数据，并对数据进行排序和筛选
创建一个库来显示有关多种产品的图像和文本，并对该信息进行排序和筛选。

在 PowerApps 中，可使用库来显示多个相关的项，正如你在目录中看到的一样。 库非常适合用于显示有关产品的信息，例如名称和价格。 在本主题中，我们将创建一个库并使用类似于 Excel 的函数对该信息进行排序和筛选。 此外，选中某项目时，该项目周围将出现边框。

> [!NOTE]
> 本主题使用平板电脑应用。 可以使用手机应用，但需要调整某些控件的大小。
> 
> 

### <a name="prerequisites"></a>先决条件
* [注册](../signup-for-powerapps.md) PowerApps，然后使用注册所用的同一凭据[登录](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
* 通过[模板](get-started-test-drive.md)、[数据](get-started-create-from-data.md)或[从头开始](get-started-create-from-blank.md)创建平板电脑应用。
* 了解如何[配置控件](add-configure-controls.md)。
* 这些步骤使用 [CreateFirstApp](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) 作为示例输入数据，其中包括 .jpg 图像。 该 zip 文件包含可以转换为 Excel 的 XML 文件。 在其他情况下，PowerApps 会自动读取 .zip 文件中的文件，并成功导入这些文件。 可以下载和使用此示例数据，或导入自己的数据。

## <a name="show-data-in-a-gallery"></a>在库中显示数据
1. 使用示例数据创建一个名为 **Inventory** 的集合。 步骤包括：  
   
   1. 在“插入”选项卡上，依次选择“控件”和“导入”：
      
      ![][1]  
   2. 将导入控件的“[OnSelect](controls/properties-core.md)”属性设置为以下公式：  
      **Collect(Inventory, Import1!Data)**
      
      ![][12]  
   3. 选择“导入数据”按钮，打开 Windows 资源管理器。 选择 *CreateFirstApp.zip*，然后选择“打开”。
   4. 在“文件”菜单中，选择“集合”。 Inventory 集合列出了所导入的数据：
      
      ![][3]  
      
      刚刚创建了 Inventory 集合，其中包含五个产品的相关信息，包括设计图像、产品名称以及库存数量。
      
      > [!NOTE]
      > 导入控件用于导入类似于 Excel 的数据并创建集合。 导入控件在创建应用和预览应用时导入数据。 目前，导入控件不在发布应用时导入数据。
      > 
      > 
2. 选择后退箭头，返回设计器。
3. 在“插入”选项卡上，依次单击或点击“库”和“水平”库。
   
    ![][4]
4. 在右侧窗格中，单击或点击标题和副标题可覆盖图形的选项：
   
    ![][15]
5. 将库的 **[Items](controls/properties-core.md)** 属性设置为 **Inventory**：
   
    ![][5]
6. 将库重命名为 **ProductGallery** 并移动库，使它不会挡住其他控件。 调整库的大小，让它显示三个产品：
   
    ![][6]
7. 在库的第一个项目中，选择底部标签：  
   
    ![][7]  
   
   > [!NOTE]
   > 更改任何库中的第一个项目时，将自动更改该库中所有其他项目。  
   > 
   > 
8. 将标签的 **[Text](controls/properties-core.md)** 属性设置为以下表达式：  
    **ThisItem!UnitsInStock** <br/>
   
    执行此操作时，标签将显示每个产品的库存数量：

![][8]  

> [!NOTE]
> 默认情况下，顶部标签的 **[Text](controls/properties-core.md)** 属性设置为 ```ThisItem!ProductName```。 可将其更改为集合中任何其他项。 例如，如果集合具有 *ProductDescription* 或 *Price* 字段，可将该标签设置为 ```ThisItem!ProductDescription``` 或 ```ThisItem!Price```。
> 
> 

使用这些步骤，将包括 .jpg 图像的数据导入一个集合。 然后添加一个显示该数据的库，并配置一个标签以显示每个产品的库存数量。

## <a name="highlight-the-gallery-item-you-select"></a>突出显示选择的库项
1. 选择库中*除*第一项以外的任何项。 将显示编辑图标（左上角）。 选择编辑图标：  
   ![][9]  
2. 在“插入”选项卡上，选择“形状”，然后选择矩形。 每个库项中将显示一个蓝色实线矩形。
3. 在“开始”选项卡上，选择“填充”，然后选择“无填充”。
4. 依次选择“边框”、“边框样式”，然后选择实线。
5. 再次选择“边框”，并将宽度设置为 3。 调整矩形的大小，使它环绕库项。 现在，库中的各项具有蓝色边框，应与下图类似：  
   ![][10]  
6. 在“形状”选项卡上，选择“可见”，然后在编辑栏中输入以下公式：  
   
    **If(ThisItem!IsSelected, true)**
   
    蓝色矩形环绕库中的当前所选项。 选择一些库项，确认矩形出现在所选的每个项的周围。 请记住，也可以打开**预览**![][2]，查看并测试所创建的内容。

> [!TIP]
> 选择矩形，在“开始”选项卡上选择“重新排序”，然后选择“置于底层”。 通过此功能，可在边框不挡住任何内容的情况下选择库项。
> 
> 

使用这些步骤，在库中的当前所选项周围添加边框。

## <a name="sort-and-filter-items-in-the-gallery"></a>对库中的项进行排序和筛选
在这些步骤中，我们将以升序和降序对库项进行排序。 此外，我们将添加一个滑块控件，按所选择的库存数量“筛选”库项。

#### <a name="sort-in-ascending-or-descending-order"></a>按升序或降序排序
1. 选择库中*除*第一项以外的任何项。
2. **[Items](controls/properties-core.md)** 属性当前设置为 Inventory（集合的名称）。 将其更改为以下内容：  
   
    **Sort(Inventory, ProductName)**
   
    执行此操作时，库中的各项按产品名称升序排序：![][11]  
   
    请尝试按降序排序。 将库的“[Items](controls/properties-core.md)”属性设置为以下公式：  
   
    Sort(Inventory, ProductName, Descending)  

#### <a name="add-a-slider-control-and-filter-items-in-the-gallery"></a>添加滑块控件，筛选库中的项
1. 添加滑块控件（“插入”选项卡>“控件”），将其命名为 **StockFilter** 并移动到库下。
2. 配置滑块，使用户可将其设置为库存数量范围以外的值：  
   
   1. 在“内容”选项卡上，选择“最小”，然后输入以下表达式：  
      ```Min(Inventory, UnitsInStock)```  
   2. 在“内容”选项卡上，选择“最大”，然后输入以下表达式：  
      ```Max(Inventory, UnitsInStock)```
3. 选择库中*除*第一项以外的任何项。 将库的 **[Items](controls/properties-core.md)** 属性设置为以下表达式：  
   ```Filter(Inventory, UnitsInStock<=StockFilter!Value)```
4. 在**预览**中，将滑块调整到库中介于最大和最小数量之间的值。 调整滑块时，库只会显示小于所选值的产品：  
   ![][13]  

现在，可添加至筛选器：

1. 返回设计器。
2. 在“插入”选项卡上，选择“文本”，选择“输入文本”，并将新控件重命名为 **NameFilter**。 将文本控件移动到滑块下方。
3. 将库的 **[Items](controls/properties-core.md)** 属性设置为以下表达式：  
   ```Filter(Inventory, UnitsInStock<=StockFilter!Value && NameFilter!Text in ProductName)```
4. 在“预览”中，将滑块滑到“30”，然后在文本输入控件中键入字母“g”。 库只会显示库存数量少于 30 且名称包含字母“g”的产品：  
   ![][14]  

## <a name="tips-and-tricks"></a>提示和技巧
* 可随时选择预览按钮 (![][2]) 以查看创建的内容并进行测试。
* 在设计应用时，可以重新调整控件大小，并使用单击-拖动移动它们。
* 按 **Esc** 或选择 **X** 关闭预览窗口。
* 使用库时，选择库中的第一项可更改库中的所有项。 例如，选择第一项可向库中的所有项添加边框。
* 若要更新库的属性，可选择库中*除*第一项以外的任何项。 例如，选择第二项，更新适用于库（而非库中的项目）的 *Items*、*ShowScrollbar* 和其他属性。  

## <a name="what-you-learned"></a>已了解的内容
在本主题中，已执行以下操作：

* 创建集合、将包括 .jpg 图像的数据导入该集合，并在库中显示该数据。
* 在库中的每个图像下，配置列出该项的库存数量的标签。
* 在选择的项周围添加边框。
* 按产品名称对项目进行升序和降序排序。
* 添加滑块和输入文本控件，按库存数量和产品名称筛选产品。

[1]: ./media/show-images-text-gallery-sort-filter/import.png
[2]: ./media/show-images-text-gallery-sort-filter/preview.png
[3]: ./media/show-images-text-gallery-sort-filter/inventorycollection.png
[4]: ./media/show-images-text-gallery-sort-filter/insert-vertical.png
[5]: ./media/show-images-text-gallery-sort-filter/itemsinventory.png
[6]: ./media/show-images-text-gallery-sort-filter/threeimages.png
[7]: ./media/show-images-text-gallery-sort-filter/firstitem.png
[8]: ./media/show-images-text-gallery-sort-filter/bottomlabel.png
[9]: ./media/show-images-text-gallery-sort-filter/editgallery.png
[10]: ./media/show-images-text-gallery-sort-filter/border.png
[11]: ./media/show-images-text-gallery-sort-filter/sort.png
[12]: ./media/show-images-text-gallery-sort-filter/onselect.png
[13]: ./media/show-images-text-gallery-sort-filter/slider.png
[14]: ./media/show-images-text-gallery-sort-filter/inputandslider.png
[15]: ./media/show-images-text-gallery-sort-filter/select-overlay.png
