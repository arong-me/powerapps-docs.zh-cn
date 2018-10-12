---
title: 通过 PowerApps 导入已翻译的实体和字段文本 | MicrosoftDocs
description: 了解如何导入已翻译的实体和字段文本
ms.custom: ''
ms.date: 06/19/2018
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
ms.openlocfilehash: e2417f7ad75e327fdfc54d4cd4fdd3f62395326b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669584"
---
# <a name="import-translated-entity-and-field-text-back-into-an-app"></a>将已翻译的实体和字段文本导回应用

如果具有自定义实体或字段文本（如字段标签或下拉列表值），则可以向组织中不使用环境基本语言版本的用户提供采用其语言的这一自定义文本。 为此，可导出所有自定义项的文本字符串，以便将它们翻译为组织中使用的语言。  
  
 翻译后，需要将已翻译的文本字符串导入环境中，用户才能利用这些更改。  
  
> [!IMPORTANT]
> - 导入的文件必须是根目录包含 CrmTranslations.xml 和 [Content_Types].xml 文件的压缩文件。  
> - 无法导入长度超过 500 个字符的已翻译文本。 如果翻译文件中的任何项目超过 500 个字符，导入进程将失败。 如果导入进程失败，请检查导致失败的文件中的行，减少字符数后再次尝试导入。 另请注意，导入已翻译的文本后，必须重新发布自定义项。  
  
1. 打开[解决方案资源管理器](../model-driven-apps/advanced-navigation.md#solution-explorer)。  
  
2. 在解决方案资源管理器的“操作”工具栏上，选择“导入翻译”。  
3.  在“导入已翻译的文本”对话框中，指定包含已翻译文本的文件，然后选择“导入”。  
  
4.  导入完成后，选择“关闭”。  
  
> [!NOTE]
>  发布自定义项可能会干扰系统的正常运行。 我们建议在对用户造成最小干扰的情况下安排发布。  

## <a name="community-tools"></a>社区工具

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) 是 XrmToolBox 社区为 Dynamics 365 Customer Engagement 开发的工具。 使用 Easy Translator 导出和导入具有上下文信息的翻译。 

> [!NOTE]
> Microsoft 不支持社区工具。 若对工具有疑问，请与发布者联系。 详细信息：[XrmToolBox](https://www.xrmtoolbox.com)。

## <a name="next-steps"></a>后续步骤  
 [导出自定义的实体和字段文本以进行翻译](export-customized-entity-field-text-translation.md)
