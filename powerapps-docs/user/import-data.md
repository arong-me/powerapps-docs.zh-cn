---
title: 在模型驱动应用中导入数据 | MicrosoftDocs
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
ms.openlocfilehash: 37e9602d48bbfbb802afefa0f6d47fad241dc6f5
ms.sourcegitcommit: 212d397284c431f5989dc7b39549e2fc170d447e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58491518"
---
# <a name="import-data"></a>导入数据

无论你的数据是存储在电子表格、手机还是电子邮件程序中，都可以使用下面的方法将数据导入应用。 例如，你可能希望将你的客户联系人列表从 Excel 电子表格导入应用，以便在一个位置即可跟踪所有客户信息。
  
## <a name="step-1-get-your-import-file-ready"></a>步骤 1:准备好导入文件  
首先，将数据导出到 Excel 文件。 支持以下文件格式：
 - Excel 工作簿 (.xlsx)
 - 逗号分隔值 (.csv)
  
对于 .zip 文件，允许的最大文件大小为 32 MB。 对于其他文件格式，允许的最大文件大小为 8 MB。  
  
### <a name="export-data-from-an-email-program"></a>从电子邮件程序中导出数据  
  
1.  将数据导出到逗号分隔值文件 (.csv)。  
  
     若要查找将联系人从电子邮件程序中导出的特定步骤，请打开程序的“帮助”并搜索“导出”。 查找标题中包含“导出联系人”或“导出通讯簿”或“导出向导”的主题。  
  
2.  将文件保存在你稍后容易找到的位置。  
  
### <a name="export-data-from-a-spreadsheet"></a>从电子表格中导出数据  
  
1.  打开电子表格。  
  
2.  如有必要，编辑电子表格中的任何列名，以完全匹配此处显示的相应名称。  
  
    > [!WARNING]
    > 如果电子表格不包含列出的所有列名，也没有关系。 但是，如果列名的确存在，则它必须完全匹配列表中相应的名称，否则无法导入。 必需包含空格。 请注意，“Email”一词不包含连字符。  

    |**电子表格中的列名（拼写必须完全匹配）**|
    |---------|
    |名字|  
    |中间名|  
    |姓氏|  
    |商务电话|  
    |移动电话|  
    |职务|  
    |公司所在街道|  
    |公司所在城市|  
    |公司所在省/自治区|  
    |公司邮政编码|  
    |公司所在国家/地区|  
    |电子邮件地址|  
  
3.  保存文件。  
  
### <a name="export-data-from-your-phone"></a>从手机中导出数据  

使用 USB 电缆或应用将数据（如联系人）从手机导出到计算机。
  
若要查找具体手机品牌导出联系人的特定步骤，请使用你喜爱的搜索引擎（如必应）搜索“从我的手机导出联系人”。  
  
若要查找应用，请搜索手机的在线商店。  
  
## <a name="step-2-import-the-file"></a>步骤 2：导入文件 
  
1. 在命令栏上，选择“从 Excel 导入”或“从 CSV 导入”。

   > [!div class="mx-imgBorder"]
   > ![PowerApps 中的主菜单](media/import.png "PowerApps 中的主菜单")
  
2. 浏览到保存了包含导出的联系人的文件的文件夹。 依次选择“文件”、“打开”，然后选择“下一步”。  
  
   > [!TIP]
   > 一次只能导入一个文件。 若要导入更多文件，请稍后再次运行向导。
   
3. 查看文件名称，并使用“查看映射”选项验证字段和数据分隔符是否正确无误。 如果一切正常，请选择“完成导入”。  
 
## <a name="step-3-check-that-the-import-is-successful"></a>步骤 3：检查导入是否成功

向导完成后，检查数据（例如，联系人列表）以确保其正确导入。  
  
1. 在主菜单中，转到“联系人”。
  
2. 滚动联系人列表。 检查是否每个人都已列出，并验证字段内容是否准确。

## <a name="import-double-byte-characters"></a>导入双字节字符 

如果要为东亚语言导入包含双字节字符的数据，请务必将该文件编码为 UTF-8 BOM。 普通 UTF-8 可能还不够。

1. 使用 Visual Studio Code 打开 CSV 文件。
2. 在底部栏中，单击标签“UTF-8”（随即打开弹出窗口）。 
3. 选择“保存时使用编码”。 

现在可以为该文件选取 UTF-8 BOM 编码了。

