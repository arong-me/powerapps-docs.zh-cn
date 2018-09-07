---
title: Language 函数 | Microsoft 文档
description: PowerApps 中 Language 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/16/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 45ffd324ff5409a49f1ec8c4c8ea3529c1cf5c5f
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42833277"
---
# <a name="language-function-in-powerapps"></a>PowerApps 中的 Language 函数
返回当前用户的语言标记。

## <a name="description"></a>描述
**Language** 函数可使用语言标记的形式返回当前用户的语言、脚本或区域。

使用不同区域设置的语言信息定制应用。  例如，如果你正在创建要在意大利和法国使用的应用，可以使用 **Language** 函数自动向位于这些不同位置的用户显示意大利语和法语字符串。 

### <a name="language-tags"></a>语言标记
“语言标记”可以是下面三种格式之一：

| 返回值 | 描述 |
| --- | --- |
| **"*lg&#8209;RE*"** |*lg* 是语言 (Language) 的两字符缩写形式，*RE* 是区域 (Region) 的两字符缩写形式。  这是最常见的返回类型。  例如，对于英国 (Great Britain)，返回“en-GB”。 |
| **"*lg*"** |*lg* 是语言的两字符缩写形式。  如果 PowerApps 获得了语言信息，但没有特定区域信息，则使用此格式。 |
| **"*lg&#8209;scrp&#8209;RE*"** |*lg* 是语言的两字符缩写形式，*scrp* 是脚本 (Script) 的四字符缩写形式，*RE* 是区域的两字符缩写形式。 |

PowerApps 使用 [IETF BCP-47 语言标记](https://tools.ietf.org/html/bcp47)格式。  

要查看支持的语言标记列表，请在公式栏或高级视图中输入 **Value( "1", )**，然后滚动查看建议作为第二个参数的值的区域设置列表。  

**[Text](function-text.md)** 和 **[Value](function-value.md)** 函数也使用语言标记。  这些函数可基于全球化考虑来回转换文本字符串。  将语言标记传递给这些函数时，如果区域没有区别，则只需使用标记的语言部分。

## <a name="syntax"></a>语法
**Language**()

## <a name="examples"></a>示例
### <a name="users-locale"></a>用户的区域设置
假设主机操作系统和/或浏览器正在使用当地的默认区域设置。

| 公式 | 位置 | 返回值 |
| --- | --- | --- |
| **Language()** |葡萄牙里斯本 |“pt-PT” |
| **Language()** |巴西里约热内卢 |“pt-BR” |
| **Language()** |美国亚特兰大 |“en-US” |
| **Language()** |英国曼彻斯特 |“en-GB” |
| **Language()** |法国巴黎 |“fr-FR” |
| **Language()** |多米尼加罗索 |“en” |
| **Language()** |塞尔维亚贝尔格莱德 |“sr-cyrl-RS”或“sr-latn-RS”，具体取决于用户的系统设置。 |

### <a name="localization-table"></a>本地化表
实现本地化的一种简便方法是创建一个 Excel 电子表格，将作者定义的 **TextID** 映射到用户语言的翻译文本。  对于这个表，虽然也可以使用集合或其他数据源，但我们选择 Excel，因为这更便于翻译在应用外编辑和管理内容。

1. 在 Excel 中创建下面的表︰ 
   
    ![](media/function-language/loc-table.png)
   
    如果找不到指定语言的任何特定文本字符串，则使用 *blank* 作为“语言”列的默认值。 这个条目放在指定 **TextID** 的所有其他条目后。
   
    对我们而言，只需要查看区域设置（而不是区域）的语言。  如果区域因素很重要，我们可以在上面的表中包含完整的语言标记值。 
2. 使用“插入”功能区中的“表”命令，将其设置为正确的 Excel 表。  默认情况下，其名称为“Table1”，但随时可以使用最左侧的“表工具/设计”功能区和“表名称：”文本框对其重命名。
3. 将 Excel 文件保存到本地文件系统。   
4. 在 PowerApps 的右侧窗格中，单击或点击“数据源”选项卡，然后单击或点击“添加数据源”。
5. 单击或点击“将静态数据添加到应用”，然后单击或点击保存的 Excel 文件，最后单击或点击“打开”。
6. 选择创建的表，然后单击或点击“连接”。

在应用中之前使用过“Hello”的所有位置，现在使用以下公式：

* **LookUp( Table1, TextID = "Hello" && (LanguageTag = Left( Language(), 2 ) || IsBlank( LanguageTag ))).LocalizedText**  

这个公式用于查找用户语言的相应 **LocalizedText** 值，如果找不到，则恢复为默认的 *blank* 版本。 

请注意，将字符串翻译成其他语言后比你的语言长得多。  在很多情况下，要将在用户界面中显示字符串的标签和其他元素设计得稍宽一些，以便容纳较长的语言版本。

### <a name="translation-service"></a>翻译服务
你可以根据需要使用翻译服务（如 Microsoft Translator 服务）来翻译文本：  

1. 在 PowerApps 的右侧窗格中，单击或点击“数据源”选项卡，然后单击或点击“添加数据源”。
2. 单击或点击“Microsoft Translator”。

在应用中之前使用过“Hello”的所有位置，现在使用以下公式：

* **MicrosoftTranslator.Translate( "Hello", Language() )**

Microsoft Translator 服务使用与 **Language** 函数返回的相同语言标记。

跟之前使用文本字符串预翻译表的例子相比，这个方法有一些缺点：

* 完成翻译比较耗时，需要通过网络调用服务才能实现。  这可能会导致在应用中查看翻译文本时出现延迟。 
* 翻译是机械式的，可能无法达到预期效果，或者对你的应用来说不是最佳选择。

