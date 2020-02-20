---
title: 在 Power Apps 中将数据导出到 Excel | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 1f9368a7630e7b2f94e7b624e0d005f89b919a59
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680618"
---
# <a name="export-data-to-excel"></a>将数据导出到 Excel

是否需要分析可操作的项中的数据，并将该数据转换为可操作的项以帮助增加销售？ 现在，可以在将数据导出到 Excel 或 Excel Online 时执行此操作。 此外，分析大型数据集也不成问题，因为最多可以导出 100,000 行数据。
  
可以选择导出静态工作表或动态工作表，这些工作表可重新导入到应用中。 如果需要更多高级函数，可以导出动态数据透视表，从而可以轻松组织和汇总数据。  
  
可以将数据导出到可在任何设备（如手机、平板电脑或台式计算机）上使用的标准 Excel 文件。 数据的导出格式与应用中显示的格式相同。 文本将仍为文本，数字将仍为数字，日期将仍为日期。 但是，将数据从应用导出到 Excel 时，某些单元格格式可能会更改。 下表总结了应用中数据的显示情况，以及将数据导出到 Excel 时单元格格式的变化情况。  
  
## <a name="cell-format-when-data-is-exported-from-model-driven-apps"></a>从模型驱动应用导出数据时的单元格格式
  
| 模型驱动应用中的数据格式 |                                            Excel 中的单元格格式                                             |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            文本、股票代号、电话、选项集和查找            |                                                       显示为文本和选项集变为显示下拉列表                                                       |
|                                 电子邮件、URL                                 |                                                                        显示为常规                                                                         |
|                                   数字                                   |                                                             显示为无组分隔符的数字                                                             |
|                                  货币                                  |                                                         显示为数字，但不包含美元符号 ($)                                                         |
|                          仅日期、日期和时间                          |                                                                       显示为仅日期                                                                        |
|                       计算和汇总字段                        | 可在 Excel 中编辑，但不能重新导入到 Power Apps |
|                               受保护的字段                               | 可在 Excel 中编辑，但不能重新导入到 Power Apps |
  
## <a name="see-which-type-of-export-works-best-for-you"></a>了解最适合的导出类型  
  
|                                                                                                               任务                                                                                                                |                                              了解详细信息                                               |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
|   在不修改应用数据的情况下进行临时或模拟分析   。 或者，快速批量编辑为多个记录。   | [导出到 Excel Online](export-to-excel-online.md) |
|                                                                   获取当前数据和时间或要与其他人共享的数据快照。                                                                    |           [导出到 Excel 静态工作表](export-excel-static-worksheet.md)           |
| 随时获取最新信息，并能够在 Excel 中进行刷新，并与应用中显示的内容相匹配。 |          [导出到 Excel 动态工作表](export-excel-dynamic-worksheet.md)          |
|                                                                      查看数据透视表中的应用数据。                                                                      |                 [导出到 Excel 数据透视表](export-excel-pivottable.md)                 |



当以 Excel（.xlsx 格式）导出数据，然后添加或修改列时，不能将数据重新导入 Dynamics 365。 对于 .xlsx 文件格式，这是不支持的。  
  
如果使用 Excel 2010，则从“帐户”区域导出数据时，可能会收到以下错误消息： 
 
`The file is corrupt and cannot be opened.`  
  
由于 Excel 中的设置，将出现此错误消息。 若要解决这一问题，请执行以下操作：  
  
1. 打开 Excel 2010。  
  
2. 转到“文件” > “选项”   。  
  
3. 转到“信任中心” > “信任中心设置”   。  
  
4. 选择“受保护的视图”，然后清除前两个选项的复选框  。  
  
5. 选择“确定”，然后关闭“选项”对话框   。  
  

