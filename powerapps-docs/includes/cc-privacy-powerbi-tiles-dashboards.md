通过启用 Power BI 磁贴和仪表板的嵌入功能，当用户嵌入 Power BI 磁贴或仪表板时，该用户对 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 的 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 授权令牌将用于通过隐式授权对 Power BI 服务进行身份验证，同时为最终用户提供无缝式“单一登录”体验。  
  
 管理员可以随时禁用 Power BI 磁贴和仪表板的嵌入功能以停止使用 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 授权令牌来对 Power BI 服务进行身份验证。 任何现有磁贴或仪表板将停止为最终用户呈现。  
  
 以下章节中详细介绍了 Power BI 磁贴的嵌入功能涉及的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件或服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 此服务提供与 Power BI 服务进行交换的授权令牌，以用于 API 和 UI 身份验证。