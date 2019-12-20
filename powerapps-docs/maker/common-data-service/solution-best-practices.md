---
title: Power Apps 中的解决方案最佳实践 | MicrosoftDocs
description: 了解使用解决方案时的最佳实践
ms.custom: ''
ms.date: 10/08/2019
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
ms.assetid: ''
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 810fd536da5236f5ac7490505e82e78179ab61da
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865279"
---
# <a name="best-practices-when-working-with-solutions"></a>使用解决方案时的最佳实践 
本主题介绍使用解决方案时的最佳实践。 


## <a name="use-a-single-managed-solution-to-manage-a-model-driven-app"></a>使用单个托管解决方案来管理模型驱动应用 
要更新托管解决方案中包含的应用，请使用更新或修补程序解决方案。 请勿在具有相同模型驱动应用的环境中安装其他托管解决方案。 详细信息：[更新解决方案](import-update-export-solutions.md#update-solutions)和[使用细分解决方案和修补程序导出选定的实体资产](use-segmented-solutions-patches-simplify-updates.md) 


## <a name="use-security-roles-to-manage-app-access"></a>使用安全角色管理应用访问
模型驱动应用应分配安全角色，以控制用户访问。 详细信息：[向应用添加安全角色](../model-driven-apps/share-model-driven-app.md#add-security-roles-to-the-app) 

## <a name="delete-the-managed-solution-to-delete-a-model-driven-app"></a>删除托管解决方案以删除模型驱动应用 
要删除作为托管解决方案的一部分安装在默认解决方案中的模型驱动应用，请删除托管解决方案。 

不要从作为托管解决方案一部分安装的默认环境中直接删除应用或应用的站点地图。 这样做可能导致解决方案升级或用于安装该应用的解决方案更新失败。 直接删除模型驱动应用的一个示例是在解决方案资源管理器中打开默认解决方案，然后转到**模型驱动应用**，选择该应用，然后选择**删除**。

### <a name="see-also"></a>另请参阅
[解决方案概述](solutions-overview.md)
