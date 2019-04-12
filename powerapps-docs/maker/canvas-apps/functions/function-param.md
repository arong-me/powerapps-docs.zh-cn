---
title: Download、Launch 和 Param 函数 | Microsoft 文档
description: 参考信息，包括语法和示例，画布应用中的 Download、 Launch 和 Param 函数
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4a53d8c20bd4b7784cb94daa574682c041f104ea
ms.sourcegitcommit: b316e0eee9946ef09e0512577ce2d11cd27aa864
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59508300"
---
# <a name="download-launch-and-param-functions-in-canvas-apps"></a>画布应用中的 download、 Launch 和 Param 函数
使用参数下载或启动网页或应用。  

## <a name="description"></a>描述
**Download** 函数可用于从 Web 将文件下载到本地设备。 系统会提示用户选择保存文件的位置。  **Download** 会返回文件的存储位置，并使用字符串表示。  

**Launch** 函数可用于启动网页或应用。  这个函数还可以将参数传递给应用（可选）。

在 Internet Explorer 和 Microsoft Edge**启动**函数将打开网站或应用程序仅在其安全设置是相同或更高版本的应用，其中包含该函数。 如果，例如，添加**启动**函数将在中运行的应用**受信任的站点**安全区域，请确保网站或你想要打开的函数的应用程序中**受信任站点**或**本地 intranet**区域 (不在**受限站点**)。 详细信息：[更改 Internet Explorer 11 的安全和隐私设置](https://support.microsoft.com/en-us/help/17479/windows-internet-explorer-11-change-security-privacy-settings)。  

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

