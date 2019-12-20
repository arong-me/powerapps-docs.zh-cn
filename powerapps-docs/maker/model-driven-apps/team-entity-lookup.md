---
title: 添加团队实体充当应用程序中的查找选项 | MicrosoftDocs
description: 了解如何添加团队实体充当应用程序中的查找选项
ms.custom: ''
ms.date: 07/24/2019
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
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 81b20a326be239445422cce51a54b2e0b991d5c4
ms.sourcegitcommit: a7f2313a048d3b8a03516a2e4c349f3fb08f4a22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2019
ms.locfileid: "2805681"
---
# <a name="add-an-entity-as-a-lookup-option-in-your-app"></a>添加实体充当应用中的查找选项

在统一接口应用中，实体只有在添加到应用中之后才可用于查找。 例如，可以将联系人记录分配给用户或团队。  

> [!div class="mx-imgBorder"] 
> ![](media/entity-lookup-teams.png "Entity lookup with both users and teams available")

但是，如果应用程序中有用户实体，但是没有团队实体，则查找中仅显示用户记录。 

> [!div class="mx-imgBorder"] 
> ![](media/entity-lookup-user-only.png "Entity lookup with users only")

## <a name="add-the-team-entity-to-an-app"></a>将团队实体添加到应用程序

1. 在应用程序设计器中打开该应用程序。 
2. 选择**组件**选项卡，选择**实体**，然后选择**团队**。    

    > [!div class="mx-imgBorder"] 
    > ![](media/add-team-entity-app.png "Add the team entity to the app")

3. 选择**保存**，然后选择**发布**，以便将更改提供给应用程序用户。   

