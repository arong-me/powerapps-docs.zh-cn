---
title: "Office 365 用户连接概述 | Microsoft 文档"
description: "参阅如何连接到 Office 365 用户，遍历某些示例，并查看所有函数"
services: 
suite: powerapps
documentationcenter: na
author: archnair
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/07/2016
ms.author: archanan
ms.openlocfilehash: c6f4d61728d41df880e595e74e91ff6012bc29aa
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="connect-to-office-365-users-connection-from-powerapps"></a>从 PowerApps 连接到 Office 365 用户连接
![Office 365 用户](./media/connection-office365-users/office365icon.png)

借助 Office 365 用户，可以使用 Office 365 帐户访问组织中的用户配置文件。 你可以执行各种操作，如获取配置文件、用户的经理或者直接上级。

可以在应用上的标签中显示此信息。 可以显示一个函数、多个函数，甚至组合不同的函数。 例如，可以创建一个组合了用户名和电话号码的表达式，然后在应用中显示此信息。

本主题演示了如何将 Office 365 用户添加为连接、如何将 Office 365 用户添加为应用的数据源，以及如何在库控件中使用表数据。

&nbsp;

[!INCLUDE [connection-requirements](../../includes/connection-requirements.md)]

## <a name="add-a-connection"></a>添加连接
1. [添加数据连接](../add-data-connection.md)并选择 **Office 365 用户**：  
   
    ![连接到 Office 365](./media/connection-office365-users/add-office.png)
2. 选择“**连接**”，如果系统提示你登录，请输入你的工作帐户。

Office 365 用户连接已创建并已添加到你的应用。 现在可供使用。

## <a name="use-the-connection-in-your-app"></a>在应用中使用连接
### <a name="show-information-about-the-current-user"></a>显示有关当前用户的信息
1. 在“插入”菜单上，选择“标签”
2. 在函数栏中，将其 **[Text](../controls/properties-core.md)** 属性设置为下列公式之一：
   
    `Office365Users.MyProfile().Department`  
    `Office365Users.MyProfile().DisplayName`  
    `Office365Users.MyProfile().GivenName`  
    `Office365Users.MyProfile().Id`  
    `Office365Users.MyProfile().JobTitle`  
    `Office365Users.MyProfile().Mail`  
    `Office365Users.MyProfile().MailNickname`  
    `Office365Users.MyProfile().Surname`  
    `Office365Users.MyProfile().TelephoneNumber`  
    `Office365Users.MyProfile().UserPrincipalName`  
    `Office365Users.MyProfile().AccountEnabled`  

此时，标签显示所输入的有关当前用户的信息。

### <a name="show-information-about-another-user"></a>显示其他用户的信息
1. 在“**插入**”菜单上，选择“**文本**”，然后选择“**文本输入**”。 将其重命名为 **InfoAbout**：  
   
    ![重命名控件](./media/connection-office365-users/renameinfoabout.png)
2. 在 **InfoAbout** 中，键入或粘贴组织中某个用户的电子邮件地址。 例如，键入 *yourName*@*yourCompany.com*。
3. 添加一个“标签”控件（使用“插入”菜单），然后将“[Text](../controls/properties-core.md)”属性设置为以下公式之一：
   
   * 显示其他用户的信息：  
     
       `Office365Users.UserProfile(InfoAbout.Text).Department`  
       `Office365Users.UserProfile(InfoAbout.Text).DisplayName`  
       `Office365Users.UserProfile(InfoAbout.Text).GivenName`  
       `Office365Users.UserProfile(InfoAbout.Text).Id`  
       `Office365Users.UserProfile(InfoAbout.Text).JobTitle`  
       `Office365Users.UserProfile(InfoAbout.Text).Mail`  
       `Office365Users.UserProfile(InfoAbout.Text).MailNickname`  
       `Office365Users.UserProfile(InfoAbout.Text).Surname`  
       `Office365Users.UserProfile(InfoAbout.Text).TelephoneNumber`  
       `Office365Users.UserProfile(InfoAbout.Text).UserPrincipalName`  
       `Office365Users.UserProfile(InfoAbout.Text).AccountEnabled`  
   * 显示其他用户经理的相关信息：  
     
       `Office365Users.Manager(InfoAbout.Text).Department`  
       `Office365Users.Manager(InfoAbout.Text).DisplayName`  
       `Office365Users.Manager(InfoAbout.Text).GivenName`  
       `Office365Users.Manager(InfoAbout.Text).Id`  
       `Office365Users.Manager(InfoAbout.Text).JobTitle`  
       `Office365Users.Manager(InfoAbout.Text).Mail`  
       `Office365Users.Manager(InfoAbout.Text).MailNickname`  
       `Office365Users.Manager(InfoAbout.Text).Surname`  
       `Office365Users.Manager(InfoAbout.Text).TelephoneNumber`  
       `Office365Users.Manager(InfoAbout.Text).UserPrincipalName`  
       `Office365Users.Manager(InfoAbout.Text).AccountEnabled`  

