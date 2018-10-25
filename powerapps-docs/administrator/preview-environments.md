---
title: 预览环境 | Microsoft Docs
description: 通过 PowerApps 预览版程序提前获得功能
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 08/29/2018
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: e2c4c735827941b32ce5e019eb8d71e4328e4a7a
ms.sourcegitcommit: b8eee36e680036accb0e7d9fc7a434906af1c4d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2018
ms.locfileid: "43297933"
---
# <a name="powerapps-preview-program"></a>PowerApps 预览版程序
PowerApps 每隔几天或数周会更新一次平台及其功能。 PowerApps 预览版程序可用于提前获取这些即将推出的功能和更新，而其他区域尚未推出（已部署客户生产应用）。 

使用 PowerApps 预览版程序，你可以：
- 试用、了解和测试即将推出的功能：许多功能将首先在预览版中推出一段时间以获取反馈。 通过参与预览版计划，可以更快地了解新功能并提供反馈。 此外，还将可以做好准备以便在已创建生产应用的区域推出新功能后快速加以利用。
- 通过即将推出的 PowerApps 更新 (vNext) 确保当前应用将继续工作以使业务保持连续性。

## <a name="what-in-powerapps-is-available-for-preview"></a>可预览 PowerApps 中的哪些功能？
若要访问 PowerApps 中的预览版功能，你需要进入预览环境。 有关预览环境的更多详细信息，请参阅下一节。
目前，我们将在 PowerApps 中针对以下情况推出预览版：
1. 创建应用：可以使用 PowerApps 的下一个版本创建基于画布的应用。 通过在预览环境中创建应用可以实现此目的。 当前限制包括 - 无法在预览版程序中构建模型驱动应用 - 我们正致力于处理此情况。
2. 管理应用：使用[PowerApps Web 门户][2]可以管理和共享应用。 若要访问预览版功能，只需进入预览环境；它将转到 [PowerApps Web 门户][3]预览版。
3. 播放应用：需要使用 Web 播放器在预览环境中播放应用。 执行此操作时，将自动转到[预览版 Web 播放器][4]。 将通过 vNext 版 PowerApps Web 播放器播放应用。 当前限制包括 - 现在无法预览适用于 iOS、Android 和 Windows 的 PowerApps Mobile。 可能无法播放在首版环境中创建的应用 - 我们正致力于处理此情况。
4. 管理 PowerApps：可以使用[预览版 PowerApps 管理中心][1]预览管理员体验

## <a name="how-to-get-early-access-to-the-upcoming-updates"></a>如何提前获得即将发布的更新？
对于 PowerApps，环境中将存储所有应用和相关资源。 通过在已部署 vNext（预览版）的区域中创建的环境，也可以提前获得所有预览版功能。 现在，只有一个区域“预览版（美国）”，如下图中所示：

![](./media/preview-environment/env3-preview.png)

选择“预览版（美国）”作为环境区域，并同意加入预览版程序来创建环境，以获取对下一版 (vNext) PowerApps 的访问权限。
此环境中创建的所有应用和其他资源均位于 vNext 版平台 (SAAS)。

## <a name="how-to-learn-about-the-latest-updates"></a>如何了解最新的更新？
要了解可供预览的新功能，请查看 [PowerApps 新增功能][5]。 仅预览版中提供的功能标记有“预览版”。

## <a name="key-scenarios-to-test-with-the-preview-program"></a>预览版程序要测试的关键方案
1. **通过即将发布的 PowerApps 更新 (vNext) 验证生产应用**

   你可能需要验证生产应用，以便其适用于即将发布的 PowerApps 更新。 你可以将应用从生产环境[复制][6]到首版环境中并播放应用，以测试方案。 请注意，所有其他必需资源（如 CustomAPI 和流等）将需要随之一起移动。 这只会创建这些应用和所需资源的另一个副本。 你可以开始测试较新更新，这些更新不只是用于播放应用，而且还可以用于编辑和管理应用。
   
2. **尝试预览版中可用的新功能**

   我们将首先在“预览版（美国）”区域推出诸多新功能。 在其余区域推出这些新功能之前，你可以提前试用（这可能会影响生产环境）。

## <a name="how-to-provide-feedback-to-the-product-team"></a>如何向产品团队提供反馈？
可以通过 [PowerApps 论坛][8]和/或联系[支持][9]以提供反馈。

## <a name="what-are-the-known-issues-and-limitations"></a>已知问题和限制有哪些？
1. **预览版中不提供的 PowerApps 门户和客户端** 

   预览版中提供某些功能、服务和门户：
   
   ![](./media/preview-environment/table.png)

2. **从 Windows 的 Desktop Studio 访问首版环境中创建的应用**

   如上所述，预览版中不提供 Windows 的 Desktop Studio。 因此，在预览环境中创建或编辑应用可能不适用于 Desktop Studio，并显示以下错误消息：
   
   ![](./media/preview-environment/error2.jpg)

   在这种情况下，我们建议使用 Web Studio 来在预览环境中创建或编辑应用。

3. **无法在预览区域中创建数据库**

   目前，无法在预览版（美国）区域环境中通过 Common Data Service for Apps 创建数据库 - 我们正致力于处理此情况。


<!--Reference links in article-->
[1]: https://preview.admin.powerapps.com
[2]: https://web.powerapps.com
[3]: https://preview.web.powerapps.com
[4]: https://preview.web.powerapps.com/webplayer
[5]: https://docs.microsoft.com/powerapps/maker/canvas-apps/release-notes
[6]: https://docs.microsoft.com/powerapps/administrator/environment-and-tenant-migration
[7]: https://preview.create.powerapps.com
[8]: https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1
[9]: https://powerapps.microsoft.com/support/

