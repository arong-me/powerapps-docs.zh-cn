---
title: 在 Power Apps 门户中实施一般数据保护条例 | MicrosoftDocs
description: 了解如何在 Power Apps 门户中实施常规数据保护法规。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6ab1f29eac3835ed1699c2656c39034480bd495d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866871"
---
# <a name="implementing-general-data-protection-regulations-in-your-power-apps-portals"></a>在 Power Apps 门户中实施一般数据保护条例

常规数据保护法规 (GDPR) 是欧盟 (EU) 的一项法律行为，旨在保护欧盟地区所有个人的数据。 通过 GDPR，用户可以控制 Common Data Service 中其个人数据的使用。

作为管理员，您可以配置您的门户以符合 GDPR 标准。 例如，未成年人必须获得家长同意才能使用门户。 您还可以为使用您的门户的用户设立条款和条件。 用户必须同意这些条款和条件才能使用门户。

GDPR 让您可以获得门户用户的以下同意：使用其个人数据、识别未成年人用户和获得未成年人的父母同意。

## <a name="audit-logging"></a>审核日志记录

门户联系人记录中的**上次成功登录**字段显示门户用户上一次登录的时间。 此日期通过进行联系人记录审核来选择，并让该信息在标准审核流中可用。 这让管理员可以查看停用的社区成员并删除其记录。

> [!NOTE]
> 登录跟踪功能已被弃用。 建议使用 Azure Application Insights 这样的分析技术来捕获此类信息。 若要查看弃用功能的列表，请单击[此处](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)。

## <a name="identifying-minor-portal-users-and-obtaining-parental-consent"></a>识别未成年人门户用户并获得家长同意

识别未成年人的法规因国家/地区而异。 由于未成年人只能访问家长同意的门户，您可以使用门户联系人记录中的以下字段来将门户配置为识别未成年人：
- **为未成年人**：指示该联系人在其管辖区内被视为未成年人。 默认情况下，选择**否**。
- **为具有家长同意函的未成年人**：指示该联系人在其管辖区内被视为未成年人并且具有家长同意函。 默认情况下，选择**否**。

    ![识别未成年人门户用户并获得家长同意](../media/identify-minor-in-portal.png "识别未成年人门户用户并获得家长同意")

以下站点设置控制未成年人以及未获得家长同意的未成年人对门户的使用：

| 姓名  | 说明   |
|-----------------------|------------------------------------------|
| Authentication/Registration/DenyMinors  | 拒绝未成年人使用门户。 默认情况下，它设置为 false。                          |
| Authentication/Registration/DenyMinorsWithoutParentalConsent | 拒绝未获得家长同意的未成年人使用门户。 默认情况下，它设置为 false。 |
|||

如果确定一个用户门户是未成年人，且门户被配置为阻止未成年人，相应的消息将出现且不会显示同意。

![年龄要求消息](../media/gdpr-age-req.png "年龄要求消息")

如果确定一个用户门户是未获得家长同意的未成年人，且门户被配置为阻止未获得家长同意的未成年人，相应的消息将出现且不会显示同意。

![家长同意消息](../media/gdpr-parental-consent.png "家长同意消息")

以下内容片段控制当未成年人和未获得家长同意的未成年人使用门户时将出现的消息。 您可以根据自己的要求更改消息。

| 姓名                                                        | Type | 值                                                                    |
|-------------------------------------------------------------|------|--------------------------------------------------------------------------|
| Account/Signin/MinorNotAllowedHeading                       | 文本 | 年龄要求                                                         |
| Account/Signin/MinorNotAllowedCopy                          | HTML | 此门户不适合供未成年人使用且不允许使用。 |
| Account/Signin/MinorWithoutParentalConsentNotAllowedHeading | 文本 | 家长同意函                                                         |
| Account/Signin/MinorWithoutParentalConsentNotAllowedCopy    | HTML | 未成年人使用该门户需要家长同意。              |
|||

当有人使用外部提供程序注册且门户被配置为阻止未成年人或未获得家长同意的未成年人时，将不创建联系人记录，且用户不会通过身份验证。

## <a name="agreeing-to-terms-and-conditions"></a>同意条款和条件

根据 GDPR，门户用户必须同意条款和条件才能允许推广、分析或访问私人信息。 作为管理员，您可以在门户用户通过身份验证访问站点前发布自己的条款和条件以获取用户的同意。

![门户条款和条件](../media/gdpr-terms-agreement.png "门户条款和条件")

以下内容片段控制条款和条件在屏幕上的显示。 您可以根据自己的要求更改文本。

| 姓名                                           | Type | 值                                 |
|------------------------------------------------|------|---------------------------------------|
| Account/Signin/TermsAndConditionsHeading       | 文本 | 条款和条件                  |
| Account/Signin/TermsAndConditionsCopy          | HTML |                                       |
| Account/Signin/TermsAndConditionsAgreementText | 文本 | 我同意这些条款和条件 |
| Account/Signin/TermsAndConditionsButtonText    | 文本 | 继续                              |
|||

`Account/Signin/TermsAndConditionsCopy` 内容片段默认情况下为空。 门户管理员必须在此内容片段中输入条款和条件。

以下站点设置控制条款发布日期，以及条款是否应在门户上显示：

| 姓名  | 说明 |
|------------|---------------|
| Authentication/Registration/TermsPublicationDate  | 表示当前发布的条款和条件的生效日期的日期/时间值（GMT 格式）。 如果启用了条款同意，在此日期后未接受条款的门户用户将在下次登录时被要求接受条款。 如果未提供日期并启用了条款同意，条款将在门户用户每次登录时显示。 <br> **注意**：如果您希望门户用户在每次登录时都要同意条款和条件，请不要为此站点设置提供值。|
| Authentication/Registration/TermsAgreementEnabled | true 或 false 值。 如果设置为 true，门户将显示网站的条款和条件。 用户必须先同意条款和条件，然后系统才会考虑通过他们的身份验证并允许他们使用站点。 默认情况下，它设置为 false。        |
|||

以下字段在门户联系人记录中添加以用来存储门户用户同意条款和条件的日期和时间：
- **门户条款同意日期**：指示该用户同意门户条款和条件的日期及时间。

    ![门户条款协议日期](../media/portal-terms-agreement.png "门户条款协议日期")

### <a name="see-also"></a>另请参阅

[将身份提供程序迁移到 Azure AD B2C](migrate-identity-providers.md)
