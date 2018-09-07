---
title: 使用 Web 资源 | Microsoft Docs
description: 了解开发人员如何使用模型驱动应用的 Web 资源。
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/17/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 88e51e4547732bed2d3e7ef3290bc8d933afded3
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849902"
---
# <a name="use-web-resources"></a>使用 Web 资源

所有 Common Data Service for Apps 实例中都有一个名为 `webresources` 的虚拟文件夹，在此文件夹中可以按名称请求 HTML、JS、CSS、图像和其他文件并在浏览器中访问。 可以使用应用程序上传这些文件或者以编程的方式将它们添加为 [WebResource 实体](../common-data-service/reference/entities/webresource.md)记录。 [XrmToolBox WebResources Manager](https://www.xrmtoolbox.com/plugins/MsCrmTools.WebResourcesManager/) 是一个有助于处理这些记录的社区工具。

这些记录可以使用内容中的相对路径名称相互引用。 上传和按名称请求文件的功能提供制作 Web 应用程序（使用在浏览器通过身份验证的会话中处理的文件）所需的所有构建基块。 仅使用带 AJAX 技术的客户端代码，可以创建在浏览器窗口或者在窗体或仪表盘的 IFrame 中运行的各种应用程序。 

通常情况下，将使用 JavaScript Web 资源将事件处理程序函数添加到窗体和命令。

详细信息：
- [有模型导向应用的客户端脚本](client-scripting.md)
- [Dynamics 365 客户参与开发人员指南：Web 资源](/dynamics365/customer-engagement/developer/web-resources)
