---
title: PowerApps 常见问题和解决方法 | Microsoft Docs
description: PowerApps 中的常见问题及解决方法列表。
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/10/2018
ms.author: anneta
ms.openlocfilehash: d5603ffacc0246dcffd1c54ab63b4e404250a7d5
ms.sourcegitcommit: fc235972d0d4661f55df7a71e2dcedafd42706b0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2018
ms.locfileid: "39202289"
---
# <a name="common-issues-and-resolutions-for-powerapps"></a>PowerApps 常见问题和解决方法
本文列出了你在使用 PowerApps 时可能遇到的一些常见问题。 并在适用情况下提供了解决方法。

## <a name="recently-addedchanged"></a>最近添加/更改的内容
1. **从嵌入的应用启动网站**

    Internet Explorer 和 Microsoft Edge 浏览器可能会阻止启动处于受保护模式的 URL 或网站或者比加载的应用中的网站更低安全性的区域。 若要解决此问题，请为你的浏览器[更改安全和隐私设置](https://support.microsoft.com/en-us/help/17479/windows-internet-explorer-11-change-security-privacy-settings)。

1. **库中的组合框控件**

    在图库中使用“组合框”控件时，用户滚动库时不保留其选项。 如果在不滚动的库中使用“组合框”控件，将不出现此问题。 当前未提供解决方法。


1. **使用自定义图像作为应用图标**

    在 PowerApps Studio for Windows 版本 3.18043 中，无法上传自定义图像以将其用作应用图标。 若要解决此问题，请使用 [PowerApps Studio for web](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上传自定义图像。 或者，可以使用 PowerApps Studio for Windows 中的一个图标并自定义背景色。

1. **跨应用复制和粘贴屏幕**

    当前不支持跨应用复制和粘贴屏幕。 若要解决此问题，向目标应用添加新屏幕，从源应用屏幕中复制控件，然后将其粘贴到目标应用屏幕。

1. **更改 SharePoint 表单布局**

    自定义某些语言的 SharePoint 列表表单时，如果尝试将布局从纵向（默认）更改为横向，应用可能会显示多个错误（控件中的黄色三角形）。 若要修复这些错误并保留横向布局，请单击“撤消”。

1. **应用程序不工作**

    如果创建的应用在未发出警告的情况下停止工作，则可能是因为在过去六个月的时间里没有对其进行更新或重新发布。 若要解决此问题，更新和/或重新发布应用以使其与最新版本的 PowerApps 同步，并确保在最后一次发布时起的六个月内继续更新和/或重新发布该应用。

1. **“数据表”控件**

    如果复制并粘贴“数据表”控件，且它的 Items 属性设置为包含 Filter 函数的公式，新“数据表”控件的 Items 属性的公式以包含 _1 后缀的字段名称结尾。 这就会导致字段名称无效，且数据表不显示任何数据。 若要解决此问题，请在复制此控件前，先确认 Filter 函数从数据源中引用的任何字段都不与“数据表”控件中的列同名。 如果是，请重命名“数据表”控件中的列。 也可以从无效的字段名称中删除 _1 后缀，让它们与实体中的名称保持一致。

1. **适用于 Windows 的 PowerApps Studio 中的照相机控件**

    如果添加照相机控件或打开使用照相机控件的应用，适用于 Windows 的 PowerApps Studio 可能会发生故障。 为了避免此问题发生，请在添加或使用照相机控件时，使用[适用于 Web 的 PowerApps Studio](create-app-browser.md)。

2. **Android 设备上的版本 2.0.700**

    如果在 Android 设备上安装版本 2.0.700，然后无法打开应用（或应用停止响应），请先卸载 PowerApps 并重启设备，再重新安装 PowerApps。

3. **打开应用时库为“空”**

    通过数据自动生成应用，保存应用，然后将其重新打开，浏览库时可能不会立即显示数据。 若要解决此问题，请在搜索框中至少键入一个字符，然后删除键入的文本。 这样库就能按预期方式显示数据了。

4. **在 Windows 8.1 上升级 PowerApps**

    如果安装 PowerApps 的计算机上运行的是 Windows 8 或 Windows 8.1，请打开 Windows 应用商店应用并使之处于活动状态，使用“设置”超级按钮检查更新程序，然后安装更新程序。

5. **自定义连接器和 Common Data Service**

   如果使用 PowerApps 生成号 2.0.540 或更低版本创建的应用依赖 Common Data Service 中的数据库和至少一个位于不同环境中的自定义连接器，需要将连接器部署到与数据库相同的环境中，并将应用更新为使用新连接器。 否则，将出现一个对话框，通知用户找不到此 API。 有关详细信息，请参阅[环境概述](../../administrator/environments-overview.md)。

6. **在 Windows 8.1 上运行应用**

    如果安装 [此适用于 Windows 8.1 的更新](https://technet.microsoft.com/library/security/ms16-118)，则无法运行在此操作系统上用 PowerApps Studio 打开的应用。 但是，你仍可以运行在 [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 中打开的或使用 PowerApps Mobile 打开的应用。

7. **带空格的列名称**

    如果使用的 SharePoint 列表或 Excel 表的列名称包含空格，PowerApps 会将空格替换为“\_x0020\_”。 例如，如果 SharePoint 或 Excel 中的“Column Name”在数据布局中显示或用于公式，它将在 PowerApps 中显示为“Column_x0020_Name”。

8. <a name="out-of-memory"></a>**浏览器内存不足**

    如果使用 PowerApps 时内存不足，请考虑下载 64 位版本的 Chrome、Edge 或 Internet Explorer。

## <a name="older"></a>之前的内容
1. **更改共享应用中的流**

    如果你将流添加到应用、共享该应用，然后在此流中添加服务或更改连接，则必须从此共享应用中删除此流、重新添加此流并刷新此应用。 否则，触发此流的用户将无法通过身份验证。

2. **使用本地化版本**。

    如果在 Windows 8.1 上运行的是版本 2.0.531 并且设备被设置为需要 IME 窗口的语言，则无法在**文本输入**控件中键入。

3. **Windows Phone 中的照相机控件**

    如果在运行内部版本 10.0.10586.107 的 Windows Phone 上打开包含照相机控件的应用，则此应用可能会崩溃。 要避免此问题，请升级到最新的内部版本（例如通过运行 [升级顾问](https://www.microsoft.com/store/p/upgrade-advisor/9nblggh0f5g4)）。

4. **从模板打开应用**。

    如果运行的是版本 2.0.500 或早期版本，在尝试从模板创建应用时会出现错误消息。 必须进行升级才能使用此功能。

    如果运行的是版本 2.0.510 或更高版本，在尝试从模板创建应用时可能会出现警告。 但是，可以关闭该消息并创建应用。

5. **扫描条形码**

    有关使用**条形码**控件的限制和最佳做法的信息，请参阅 [扫描条形码](scan-barcode.md)。

6. **在浏览器中创建和修改应用**

    在适用于 Web 的 PowerApps Studio 中，可以执行在适用于 Windows 的 PowerApps Studio 中执行的许多相同操作，但不是全部。 有关详细信息，请参阅 [在浏览器中创建应用](create-app-browser.md)。

7. **更改实体中的标题字段**

    如果更改由其他实体通过一个或多个查找引用的实体的标题字段，则在尝试保存更改时会出错。 要解决此问题，请删除针对要更改标题字段的实体的全部查找，做出更改，然后重新创建查找。 有关查找的详细信息，请参阅 [实体之间的关系](../common-data-service/data-platform-entity-lookup.md)。

8. **连接到本地 SharePoint 的应用**

    如果共享的应用依赖于未自动共享的连接（例如本地 SharePoint 站点），则用户在单击或点击“**登录**”，在浏览器中打开应用时，将看到不包含任何文本的对话框。 要关闭对话框，请单击或点击右上角的关闭 (X) 图标。 如果在 PowerApps Studio 或 PowerApps Mobile 中打开应用，则不会出现此对话框。 有关共享连接的详细信息，请参阅 [共享应用资源](share-app-resources.md)。

9. **PowerApps 通过数据生成应用时，系统不会自动配置用于排序和搜索的字段**。

   要配置此字段，按照 [添加库](add-gallery.md) 中筛选和排序部分所述，编辑库的 **[项](controls/properties-core.md)** 公式。

10. **通过数据创建的应用只能访问数据源的前 500 条记录**。

     一般情况下，通过向数据源委派操作，PowerApps 可用于任意大小的数据源。 对于不能委派的操作，PowerApps 在创作时将发出警告，并仅对该数据源的前 500 条记录执行操作。  请参阅 [筛选器函数](functions/function-filter-lookup.md) 文章，了解有关委派的详细信息。

11. **Excel 数据必须为表格式**。

     有关将 Excel 用作数据源的限制的信息，请参阅 [云存储连接](connections/cloud-storage-blob-connections.md#known-limitations)。

12. **支持 SharePoint 自定义列表，但不支持库、某些类型的列表列或者支持多个值或选择的列**。

     有关详细信息，请参阅 [SharePoint Online](connections/connection-sharepoint-online.md#known-issues)。

13. **共同创作不受支持。每次仅支持一位作者创作**。

     如果多人同时修改同一应用，可能会损坏应用或覆盖他人所做的更改。 在他人编辑之前关闭应用。

14. **新共享的应用要在几分钟后才能使用**。

     在某些情况下，新共享的应用不会立即可用。 请稍等片刻即可使用。

15. **在 [窗体控件](controls/control-form-detail.md) 中，无法使用自定义卡更改数据**。

     常用自定义卡缺少写回更改所需的 **[更新](controls/control-card.md)** 属性。 要解决此问题：

    * 选择窗体控件，并根据希望卡显示的字段通过右侧窗格插入一个卡。  
    * 按照 [了解数据卡](working-with-cards.md#unlock-a-card) 中所述内容来解锁卡。
    * 根据需要删除或重新排列卡内的控件，类似于自定义卡的操作。

16. **在 Android 5.0、具有 Webview 版本 v48 或 v49 的 Nexus 6 上运行的应用可能会崩溃**。

     用户更新到 Webview (3x) 之前的版本或更新到 Android 6.0 即可解决此问题。

17. **如果内存不足，可能会暂时禁用照相机**。

     如果移动设备内存不足，照相机将暂时禁用，以避免设备崩溃。

18. **Office 365 视频连接器不受支持**。

19. **卡片库已停用**。

     使用此功能的现有应用目前可继续运行，但无法添加卡片库。 请将卡片库替换为新的 **[编辑窗体](controls/control-form-detail.md)** 和 **[显示窗体](controls/control-form-detail.md)** 控件。
