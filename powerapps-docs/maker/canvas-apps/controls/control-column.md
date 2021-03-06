---
title: 列控件：参考 | Microsoft 文档
description: 本主题提供有关 Microsoft Power Apps 中的列控件的信息。
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/05/2017
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6fcf4d94677a21f013734fedc8a4db70955f40b9
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74727470"
---
# <a name="column-control-in-power-apps"></a>Power Apps 中的列控件
用于在“[数据表](control-data-table.md)”控件中显示单个字段。

## <a name="description"></a>描述
“[数据表](control-data-table.md)”控件以表格格式显示数据集，表格格式中的每一列都由“列”控件表示。 “列”控件为应用开发者提供用于自定义列外观和行为的属性。

## <a name="capabilities"></a>功能
### <a name="now-available"></a>现可用
* 更改“列”控件的宽度。
* 更改“列”控件的文本。
* 通过单击或点击“列”控件中的值进行导航。

### <a name="not-yet-available"></a>尚未推出
* 自定义“列”控件的样式。

### <a name="known-issues"></a>已知问题
* “Visible”属性不起作用。

## <a name="properties"></a>属性
* **DisplayName** - 列标题文本。
  
  > [!NOTE]
  > 此属性很快将会重命名为“HeaderText”。
  > 
  > 
* **IsHyperlink** - 指明是否应为列中数据加上下划线以表明这是超链接的值。
* [**Width**](properties-size-location.md) -“列”控件左右边缘之间的距离。

## <a name="examples"></a>示例
### <a name="resize-a-column"></a>重设列大小
1. 创建一个空白的平板电脑应用。
2. 在“插入”选项卡上，单击或点击“数据表”，再重设“数据表”控件的大小，使其全屏显示。
3. 在右侧窗格中，依次单击或点击“未选择数据源”右侧的向下箭头和“添加数据源”。
4. 在连接列表中，单击或点击 Common Data Service 数据库的连接。
5. 在实体列表中，依次单击或点击“帐户”和“连接”。
   
    此时，“数据表”控件已初始化，显示一组默认字段。
6. 单击或点击“全名”列。
   
    ![已选择“列”控件](./media/control-column/pre-resize-column.png)
7. 拖动右侧的装饰器，以重设字段大小。
   
    ![重设大小后的“列”控件](./media/control-column/post-resize-column.png)


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="screen-reader-support"></a>屏幕阅读器支持
* “DisplayName”必须存在。
