---
title: 连接到 Oracle 数据库 | Microsoft 文档
description: 了解如何连接到 Oracle Database 并使用它生成 Power Apps 应用。
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/29/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b60ab00d4f4fecca7ead1cac629e0e34f26f302b
ms.sourcegitcommit: d0f02fdaa125feaea884932e1ef31b8fea1bd10c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886285"
---
# <a name="connect-to-an-oracle-database-from-power-apps"></a>从 Power Apps 连接到 Oracle 数据库
创建连接并生成 Power Apps 应用后，可以列出表，并创建、读取、更新和删除 Oracle 数据库中的表行。 Oracle 数据库连接支持完全委派筛选、排序和其他功能，但触发器或存储过程除外。

## <a name="prerequisites"></a>先决条件
* Oracle 9 及更高版本
* Oracle 客户端软件 8.1.7 及更高版本
* 安装本地数据网关
* 安装 Oracle 客户端 SDK

### <a name="install-an-on-premises-data-gateway"></a>安装本地数据网关
若要安装网关，请按照[本教程](../gateway-management.md)中的步骤操作。

本地数据网关充当网桥，在本地数据（非云中的数据）与 Power BI、Power Automate、逻辑应用和 Power Apps 服务之间提供快速、安全的数据传输。 可以将同一个网关与多个服务和多个数据源一起使用。 有关详细信息，请参阅[了解网关](../gateway-reference.md)。

### <a name="install-oracle-client"></a>安装 Oracle 客户端
在作为本地数据网关的同一台计算机上，安装[适用于 Windows x64 的 64 位 ODAC 12c 版本 4 (12.1.0.2.4)](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)。 否则，如已知问题列表中所述，在尝试创建或使用连接时将会出现错误。

## <a name="create-an-app-from-a-table-in-an-oracle-database"></a>通过 Oracle 数据库中的表创建应用
1. 在 Power Apps Studio 中，单击或点击“文件”  菜单上的“新建”  （靠近左边缘）。
   
   ![“新建”选项](./media/connection-oracledb/new-app.png)
2. 在“开始处理数据”  下，单击或点击箭头。
   
      显示已有的连接列表。
3. 单击或点击“新建连接”  。
   
   ![新连接](./media/connection-oracledb/new-connection.png)
4. 在连接列表中，单击或点击“Oracle 数据库”  。
   
   ![新建数据库](./media/connection-oracledb/oracle-db.png)
5. 指定 Oracle 服务器名称、用户名和密码。
   
    如果需要 SID，则使用以下格式指定服务器：<br>
    *ServerName*/*SID*
   
   ![连接参数](./media/connection-oracledb/connection-params.png)
6. 单击或点击要使用的网关或安装一个网关。
   
    如果安装网关后该网关未出现，则单击“刷新网关列表”  。
   
   ![新建网关](./media/connection-oracledb/choose-gateway.png)
7. 单击或点击“创建”  以创建连接。
   
   ![新建](./media/connection-oracledb/create-button.png)
8. 单击或点击“默认”  数据集。
   
   ![新建](./media/connection-oracledb/choose-dataset.png)
9. 在表列表中，单击或点击要使用的表。
   
   ![新建](./media/connection-oracledb/choose-table.png)
10. 单击“连接”  创建应用。
    
    ![新建](./media/connection-oracledb/connect-button.png)

此时，Power Apps 会创建包含三个屏幕的应用，其中显示选定表中的数据：

* **BrowseScreen1**，列出表中的所有条目。
* **DetailScreen1**，提供单个条目的详细信息。
* **EditScreen1**，用户可以在此处更新条目或创建条目。

![新建](./media/connection-oracledb/afd-app.png)

## <a name="next-steps"></a>后续步骤
* 要保存刚才生成的应用，请按 Ctrl-S。
* 要自定义 **BrowseScreen1**（默认情况下会显示），请参阅[自定义布局](../customize-layout-sharepoint.md)。
* 若要自定义 **DetailsScreen1** 或 **EditScreen1**，请参阅[自定义窗体](../customize-forms-sharepoint.md)。

## <a name="known-issues-tips-and-troubleshooting"></a>已知问题、建议和疑难解答
1. 无法访问网关。
   
    本地数据网关无法连接到云时将出现此错误。 若要检查网关状态，请登录到 powerapps.microsoft.com，单击或点击“网关”  ，然后单击或点击要使用的网关。
   
    确保网关正在运行且可以连接到 Internet。 避免在可能会关机或进入休眠状态的计算机上安装网关。 同时尝试重启本地数据网关服务 (PBIEgwService)。
2. System.Data.OracleClient 需要具备 Oracle 客户端软件 8.1.7 版本或更高版本。
   
    如果未将 Oracle 客户端 SDK 安装在作为本地数据网关的同一台计算机上，则会出现此错误。 若要解决此问题，请[安装正式提供程序](https://go.microsoft.com/fwlink/p/?LinkID=272376)。
3. 表“[Tablename]”未定义任何键列。
   
    如果连接到的表不包含 Oracle 数据库连接所需的任何主键，则会出现此错误。
4. 截至本文撰写之时，Power Apps 不直接支持存储过程、包含组合键的表以及表中的嵌套对象类型。 不过，使用 Power Automate 的存储过程受支持。

