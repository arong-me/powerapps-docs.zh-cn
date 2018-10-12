---
title: 为模型驱动应用翻译可本地化文本 | MicrosoftDocs
description: 了解如何翻译可本地化文本以支持多种语言
ms.custom: ''
ms.date: 06/03/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 3d77d149-819b-45e6-8e70-1fbe54d5c153
caps.latest.revision: 19
ms.author: matp
manager: kvivek
ms.openlocfilehash: e2e305313f3b86be2ea410f6668676b56aa79d95
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667810"
---
# <a name="translate-localizable-text-for-model-driven-apps"></a>为模型驱动应用翻译可本地化文本

如果具有自定义实体或字段文本（如字段标签或下拉列表值），则可以向环境中不使用基本语言版本环境的用户提供采用其首选语言的这一自定义文本。 

该过程具有以下步骤：
1. 为环境启用其他语言
2. 导出可本地化文本
3. 翻译可本地化文本
4. 导入本地化文本

## <a name="enable-other-languages-for-your-environment"></a>为环境启用其他语言

如果尚未为环境启用语言，请使用[启用语言](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages)中所述的步骤来启用它们。

> [!IMPORTANT]
> 每种语言可能需要几分钟时间才能启用。 在此期间，环境的其他用户可能无法使用你的应用。 应在对用户干扰最小的时间启用语言。

> [!TIP]
> 在启用语言时，记下用于每种语言的 LCID 值。 此值在为可本地化文本导出的数据中表示相应语言。 语言代码是四位数或五位数区域设置 ID。 有效区域设置 ID 值可以在[区域设置 ID (LCID) 图表](http://go.microsoft.com/fwlink/?LinkId=122128)中找到。

## <a name="export-the-localizable-text"></a>导出可本地化文本

将导出的可本地化文本的范围是包含可本地化文本的非托管解决方案。 这只能使用解决方案资源管理器进行

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

打开包含可本地化文本的非托管解决方案，在菜单栏中选择“翻译” > “导出翻译”。 

![导出翻译](media/export-localizable-text.png)

应会看到一个警报，其中显示：
> 导出自定义标签进行翻译可能需要几分钟。 在第一个导出完成之前请勿再次单击导出链接。 是否确定要立即导出? 

如果要继续，则单击“确定”。

导出完成后，可以在下载文件夹中找到一个名称类似于 `CrmTranslations_{0}_{1}.zip` 的文件，其中 `{0}` 是解决方案的唯一名称，`{1}` 是解决方案的版本号。

## <a name="get-the-localizable-text-translated"></a>翻译可本地化文本

可以将此文件发送给语言专家、翻译机构或本地化公司。

如果你拥有翻译文本的知识，或者如果只想查看格式，则可以解压缩导出的 zip 文件，你会看到它包含两个 XML 文件。 
 - `[Content_Types].xml`
 - `CrmTranslations.xml`

可以使用 Microsoft Office Excel 打开 CrmTranslations.xml 文件。

> [!TIP]
> 除非通常使用 Excel 打开 XML 文件，否则打开 Excel，然后通过粘贴解压缩的 CrmTranslations.xml 文件路径来打开该文件可能会更加容易。

> [!IMPORTANT]
> 请确保不要更改文件格式。 如果将文件保存为其他格式，则你将无法重新导入它。

在 Excel 中查看数据时，看看“本地化标签”选项卡。

![用于本地化的导出文本](media/localized-labels-tab-exported-languages.png)

任何自定义实体或字段都具有用于可本地化文本的空单元格。 为这些项添加本地化值。

> [!NOTE]
> 如果为任何标准实体或实体字段更改了显示名称或描述，则本地化字符串仍会反映原始值的翻译。 这些内容应进行本地化以反映新值。

“显示字符串”选项卡包含为其他 UI 元素（如功能区命令、错误消息和窗体标签）显示的文本。

### <a name="updating-localizable-text-in-the-base-language"></a>更新采用基本语言的可本地化文本

如果为包含在任何特殊消息中的任何标准实体或实体字段更改显示名称，则可以在“显示字符串”选项卡中更新信息以使用自定义名称。

> [!TIP]
> 虽然为编辑系统实体消息而公开的 UI 包括许多对实体名称的引用，但是它并不包括所有内容。 使用此方法可以找到更多。 详细信息：[编辑系统实体消息](../common-data-service/edit-system-entity-messages.md)

例如，如果将 Account 实体的显示名称更改为 Company，则在“显示字符串”中的基本语言列中搜索以下匹配项：`account`、`accounts`、`Account` 和 `Accounts`，然后分别相应地替换为 `company`、`companies`、`Company` 和 `Companies`。

> [!IMPORTANT]
> 请勿为此在文件中执行常规查找/替换。 应注意的是，匹配文本实际引用已更改的名称。


## <a name="import-the-localized-text"></a>导入本地化文本
导入文本需要压缩文件并将它们导入系统中。

### <a name="compress-the-files"></a>压缩文件

更改 `CrmTranslations.xml` 文件之后，必须将该文件与 `[Content_Types].xml` 文件一起压缩为 zip 格式。 只需选择这两个文件，然后单击鼠标右键按钮以打开上下文菜单。 在上下文菜单中，选择“发送到” > “压缩的文件夹(zip 格式)”。

### <a name="import-the-files"></a>导入文件

从导出翻译的相同非托管解决方案，在菜单中选择“翻译” > “导入翻译”。 

![导入翻译](media/import-translations.png)

选择包含压缩翻译文本的文件，然后选择“导入”。

![导入所选文件](media/import-translated-text-dialog.png)

导入翻译文本之后，应发布所有自定义项以查看应用中的更改；

## <a name="community-tools"></a>社区工具

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) 是 XrmToolBox 社区开发的工具。 使用 Easy Translator 导出和导入具有上下文信息的翻译。 

> [!NOTE]
> Microsoft 不支持社区工具。
> 若对工具有疑问，请与发布者联系。 详细信息：[XrmToolBox](https://www.xrmtoolbox.com)。


## <a name="next-steps"></a>后续步骤
[组织的区域和语言选项](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages)<br />
[编辑系统实体消息](../common-data-service/edit-system-entity-messages.md)