此时，标签显示所输入的有关指定用户或其经理的信息。

**注意**：如果正在基于 Common Data Service 中的某个实体开发应用，则可以基于 ID 而非电子邮件地址指定用户。

例如，可以[自动创建应用](../data-platform-create-app.md)，添加包含“标签”控件的屏幕，然后将控件的“Text”属性设置为以下公式：
<br>**Office365Users.UserProfile(BrowseGallery1.Selected.CreatedByUser).DisplayName**

如果创建联系人，并在应用的浏览屏幕中选择此联系人，那么“标签”控件会显示你的显示名称。

### <a name="show-the-direct-reports-of-another-user"></a>显示其他用户的直接上级
1. 添加“**文本输入**”控件（“**插入**”菜单 >“**文本**”），并将其重命名为 **InfoAbout**。
2. 在 **InfoAbout** 中，输入组织中用户的电子邮件地址。 例如，输入 *yourManagersName*@*yourCompany.com*
3. 添加**带有文本**库（“**插入**”菜单 >“**库**”），并将其 **[Items](../controls/properties-core.md)** 属性设置为下列公式：
   
    `Office365Users.DirectReports(InfoAbout.Text)`
   
    库将显示有关所输入用户的直接上级的信息。
   
    选择库后，右侧窗格显示该库的选项。
4. 在第二个列表中，选择 **JobTitle** 在第三个列表中，选择 **DisplayName** 库将更新，以显示这些值。  
   
    <br/>**注意**：第一个框实际上是图像控件。 如果没有图像，可以删除图像控件，然后在原处添加一个标签控件。 [添加和配置控件](../add-configure-controls.md)是一个好资源。

### <a name="search-for-users"></a>搜索用户
1. 添加“**文本输入**” 控件（“**插入**”菜单 >“**文本**”），并将其重命名为 **SearchTerm**。 输入要搜索的名称。 例如，输入你的名。
2. 添加**带有文本**库（“**插入**”菜单 >“**库**”），并将其 **[Items](../controls/properties-core.md)** 属性设置为下列公式：
   
    `Office365Users.SearchUser({searchTerm: SearchTerm.Text})`
   
    库显示名称中包含所输入的搜索文本的用户。
   
    选择库后，右侧窗格显示该库的选项。
3. 在第二个列表中，选择 **Mail**。 在第三个列表中，选择 **DisplayName**
   
    此时，库中的第二个和第三个标签会进行更新。

## <a name="view-the-available-functions"></a>查看可用函数
此连接包括以下函数：

