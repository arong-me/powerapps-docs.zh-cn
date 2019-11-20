通过启用“电子邮件参与度”这一嵌入式智能功能，在从 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 发送了标记有**跟进**设置的电子邮件后，将收集收件人与电子邮件交互的信息并将其存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中，以用于计算收件人活动 KPI 以及与“跟进的”电子邮件的交互。  
  
 系统管理员通过在**电子邮件参与度**选项卡中的“嵌入式智能”菜单中配置电子邮件参与度功能，来启用该功能。 之后，管理员可以通过**设置**下的**智能配置**节点，在组织中禁用电子邮件参与度功能。  
  
 禁用此功能后，不论是从用户界面还是以编程方式都无法跟进从 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 发出的电子邮件。 此外，对于标记有**跟踪**设置的已发送电子邮件，也不再收集收件人交互数据。 以前收集的所有数据将保留在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中，如果组织中重新启用该功能，这些数据将再次可用。 客户终止 Microsoft 订阅之后，数据将保留 90 天。 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 用户也可以通过在**联系人首选项**下更改**跟进电子邮件**设置，按照各个联系人或各个潜在客户来禁用“嵌入式智能 - 电子邮件参与度”功能。  
  
 下面详细介绍了电子邮件参与度功能涉及的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)]**  
  
 电子邮件参与度功能使用 [!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)] 来临时存储电子邮件交互 Blob。