---
title: 添加连接角色以将记录彼此链接 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 8/01/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4552c874ca6be72d37465abd2492a64979aba865
ms.sourcegitcommit: 5ec4cab1dd934446ec57c320a375e577560ac88a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2019
ms.locfileid: "72239575"
---
# <a name="add-a-connection-role-to-link-records-to-each-other"></a>添加连接角色以将记录彼此链接

使用连接可以轻松地将用户、联系人、报价、销售订单和其他许多实体记录彼此关联。 可以为关联中的记录分配特定的角色，以帮助定义关系的目的。

这是为特定记录创建多个连接和角色的快捷方法。 例如，一个联系人可能与其他联系人、帐户或合同有许多关系。 在每个关系中，联系人可能扮演着不同的角色。

连接角色直接与连接相关联。 要使用连接角色，必须首先将连接添加到记录。

在添加连接角色之前，需要由管理员启用连接角色。有关详细信息，请参阅[配置连接角色](https://docs.microsoft.com/powerapps/maker/common-data-service/configure-connection-roles)。

1. 要添加或管理连接，请选择想要管理的记录，如“机会”。  
2. 选择“相关内容”选项卡，然后选择“连接”   。 此操作将打开连接网格，其中包含该记录的连接列表。

    > [!div class="mx-imgBorder"]
    > ![添加新的连接角色](media/connection1.png "Add a new connection role") 

3. 选择“连接”，然后选择“到其他人”或“到我”    。

    > [!div class="mx-imgBorder"]
    > ![选择连接类型](media/connection2.png "Select connection type") 
  
4. 在“名称”字段中，输入或查找连接的记录名称  。

5. 在“作为此角色”字段中，选择“查找”图标，然后选择“新建连接角色”   。 或者，使用搜索来查找想要关联到连接的现有角色，然后选择“保存”  。

    > [!div class="mx-imgBorder"]
    > ![选择新的连接角色](media/connection3.png "Choose new connection role")  

    > [!NOTE]
    > 如果在创建新的连接角色之前输入了信息，则将显示警告对话框，询问是要取消并继续处理该连接，还是继续操作并保留正在处理的当前记录。

6. 要创建新的连接角色，请在“新建连接角色”屏幕上输入名称，然后选择“连接角色类别”   。

    > [!div class="mx-imgBorder"]
    >  ![添加连接角色类别](media/connection4.png "Add connection role category") 

7. 完成后，选择“保存并关闭”  。

  
## <a name="manage-connection-roles"></a>管理连接角色

要管理连接角色，请从连接实体中选择连接角色。 此操作将打开连接角色实体记录。  可以编辑名称，选择连接角色类别，并添加说明。


   > [!div class="mx-imgBorder"]
   > ![编辑连接角色](media/connection7.png "Editconnection role") 
  
此外，还可以管理要与连接角色关联的连接角色类型。

1. 打开连接角色，然后在命令中选择“管理记录类型”  。 

    > [!div class="mx-imgBorder"]
    > ![编辑连接角色](media/connection5.png "Editconnection role") 
  

2. 此操作将打开连接角色类型列表，可为此连接角色进行添加或删除。

    > [!div class="mx-imgBorder"]
    > ![管理记录类型](media/connection6.png "Manage Record Type") 


