---
ms.openlocfilehash: ce9db35844f46e9779055ec30dcba0f9459c3a16
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61567348"
---
通过安装 [!INCLUDE[pn_connected_field_service_msdyn365](pn-connected-field-service-msdyn365.md)]，当你提供 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 订阅信息时，将部署所需的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 资源（如下所列），[!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 实例将向 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 发送数据（例如命令和注册）以启用支持 IoT 的方案，用于注册设备并将命令发送到已注册的设备以及从中接收命令。 管理员可以卸载连接的现场服务以删除功能，然后导航到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 门户以管理不再需要的任何相关 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 服务。  
  
 以下各节详细介绍了与连接的现场服务功能相关的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [服务总线队列](https://azure.microsoft.com/documentation/articles/service-bus-dotnet-get-started-with-queues/)  
  
 这为在 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 和 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 之间流动的入站和出站消息（命令）提供队列。 当 IoT 警报发送到 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]或命令从 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 发送到 IoT 中心时，它将在此处排队。  
  
 [逻辑应用](https://azure.microsoft.com/services/logic-apps/)  
  
 这提供了使用 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 连接器和队列连接器的业务流程服务。 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 连接器用于构造特定于 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 的实体，队列连接器用于轮询队列。  
  
 [流分析](https://azure.microsoft.com/services/stream-analytics/)  
  
 这提供了一种完全托管的实时事件处理引擎，有助于从数据中解锁深入的见解。 通过流分析，可以轻松地设置针对来自设备、传感器、网站、社交媒体、应用程序和基础结构系统等数据流的实时分析计算。 它充当向 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 发送选择性 IoT 警报的漏斗。  
  
 [IoT 中心](https://azure.microsoft.com/services/iot-hub/)  
  
 连接的现场服务使用 IoT 中心来管理已注册设备和资产的状态。 此外，IoT 中心还会向连接的设备发送命令和通知，并通过确认回执跟踪消息传递。 通过持久的方法发送设备消息，以适应间歇性连接的设备。  
  
 **模拟器**  
  
 这是测试 Web 应用，用于模拟从 IoT 中心发送或接收命令的设备。  
  
 [Azure SQL 数据库](https://azure.microsoft.com/services/sql-database/)  
  
 连接的现场服务使用 SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储设备检测信号消息，供 PowerBI 稍后用于在 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 中显示设备的状态。  
  
 [Azure Blob 存储](https://azure.microsoft.com/services/storage/)  
  
 流分析将使用的查询存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中。