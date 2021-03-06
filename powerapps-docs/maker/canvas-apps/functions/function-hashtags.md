---
title: HashTags 函数 | Microsoft 文档
description: Power Apps 中井号标签函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a88371e9c151ed097d2c86bcb64121c68a6d62d0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730799"
---
# <a name="hashtags-function-in-power-apps"></a>Power Apps 中的井号标签函数
从文本字符串中提取井号标签 (#strings)。

## <a name="description"></a>描述
**HashTags** 函数扫描字符串中的井号标签。 井号标签以井号字符 (#) 开头，后跟以下任意组合：

* 大写和小写字母
* 数字
* 下划线
* 货币符号（如 $）

**HashTags** 返回一个单列[表](../working-with-tables.md)，此表包含字符串中的井号标签。  如果字符串不包含井号标签，此函数将返回仅包含一个列的[空](function-isblank-isempty.md)表。

## <a name="syntax"></a>语法
**HashTags**( *String* )

* *String* - 必需。  用于扫描井号标签的字符串。

## <a name="examples"></a>示例
### <a name="step-by-step"></a>分步操作
1. 添加“[文本输入](../controls/control-text-input.md)”控件，将它命名为 **“Tweet”** ，然后在其中键入下面这句话：
   
    **This #app is #AMAZING and can #coUnt123 or #123abc but not #1-23 or #$\*(#\@")**
2. 添加垂直自定义库，并将其 **[Items](../controls/properties-core.md)** 属性设置为此函数：
   
    **HashTags(Tweet.Text)**
3. 将“[标签](../controls/control-text-box.md)”控件添加到库模板中。
   
    库将显示以下井号标签：
   
   * **\#app**
   * **\#AMAZING**
   * **\#coUnt123**
   * **\#123abc**
   * **\#1**