| 函数名称 | 说明 |
| --- | --- |
| [MyProfile](connection-office365-users.md#myprofile) |检索当前用户的配置文件 |
| [UserProfile](connection-office365-users.md#userprofile) |检索特定用户配置文件 |
| [Manager](connection-office365-users.md#manager) |检索指定用户经理的用户配置文件 |
| [DirectReports](connection-office365-users.md#directreports) |返回指定用户的直接上级 |
| [SearchUser](connection-office365-users.md#searchuser) |检索用户配置文件的搜索结果 |

### <a name="myprofile"></a>MyProfile
获取我的配置文件：检索当前用户的配置文件。

#### <a name="input-properties"></a>输入属性
无。

#### <a name="output-properties"></a>输出属性
| 属性名称 | 类型 | 说明 |
| --- | --- | --- |
| Department |字符串 |用户的部门。 |
| DisplayName |字符串 |用户的显示名称。 |
| GivenName |字符串 |用户的名字。 |
| ID |字符串 |用户 ID |
| JobTitle |字符串 |用户的职务。 |
| 邮件 |字符串 |用户的电子邮件 ID。 |
| MailNickname |字符串 |用户的昵称。 |
| Surname |字符串 |用户的姓氏。 |
| TelephoneNumber |字符串 |用户的电话号码。 |
| UserPrincipalName |字符串 |用户的主体名。 |
| AccountEnabled |布尔值 |帐户启用标志。 |

### <a name="userprofile"></a>UserProfile
获取用户配置文件：检索特定用户配置文件。

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| ID |字符串 |是 |用户主体名或电子邮件 ID |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 类型 | 说明 |
| --- | --- | --- |
| Department |字符串 |用户的部门。 |
| DisplayName |字符串 |用户的显示名称。 |
| GivenName |字符串 |用户的名字。 |
| ID |字符串 |用户 ID |
| JobTitle |字符串 |用户的职务。 |
| 邮件 |字符串 |用户的电子邮件 ID。 |
| MailNickname |字符串 |用户的昵称。 |
| Surname |字符串 |用户的姓氏。 |
| TelephoneNumber |字符串 |用户的电话号码。 |
| UserPrincipalName |字符串 |用户的主体名。 |
| AccountEnabled |布尔值 |帐户启用标志。 |

### <a name="manager"></a>Manager
获取经理：检索指定用户经理的用户配置文件

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| ID |字符串 |是 |用户主体名或电子邮件 ID |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 类型 | 说明 |
| --- | --- | --- |
| Department |字符串 |用户的部门。 |
| DisplayName |字符串 |用户的显示名称。 |
| GivenName |字符串 |用户的名字。 |
| ID |字符串 |用户 ID |
| JobTitle |字符串 |用户的职务。 |
| 邮件 |字符串 |用户的电子邮件 ID。 |
| MailNickname |字符串 |用户的昵称。 |
| Surname |字符串 |用户的姓氏。 |
| TelephoneNumber |字符串 |用户的电话号码。 |
| UserPrincipalName |字符串 |用户的主体名。 |
| AccountEnabled |布尔值 |帐户启用标志。 |

### <a name="directreports"></a>DirectReports
获取直接上级：获取直接上级

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| ID |字符串 |是 |用户主体名或电子邮件 ID |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 类型 | 说明 |
| --- | --- | --- |
| Department |字符串 |用户的部门。 |
| DisplayName |字符串 |用户的显示名称。 |
| GivenName |字符串 |用户的名字。 |
| ID |字符串 |用户 ID |
| JobTitle |字符串 |用户的职务。 |
| 邮件 |字符串 |用户的电子邮件 ID。 |
| MailNickname |字符串 |用户的昵称。 |
| Surname |字符串 |用户的姓氏。 |
| TelephoneNumber |字符串 |用户的电话号码。 |
| UserPrincipalName |字符串 |用户的主体名。 |
| AccountEnabled |布尔值 |帐户启用标志。 |

### <a name="searchuser"></a>SearchUser
搜索用户：检索用户配置文件的搜索结果

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| searchTerm |字符串 |否 |搜索字符串。 适用于：显示名称、名字、姓氏、邮件、邮件昵称和用户主体名 |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 类型 | 说明 |
| --- | --- | --- |
| Department |字符串 |用户的部门。 |
| DisplayName |字符串 |用户的显示名称。 |
| GivenName |字符串 |用户的名字。 |
| ID |字符串 |用户 ID |
| JobTitle |字符串 |用户的职务。 |
| 邮件 |字符串 |用户的电子邮件 ID。 |
| MailNickname |字符串 |用户的昵称。 |
| Surname |字符串 |用户的姓氏。 |
| TelephoneNumber |字符串 |用户的电话号码。 |
| UserPrincipalName |字符串 |用户的主体名。 |
| AccountEnabled |布尔值 |帐户启用标志。 |

## <a name="helpful-links"></a>有用链接
* 查看所有[可用连接](../connections-list.md)。
* 了解如何向你的应用[添加连接](../add-manage-connections.md)。

