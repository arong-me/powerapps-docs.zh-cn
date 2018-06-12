---
title: 管理员数据集成中的客户数据
description: 标识、导出和删除 CDS for Apps 管理员数据集成中的个人数据
author: sabinn-msft
ms.service: powerapps
ms.topic: how-to
ms.component: cds
ms.date: 05/20/2018
ms.author: sabinn
ms.openlocfilehash: 01dafceacff89cb9b3a400caad5dde07a0995f1c
ms.sourcegitcommit: e59c849a88c6fc0ed333ef4ce2d982a5b8623c97
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34754107"
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-data-integration-for-common-data-service-for-apps-customer-data"></a>响应针对 Common Data Service for Apps 客户数据的数据集成的数据主体权限 (DSR) 请求

## <a name="introduction-to-dsr-requests"></a>DSR 请求简介

欧盟 (EU) 一般数据保护条例 (GDPR) 为用户（在条例中称为“数据主体”）提供了多种权限，使其有权管理由雇主或其他类型的机构或组织（称为“数据控制者”或简称为“控制者”）收集的个人数据。 在 GDPR 下，个人数据被广泛定义为与确定的或可识别的自然人相关的任何数据。 GDPR 为数据主体提供针对其个人数据的以下权限：

- 获取副本
- 请求更正
- 限制处理
- 删除个人数据
- 接收电子格式的个人数据，以便将其发送给另一个控制者

数据主体权限 (DSR) 请求是数据主体向控制者发出的正式请求，请求对其个人数据执行操作。

本文介绍 Microsoft 如何针对 GDPR 进行准备工作，还提供了一些在 CDS for Apps 中通过管理员门户使用管理员数据集成时可用于支持 GDPR 符合性的步骤示例。 你可了解如何使用 Microsoft 产品、服务和管理工具，帮助控制者客户发现、访问并处理 Microsoft 云中的个人数据，以响应 DSR 请求。

### <a name="searching-for-and-identifying-personal-data"></a>搜索并标识个人数据

CDS for Apps 中的管理员数据集成允许集成者应用程序的任何用户通过使用“数据集成”选项卡查看其数据，具体位置：

[https://admin.powerapps.com/dataintegration](https://admin.powerapps.com/dataintegration)

为用户存储的数据显示在门户中。 所有项目均可在“项目”选项卡上查看：

![在“项目”选项卡下查看项目](./media/data-integration-gdpr-dsr/projects-tab.png)

所有连接集均可在“连接集”选项卡上查看：

![在“连接集”选项卡下查看连接集](./media/data-integration-gdpr-dsr/connections-tab.png)

所有模板均可在“模板”选项卡上查看：

![在“模板”选项卡下查看模板](./media/data-integration-gdpr-dsr/templates-tab.png)

## <a name="securing-and-controlling-access-to-personal-information"></a>保护和控制对个人信息的访问

在 CDS for Apps 的管理员数据集成中，数据集成应用程序存储的数据只能通过管理员门户进行访问。

## <a name="deleting-personal-data"></a>删除个人数据

在 CDS for Apps 的管理员数据集成中，用户创作的数据、项目和连接集可以由与相应数据关联的用户删除。 若要删除个人数据，用户可以登录到管理员门户：[https://admin.powerapps.com](https://admin.powerapps.com)

用户可以导航到“项目”选项卡，单击项目旁的省略号，然后选择“删除”选项来删除该项目：

![通过单击省略号删除项目](./media/data-integration-gdpr-dsr/projects-del.png)

用户可以导航到“模板”选项卡，单击模板旁的省略号，然后选择“删除”选项来删除该模板：

![通过单击省略号删除模板](./media/data-integration-gdpr-dsr/templates-del.png)

用户可以导航到“连接集”选项卡，单击连接集旁的省略号，然后选择“删除”选项来删除该连接集：

![通过单击省略号删除连接集](./media/data-integration-gdpr-dsr/connsets-del.png)

## <a name="exporting-personal-data"></a>导出个人数据

在 CDS for Apps 的管理员数据集成中，用户创作的数据可以由与该数据关联的用户导出。 若要导出个人数据，用户可以登录到管理员门户：

[https://admin.powerapps.com](https://admin.powerapps.com)

若要导出项目或将项目与执行历史记录一同导出，用户可以导航到“项目”选项卡，单击该项目旁的省略号，然后选择所需的“导出”选项：

![通过单击省略号导出项目](./media/data-integration-gdpr-dsr/projects-exp.png)

若要导出模板，用户可以导航到“模板”选项卡，单击该模板旁的省略号，然后选择“导出”选项：

![通过单击省略号导出模板](./media/data-integration-gdpr-dsr/templates-exp.png)

若要导出连接集，用户可以导航到“连接集”选项卡，单击该连接集旁的省略号，然后选择“导出”选项：

![通过单击省略号导出连接集](./media/data-integration-gdpr-dsr/connsets-exp.png)
