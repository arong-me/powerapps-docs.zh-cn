---
title: 适用于电源应用的常见问题和解决方法 |Microsoft Docs
description: PowerApps 中的常见问题及解决方法列表。
author: KumarVivek
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/21/2019
ms.author: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c8f05c74141301d0c41238daa20625874eec98aa
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678778"
---
# <a name="common-issues-and-resolutions-for-powerapps"></a>PowerApps 常见问题和解决方法

本文列出了在使用电源应用时可能遇到的一些常见问题。 并在适用情况下提供了解决方法。

1. **使用身份验证器时，某些 Android 移动设备上的登录问题**（2019年8月21日）

    在某些设备和方案中，你可能会在使用验证器时遇到登录失败。 这是因为 OEM 限制了此功能。 有关错误和可能的缓解措施的详细信息，请参阅[此处](https://github.com/AzureAD/azure-activedirectory-library-for-android/wiki/ADALError:-BROKER_AUTHENTICATOR_NOT_RESPONDING)。    

1. **Android 移动设备上的照相机问题**（2019年1月1日）

    如果相机控件停止在 Android 设备上工作，请重新发布应用程序，并将其重新打开到设备上。 照相机控件已更新以响应 Android 操作系统中的更改，你的应用程序将在重新发布时从更新中获益。

1. **在灵活高度的库中滚动**（11月27日，2018）

    如果使用手指滚动时遇到限制，请将其抬起，并再次开始滚动。

1. **在适用于 Windows 的 Power Apps 中，用鼠标或触摸输入进行绘制不平滑**（2018年9月24日）

    钢笔控件仅对在 Windows 应用中使用鼠标或触摸输入进行绘制的部分支持。 笔划可能是间歇性的。 对于平滑绘图，请在浏览器中使用笔或运行应用程序。

1. **Power Apps Mobile 中的多个媒体控件**（2018年8月2日）

    Power Apps Mobile 在各种类型的设备上运行，其中某些设备具有特定于该平台的限制：

    - 可在除 iPhone 设备之外的所有平台上同时在多个视频控件中播放视频。
    - 可在除 Web 播放器之外的所有平台上同时使用多个麦克风控件录制音频。

1. 重新发布应用（2018 年 8 月 2 日）

    如果你尚未在几个月内更新应用，请将其重新发布以与最新版本的 Power Apps 同步，其中包括性能改进和其他修复。

1. <a name="out-of-memory"></a>浏览器内存不足（2018 年 7 月 23 日）

    如果使用 Power Apps 时内存不足，请考虑下载64位版本的 Chrome、Microsoft Edge 或 Internet Explorer。

1. 从嵌入的应用启动网站（2018 年 5 月 10 日）

    Internet Explorer 和 Microsoft Edge 浏览器可能会阻止启动处于受保护模式的 URL 或网站或者比加载的应用中的网站更低安全性的区域。 若要解决此问题，请为你的浏览器[更改安全和隐私设置](https://support.microsoft.com/help/17479/windows-internet-explorer-11-change-security-privacy-settings)。

1. 库中的组合框控件（2018 年 5 月 3 日）

    在图库中使用“组合框”控件时，用户滚动库时不保留其选项。 如果在不滚动的库中使用“组合框”控件，将不出现此问题。 当前未提供解决方法。

1. 使用自定义图像作为应用图标（2018 年 4 月 11 日）

    在适用于 Windows 版本3.18043 的 Power Apps Studio 中，无法上传自定义映像以用作应用图标。 若要解决此问题，请使用[Power Apps Studio for web](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)上传自定义映像。 或者，你可以使用适用于 Windows 的 Power Apps Studio 附带的其中一个图标，并自定义背景色。

1. 跨应用复制和粘贴屏幕（2018 年 4 月 4 日）

    当前不支持跨应用复制和粘贴屏幕。 若要解决此问题，向目标应用添加新屏幕，从源应用屏幕中复制控件，然后将其粘贴到目标应用屏幕。

1. 更改 SharePoint 窗体布局（2018 年 3 月 7 日）

    自定义某些语言的 SharePoint 列表表单时，如果尝试将布局从纵向（默认）更改为横向，应用可能会显示多个错误（控件中的黄色三角形）。 若要修复这些错误并保留横向布局，请单击“撤消”。

1. **“数据表”控件**

    如果复制并粘贴“数据表”控件，且它的 Items 属性设置为包含 Filter 函数的公式，新“数据表”控件的 Items 属性的公式以包含 _1 后缀的字段名称结尾。 这就会导致字段名称无效，且数据表不显示任何数据。 若要解决此问题，请在复制此控件前，先确认 Filter 函数从数据源中引用的任何字段都不与“数据表”控件中的列同名。 如果是，请重命名“数据表”控件中的列。 也可以从无效的字段名称中删除 _1 后缀，让它们与实体中的名称保持一致。

1. **Power Apps Studio for Windows 中的照相机控件**

    如果添加了照相机控件或打开使用照相机控件的应用，则 Power Apps Studio for Windows 可能会崩溃。 若要避免此问题，请在添加或使用照相机控件时使用[Power Apps Studio for web](create-app-browser.md) 。

1. **Android 设备上的版本 2.0.700**

    如果在 Android 设备上安装 release 2.0.700，然后无法打开应用（或应用停止响应），请卸载 Power Apps，重新启动设备，然后重新安装 PowerApps。

1. **打开应用时库为“空”**

    通过数据自动生成应用，保存应用，然后将其重新打开，浏览库时可能不会立即显示数据。 若要解决此问题，请在搜索框中至少键入一个字符，然后删除键入的文本。 这样库就能按预期方式显示数据了。

1. **升级 Windows 8.1 上的 Power Apps**

    如果在运行 Windows 8 或 Windows 8.1 的计算机上安装 Power Apps，请使 Windows 应用商店应用程序处于打开和活动状态，使用 "设置" 超级按钮检查更新，然后安装它们。

1. **自定义连接器和 Common Data Service**

    如果使用 Power Apps build 2.0.540 或更早版本创建的应用依赖于 Common Data Service 中的数据库和在不同环境中至少有一个自定义连接器，则需要将连接器部署到与数据库相同的环境，并更新应用程序以使用 th新建连接器。 否则，将出现一个对话框，通知用户找不到此 API。 有关详细信息，请参阅[环境概述](../../administrator/environments-overview.md)。

1. **在 Windows 8.1 上运行应用**

    如果[为 Windows 8.1 安装此更新](https://technet.microsoft.com/library/security/ms16-118)，则无法运行在该操作系统上的 Power apps Studio 中打开的应用。 但是，你仍然可以运行在[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)中打开的应用或使用 Power apps Mobile。

1. **带空格的列名称**

    如果你使用的是包含空格的 SharePoint 列表或 Excel 表，则 Power Apps 会将其替换为 **"\_x0020\_"** 。 例如，当在数据布局中显示或用于公式时，SharePoint 或 Excel 中的 **"列名"** 将显示为 **"Column_x0020_Name"** 。

1. **更改共享应用中的流**

    如果你将流添加到应用、共享该应用，然后在此流中添加服务或更改连接，则必须从此共享应用中删除此流、重新添加此流并刷新此应用。 否则，触发此流的用户将无法通过身份验证。

1. **使用本地化版本**。

    如果在 Windows 8.1 上运行的是版本 2.0.531 并且设备被设置为需要 IME 窗口的语言，则无法在**文本输入**控件中键入。

1. **Windows Phone 中的照相机控件**

    如果在运行内部版本 10.0.10586.107 的 Windows Phone 上打开包含照相机控件的应用，则此应用可能会崩溃。 要避免此问题，请升级到最新的内部版本（例如通过运行 [升级顾问](https://www.microsoft.com/store/p/upgrade-advisor/9nblggh0f5g4)）。

1. **从模板打开应用**。

    如果运行的是版本 2.0.500 或早期版本，在尝试从模板创建应用时会出现错误消息。 必须进行升级才能使用此功能。

    如果运行的是版本 2.0.510 或更高版本，在尝试从模板创建应用时可能会出现警告。 但是，可以关闭该消息并创建应用。

1. **扫描条形码**

    有关使用**条形码**控件的限制和最佳做法的信息，请参阅 [扫描条形码](scan-barcode.md)。

1. **在浏览器中创建和修改应用**

    在 power apps studio for Windows 中，你可以在 Power Apps Studio for web 中执行许多（但不是全部）相同的操作。 有关详细信息，请参阅 [在浏览器中创建应用](create-app-browser.md)。

1. **更改实体中的标题字段**

    如果更改由其他实体通过一个或多个查找引用的实体的标题字段，则在尝试保存更改时会出错。 要解决此问题，请删除针对要更改标题字段的实体的全部查找，做出更改，然后重新创建查找。 有关查找的详细信息，请参阅 [实体之间的关系](../common-data-service/data-platform-entity-lookup.md)。

1. **连接到本地 SharePoint 的应用**

    如果共享的应用依赖于未自动共享的连接（例如本地 SharePoint 站点），则用户在单击或点击“**登录**”，在浏览器中打开应用时，将看到不包含任何文本的对话框。 要关闭对话框，请单击或点击右上角的关闭 (X) 图标。 如果在 Power Apps Studio 或 Power Apps Mobile 中打开该应用，则不会显示该对话框。 有关共享连接的详细信息，请参阅 [共享应用资源](share-app-resources.md)。

1. **当 Power Apps 从数据生成应用时，不会自动配置用于排序和搜索的字段**。

   要配置此字段，按照 [添加库](add-gallery.md) 中筛选和排序部分所述，编辑库的 **[项](controls/properties-core.md)** 公式。

1. **通过数据创建的应用只能访问数据源的前 500 条记录**。

     通常情况下，通过将操作委托给数据源，Power Apps 可以使用任何大小的数据源。 对于无法委派的操作，Power Apps 在创作时将发出警告，并仅对数据源的前500条记录执行操作。  请参阅 [筛选器函数](functions/function-filter-lookup.md) 文章，了解有关委派的详细信息。

1. **Excel 数据必须为表格式**。

     有关将 Excel 用作数据源的限制的信息，请参阅 [云存储连接](connections/cloud-storage-blob-connections.md#known-limitations)。

1. **支持 SharePoint 自定义列表，但不支持库、某些类型的列表列或者支持多个值或选择的列**。

     有关详细信息，请参阅 [SharePoint Online](connections/connection-sharepoint-online.md#known-issues)。

1. **不支持共同创作。一次一个作者，请**。

     如果多人同时修改同一应用，可能会损坏应用或覆盖他人所做的更改。 在他人编辑之前关闭应用。

1. **新共享的应用要在几分钟后才能使用**。

     在某些情况下，新共享的应用不会立即可用。 请稍等片刻即可使用。

1. **在 [窗体控件](controls/control-form-detail.md) 中，无法使用自定义卡更改数据**。

     常用自定义卡缺少写回更改所需的 **[更新](controls/control-card.md)** 属性。 要解决此问题：

    * 选择窗体控件，并根据希望卡显示的字段通过右侧窗格插入一个卡。  
    * 按照 [了解数据卡](working-with-cards.md#unlock-a-card) 中所述内容来解锁卡。
    * 根据需要删除或重新排列卡内的控件，类似于自定义卡的操作。

1. **在 Android 5.0、具有 Webview 版本 v48 或 v49 的 Nexus 6 上运行的应用可能会崩溃**。

     用户更新到 Webview (3x) 之前的版本或更新到 Android 6.0 即可解决此问题。

1. **如果内存不足，可能会暂时禁用照相机**。

     如果移动设备内存不足，照相机将暂时禁用，以避免设备崩溃。

1. **Office 365 视频连接器不受支持**。

1. **卡片库已停用**。

     使用此功能的现有应用目前可继续运行，但无法添加卡片库。 请将卡片库替换为新的 **[编辑窗体](controls/control-form-detail.md)** 和 **[显示窗体](controls/control-form-detail.md)** 控件。
