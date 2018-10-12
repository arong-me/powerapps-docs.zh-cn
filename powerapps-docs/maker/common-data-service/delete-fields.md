---
title: 在 PowerApps 中删除字段 | MicrosoftDocs
description: 了解如何删除字段
ms.custom: ''
ms.date: 06/20/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 82e560f063f2e46190420b6be5cef4cc55d9ab4f
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668277"
---
# <a name="delete-fields"></a>删除字段

<a name="BKMK_DeletingFields"></a>   
 
 作为具有系统管理员安全角色的人员，可以删除任何不属于托管解决方案的自定义字段。 删除字段时，任何存储在此字段中的数据都将丢失。 从已删除的字段恢复数据的唯一方法是从删除字段之前的时间点还原数据库。  
  
 在删除自定义实体之前，必须删除其他解决方案组件中可能存在的所有依赖项。 打开字段，并使用菜单栏中的“显示依赖项”按钮查看所有“依赖组件”。 例如，如果在窗体或视图中使用此字段，则必须首先删除在这些解决方案组件中对此字段的引用。  
  
 如果删除查找字段，将自动删除其 1:N 实体关系。  

 ## <a name="next-steps"></a>后续步骤

 [删除自定义实体](data-platform-delete-entity.md)
