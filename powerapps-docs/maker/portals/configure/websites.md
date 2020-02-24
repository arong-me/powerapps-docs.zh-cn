---
title: 管理门户中的网站 | MicrosoftDocs
description: 了解如何管理门户中的网站。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/14/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: ae3d928a6beb05819c7c752503993a7b789a0fd7
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2976861"
---
# <a name="manage-websites"></a>管理网站

网站是门户应用程序的核心实体。 一个门户应用程序选择一个网站记录，这确定哪些门户实体（[网页](web-page.md)、[Web 文件](web-files.md)、[Web 角色](create-web-roles.md)、[内容片段](customize-content-snippets.md)等）应用于此应用程序。

拥有提供应用程序范围的网站，多个不同的门户应用程序可以连接到单个组织。

> [!NOTE]
> 确定给定门户应用程序绑定到哪个网站记录通常通过网站名称，其在门户部署的配置中指定。
不过，也可以通过 URL 路径前缀（请参阅[网站属性](#website-attributes)下的父网站和部分 URL 说明）或通过域使用网站绑定进行控制。

## <a name="manage-websites"></a>管理网站

网站是在创建新门户时创建的。 但是，可以通过门户管理应用执行网站高级管理。 

> [!WARNING]
> 删除网站记录时，也将删除门户元数据实体中与该网站记录有关的数据，如网页和 Web 链接。 通常这是预期行为，因为其整个网站及其所有相关数据均可以在一项操作中从组织中移除。

1. 打开[“门户管理”应用](configure-portal.md)。

2. 转到**门户** > **网站**。

3. 若要编辑现有的网站，请选择网站的名称。

4. 在这些字段中输入或编辑相应值。

5. 选择**保存并关闭**。

### <a name="website-attributes"></a>网站属性

|​名称|说明|
|-----|----------|
|​名称|网站的描述性名称。 此字段为必填字段。|
|主域名|将把此网站记录添加到的门户的主域名。|
|父网站|网站的父网站。 除了单个门户应用程序绑定到应用程序根路径的一个主网站的某些高级门户配置外，此字段通常被忽略，在特定子路径提供一个或多个子网站。|
|部分 URL|为与此网站相关的门户实体生成的所有 URL 的根 URL 路径段。<br>例如，如果将门户应用程序部署为在域 example.com 的根位置提供，此属性将没有值，`http://example.com/` 请求将呈现应用程序网站的主网页（因为需要主网页来将其部分 URL 设置为 "/"）。<br>如果该属性设置为值 "my-website"，主网页将具有 `http://example.com/my-website/` URL，网站上的所有页面将具有相同的 "/my-website/" 路径前缀。<br>在大多数门户配置中，此字段可以忽略，保留为空。<br>部分 URL 值用作 URL 路径段。 这样，他们不应包含非法 URL 路径字符，如 "?"、"#"、"!"、"%"。 因为门户 URL 是通过将部分 URL 值与斜线 ("/") 连在一起生成，所以它们通常不应包含斜线。<br>建议的做法是限制部分 URL 值为字母、数字和连字符或下划线。 例如："press-releases"、"Users_Guide"、"product1"。|
|||

### <a name="see-also"></a>另请参阅
[网站绑定](website-bindings.md)
