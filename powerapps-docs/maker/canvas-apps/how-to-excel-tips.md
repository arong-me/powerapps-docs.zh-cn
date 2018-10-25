---
title: 在 Excel 中设置表格格式 | Microsoft Docs
description: 若要在 PowerApps 中使用 Excel 数据，必须将数据设置为表格格式。 在列名中添加“图像”关键字
author: yifwang
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/03/2018
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ea4bda4857c89a9e28359f63811e70744f111499
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42830948"
---
# <a name="format-a-table-in-excel-and-naming-tips"></a>在 Excel 中设置表格格式和命名的相关提示
在 PowerApps 中，仅当将 Excel 数据设置为表格格式时，才能基于该数据创建画布应用。 通过按照本文内容操作，你将了解如何在 Excel 中设置表格格式以及命名 Excel 列的一些提示。

## <a name="how-to-format-a-table-in-excel"></a>如何在 Excel 中设置表格格式
通过选择 Excel“开始”选项卡中的“套用表格格式”，可将数据转换为表格。

![Excel 表格格式设置](./media/how-to-excel-tips/format-table.png)

也可以通过选择“插入”选项卡上的“表格”来创建表格。

![Excel 插入表格](./media/how-to-excel-tips/insert-table.png)

为了轻松查找表格，请转到“表格工具”下的“设计”，对表格进行重命名。 通过此操作可为表格提供有意义的名称，对于同一 Excel 文件中包含多个表格的情况尤其有用。

![Excel 表格重命名](./media/how-to-excel-tips/rename-table.png)

## <a name="naming-tips-in-excel"></a>Excel 中的命名提示
如果表格中的列包含图像，请在该列的名称中包括“image”。 此关键字会将该列绑定到库中的图像控件。

![将 Excel 表格与图像相互连接](./media/how-to-excel-tips/connect-gallery.png)

## <a name="next-steps"></a>后续步骤
* 基于你指定的表[在 PowerApps 中从 Excel 生成应用](get-started-create-from-data.md)。 默认情况下，应用包含三个屏幕，分别用于浏览记录、显示有关单个记录的详细信息以及创建或更新记录。
* 使用在 Excel 中格式化的表[从零开始创建应用](get-started-create-from-blank.md)。 可以手动创建和自定义应用以显示、浏览或编辑表中的数据。
