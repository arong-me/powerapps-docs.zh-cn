---
title: 查看联系人或用户的个人资料卡片 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 276c7d3cbf95947306fab768da8af3c4c66b33e0
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543378"
---
# <a name="view-the-profile-card-for-a-contact-or-user"></a>查看联系人或用户的个人资料卡片

使用个人资料卡片快速获取有关联系人或用户的信息。 如果在 Dynamics 365 的模型驱动应用（如 Dynamics 365 Sales 和 Dynamics 365 Customer Service）中选择联系人或用户字段，则可以在其个人资料卡片上查找相关信息。 有关个人资料卡片的详细信息，请参阅 [Office 365 中的](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501)。

> [!NOTE]
>  - 个人资料卡片可用于“联系人”和“用户”实体   。 有关信息，请参阅[启用个人资料卡片（适用于管理员）](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-profile-card)。
>  - 如果在 Azure Active Directory 中针对 Office Delve 服务启用了多重身份验证，则不会显示 Common Data Service 中的个人资料卡片。

## <a name="view-a-contacts-profile"></a>查看联系人的个人资料

1.  转到“活动”  。
2.  选择现有活动或创建新活动。
3.  如果“被叫方”字段包含联系人记录，则将鼠标悬停在该字段上  。 

可以查看内联联系人的详细信息，其中包括联系人图片、名称、标题和帐户。

4. 要查看更多详细信息，请选择“显示更多”以展开联系人的个人资料  。
 
    > [!div class="mx-imgBorder"] 
    > ![展开联系人个人资料卡片详细信息](media/profile1.png "展开联系人个人资料卡片详细信息")
   
 ## <a name="view-a-users-profile"></a>查看用户的个人资料
 
1.  转到“帐户”  。
2.  选择帐户记录。
3.  如果“所有者”字段具有用户记录，则将鼠标悬停在该字段上。 可以查看内联用户的详细信息。
4.  要查看更多详细信息（例如用户的电子邮件和共享文件），请选择“显示更多”以展开联系人的个人资料  。
 
    > [!div class="mx-imgBorder"] 
    > ![展开用户个人资料卡片详细信息](media/profile2.png "展开用户个人资料卡片详细信息")


 ## <a name="faqs"></a>常见问题解答
 
### <a name="where-can-i-see-profile-cards-in-dynamics-365"></a>在哪里可以查看 Dynamics 365 中的个人资料卡片？
个人资料卡片可以在联系人和用户记录上进行查看。 只有在查找时才能查看它们。

### <a name="where-is-information-shown-in-the-profile-card-coming-from"></a>个人资料卡片中显示的信息来自哪里？
联系人个人资料卡片上显示的信息是从 Common Data Service（而非 Microsoft Exchange）提取而来的。 这意味着联系人详细信息来自 Dynamics 365。

用户个人资料卡片上显示的信息是从 Office 365 (Azure Active Directory) 提取而来的。 有关详细信息，请参阅 [Office 365 中的个人资料卡片（管理员部分）](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501)。

### <a name="how-can-i-customize-the-fields-shown-on-the-profile-card"></a>如何自定义个人资料卡片上显示的字段？
目前，个人资料卡片上显示的字段列表不允许进行自定义。

### <a name="why-is-the-start-chat-option-on-the-profile-card-disabled-greyed-out"></a>为什么禁用了个人资料卡片上的“开始聊天”选项（灰显）  ？
个人资料卡片上的“开始聊天”和“发送电子邮件”选项将打开默认的即时消息和电子邮件应用   。 如果尝试联系的人员在与你相同的 Azure Active Directory 环境中，或者是联盟联系人，则会启用“开始聊天”选项  。


  
