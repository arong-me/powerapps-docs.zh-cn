---
title: 为门户配置站点设置 |MicrosoftDocs
description: 说明如何为组织中的所有门户添加和配置站点设置以及全局设置。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 19dca44c26565bc55dcfaace48987b69dd0a195f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542713"
---
# <a name="configure-site-settings-for-portals"></a>为门户配置站点设置

站点设置是网站代码用于修改门户的行为或视觉样式的可配置的命名值。 通常，当开发人员创建网站代码时，他们将引用各种组件的站点设置，使最终用户能够修改设置值以更改网站，而无需更改代码、重新编译和重新部署该网站。

与安装 PowerApps 门户一起提供的示例门户包含多个可配置的网站设置，这些设置用于修改网站内的多个可视元素（例如背景样式、文本颜色和布局宽度）的各种样式。
你可以管理以下类型的站点设置：

- **全局门户设置**：这些设置适用于与添加它们的 Common Data Service 环境相关联的所有门户。
- **门户网站设置**：这些设置适用于与添加它们的 Common Data Service 环境相关联的特定门户（网站记录）。


## <a name="manage-portal-site-settings"></a>管理门户网站设置

1. 中转到 "[门户网站设置](../manage-existing-portals.md#settings)" 并选择 "**站点设置**"。

2. 若要创建新的设置，请选择 "**新建**"。

3. 若要编辑现有设置，请选择网格中列出的**站点设置**。

4. 指定提供的字段值： 

    - **名称**：网站代码所引用的用于检索相应设置的标签。 该名称对于关联的网站应是唯一的，因为检索该设置的代码将采用使用匹配名称找到的第一个记录。
    
    - **网站**：相关网站。 
    
    - **值**：设置
    
    - **说明**：设置或特殊说明的目的。

5. 选择“保存并关闭”。

> [!NOTE] 
> 德国主权云不支持必应地图集成。 如果尝试在此环境中创建 Bingmaps/凭据设置，将显示一条错误消息。

## <a name="portal-site-settings"></a>门户网站设置

|名称|Value|描述|
|----|-----|-----------|
|Authentication/Registration/RequiresConfirmation|FALSE |布尔值 true 可启用电子邮件确认并禁用打开注册。 默认值： False |
|Authentication/Registration/RequiresInvitation|FALSE |如果布尔值为 true，则启用邀请代码功能并禁用打开的注册。 默认值： False |
|会议名称|门户会议|表示给定门户的会议的 adx_conference 记录的名称。|
|支持人员/CaseEntitlementEnabled|TRUE|一个布尔值，指示是否启用了技术支持案例。 默认值： false|
|支持人员/偏转/DefaultSelectedProductName| |如果有多个产品，其中 producttypecode 等于100000001，则产品记录是在支持人员的下拉列表中显示的默认选定产品的名称。|
|Profile/ForceSignUp|FALSE|当设置为 "True" 时，布尔值将强制用户更新其配置文件信息，然后才会获得网站内容的访问权限。 默认值： False|
|Profile/ShowMarketingOptionsPanel|TRUE|一个布尔值，指示是否显示面板，该面板列出了用于指定配置文件上的营销通信首选项的字段。 默认值： False|
|搜索/启用|TRUE|指示是否启用搜索的布尔值。|
|搜索/筛选器|内容： adx_webpage;事件： adx_event、adx_eventschedule;<br>博客： adx_blog、adx_blogpost、adx_blogpostcomment;<br>论坛： adx_communityforum、adx_communityforumthread、adx_communityforumpost;<br>创意： adx_ideaforum、adx_idea、adx_ideacomment;<br>问题： adx_issueforum、adx_issue、adx_issuecomment;技术支持：事件|搜索逻辑名称筛选器选项的集合。 此处定义值会将下拉筛选器选项添加到站点范围的搜索。 此值应采用名称/值对的形式，名称和值之间用冒号分隔，对用分号分隔。<br>例如： "论坛： adx_communityforum、adx_communityforumthread、adx_communityforumpost;博客： adx_blog、adx_blogpost、adx_blogpostcomment "。|
|搜索/IndexQueryName|门户搜索|门户搜索查询使用的系统视图的名称。 默认值：门户搜索|
|搜索/查询|\+ （@Query） _title：（@Query） _logicalname： adx_webpage ~ 0.9 ^ 0。2<br> -_logicalname： adx_webfile ~ 0.9 adx_partialurl：（@Query）<br> _logicalname： adx_blogpost ~ 0.9 ^ 0.1-_logicalname： adx_communityforumthread ~ 0。9|覆盖站点搜索的查询，以应用额外的权重和筛选器。 @Query 是用户输入的查询文本。 Lucene 查询语法参考： [https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|搜索/词干分析器|英语|门户搜索的词干算法使用的语言。 默认值：英语|
|CustomerSupport/DisplayAllUserActivitiesOnTimeline|FALSE| |
|Authentication/[协议]/[Provider]/AllowContactMappingWithEmail| |允许基于电子邮件自动关联到联系人记录。 有关详细信息，请单击[此处](azure-ad-b2c.md#allow-auto-association-to-a-contact-record-based-on-email)。|
|||

对于与各种门户功能相关的站点设置，请参阅：

- [身份验证标识](set-authentication-identity.md)
- [Azure AD B2C 提供程序](azure-ad-b2c.md)
- [OAuth 2。0](configure-oauth2-settings.md)
- [打开 ID 连接](configure-openid-settings.md)
- [WS 联合身份验证](configure-ws-federation-settings.md)
- [SAML 2。0](configure-saml2-settings.md)
- [将标识提供者迁移到 Azure AD B2C](migrate-identity-providers.md)
- [在文件附件内容内搜索](search-file-attachment.md)
- [日期和时间字段的行为和格式](behavior-format-date-time-field.md)
- [添加地理位置](add-geolocation.md)
- [实施一般数据保护条例](https://docs.microsoft.com/dynamics365/customer-engagement/portals/implement-gdpr)
- [启用页眉和页脚输出缓存](https://docs.microsoft.com/dynamics365/customer-engagement/portals/enable-header-footer-output-caching)

## <a name="manage-global-portal-settings"></a>管理全局门户设置

1. 中转到 "[门户网站设置](../manage-existing-portals.md#settings)" 并选择 "**站点设置**"。

2. 请参阅**设置**&gt;**设置**。

3. 若要创建新的设置，请选择 "**新建**"。

4. 若要编辑现有设置，请选择网格中列出的**站点设置**。

5. 指定提供的字段值： 

    - **名称**：代码所引用的唯一名称，用于检索相应的设置。

    - **值**：设置

    - **说明**：设置或特殊说明的目的。

6. 选择“保存并关闭”。

> [!NOTE] 
> 德国主权云不支持必应地图集成。 如果尝试在此环境中创建 BinMap/Key 或 Adxstudio/ProductivityPack/BingMap/Key 设置，将显示一条错误消息。


