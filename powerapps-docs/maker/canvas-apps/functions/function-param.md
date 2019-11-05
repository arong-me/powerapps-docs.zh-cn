---
title: Download、Launch 和 Param 函数 | Microsoft 文档
description: 画布应用中的下载、启动和参数函数的参考信息（包括语法和示例）
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
ms.openlocfilehash: 15bef0fc30c2efe90647d9f190cf8917de11a109
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73536944"
---
# <a name="download-launch-and-param-functions-in-canvas-apps"></a>在画布应用中下载、启动和参数函数
使用参数下载或启动网页或应用。  

## <a name="description"></a>描述
**Download** 函数可用于从 Web 将文件下载到本地设备。 系统会提示用户选择保存文件的位置。  **Download** 会返回文件的存储位置，并使用字符串表示。  

**Launch** 函数可用于启动网页或应用。  这个函数还可以将参数传递给应用（可选）。

在 Internet Explorer 和 Microsoft Edge 中，只有当某个网站或应用的安全设置与包含该函数的应用程序的安全设置相同或更高时，**启动**函数才会将其打开。 例如，如果将**启动**函数添加到将在 "**受信任的站点**" 安全区域中运行的应用，请确保你希望此函数打开的网站或应用位于 "**受信任的站点**" 或 "**本地 intranet** " 区域（不在**受限制的站点**）。 详细信息：[更改 Internet Explorer 11 的安全和隐私设置](https://support.microsoft.com/help/17479/windows-internet-explorer-11-change-security-privacy-settings)。  

当应用启动时，**Param** 函数可用于检索传递给应用的参数。 如果没有传递指定的参数，**Param** 会返回 *blank*。

## <a name="syntax"></a>语法
**Download**( *Address* )

* *Address* - 必需。  要下载的 Web 资源的地址。

**Launch**( *Address* [, *ParameterName1*, *ParameterValue1*, ... ] )

* *Address* - 必需。  要启动的网页的网址或应用的 ID。
* *ParameterName* - 可选。  参数名称。
* *ParameterValue* - 可选。  要传递给应用或网页的相应参数的值。

**Param**( *ParameterName* )

* *ParameterName* - 必需。  传递给应用的参数的名称。

