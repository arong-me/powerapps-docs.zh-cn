---
title: 添加连接角色以将记录链接到彼此之间 |MicrosoftDocs
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
ms.openlocfilehash: d824e76f6ffd5cc72f2f030f7009d3f4a140bf8a
ms.sourcegitcommit: d6b7f98b4ae011a753c1e72d7708f0f8dfbfb1fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896256"
---
# <a name="add-a-connection-role-to-link-records-to-each-other"></a>添加连接角色以将记录相互链接

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

使用连接可以轻松地将用户、联系人、报价、销售订单和其他许多实体记录彼此关联起来。 可以为关联中的记录分配特定的角色, 以帮助定义关系的目的。

这是为特定记录创建多个连接和角色的快速方法。 例如, 联系人可能有许多与其他联系人、帐户或合同的关系。 在每个关系中, 联系人可能扮演着不同的角色。

连接角色直接与连接关联。 若要使用连接角色, 必须首先将连接添加到记录。

在添加连接角色之前, 必须由管理员启用。有关详细信息, 请参阅[配置连接角色](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/configure-connection-roles)。

1. 若要添加或管理连接, 请选择想要管理的记录, 如 "机会"。  
2. 选择 "**相关**" 选项卡, 然后选择 "**连接**"。 这会打开连接网格, 其中包含记录的连接列表。

    > [!div class="mx-imgBorder"]
    > ![添加新的连接角色](media/connection1.png "添加新的连接角色") 

3. 选择 "**连接**", 然后选择 "**其他**" 或 "**到我**"。

    > [!div class="mx-imgBorder"]
    > ![选择连接类型](media/connection2.png "选择连接类型") 
  
4. 在 "**名称**" 字段中, 输入或查找连接的记录的名称。

5. 在 "**作为此角色**字段" 中, 选择 "查找" 图标, 然后选择 "**新建连接角色**"。 或者, 使用搜索来查找想要关联到连接的现有角色, 然后选择 "**保存**"。

    > [!div class="mx-imgBorder"]
    > ![选择新连接角色](media/connection3.png "选择新连接角色")  

    > [!NOTE]
    > 如果在创建新的连接角色之前输入了信息, 将显示警告对话框, 询问你是要取消还是继续处理该连接, 或继续操作并保留正在处理的当前记录。

6. 若要创建新的连接角色, 请在 "**新建连接角色**" 屏幕上输入名称, 然后选择 "**连接" 角色类别**。

    > [!div class="mx-imgBorder"]
    >  ![添加连接角色类别](media/connection4.png "添加连接角色类别") 

7. 完成后, 选择 "**保存" & "关闭**"。

  
## <a name="manage-connection-roles"></a>管理连接角色

若要管理连接角色, 请从连接实体中选择连接角色。 这将打开连接角色实体记录。  你可以编辑该名称, 选择连接角色类别, 然后添加说明。


   > [!div class="mx-imgBorder"]
   > ![编辑连接角色](media/connection7.png "Editconnection 角色") 
  
你还可以管理要与连接角色关联的连接角色类型。

1. 打开连接角色, 然后在命令中选择 "**管理记录类型**"。 

    > [!div class="mx-imgBorder"]
    > ![编辑连接角色](media/connection5.png "Editconnection 角色") 
  

2. 这将打开可为此连接角色添加或删除的连接角色类型的列表。

    > [!div class="mx-imgBorder"]
    > ![管理记录类型](media/connection6.png "管理记录类型") 


