---
title: "Download、Launch 和 Param 函数 | Microsoft 文档"
description: "PowerApps 中 Download、Launch 和 Param 函数的参考信息（包括语法和示例）"
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
ms.openlocfilehash: 4ed646431263e96a079483bc514c8154b6d9b653
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2018
---
# <a name="download-launch-and-param-functions-in-powerapps"></a>PowerApps 中的 Download、Launch 和 Param 函数
使用参数下载或启动网页或应用。  

## <a name="description"></a>说明
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

