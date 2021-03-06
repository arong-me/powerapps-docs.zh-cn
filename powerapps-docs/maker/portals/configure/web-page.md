---
title: 管理 Power Apps 门户中的网页 | MicrosoftDocs
description: 了解如何管理门户中的网页。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/12/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 077d87c3636ae809ed63fc016df77402f52ebe89
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978137"
---
# <a name="manage-web-pages"></a>管理网页

网页在门户网站中表示特定的 URL，是门户内容管理系统核心实体之一。 通过与其他网页的父和子关系，该实体建立网站的层次结构（即站点地图）。

网页还为在门户站点地图中包括其他特殊的实体类型建立基础，Web 文件、快捷方式、论坛、Web 窗体和博客全部置于门户站点地图中，因而从与父网页的关系派生其 URL。

## <a name="manage-web-pages"></a>管理网页

可以在 Power Apps Portals Studio 中创建、编辑和管理网页。 但是，可以通过门户管理应用执行高级自定义。  

1. 打开[“门户管理”应用](configure-portal.md)。

2. 转至**门户** > **网页**。

3. 若要编辑现有的网页，选择网页名称。

4. 在这些字段中输入相应值。

5. 选择**保存并关闭**。

### <a name="web-page-attributes"></a>网页属性

下面的表说明门户使用多少标准网页属性。 务必注意，许多内容/显示导向的属性的呈现方式由使用的页面模板控制，因而由门户开发人员控制。


|        客户         |                                                                                                                                                                                                                                                                                                                                   说明                                                                                                                                                                                                                                                                                                                                   |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        客户         |                                                                                                                                                                                                                                                     实体的描述性名称。 该值在大部分模板中将用作页面标题，尤其是未提供标题值时。 此字段为必填字段。                                                                                                                                                                                                                                                     |
|       网站       |                                                                                                                                                                                                                                                                                                        实体所属的网站。 此字段为必填字段。                                                                                                                                                                                                                                                                                                         |
|     父页     |                                                                                                                                                                                                                                                      实体的父网页，在网站内容层次结构中。 <br>所有网页应有父页，除网站的单一根（主）页面外。                                                                                                                                                                                                                                                      |
|     部分 URL     | 用于构建此页的门户 URL 的 URL 路径段。 <br>您网站的单一根（主）页面，没有关联的父页的单一页面必须具有部分 URL 值 /。<br>部分 URL 值用作 URL 路径段。 这样，他们不应包含非法 URL 路径字符，如 "?"、"#"、"!"、"%"。 因为门户 URL 是通过将部分 URL 值与斜线 (/) 连在一起生成，所以它们通常不应包含斜线。 建议的做法是限制部分 URL 值为字母、数字和连字符或下划线。 例如：press-releases、Users_Guide、product1。 |
|    页面模板    |                                                                                                                                                                                                                                                                                             用于在门户中呈现此页面的页面模板。 此字段为必填字段。                                                                                                                                                                                                                                                                                             |
|  发布状态   |                                                                                                                                                 页面的当前发布工作流状态，可能指明页面是否在网站中可见。 此功能最常用于提供对内容的“发布/草稿”控制。<br>具有内容管理权限的用户可以被授予使用“预览模式”的能力，这允许这些用户查看（预览）未发布的内容。                                                                                                                                                  |
|    日期显示     |                                                                                                                                                                                                         此属性是模板可以使用的日期/时间值，纯粹地用于查看目的。 其没有功能意义，但对，例如，手动指定新闻稿或新闻项目页面的发布日期这样的操作很有用。                                                                                                                                                                                                          |
|    发布日期     |                                                                                                             控制页面将在之后在门户可见的日期/时间。 如果当前日期/时间在此日期之前，则该页面不可见。 （例外情况是，具有内容管理权限的用户可以被授予使用“预览模式”的能力，这允许这些用户查看（预览）未发布的内容。）这对控制时间敏感内容（如新闻或新闻稿）的发布非常有用。                                                                                                              |
|   到期日期   |                                                                                                                                                                控制页面将在之前在门户可见的日期/时间。 如果当前日期/时间在此日期之后，则该页面不可见。 （例外情况是，具有内容管理权限的用户可以被授予使用“预览模式”的能力，这允许这些用户查看（预览）已过期的内容。）                                                                                                                                                                 |
|      Web 窗体       |                                                                                                                                                                                                                                                                                                                   将在此页中显示的 Web 窗体。                                                                                                                                                                                                                                                                                                                    |
|        标题        |                                                                                                                                                                   页面的可选标题。 如果提供了此字段，该值在门户中使用，而不是“名称”字段。 如果您希望其他标题显示在门户中，并让名称对内容作者和用户非常有用，此方法很有用。                                                                                                                                                                   |
|       摘要       |                                                                                                                                                                                                                                                      页面的一个简短说明，该值通常用于添加页面的说明到呈现页面链接的门户导航元素。                                                                                                                                                                                                                                                       |
|        副本         |                                                                                                                                                                                                                                                                                                                    页面的主 HTML 内容字段。                                                                                                                                                                                                                                                                                                                     |
| 从站点地图隐藏 |                                                                                                                                                                                                        控制页面是否作为门户站点地图的一部分可见。 如果选中此值，页面仍在网站上在其 URL 中显示，并可以链接到，但标准导航元素（菜单等）将不会包括此页面。                                                                                                                                                                                                        |
|       作者        |                                                                                                                                                                                                                                  表示页面作者的联系人记录。 通常为管理目的使用该值，但是，这些信息可能呈现在门户中，前提是页面的页面模板支持它。                                                                                                                                                                                                                                   |
|    显示顺序    |                                                                                                                                                                                       整数值指示页面的放置顺序，相对于具有相同父页的其他实体。 这控制当指定页面的子实体的链接列表呈现门户中时（举例）页面和其他站点地图实体的排序。                                                                                                                                                                                        |
|     导航​​      |                                                                       Web 链接集记录。 这由 WebLinkNavigationPage.aspx 页面模板用于呈现页面左侧导航链接的列表。 在 CRM 中创建页面模板并指定重写 URL 属性为 ~/Pages/WebLinkNavigationPage.aspx。 设置网页的页面模板为此模板记录。 这通常只对父页执行，所有子页将自动接收其父页链接的同一列表。 当前页面上将具有突出显示的相应链接。                                                                        |
|   启用跟踪   |                                                                                                                                                                                                                                              如果启用，此页面的每个请求都将被记录。 如果用户通过身份验证，创建的网页日志记录将包含日期和时间、IP 地址和联系人记录。                                                                                                                                                                                                                                               |
|                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

## <a name="enable-page-comments"></a>启用页面评论

页面评论为用户提供在网页上查看和发布评论的功能。 在默认情况下，此功能禁用，可以按页面在页面中启用。

1. 打开[“门户管理”应用](configure-portal.md)。

2. 转至**门户** > **网页**。

3. 选择需要启用评论的网页。

4. 从**评论政策**列表，选择所需的评论政策：
   - **继承**：将使用父页的评论政策。 这是默认设置。
   - **开放**：允许所有用户（匿名和已通过身份验证）的提交并立即显示。
   - **对已通过身份验证的用户开放**：只允许通过身份验证的用户提交并会立即显示。
   - **已审查**：允许所有用户（匿名或通过身份验证）提交。 提交将不会显示，直到审查人批准。
   - **已关闭**：现有提交会显示，但不允许新提交。
   - **无**：用户提交被禁用。 提交无法创建或查看。

5. 保存更改。
