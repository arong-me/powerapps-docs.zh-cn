---
title: 组件实现库 |Microsoft Docs
description: 使用 JavaScript 或 TypeScript 创建代码组件
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: 31b7d2b30a1ef83ca4400011d50854713cb260f6
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347236"
---
# <a name="component-implementation-library"></a>组件实现库

使用 PowerApps 组件框架开发代码组件时，实现组件库是关键步骤之一。 开发人员可以使用 TypeScript 来实现组件库。 每个代码组件都必须有一个包含函数定义的库，该函数将返回一个对象，该对象可实现代码组件接口中所述的方法。 

对象实现以下方法：

- [init](reference/control/init.md) （必需）
- [updateView](reference/control/updateview.md) （必需）
- [getOutputs](reference/control/getoutputs.md) （可选）
- [销毁](reference/control/destroy.md)（必需）

这些方法控制代码组件的生命周期。

