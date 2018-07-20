---
title: Download、Launch 和 Param 函数 | Microsoft 文档
description: PowerApps 中 Download、Launch 和 Param 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: f2af4fef413aa5502c57e7158d9efdddd36757c9
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39021863"
---
# <a name="download-launch-and-param-functions-in-powerapps"></a>PowerApps 中的 Download、Launch 和 Param 函数
使用参数下载或启动网页或应用。  

## <a name="description"></a>描述
**Download** 函数可用于从 Web 将文件下载到本地设备。  系统会提示用户选择保存文件的位置。  **Download** 会返回文件的存储位置，并使用字符串表示。  

**Launch** 函数可用于启动网页或应用。  这个函数还可以将参数传递给应用（可选）。  

当应用启动时，**Param** 函数可用于检索传递给应用的参数。  如果没有传递指定的参数，**Param** 会返回 *blank*。

## <a name="syntax"></a>语法
**Download**( *Address* )

* *Address* - 必需。  要下载的 Web 资源的地址。

**Launch**( *Address* [, *ParameterName1*, *ParameterValue1*, ... ] )

* *Address* - 必需。  要启动的网页的网址或应用的 ID。
* *ParameterName* - 可选。  参数名称。
* *ParameterValue* - 可选。  要传递给应用或网页的相应参数的值。

**Param**( *ParameterName* )

* *ParameterName* - 必需。  传递给应用的参数的名称。

