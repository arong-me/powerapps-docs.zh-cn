通过启用 Dynamics 365 客户意见功能，当您在 Dynamics 365 中发布调查时，调查定义将发送到 Azure 并存储在 Azure 存储中。 当受访者提交调查时（通过打开借助电子邮件发送到受访者的调查邀请链接），系统会将调查回复暂时存储在 Azure 服务总线中，然后进行检索并将其存储在 Dynamics 365 中。 在回复存储在 Dynamics 365 中之后，它们将从 Azure 中删除。  
  
 请注意，在向受访者呈现调查内容时，可以将客户名称、产品名称、案例号等 Dynamics 365 数据包含在调查（问题、答案等调查元素内）中。 生成调查邀请链接后，此 Dynamics 365 数据将从 Dynamics 365 中发出并存储在 Azure SQL 数据库中，用来交换调查邀请链接中使用的标识符。 此标识符用于在使用调查邀请链接打开调查后显示调查中的 Dynamics 365 数据。 通过电子邮件发送给受访者的调查链接中的标识符将存储在受访者的电子邮件系统中。  
  
 管理员可通过在 Dynamics 365 组织中以解决方案的形式安装 Dynamics 365 客户意见功能来启用此功能。 此外，管理员随后可以通过从 Dynamics 365 组织中卸载该解决方案来禁用此功能。  
  
 以下章节中详细介绍了 Dynamics 365 客户意见功能涉及的 Azure 组件和服务。  
  
 注意：有关其他 Azure 服务/产品的更多信息，请访问 Microsoft Azure 信任中心 ([https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/))。  
  
 **云服务** ([https://azure.microsoft.com/services/cloud-services/](https://azure.microsoft.com/services/cloud-services/))  
  
 **设计器服务（Web 角色）**  
  
 这提供了多种用于在 Dynamics 365 组织与多租户 Dynamics 365 客户意见 Azure 组件之间通信的 Web 服务。  例如，发布调查并将其存储到 Azure Blob 存储中。  从 Azure 服务总线队列检索调查响应并将其返回，以保留在 Dynamics 365 组织中。  针对 Azure Active Directory 验证所有请求。  
  
 **调查运行时（Web 角色）**  
  
 这是服务于针对受访者的调查的 Web 应用程序。  提交的调查响应在由 Dynamics 365 异步服务检索之前将暂时存储在 Azure 服务总线队列上。  
  
 **响应处理器（工作人员角色）**  
  
 此工作人员角色负责将原始的已完成调查处理成可在 Dynamics 365 中创建的有效调查响应。  
  
 **推送处理器（工作人员角色）**   此工作人员角色负责处理有效调查响应并更新为 Dynamics 365 实体记录。 
 
 **Azure Key Vault** ([https://azure.microsoft.com/services/key-vault/](https://azure.microsoft.com/services/key-vault/))  
  
 所有云服务都将配置数据存储在 Azure Key Vault 中。  组织和租户数据将存储在 SQL Azure 中。  
  
 **Azure SQL 数据库** ([https://azure.microsoft.com/services/sql-database/](https://azure.microsoft.com/services/sql-database/))  
  
 Dynamics 365 客户意见使用 SQL Azure 存储：  
  
-   管道数据  
  
-   调查元数据  
  
-   组织（租户）数据  
  
 **Azure Blob 存储** ([https://azure.microsoft.com/services/storage/](https://azure.microsoft.com/services/storage/))  
  
 调查定义和部分已完成（已保存）的响应将存储到 Azure Blob 存储中。  
  
 **Azure 内容传送网络 (CDN)** ([https://azure.microsoft.com/services/cdn/](https://azure.microsoft.com/services/cdn/))  
  
 Dynamics 365 客户意见解决方案使用 Azure 内容传送网络向调查运行时提供静态内容，例如图像（包括客户徽标等上载的图像）、JavaScript 和 CSS。  
  
 **Azure Active Directory** ([https://azure.microsoft.com/services/active-directory/](https://azure.microsoft.com/services/active-directory/))  
  
 Dynamics 365 客户意见解决方案使用 Azure Active Directory 服务对 Web 服务进行身份验证。  
  
 **Azure 服务总线** ([https://azure.microsoft.com/services/service-bus/](https://azure.microsoft.com/services/service-bus/))  
  
 显示/提交调查时创建的消息将暂时存储到组织（租户）的 Azure 服务总线队列中，直到 Azure 工作人员角色将调查响应推送到组织的 Dynamics 365 实例并将其保留为 Dynamics 365 实体记录。
