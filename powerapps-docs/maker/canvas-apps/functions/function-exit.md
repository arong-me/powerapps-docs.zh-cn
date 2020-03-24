---
title: Exit 函数 | Microsoft 文档
description: Power Apps 中的 Exit 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/21/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1e66c9a6c079baef3b7f67631c4a21cda6334478
ms.sourcegitcommit: 1b29cd1fa1492037ef04188dd857a911edeb4985
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80122784"
---
# <a name="exit-function-in-power-apps"></a>Power Apps 中的 Exit 函数
退出当前正在运行的应用程序，并选择性地注销当前用户。

## <a name="description"></a>说明
**Exit** 函数用于退出当前运行的应用。 将用户返回到应用列表。 然后，用户可以选择另一个要打开的应用程序。  

**Exit**停止任何进一步的公式求值。 在**退出**后，任何使用[分号运算符](operators.md)链接的函数调用都不会执行。   

使用可选的*Signout*参数将当前用户从 Power Apps 中注销。 当共享设备以确保用户安全时， *Signout*非常有用。

创作应用程序时，调用**Exit**不会退出或注销用户。  但是，它不会停止计算公式的其余部分。

**Exit**只能在[行为公式](../working-with-formulas-in-depth.md)中使用。

> [!NOTE]
> 在 web 浏览器中运行应用程序时，不支持注销。

## <a name="syntax"></a>语法
**Exit**（[*Signout*]）

* *Signout* -可选。 一个布尔值，如果*为 true* ，则将对当前用户使用 Power Apps 进行签名。  默认值为*false* ，用户保持登录状态。

## <a name="examples"></a>示例

| 公式 | 说明 | 
| --- | --- | 
| **Exit （）** | 退出当前应用并使用户保持登录。  将用户返回到应用列表。  |
| **Exit （&nbsp;true&nbsp;）** | 退出当前应用，用户已注销。 用户需要在运行应用之前使用其凭据重新登录。 | 


