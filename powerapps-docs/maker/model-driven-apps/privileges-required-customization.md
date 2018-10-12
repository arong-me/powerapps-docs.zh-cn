---
title: 模型驱动应用自定义的所需特权 | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 43cf7f3a-7e26-4990-8b5a-c817ac6d51bb
caps.latest.revision: 13
ms.author: matp
manager: kvivek
author: Mattp123
ms.openlocfilehash: dd0c7e05d756145a701bb6bfb137dc07cb8c45fb
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668147"
---
# <a name="privileges-required-for-model-driven-app-customization"></a>模型驱动应用自定义的所需特权

应用用户可以对系统进行个性化设定，甚至可以与其他人共享他们的一些自定义项，但只有具有正确特权的用户才能为每个人应用更改。  
  
> [!NOTE]
>  本节假定你知道如何使用安全角色。 有关使用安全角色的详细信息，请参阅[创建用户和分配安全角色](https://docs.microsoft.com/dynamics365/customer-engagement/admin/create-users-assign-online-security-roles)。  
  
<a name="BKMK_SysAdminAndSysCustomizer"></a>   
## <a name="system-administrator-and-system-customizer-security-roles"></a>系统管理员和系统定制员安全角色  
 进行自定义的人员将具有与其帐户关联的系统管理员或系统定制员安全角色。 这些安全角色提供对应用进行自定义所需的权限。  
  
|系统管理员|系统定制员|  
|--------------------------|-----------------------|  
|具有对系统进行自定义的完整权限|具有对系统进行自定义的完整权限|  
|可以查看系统中的所有数据|仅可以查看他们所创建的系统实体的记录|  
  
 系统管理员和系统定制员安全角色之间的区别在于系统管理员对系统中的大多数记录具有读取特权，并且可以查看所有内容。 将系统定制员角色分配给需要执行自定义任务但不应看到系统实体中任何数据的人员。 但是，测试是对系统进行自定义的重要部分。 如果系统定制员无法查看任何数据，他们则需要创建记录以测试其自定义项。 默认情况下，系统定制员具有自定义实体的完全访问权限。 如果你想让系统实体具有相同的限制，需要调整系统定制员安全角色，使针对自定义实体的访问级别为“用户”而非“组织”。  
  
<a name="BKMK_DelegatingCustomizationTasks"></a>   
## <a name="delegate-customization-tasks"></a>委派自定义任务  
 你可能需要将一些任务委派给受信任的人员，使他们能够应用所需的更改。 请记住，任何人都可以拥有与其用户帐户相关联的多个安全角色，并且安全角色授予的特权和访问权限基于的是限制性最低的权限级别。  
  
 这意味着你可以将系统定制员安全角色授予已经拥有其他安全角色的人员，例如销售经理。 除了他们已有的其他特权外，这使他们可以对系统进行自定义。 你无需编辑他们已有的安全角色，并且可以根据需要从该人员的用户帐户中删除系统定制员安全角色。  
  
<a name="BKMK_UsingTwoUserAccounts"></a>   
## <a name="test-customizations-without-customization-privileges"></a>测试在没有自定义权限的情况下进行的自定义  
 你应该始终测试通过使用没有自定义特权的用户帐户所做的任何自定义。 这样可以确保没有系统管理员或系统定制员安全角色的人员能够使用你的自定义项。 若要有效地执行此操作，需要访问两个用户帐户：一个具有系统管理员安全角色的帐户，一个具有代表将使用自定义项的人员的安全角色的帐户。  
  
> [!IMPORTANT]
>  如果只有一个用户帐户，请不要尝试删除系统管理员安全角色。 如果尝试删除，系统将发出警告；但如果继续操作，则可能无法将其恢复。 大多数安全角色不允许编辑用户的安全角色。  
  
## <a name="next-steps"></a>后续步骤  
 [自定义入门](getting-started-customization.md)

