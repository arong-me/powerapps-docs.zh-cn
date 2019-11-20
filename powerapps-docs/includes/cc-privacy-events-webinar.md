接受活动管理的条款和条件时，网络研讨会集成功能将激活。 网络研讨会集成功能利用合作伙伴网络研讨会提供商，将活动或会期作为网络研讨会执行。 若要使用任何网络研讨会提供商的服务，必须有相应的帐户。 目前提供现成可用服务的唯一合作伙伴网络研讨会提供商是 ON24。 使用网络研讨会集成功能时，将在 [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] 上处理和存储提供和运行网络研讨会的关键数据，然后发送到 ON24。 此类数据将包括网络研讨会参与者注册数据（如姓名、电子邮件和公司名称）。 此外，ON24 将把网络研讨会度量（如网络研讨会查看持续期）通过 [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] 发送至 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]。

您无需激活网络研讨会功能，即可使用活动管理解决方案的其余部分。 管理员可以通过删除网络研讨会配置中的凭据来关闭网络研讨会集成功能。

网络研讨会集成功能使用的 [!INCLUDE[pn-windows-azure](../includes/pn-windows-azure.md)] 组件和服务是：

- [!INCLUDE[pn_azure_key_vault](../includes/pn_azure_key_vault.md)]（[!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [什么是 Azure Key Vault？](https://docs.microsoft.com/azure/key-vault/key-vault-whatis)）
  - 为加密/解密客户的 ON24 帐户凭据提供加密密钥
- [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Azure Service Fabric 概述](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview))
  - 将注册数据和网络研讨会帐户凭据处理和发送至 ON24
  - 检索从 On24 到 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] 的网络研讨会度量 - 存储客户的 ON24 帐户凭据（自定义加密）