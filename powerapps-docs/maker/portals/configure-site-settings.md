---
title: 配置门户的站点设置 | MicrosoftDocs
description: 有关如何为组织添加和配置一个门户的网站设置和所有门户的全局设置的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="configure-site-settings-for-portals"></a>配置门户的网站设置

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

网站设置是网站代码用于修改门户的行为或视觉样式的可配置命名值。 通常，当开发人员创建网站代码时，他们将引用不同组件的网站设置才能让最终用户修改设置值以修改网站，而无需更改代码、重新编译和重新部署该网站。

[!INCLUDE[pn-dynamics-crm](../../includes/pn-dynamics-crm.md)] 门户安装程序随附的示例门户包含几种针对各种样式的可配置网站设置，可用于修改网站内许多可视元素（例如，背景样式、文本颜色和布局宽度）。
您可以管理下列类型的站点设置：

- **全局门户设置**：这些设置应用于与添加门户的 [!INCLUDE[pn-dynamics-crm](../../includes/pn-dynamics-crm.md)] 组织关联的所有门户。
- **全局站点设置**：这些设置应用于与添加门户的 [!INCLUDE[pn-dynamics-crm](../../includes/pn-dynamics-crm.md)] 组织关联的特定门户（网站记录）。


## <a name="manage-portal-site-settings"></a>管理门户站点设置

1. 转到[门户设置](manage-existing-portals.md#settings)，选择**站点设置**。

2. 若要新建设置，请选择**新建**。

3. 若要编辑现有设置，请选择网格中列出的**网站设置**。

4. 指定提供的字段的值： 

    - **名称**：网站代码引用的标签，用于检索相应设置。 此名称应是关联网站的唯一名称，因为检索设置的代码将采用匹配名称中找到的第一个记录。
    
    - **网站**：关联的网站。 
    
    - **值**：设置
    
    - **说明**：设置或特定说明的用途。

5. 选择**保存并关闭**。

> [!NOTE] 
> Bing 地图集成在德国 Sovereign 云中不受支持。 如果您尝试在此环境中创建 Bingmaps/凭据，将显示错误消息。

## <a name="portal-site-settings"></a>门户站点设置

|姓名|Value|说明|
|----|-----|-----------|
|Authentication/Registration/RequiresConfirmation|FALSE |布尔值 true 启用电子邮件确认并禁用开放式注册。 默认值：False |
|Authentication/Registration/RequiresInvitation|FALSE |布尔值 true 启用邀请代码功能并禁用开放式注册。 默认值：False |
|conference-name|门户会议|表示指定门户的会议的 adx_conference 记录的名称。|
|HelpDesk/CaseEntitlementEnabled|TRUE|指示是否启用帮助中心案例权利的布尔值。 默认值：false|
|HelpDesk/Deflection/DefaultSelectedProductName| |当存在多个 producttypecode 等于 100000001 的产品时，属于显示在帮助中心案例变体上下拉列表中的默认选定产品的产品记录的名称。|
|Profile/ForceSignUp|FALSE|布尔值设置为“True”时将强制用户在获得网站内容的访问权限前更新其配置文件信息。 默认值：False|
|Profile/ShowMarketingOptionsPanel|TRUE|指示是否显示列出字段以在配置文件上指定市场营销通信首选项的面板的布尔值。 默认值：False|
|Search/Enabled|TRUE|表示搜索是否启用的布尔值。|
|search/filters|Content:adx_webpage;Events:adx_event,adx_eventschedule;<br>Blogs:adx_blog,adx_blogpost,adx_blogpostcomment;<br>Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;<br>Ideas:adx_ideaforum,adx_idea,adx_ideacomment;<br>Issues:adx_issueforum,adx_issue,adx_issuecomment;Help Desk:incident|搜索逻辑名称筛选器选项的集合。 在此处定义值会将下拉筛选器选项添加到站点范围的搜索。 此值应采用名称/值对的形式，名称和值以冒号分隔，对以分号分隔。<br>例如："Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Blogs:adx_blog,adx_blogpost,adx_blogpostcomment"。|
|Search/IndexQueryName|门户搜索|门户搜索查询使用的系统视图的名称。 默认值：门户搜索|
|search/query|+(@Query) _title:(@Query) _logicalname:adx_webpage~0.9^0.2<br> -_logicalname:adx_webfile~0.9 adx_partialurl:(@Query)<br> _logicalname:adx_blogpost~0.9^0.1 -_logicalname:adx_communityforumthread~0.9|覆盖对站点搜索的查询，以便应用更多权重和筛选器。 @Query 是用户输入的查询文本。 Lucene 查询语法参考：[http://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](http://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|Search/Stemmer|英语|门户搜索的词干分析算法使用的语言。 默认值：英语|
|CustomerSupport/DisplayAllUserActivitiesOnTimeline|FALSE| |
|||

与各种门户功能相关的站点设置，请参阅：

- [身份验证标识](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/set-authentication-identity)
- [Azure AD B2C 提供程序](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/azure-ad-b2c)
- [OAuth 2.0](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-oauth2-settings)
- [Open ID Connect](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-openid-settings)
- [WS 联合身份验证](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-ws-federation-settings)
- [SAML 2.0](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-saml2-settings)
- [将身份提供程序迁移到 Azure AD B2C](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/migrate-identity-providers)
- [在文件附件内容中搜索](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/search-file-attachment)
- [行为和日期及时间字段的格式](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/behavior-format-date-time-field)
- [添加地理位置](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/add-geolocation)
- [集成 Field Service](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/integrate-field-service)
- [实施一般数据保护条例](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/implement-gdpr)
- [启用页眉和页脚输出缓存](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/enable-header-footer-output-caching)

## <a name="manage-global-portal-settings"></a>管理全局门户设置

1. 转到[门户设置](manage-existing-portals.md#settings)，选择**站点设置**。

2. 转到**设置** &gt; **设置**。

3. 若要新建设置，请选择**新建**。

4. 若要编辑现有设置，请选择网格中列出的**网站设置**。

5. 指定提供的字段的值： 

    - **名称**：代码引用的唯一名称，用于检索相应设置。

    - **值**：设置

    - **说明**：设置或特定说明的用途。

6. 选择**保存并关闭**。

> [!NOTE] 
> Bing 地图集成在德国 Sovereign 云中不受支持。 如果您尝试在此环境中创建 BinMap/Key 或 Adxstudio/ProductivityPack/BingMap/Key，将显示错误消息。


