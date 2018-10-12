---
title: 为 PowerApps 中的字段设置托管属性 | MicrosoftDocs
description: 了解如何为字段设置托管属性
ms.custom: ''
ms.date: 06/19/2018
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
ms.assetid: 4ddcfcf3-5604-4b93-a5ee-589d4fb97fa4
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: be3b04bbc324520904c765506e32d6027927e214
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669452"
---
# <a name="set-managed-properties-for-fields"></a>设置字段的托管属性

<a name="BKMK_SettingManagedProperties"></a>   

 托管属性仅在将字段纳入托管解决方案并将解决方案导入另一个环境时才适用。 这些设置使解决方案制定者对安装托管解决方案的人员在自定义此字段时可以拥有的自定义级别进行一些控制。 若要为字段设置托管属性，请在菜单栏上选择“托管属性”。  
  
 “可以自定义”选项控制所有其他选项。 如果此选项为 `False`，其他任何设置均不适用。 如果为 `True`，则可以指定其他自定义选项。  
  
 如果可自定义该字段，请将以下选项设置为 `True` 或 `False`。  
  
- **可以修改显示名称**  
  
- **可以更改要求级别**  
  
- **可以更改其他属性**  
  
 这些选项一目了然。 如果将所有单个选项都设置为 `False`，也应将“可自定义”设置为 `False`。  

 ## <a name="next-steps"></a>后续步骤

 [创建并编辑字段](create-edit-fields.md)