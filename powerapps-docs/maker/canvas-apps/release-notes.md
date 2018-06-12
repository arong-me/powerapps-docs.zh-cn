---
title: 新增功能 | Microsoft Docs
description: 按发布日期列出的 PowerApps 更新
documentationcenter: na
author: AFTOwen
ms.service: powerapps
ms.topic: conceptual
ms.component: canvas
ms.date: 05/21/2018
ms.author: anneta
ms.openlocfilehash: ef4360dda5d4003ff91389af78958052bbb1e052
ms.sourcegitcommit: 68e2c696397f3002dd14e72a4c2054a603a5e2d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2018
ms.locfileid: "34851698"
---
# <a name="whats-new-in-powerapps"></a>PowerApps 的最近更新
> [!IMPORTANT]
> **宣布发行说明**<br>
> 想要了解 PowerApps 中即将推出和最近发布的功能？<br>
[查看发行说明](https://docs.microsoft.com/en-us/business-applications-release-notes/april18/powerapps/overview)。 我们已捕获所有详细信息（从头到尾方方面面），你可在规划时使用。

有关已知限制的信息，请参阅[常见问题和解决方法](common-issues-and-resolutions.md)。

> [!NOTE]
> 版本会在几天内推出。 新功能或更新功能可能不会立即显示。

## <a name="may-30"></a>5 月 30 日
1. [RTF 编辑器控件](controls/control-richtexteditor.md)（实验性）- 允许最终用户在 WYSIWYG 编辑区域中设置文本格式。 

## <a name="may-21"></a>5 月 21 日
1. 允许应用用户使用升级的 Common Data Service (CDS) for Apps 环境中当前提供的“从 Excel 文件获取数据”和“导出数据”功能从本地存储的 Excel 或 CSV 文件导入和导出数据。 
1. 允许应用用户[在 Excel 中打开实体](../common-data-service/data-platform-excel-addin.md)，以使用适用于 PowerApps 的 Excel 加载项在 CDS for Apps 中创建数据，更新和删除其中存储的数据。 
1. 使用连接到 CDS for Apps 的 Power BI Desktop [创建和发布 Power BI 报表](../common-data-service/data-platform-powerbi-connector.md)。 

## <a name="april-23"></a>4 月 23 日
* 在 SharePoint 自定义列表窗体中，从 Internet Explorer 下载[附件](controls/control-attachments.md)。

## <a name="april-9"></a>4 月 9 日
* web 浏览器的应用中的剪切 (Ctrl+X)、复制 (Ctrl+C) 和粘贴 (Ctrl+V) 控件，包括控件的样式、公式和属性&mdash;&mdash;。

## <a name="march-21"></a>3 月 21 日
1. 创建[模型驱动应用](../model-driven-apps/model-driven-app-overview.md)，它从数据模型入手，通过你的核心业务数据和流程在 Common Data Service for Apps 中的形态生成数据模型，对窗体、视图和其他组件建模。 模型驱动应用自动生成在各种设备中反应敏捷的好用 UI。
2. 在环境中使用 CDS for Apps 最新版本[创建数据库](../../administrator/create-database.md)。
3. CDS for Apps 现包括：
    - 其他数据类型支持更复杂的实体定义并提供更丰富的体验。 （适用于画布和模型驱动应用。）
    - 直接从 PowerApps 站点的 CDS for Apps [创建和自定义实体](../common-data-service/data-platform-create-entity.md)。 更新的体验包括性能改进、更好用的 UI 和有用的功能，如在行中创建选项集。 （适用于画布和模型驱动应用。）
    - 创建服务器端业务规则，用于验证输入到 CDS for Apps 中的数据。 （适用于画布和模型驱动应用。）
    - 直接从 PowerApps 站点在 CDS for Apps 实体中创建计算和汇总字段。 （适用于画布和模型驱动应用。）  
    - 开发人员可以使用 CDS for Apps 软件开发工具包 (SDK) 为 CDS for Apps 创建基于代码的自定义项。
    - 高级用户可以通过新 OData Web API 访问存储在 CDS for Apps 中的数据。
    - 使用 Power Query [将数据导入](../common-data-service/data-platform-cds-newentity-pq.md) CDS for Apps。 在 Web 上使用 Power Query 将数据直接从多个源导入到 CDS for Apps

## <a name="march-5"></a>3 月 5 日
1. 在 SharePoint 列表中添加（和删除）[附件](controls/control-attachments.md)。
2. 在 Web 浏览器中打开外部 [PDF](controls/control-pdf-viewer.md) 文件。 （实验性功能）

## <a name="feb-12"></a>2 月 12 日
* 现已内联嵌入[视频](controls/control-audio-video.md)和[音频](controls/control-audio-video.md)播放的音量控件。 若要静音模式播放，用户不能单击或点击按钮，而是必须使用音量控件来降低音量。

## <a name="feb-7"></a>2 月 7 日
1. 从[相机](controls/control-camera.md)和[条形码扫描程序](controls/control-barcodescanner.md)控件中删除 Zoom、Brightness 和 Contrast属性。
2. 修复了[文本输入](controls/control-text-input.md)控件上的“清除”按钮限制对用户输入分配空间的问题。 在此修补后，仅在 Microsoft Edge（最新版本）和 Internet Explorer 11 Web 浏览器中支持文本输入控件的 [Clear](controls/control-text-input.md#additional-properties) 属性。
3. 添加了对[多媒体](add-images-pictures-audio-video.md)控件的辅助功能增强。

## <a name="jan-31"></a>1 月 31 日
1. 将隐藏式字幕添加到[视频](controls/control-audio-video.md)控件。
2. 改进了 [PDF 查看器](controls/control-pdf-viewer.md)控件中的错误处理。

## <a name="jan-18"></a>1 月 18 日
1. 适用于 iOS 和 Android 的 PowerApps 现在支持与 Microsoft Authenticator 集成。
2. [组合框](controls/control-combo-box.md)替换了表单中的 [SharePoint 查阅控件](sharepoint-lookup-fields.md)，并且单选查阅字段的新[数据卡](working-with-cards.md)模板在 PowerApps Studio 中默认处于选择状态。
3. 在[组合框](controls/control-combo-box.md)中，通过增强型阅读模式在长列表中查看所有项。
4. 控制本地记录存储大小限制，最多能够在[非可委派查询](delegation-overview.md#non-delegable-limits)中存储 2000 条记录。 （实验性功能）

## <a name="jan-5"></a>1 月 5 日
* 通过集成 [PowerApps 自定义视觉对象（预览版）](https://powerapps.microsoft.com/blog/powerbi-powerapps-visual/)，从 Power BI 报表拉取上下文数据，从而直接通过 Power BI 报表或仪表板处理数据。
