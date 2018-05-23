---
title: Power Query 疑难解答 | Microsoft Docs
description: 解决了使用 Power Query 在 Common Data Service (CDS) for Apps 中创建自定义实体时遇到的问题。
author: mllopis
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/16/2018
ms.author: millopis
ms.openlocfilehash: b89d7a59406d19759b84c34dbda84b98b10d5e58
ms.sourcegitcommit: f236364ecb06dd86244cd9a607c31e0d716912e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
---
# <a name="troubleshooting-power-query"></a>Power Query 疑难解答
使用 Power Query 创建包含外部数据源数据的自定义实体时，可能会看到以下错误消息：

`Your Azure Active Directory administrator has set a policy that prevents you from using this feature. Please contact your administrator, who can grant permissions for this feature on your behalf.`

如果 Power Query 无法访问组织在 PowerApps 或 ommon Data Service (CDS) for Apps 中的数据，此错误消息就会出现。 在下列两种情况下，可能会遇到此问题：

* Azure Active Directory (AAD) 租户管理员已禁止用户授权应用代表他们访问公司数据。
* 使用非托管 Active Directory 租户。 非托管租户是不含全局管理员的目录，旨在完成自助注册服务。 若要在这种情况下解决问题，用户必须先转换为托管租户，再使用以下部分中介绍的两个解决方案之一来解决此问题。

若要解决此问题，Azure Active Directory 管理员必须按照本主题稍后介绍的其中一个过程的步骤操作。

## <a name="allow-users-to-consent-to-apps-that-access-company-data"></a>允许用户授权应用访问公司数据
相较下一种方法，这种方法可能更简单，但授予的权限更宽泛。

1. 在 [https://portal.azure.com](https://portal.azure.com) 中，打开“Azure Active Directory”边栏选项卡，再选择“用户设置”。
2. 选中“用户可以同意应用代表他们访问公司数据”旁边的“是”，再选择“保存”。

## <a name="allow-power-query-to-access-company-data"></a>允许 Power Query 访问公司数据
另一种解决方案是让租户管理员授权 Power Query 访问公司数据，而不修改租户范围权限。

1. 安装 [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps)。
2. 运行以下 PowerShell 命令：
   * Login-AzureRmAccount（并以租户管理员身份登录）
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128

与全租户解决方案相比，此方法的优势在于，这种解决方案非常具有针对性。 它仅预配 Power Query 服务主体，不会对租户进行其他任何权限更改。

## <a name="updating-personal-data"></a>更新个人数据

用户可通过查询编辑器以及可从查询编辑器访问的 `Options` 对话框更新混合数据及其他信息（如查询名称和混合元数据）。

在 PowerApps 中，可按照以下步骤访问查询编辑器：转到“数据”窗格，展开，然后单击“实体”窗格菜单项。 进入查询编辑器后，单击“...”菜单并选择“编辑查询”。 然后，单击功能区中的 `Options` 按钮，单击 `Export Diagnostics` 按钮。


## <a name="deleting-personal-data"></a>删除个人数据

大多数数据都在 30 天后自动删除。 对于混合数据和元数据，用户需要通过 PowerApps 删除其所有混合数据。 所有相关数据和元数据都将在 30 天后删除。

可从 PowerApps 删除混合数据，操作步骤：从“数据集成器”选项卡删除数据集成器项目，单击“...”，然后选择 `Delete` 选项。

如果通过“基于数据新建实体（技术预览版）”功能创建混合数据，则可按以下步骤删除它：单击“...”按钮，选择“编辑查询”，然后选择功能区中的“选项”，最后单击“删除所有查询”按钮。 确认需要删除查询后，将删除查询。


## <a name="exporting-personal-data"></a>导出个人数据

用户可打开查询编辑器，单击功能区中的 `Options` 按钮，然后单击 `Export Diagnostics` 按钮。

在 PowerApps 中，可按照以下步骤访问查询编辑器：转到“数据”窗格，展开，然后单击“实体”窗格菜单项。 进入查询编辑器后，单击“...”菜单并选择“编辑查询”。 然后，单击功能区中的 `Options` 按钮，单击 `Export Diagnostics` 按钮。

可在 Azure 门户中访问关于用户界面 (UI) 中用户操作的系统生成日志。


