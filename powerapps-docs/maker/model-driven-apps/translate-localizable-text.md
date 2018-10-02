---
title: 翻译模型驱动应用程序的可本地化文本 | MicrosoftDocs
description: 了解如何翻译可本地化的文本以支持多种语言
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="translate-localizable-text-for-model-driven-apps"></a>翻译模型驱动应用程序的可本地化文本

如果您自定义了实体或字段文本（如字段标签或下拉列表值），可以以其各自语言向您的环境内不使用首选语言版本的环境的用户提供该自定义文本。 

此流程具有以下步骤：
1. 为您的环境启用其他语言
2. 导出可本地化文本
3. 翻译可本地化的文本
4. 导入已本地化的文本

## <a name="enable-other-languages-for-your-environment"></a>为您的环境启用其他语言

如果尚未为您的环境启用语言，请使用[启用语言](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages)中描述的步骤启用它们。

> [!IMPORTANT]
> 启用每种语言可能需要几分钟的时间。 在此期间，环境的其他用户可能无法使用您的应用程序。 您应该在对用户影响最小的时段启用语言。

> [!TIP]
> 当您启用语言时，请注意每种语言使用的 LCID 值。 该值将在可本地化文本的导出数据中代表语言。 四位数或五位数区域设置 ID 的语言代码。 可在[区域设置 ID (LCID) 图表](http://go.microsoft.com/fwlink/?LinkId=122128)中找到有效区域设置 ID 值。

## <a name="export-the-localizable-text"></a>导出可本地化文本

将导出的可本地化文本的范围是包含可本地化文本的非托管解决方案。 这只能使用解决方案资源管理器执行

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

在菜单栏中打开包含可本地化文本的非托管解决方案，选择**翻译** > **导出翻译**。 

![导出转换](media/export-localizable-text.png)

您应看到一条警报，显示：
> 导出要翻译的自定义标签可能需要几分钟时间。 在首次导出完成前不要再次单击导出链接。 是否确实要立即导出？ 

如果要继续，请单击**确定**。

导出完成后，可以在下载文件夹中找到名称类似于 `CrmTranslations_{0}_{1}.zip` 的文件，其中 `{0}` 是解决方案的唯一名称，`{1}` 是解决方案的版本号。

## <a name="get-the-localizable-text-translated"></a>翻译可本地化的文本

可将此文件发送给语言专家、翻译机构或本地化公司。

如果您具有文本翻译知识，或者您只是想查看格式，您可以提取所导出的 zip 文件，您将看到它包含两个 XML 文件。 
 - `[Content_Types].xml`
 - `CrmTranslations.xml`

您可以使用 Microsoft Office Excel 打开 CrmTranslations.xml 文件。

> [!TIP]
> 除非您习惯于使用 Excel 打开 XML 文件，否则打开 Excel 可能更方便，然后通过粘贴所提取的 CrmTranslations.xml 文件的路径选择打开文件。

> [!IMPORTANT]
> 请确保您没有更改文件格式。 如果您使用其他格式保存文件，将无法重新导入它。

在 Excel 中查看数据时，请查看**本地化标签**选项卡。

![导出的要进行本地化的文本](media/localized-labels-tab-exported-languages.png)

任何自定义实体或字段将具有可本地化文本的空单元格。 为这些项添加本地化值。

> [!NOTE]
> 如果更改了任何标准实体或实体字段的显示名称或描述，本地化的字符串将反映初始值的翻译。 这些值应该本地化以反映新值。

**显示字符串**选项卡包含为其他 UI 元素显示的文本，如功能区命令、错误消息和窗体标签。

### <a name="updating-localizable-text-in-the-base-language"></a>使用基本语言更新可本地化文本

如果更改包含在任何特殊消息中的任何标准实体或实体字段的显示名称，可以更新**显示字符串**选项卡中的信息以使用自定义的名称。

> [!TIP]
> 虽然显示的用于编辑系统实体消息的 UI 包括很多对实体名称的引用，但不包括所有引用。 使用此技巧可能找到更多。 详细信息：[编辑系统实体消息](../common-data-service/edit-system-entity-messages.md)

例如，如果将“客户”实体的显示名称更改为*公司*，搜索**显示字符串**中的基本语言列来查找以下匹配项：`account`、`accounts`、`Account` 和 `Accounts`，然后对 `company`、`companies`、`Company` 和 `Companies` 分别进行适当的替换。

> [!IMPORTANT]
> 不要为此在文件中执行常规查找/替换。 您应注意，匹配文本实际引用您更改的名称。


## <a name="import-the-localized-text"></a>导入已本地化的文本
导入文本需要压缩文件并将它们导入到系统。

### <a name="compress-the-files"></a>压缩文件

在对 `CrmTranslations.xml` 文件进行更改之后，您必须将此文件连同 `[Content_Types].xml` 文件压缩为 zip 格式。 只需选择*两个文件*，然后使用鼠标右键单击以打开上下文菜单。 在上下文菜单中，选择**发送到** > **压缩文件夹**。

### <a name="import-the-files"></a>导入文件

在您从中导出翻译的同一个非托管解决方案中，在菜单中选择**翻译** > **导入翻译**。 

![导入翻译](media/import-translations.png)

选择包含压缩的已翻译文本的文件，然后选择**导入**。

![导入所选文件](media/import-translated-text-dialog.png)

在翻译的文本导入后，应该发布所有自定义项以查看您的应用程序的更改；

## <a name="community-tools"></a>社区工具

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) 是一款 XrmToolBox 社区开发的工具。 可使用 Easy Translator 导出和导入翻译和上下文信息。 

> [!NOTE]
> 这些社区工具不受 Microsoft 支持。
> 如果您对该工具有任何疑问，请联系发布者。 详细信息：[XrmToolBox](https://www.xrmtoolbox.com)。


## <a name="next-steps"></a>后续步骤
[组织的区域和语言选项](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages)<br />
[编辑系统实体消息](../common-data-service/edit-system-entity-messages.md)

