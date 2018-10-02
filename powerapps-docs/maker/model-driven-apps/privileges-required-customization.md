---
title: 模型驱动应用程序自定义所需的权限 | MicrosoftDocs
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="privileges-required-for-model-driven-app-customization"></a>模型驱动应用程序自定义所需的权限

应用用户可以个性化系统，甚至可以将其部分自定义项与他人共享，但只有具有正确权限的用户可以为每个人应用更改。  
  
> [!NOTE]
>  本部分假定您知道如何使用安全角色。 有关处理安全角色的详细信息，请参阅[创建用户和分派安全角色](https://docs.microsoft.com/dynamics365/customer-engagement/admin/create-users-assign-online-security-roles)。  
  
<a name="BKMK_SysAdminAndSysCustomizer"></a>   
## <a name="system-administrator-and-system-customizer-security-roles"></a>系统管理员和系统定制员安全角色  
 执行自定义的每个人都将拥有与其帐户关联的系统管理员或系统定制员安全角色。 这些安全角色为您提供自定义应用所需的权限。  
  
|系统管理员|系统定制员|  
|--------------------------|-----------------------|  
|拥有自定义系统的所有权限|拥有自定义系统的所有权限|  
|可以查看系统中的所有数据|只能查看其创建的系统实体的记录|  
  
 系统管理员和系统定制员安全角色之间的区别在于：系统管理员对系统中的大多数记录有读取权限，可以查看所有信息。 为需要执行自定义任务但不应该看到系统实体中的任何数据的人分派系统定制员角色。 但是，测试是系统自定义的一个重要部分。 如果系统定制员看不到任何数据，则将需要创建记录来测试其自定义项。 默认情况下，系统定制员对自定义实体拥有完全访问权限。 如果您需要为系统实体设置相同的限制，您需要调整系统定制员的安全角色，这样访问级别为**用户**，而不是自定义实体的**组织**。  
  
<a name="BKMK_DelegatingCustomizationTasks"></a>   
## <a name="delegate-customization-tasks"></a>代理自定义任务  
 您可能需要将某些任务委派给可信人员，从而使他们可以应用所需的更改。 请记住，任何人都可以有多个与其用户帐户关联的安全角色，并且安全角色所授予的特权和访问权限基于*最低限制*权限级别。  
  
 这表示可为已拥有其他安全角色（可能是销售经理）的用户提供系统定制员安全角色。 这样他们除了已拥有的其他权限，还可以自定义系统。 您不需要编辑他们已有的安全角色；在需要的时候，您可以从该人的用户帐户中删除系统定制员安全角色。  
  
<a name="BKMK_UsingTwoUserAccounts"></a>   
## <a name="test-customizations-without-customization-privileges"></a>在没有自定义权限情况下测试自定义项  
 务必使用没有自定义权限的用户帐户来测试所做的自定义内容。 这样，可以确保没有系统管理员或系统定制员安全角色的用户可以使用您的自定义项。 为了有效地做到这一点，您需要访问两个用户帐户：一个具有系统管理员安全角色的帐户，一个具有代表要使用自定义项的人的安全角色的帐户。  
  
> [!IMPORTANT]
>  如果您只有一个用户帐户，请不要尝试删除您的系统管理员安全角色。 如果您试图这样做，系统会警告您；但是，如果仍要这样做，则可能会发现自己无法撤消。 大多数安全角色不允许编辑用户的安全角色。  
  
## <a name="next-steps"></a>后续步骤  
[了解模型驱动应用程序组件](model-driven-app-components.md)

