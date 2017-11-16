---
title: "Enable 和 Disable 函数 | Microsoft 文档"
description: "PowerApps 中 Enable 和 Disable 函数的参考信息（包括语法和示例）"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: b4051bdb312707cfafe63a97b5e77a2860feb60c
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="enable-and-disable-functions-in-powerapps"></a>PowerApps 中的 Enable 和 Disable 函数
打开或关闭[信号](signals.md)。

## <a name="overview"></a>概述
某些信号可能经常发生变化，这要求应用在信号更改时重新计算结果。  长时间内快速更改可能会耗尽设备电池的电量。 可以使用这两个函数手动打开或关闭信号。

未使用某个信号时，这个信号就会自动关闭。

## <a name="description"></a>说明
**Enable** 和 **Disable** 函数分别用于打开和关闭信号。

这两个函数仅对**[定位](signals.md)**信号有效。

这两个函数没有返回值。 它们只能在[行为公式](../working-with-formulas-in-depth.md#behavior-formulas)中使用。

## <a name="syntax"></a>语法
**Enable**( *Signal* )<br>**Disable**( *Signal* )

* *Signal* - 必需。  要打开或关闭的信号。
