---
title: Enable 和 Disable 函数 | Microsoft 文档
description: 适用于 Power Apps 中的 Enable 和 Disable 函数的参考信息（包括语法和示例）
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
ms.openlocfilehash: af1522934bcfee13c00950a3686583393699d0ad
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731107"
---
# <a name="enable-and-disable-functions-in-power-apps"></a>启用和禁用 Power Apps 中的函数
打开或关闭[信号](signals.md)。

## <a name="overview"></a>概述
某些信号可能经常发生变化，这要求应用在信号更改时重新计算结果。  长时间内快速更改可能会耗尽设备电池的电量。 可以使用这两个函数手动打开或关闭信号。

未使用某个信号时，这个信号就会自动关闭。

## <a name="description"></a>描述
**Enable** 和 **Disable** 函数分别用于打开和关闭信号。

这两个函数仅对 **[定位](signals.md)** 信号有效。

这两个函数没有返回值。 它们只能在[行为公式](../working-with-formulas-in-depth.md)中使用。

## <a name="syntax"></a>语法
**Enable**( *Signal* )<br>**Disable**( *Signal* )

* *Signal* - 必需。  要打开或关闭的信号。

