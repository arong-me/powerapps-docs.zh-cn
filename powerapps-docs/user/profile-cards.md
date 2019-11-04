---
title: 查看联系人或用户的配置文件卡 |MicrosoftDocs
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
ms.openlocfilehash: 67441e506ba2715a9994f6b81cd08426e37e0fc8
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "71950901"
---
# <a name="view-the-profile-card-for-a-contact-or-user"></a>查看联系人或用户的个人资料卡

使用配置文件卡获取有关联系人或用户的快速信息。 如果在 Dynamics 365 的模型驱动应用中选择联系人或用户字段（如 Dynamics 365 Sales 和 Dynamics 365 Customer Service），则可以在其个人资料卡片上查找相关信息。 有关配置文件卡的详细信息，请参阅[Office 365 中的个人资料卡](https://support.office.com/en-us/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501)。

> [!NOTE]
>  - 配置文件卡可用于 "**联系人**" 和 "**用户**" 实体。 有关信息，请参阅[启用配置文件卡（适用于管理员）](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/enable-profile-card)。
>  - 如果在 Azure Active Directory 中为 Office Delve 服务启用多重身份验证，则不会显示 Common Data Service 中的配置文件卡。

## <a name="view-a-contacts-profile"></a>查看联系人的个人资料

1.  转到“活动”。
2.  选择现有的活动或创建一个新的活动。
3.  将鼠标悬停在包含联系人记录**的字段上**。 

可以查看内嵌联系人的详细信息，其中包括联系人图片、名称、标题和帐户。

4. 若要查看更多详细信息，请选择 "**显示更多**" 以展开联系人的个人资料。
 
    > [!div class="mx-imgBorder"] 
    > ![展开联系人配置文件卡详细信息](media/profile1.png "展开联系人配置文件卡详细信息")
   
 ## <a name="view-a-users-profile"></a>查看用户的配置文件
 
1.  中转到 "**帐户**"。
2.  选择帐户记录。
3.  如果具有用户记录，则将鼠标悬停在 "所有者" 字段上。 可以查看用户内联的详细信息。
4.  若要查看更多详细信息（例如，用户的电子邮件和共享文件），请选择 "**显示更多**" 以展开联系人的个人资料。
 
    > [!div class="mx-imgBorder"] 
    > ![展开用户配置文件卡详细信息](media/profile2.png "展开用户配置文件卡详细信息")


 ## <a name="faqs"></a>常见问题
 
### <a name="where-can-i-see-profile-cards-in-dynamics-365"></a>在哪里可以查看 Dynamics 365 中的配置文件卡？
可以在联系人和用户记录上查看个人资料卡。 只能在查找时查看它们。

### <a name="where-is-information-shown-in-the-profile-card-coming-from"></a>配置文件卡中显示的信息在哪里？
联系人配置文件卡上显示的信息从 Common Data Service （而不是 Microsoft Exchange）提取。 这意味着联系详细信息来自 Dynamics 365。

用户配置文件卡上显示的信息是从 Office 365 （Azure Active Directory）中提取的。 有关详细信息，请参阅[Office 365 （管理部分）中的个人资料卡](https://support.office.com/en-us/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501)。

### <a name="how-can-i-customize-the-fields-shown-on-the-profile-card"></a>如何自定义配置文件卡上显示的字段？
目前，配置文件卡上显示的字段列表未打开，无法进行自定义。

### <a name="why-is-the-start-chat-option-on-the-profile-card-disabled-greyed-out"></a>为什么禁用了配置文件卡上的 "**开始聊天**" 选项（灰显）？
配置文件卡上的 "**开始聊天**" 和 "**发送电子邮件**" 选项将打开默认的即时消息和电子邮件应用。 如果你尝试在与你相同的 Azure Active Directory 环境中联系的人员，或者是联合联系人，则启用 "**开始聊天**" 选项。


  
