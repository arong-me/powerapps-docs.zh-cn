---
title: 在 Power Apps 中删除字段 | MicrosoftDocs
description: 了解如何删除字段
ms.custom: ''
ms.date: 06/20/2018
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
ms.assetid: 578ac950-da16-4ec6-a0a4-25f3aaa3b96e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 224c07600a13b0adf9cedd7592be7f1c2befec90
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2864035"
---
# <a name="delete-fields"></a>删除字段

<a name="BKMK_DeletingFields"></a>   
 
 具有系统管理员安全角色用户可以删除不属于托管解决方案的任何自定义字段。 删除字段时，字段中存储的所有数据都将丢失。 从删除的字段中恢复数据的唯一方式是从删除字段前的某个点恢复数据库。  
  
 在删除自定义实体之前，必须删除其他解决方案组件中可能存在的所有依赖项。 打开字段并使用菜单栏中的**显示依赖项** 按钮查看所有**从属组件** 。 例如，如果在窗体或视图中使用了字段，则必须先取消在这些解决方案组件中对字段的引用。  
  
 如果删除查找字段，则将自动删除它的 1:N 实体关系。  

 ## <a name="next-steps"></a>后续步骤

 [删除自定义实体](data-platform-delete-entity.md)
