---
title: 配置联系人以在门户中使用 |MicrosoftDocs
description: 说明如何添加和配置要在门户中使用的联系人。
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553178"
---
# <a name="configure-a-contact-for-use-on-a-portal"></a>配置联系人以在门户上使用

填写联系人的基本信息后（或让用户在门户中填写注册表单）后，请访问门户联系人窗体上的 web 身份验证选项卡，使用本地身份验证来配置联系人。 有关联合身份验证选项的详细信息，请参阅为[门户设置身份验证标识](set-authentication-identity.md)。 若要使用本地身份验证为门户配置联系人，请遵循以下说明：  

1.  输入**用户名**。
2.  在命令功能区中，转到 "**更多命令**" &gt;**更改密码**。

完成更改密码工作流，将自动配置所需字段。 完成此操作后，将为你的门户配置你的联系人。

## <a name="change-password-for-a-contact-from-portal-management-app"></a>从门户管理应用更改联系人密码

1.  打开[门户管理应用](configure-portal.md)。

2.  转到**门户** > **联系人**"，并打开要更改其密码的联系人。
    或者，也可以从 "[共享](../manage-existing-portals.md#share)" 窗格打开 "**联系人**" 页。 

3.  在顶部的工具栏中选择 "**任务流**"。

    > [!div class="mx-imgBorder"]
    > ![任务流图标](../media/task-flow.png "任务流图标")

4.  选择 "**更改门户联系人的密码**" 任务流。

5.  在 "**更改门户联系人的密码**" 窗格中，选择或创建一个联系人以更改密码，然后选择 "**下一步**"。

    > [!div class="mx-imgBorder"]
    > ![选择要更改密码的联系人](../media/change-password-select-contact.png "选择要更改密码的联系人")

6.  在 "**新密码**" 字段中，输入新密码，然后选择 "**下一步**"。

    > [!div class="mx-imgBorder"]
    > ![输入联系人的新密码](../media/change-password-new-password.png "输入联系人的新密码")

    如果不输入密码并选择 "**下一步**"，系统会询问你是否要删除所选联系人的密码。

    > [!div class="mx-imgBorder"]
    > ![删除联系人的密码](../media/change-password-remove-password.png "删除联系人的密码")

7.  进行更改后，选择 "**完成**"。


### <a name="see-also"></a>另请参阅
[邀请联系人加入门户](invite-contacts.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  