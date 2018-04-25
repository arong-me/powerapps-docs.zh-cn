---
title: ShowError 函数 | Microsoft Docs
description: PowerApps 中 ShowErro 函数的参考信息（包括语法和示例）
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: gregli
ms.openlocfilehash: 7c1d5a8c7b35d316a2720d564977170029e28359
ms.sourcegitcommit: a9d33322228c398d29964429602dc3fe19fa67d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2018
---
# <a name="showerror-function-in-powerapps"></a>PowerApps 中的 ShowError 函数
向用户显示错误。

## <a name="description"></a>说明
ShowError 函数向用户显示错误。  当你创作应用和终端用户使用应用时，均会显示消息。

ShowError 只能在[行为公式](../working-with-formulas-in-depth.md)中使用。

ShowError 始终返回“true”。

ShowError 可以搭配[ IfError ](function-iferror.md)函数使用，以检测和使用自定义错误消息报告错误。

## <a name="syntax"></a>语法
ShowError( Message )

* 消息 - 必需。  要向用户显示的消息。 

## <a name="examples"></a>示例

### <a name="step-by-step"></a>分步操作

1. 向屏幕添加“按钮”控件。

2. 将按钮的 OnSelect 属性设置为：

    ShowError( "Hello, World" )

3. 单击或按下该按钮。  

    每次单击该按钮时，会向用户显示消息“Hello，World”。

    ![在创作环境中，显示 Button.OnSelect、调用 ShowError 并将生成的“Hello，World”消息作为红色横幅消息显示给用户](media/function-showerror/hello-world.png)