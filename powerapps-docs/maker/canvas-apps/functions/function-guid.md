---
title: GUID 函数 | Microsoft Docs
description: PowerApps 中 GUID 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/14/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ea2668ca295d807bbc19f71c9aa9f477c3b96041
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992681"
---
# <a name="guid-function-in-powerapps"></a>PowerApps 中的 GUID 函数
将 GUID（[全局唯一标识符](https://en.wikipedia.org/wiki/Universally_unique_identifier)）字符串转换为 GUID 值或创建新的 GUID 值。

## <a name="description"></a>说明
使用 GUID 函数将包含 GUID 的十六进制表示形式的字符串转换为可以传递到数据库的 GUID 值。 GUID 值用作数据库系统（如 Common Data Service 和 SQL Server）的键。

传递的字符串可以包含大写或小写字母，但必须是采用以下任意格式的 32 位十六进制数字：

- **"123e4567-e89b-12d3-a456-426655440000"** （标准位置中带有连字符）
- **"123e4567e89b12d3a456426655440000"** （不带连字符）

如果未指定参数，此函数将创建新的 GUID。

若要将 GUID 值转换为字符串，只需将其用于字符串上下文。 GUID 值将转换为包含连字符和小写字母的十六进制表示形式字符串。 

生成新的 GUID 时，此函数使用伪随机数字创建版本 4 [IETF RFC 4122](https://www.ietf.org/rfc/rfc4122.txt) GUID。 将字符串转换为 GUID 时，此函数通过接受任何32十六进制数字字符串来支持任何 GUID 版本。

## <a name="volatile-functions"></a>易失函数
GUID 是不带参数时使用的易失函数。 每次计算该函数时会返回不同的值。  

在数据流公式中使用易失函数时，如果对含有该函数的公式进行重新计算，该函数会返回不同的值。 如果公式中没有任何其他更改，在应用执行期间，它会具有相同的值。

例如，当你的应用处于活动状态时，不会更改“文本”属性设置为“GUID()”的标签控制。 只有关闭和重新打开应用会得到不同的值。

如果包含该函数的公式的其他内容发生了任何更改，会导致该函数进行重新计算。 如果将“标签”控件的“文本”属性设置为以下公式，例如，用户每次更改“文本输入”控件的值时会生成 GUID：

**TextInput1.Text & " " & GUID()**

如果在[行为公式](../working-with-formulas-in-depth.md)中使用，则每当计算该公式时，也会计算 GUID。 有关详细信息，请参阅本主题后面部分的示例。

## <a name="syntax"></a>语法
**GUID**( [ *GUIDString* ] )

* *GUIDString* – 可选。  包含 GUID 的十六进制表示形式的文本字符串。 如果未提供任何字符串，则会创建新的 GUID。

## <a name="examples"></a>示例

#### <a name="basic-usage"></a>基本用法

基于十六进制字符串表示形式返回 GUID 值：

* **GUID( "0f8fad5b-d9cb-469f-a165-70867728950e" )**

还可以提供不带连字符的 GUID 字符串。 此公式将返回相同的 GUID 值：

* **GUID( "0f8fad5bd9cb469fa16570867728950e" )**

在上下文中使用该值，以将新数据库记录的“状态”字段设置为完整的值：

* @no__t 0Patch （产品、默认值（产品）、{Status：GUID （"F9168C5E-CEB2-4faa-B6BF-329BF39FA1E4"）}） **

你可能不希望向用户显示 GUID，但 GUID 有助于调试你的应用。 若要在前一个示例中创建的记录中显示“状态”字段的值，请将“标签”控件的“文本”属性设置为以下公式：

* **First( Products ).Status**

“标签”控件将显示 **f9168c5e-ceb2-4faa-b6bf-329bf39fa1e4**。

#### <a name="create-a-table-of-guids"></a>创建 GUID 的表

1. 将[按钮](../controls/control-button.md)控件的 [OnSelect](../controls/properties-core.md) 属性设置为以下公式：

    **ClearCollect( NewGUIDs, ForAll( [ 1, 2, 3, 4, 5 ], GUID() ) )**

    此公式创建一个单列的表，用于循环五次，从而得到五个 GUID。

1. 添加[数据表](../controls/control-data-table.md)控件，将其“项目”属性设置为“NewGUIDs”，并显示“值”字段。

1. 按住 Alt 键，通过单击或点击按钮来选择按钮。

    该数据表显示了 GUID 的列表：

    ![屏幕显示一个数据表，该表含有五个不同的 GUID 值](media/function-guid/guid-collection-1.png)

1. 再次选择该按钮以显示不同的 GUID 列表：

    ![同一屏幕显示一个数据表，该表含有五个不同的新的 GUID 值](media/function-guid/guid-collection-2.png)

若要生成单个 GUID 而不是表，请使用以下公式：

**Set( NewGUID, GUID() )**
