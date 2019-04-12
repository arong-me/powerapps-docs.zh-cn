---
title: 使用 PowerApps 导入翻译后的实体和字段文本 | MicrosoftDocs
description: 了解如何导入已翻译的实体和字段文本
ms.custom: ''
ms.date: 06/19/2018
ms.reviewer: ''
ms.service: powerapps
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
# <a name="import-translated-entity-and-field-text-back-into-an-app"></a>将经过翻译的实体和字段文本导回应用

如果您自定义了实体或字段文本（如字段标签或下拉列表值），可以以其各自语言向贵公司内不使用基本语言版本的环境的用户提供该自定义文本。 为此，您可以导出所有自定义项的文本字符串，使其转换为贵公司内使用的语言。  
  
 经过翻译之后，在用户利用更改之前，您需要将翻译后的文本字符串导入到环境中。  
  
> [!IMPORTANT]
> - 您导入的文件必须是在根目录中包含 CrmTranslations.xml 和 [Content_Types].xml 文件的压缩文件。  
> - 无法导入长度超过 500 个字符的已翻译文本。 如果翻译文件中的任何一项的长度超过 500 个字符，则导入过程将失败。 如果导入过程失败，请检查文件中导致失败的行并减少该行的字符数，然后重新尝试导入。 同时注意在导入已翻译的文本后，您必须重新发布自定义项。  
  
1. 打开[解决方案资源管理器](../model-driven-apps/advanced-navigation.md#solution-explorer)。  
  
2. 在解决方案资源管理器的“操作”工具栏上，选择**导入翻译**。  
3.  在**导入已翻译的文本**对话框中，指定包含翻译文本的文件，然后选择**导入**。  
  
4.  导入完成后，选择**关闭**。  
  
> [!NOTE]
>  发布自定义项会干扰常规系统运行。 我们建议您以对用户造成的干扰最少为宗旨，合理安排发布时间。  

## <a name="community-tools"></a>社区工具

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) 是一款 XrmToolBox 社区为 Dynamics 365 Customer Engagement 开发的工具。 可使用 Easy Translator 导出和导入翻译和上下文信息。 

> [!NOTE]
> 这些社区工具不受 Microsoft 支持。 如果您对该工具有任何疑问，请联系发布者。 详细信息：[XrmToolBox](https://www.xrmtoolbox.com)。

## <a name="next-steps"></a>后续步骤  
 [导出要翻译的自定义实体和字段文本](export-customized-entity-field-text-translation.md)
