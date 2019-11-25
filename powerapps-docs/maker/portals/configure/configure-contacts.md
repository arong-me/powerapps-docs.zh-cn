---
title: 配置在门户中使用的联系人 | MicrosoftDocs
description: 有关如何添加和配置要在门户中使用的联系人的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a8c70304385007c132f2c13ec0ddca4b68e2231
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760156"
---
# <a name="configure-a-contact-for-use-on-a-portal"></a>配置在门户中使用的联系人。

填写联系人的基本信息后（或让用户在门户中填写注册表格），转至门户联系人窗体上的 Web 身份验证选项卡，使用本地身份验证配置联系人。 有关联合身份验证选项的详细信息，请参阅[为门户设置联合身份](set-authentication-identity.md)。 使用本地身份验证配置门户的联系人，请按照以下说明操作：  

1.  输入**用户名**。
2.  在命令功能区上，转至**更多命令** &gt; **更改密码**。

完成更改密码工作流后，必要字段将自动配置。 执行此操作后，会配置门户的联系人。

## <a name="change-password-for-a-contact-from-portal-management-app"></a>从“门户管理”应用更改联系人的密码

1.  打开[“门户管理”应用](configure-portal.md)。

2.  转到**门户** > **联系人**，然后打开要更改其密码的联系人。
    或者，您还可以从[共享](../manage-existing-portals.md#share)窗格打开**联系人**页面。 

3.  在顶部工具栏中选择**任务流**。

    > [!div class="mx-imgBorder"]
    > ![任务流图标](../media/task-flow.png "任务流图标")

4.  选择**更改门户联系人的密码**任务流。

5.  在**更改门户联系人的密码**窗格中，选择或创建联系人以更改密码，然后选择**下一步**。

    > [!div class="mx-imgBorder"]
    > ![选择联系人以更改密码](../media/change-password-select-contact.png "选择联系人以更改密码")

6.  在**新密码**字段中，输入新密码，然后选择**下一步**。

    > [!div class="mx-imgBorder"]
    > ![为联系人输入新密码](../media/change-password-new-password.png "为联系人输入新密码")

    如果不输入密码就选择**下一步**，将询问您是否要删除所选联系人的密码。

    > [!div class="mx-imgBorder"]
    > ![为联系人删除密码](../media/change-password-remove-password.png "为联系人删除密码")

7.  进行更改后，请选择**完成**。


### <a name="see-also"></a>另请参阅
[为门户邀请联系人](invite-contacts.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  