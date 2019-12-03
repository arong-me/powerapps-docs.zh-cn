---
title: 使用 Azure SQL 数据库创建画布应用 |Microsoft Docs
description: 介绍如何通过 Azure SQL 数据库中的数据创建画布应用
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/29/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 140fa7c51c30199360a08adc86c6e118e4e5bc52
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679928"
---
# <a name="preview-create-a-canvas-app-from-azure-sql-database"></a>预览：创建 Azure SQL 数据库中的画布应用

[本主题为预发布文档，随时可能会有所更改。]

在本主题中，你将在几分钟内使用 Azure SQL 数据库中的数据创建一个具有 Power Apps 的应用。 你将拥有一个功能齐全的应用程序，其中包含你的数据，你可以自定义该应用以适应你的业务需求并在任何设备上共享。

> [!IMPORTANT]
> - 这是一项预览功能。
> - 预览功能的可用性和受限功能可能会受到限制。 预览版功能在正式发布之前提供，因此客户可以提前获取访问权限并提供反馈。

## <a name="prerequisites"></a>必备组件

- 你的浏览器必须启用弹出窗口。
- 需要一个 Azure 订阅。 </br>如果没有 Azure 订阅，请[创建一个免费帐户](https://azure.microsoft.com/free/)。
- 需要具有对现有 SQL 数据库的访问权限。 </br> 如果没有现有的 SQL 数据库，请[创建新的数据库](https://docs.microsoft.com/azure/sql-database/sql-database-single-database-get-started?tabs=azure-portal)。
- 需要在 "防火墙设置" 中允许 Power Apps 区域的[IP 地址或 Azure 服务](#app-access-to-sql-database)访问 SQL 数据库。
- SQL 数据库表必须至少具有一个文本数据类型的列。
- 你需要有效的 Power Apps 许可证或注册[30 天试用版许可证](../signup-for-powerapps.md)。

## <a name="create-an-app"></a>创建应用

1. 登录到[Azure 门户](https://portal.azure.com)。
2. 导航到 SQL 数据库。
3. 选择 PowerApps。

    
    ![SQL 数据库选项中的 Power Apps 选项](./media/app-from-azure-sql-database/powerapps-link-azure-portal.png "SQL 数据库中的 Power Apps 选项")

    > [!NOTE]
    > 如果没有 Power Apps 许可证，你会看到蓝色信息栏，其中包含用于开始试用的链接。 选择启动试用版时，将转到新的选项卡，你将在其中注册许可证。 完成后，返回到 Azure 门户并刷新边栏选项卡以继续。

4. 键入应用程序的名称，例如 "站点检查"、"Fundraiser" 或 "预算跟踪器"。

5. 输入 SQL 身份验证密码，并在需要时更改用户名。
6. 从下拉列表中选择要用于创建应用的表。

7. 选择“创建”。


    ![指定应用的信息](./media/app-from-azure-sql-database/powerapps-create-page-azure-portal.png "指定应用的信息")

    [Power Apps Studio](https://create.powerapps.com/studio/)会在新选项卡中打开。如果弹出窗口被阻止，请更新浏览器以允许弹出窗口，然后重试。 创建后，会获得一个包含 SQL 数据库数据的3页应用。

## <a name="accessing-your-app"></a>访问应用

若要再次访问创建的应用，请访问[make.powerapps.com](https://make.powerapps.com)。

## <a name="app-environment-and-region"></a>应用环境和区域

使用此方法创建的应用将使用租户的[默认环境](https://docs.microsoft.com/power-platform/admin/environments-overview#the-default-environment)，并部署到此环境的区域。 你可以从[管理中心](https://docs.microsoft.com/power-platform/admin/regions-overview#how-do-i-find-out-where-my-app-is-deployed)找到已部署的应用或租户的默认环境的区域。 若要查看特定环境中的所有应用，请执行[make.powerapps.com](https://make.powerapps.com)，从功能区中选择**环境**，然后选择左侧的 "**应用**"。

## <a name="app-access-to-sql-database"></a>应用对 SQL 数据库的访问

你可以使用 IP 地址或 Azure 服务将电源应用配置为连接到 SQL 数据库。

### <a name="app-access-using-ip-address"></a>使用 IP 地址进行应用访问

[Power apps 系统要求](limits-and-config.md#ip-addresses)列出了电源应用使用的 IP 地址，具体取决于应用的区域。

您可以使用 Transact-sql 存储过程或 Azure 门户来配置此访问权限：

- SQL 数据库的存储过程[sp_set_firewall_rule](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database?view=azuresqldb-current)或 SQL Server 防火墙规则
- SQL Server 防火墙规则的[Azure 门户](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure)

### <a name="app-access-as-an-azure-service"></a>Azure 服务形式的应用程序访问

Power Apps 可以使用 Azure 门户连接到 SQL 数据库，**以允许访问 Azure 服务**控件。 若要配置此访问权限，请登录到[Azure 门户](https://portal.azure.com/)并在门户中导航以**SQL Server**。 选择 "**防火墙和虚拟网络**"，并设置控件 "**允许 Azure 服务和资源访问此服务器** **"** 。 选择 "**保存**" 以提交更改。

> [!IMPORTANT]
> 如果将控制设置为 "打开"，则 Azure SQL 数据库服务器接受来自 Azure 边界内的任何子网的通信，该 IP 地址来自可识别为 Azure 数据中心定义的范围内的 IP 地址。 将控件设置为 "开" 可能对安全点的访问权限很高。

## <a name="limitations"></a>限制

- 应用名称只能包含字母、数字、连字符、括号或下划线。
- Power Apps 需要 SQL 身份验证以连接到 SQL 数据库。
- 从 Azure 门户创建画布应用时，只能选择一个表。 如果要通过添加更多的数据连接来添加更多的表和其他数据源，请在创建应用后自定义应用。
- Power Apps 无法使用 VNet 服务终结点连接到 SQL 数据库。 有关详细信息，请阅读[允许通过 VNet 服务终结点访问](https://docs.microsoft.com/azure/sql-database/sql-database-vnet-service-endpoint-rule-overview)。

## <a name="other-considerations"></a>其他注意事项

- 对 SQL 数据库的应用程序的访问权限将隐式共享到您与之[共享此应用程序](share-app.md)的所有用户。 确保 SQL 身份验证凭据具有读取和写入数据的适当访问权限。 </br> 例如，你可以创建一个单独的应用程序，该应用程序使用不同的 SQL 身份验证凭据连接到相同的 SQL 数据库，以分离读取和读/写访问权限。
- 查看限制的限制、delegatable 函数和操作、已知问题，以及此功能对性能注意事项使用的[SQL 数据库](https://docs.microsoft.com/connectors/sql/)连接器的限制。
- 如果需要使用 SQL 数据库中的数据为非默认环境和不同的租户区域创建应用，请从[make.powerapps.com](https://make.powerapps.com)创建应用。

## <a name="next-steps"></a>后续步骤

在本快速入门中，你使用了 SQL 数据库中的数据创建了一个应用，该应用使用 Azure 门户。 下一步，使用控件、图像和逻辑自定义应用，以便更好地满足你的业务需求。

> [!div class="nextstepaction"]
> [在 PowerApps 中设计 canvas 应用接口](add-configure-controls.md)

## <a name="see-also"></a>另请参阅

- [在 PowerApps 中共享画布应用](share-app.md) </br>
- [在 PowerApps 中向画布应用添加数据连接](add-data-connection.md#add-data-source)</br>
- [Microsoft Learn：在 PowerApps 中自定义画布应用](https://docs.microsoft.com/learn/modules/customize-apps-in-powerapps/)
