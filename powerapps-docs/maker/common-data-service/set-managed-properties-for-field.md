---
title: 在 Power Apps 中设置字段的托管属性 | MicrosoftDocs
description: 了解如何设置字段的托管属性
ms.custom: ''
ms.date: 06/19/2018
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
ms.assetid: 4ddcfcf3-5604-4b93-a5ee-589d4fb97fa4
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0b14b5ab55fe6bbaeeb11fb2de548621eb66501a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865320"
---
# <a name="set-managed-properties-for-fields"></a>设置字段的托管属性

<a name="BKMK_SettingManagedProperties"></a>   

 托管属性仅适用于以下情况：字段包括在某个托管解决方案中，并将该解决方案导入到另一个环境。 利用这些设置，解决方案制造者可以对安装托管解决方案的人在自定义此字段时可以拥有的自定义级别有一定的控制。 若要设置字段的托管属性，请选择菜单栏上的**托管属性**。  
  
 **可以自定义** 选项控制其他所有选项。 如果此选项为 `False`，则其他设置都不适用。 如果这是 `True`，则可指定其他自定义选项。  
  
 如果字段可以自定义，柯将以下选项设置为 `True` 或 `False`。  
  
- **可以修改显示名称**  
  
- **可以更改需求级别**  
  
- **可以更改其他属性**  
  
 这些选项有明确的含义。 如果将所有单个选项都设置 `False`，则也可以将**可以自定义** 设置为 `False`。  

 ## <a name="next-steps"></a>后续步骤

 [创建和编辑字段](create-edit-fields.md)
