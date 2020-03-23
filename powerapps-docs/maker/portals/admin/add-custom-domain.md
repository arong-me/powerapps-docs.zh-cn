---
title: 添加自定义域名 | MicrosoftDocs
description: 添加自定义域名的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e354a3a784a984e070f5948b4b14c9eb4c32417b
ms.sourcegitcommit: 6cffa70358fd2e388d64a01f906c8c196fbbdefb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "3069527"
---
# <a name="add-a-custom-domain-name"></a>添加自定义域名

自定义域有助于您的客户更加轻松地找到您的支持资源，提高您的品牌知名度。 只能向一个门户添加一个自定义域名。 设置门户并获得域名后，需要 SSL 证书才能设置自定义主机名称。 可通过向导使用为域购买的 SSL 证书，以便将门户链接到自定义域。

1. 打开 [Power Apps 门户管理中心](admin-overview.md)。

2. 转至**门户操作** > **添加自定义域名**。 将打开一个向导，供您选择 SSL 证书。

3. 在**选择 SSL 证书**页上，选择以下选项之一：
   - **上传新证书**：如果尚未将 .pfx 文件上传到组织，则选择此选项以上传。 选择**文件**下的上传按钮以选择 .pfx 文件。 选择文件后，在**密码**字段中输入 SSL 证书的密码。
   - **使用现有证书**：选择此选项以从下拉列表选择正确证书。

     > [!Note]
     > SSL 证书必须满足以下要求：
     > - 由可信证书颁发机构签署
     > - [导出](https://docs.microsoft.com/powershell/module/pkiclient/export-pfxcertificate?view=win10-ps)为密码保护的 PFX 文件
     > - 包含长度至少为 2048 位的私钥
     > - 包含证书链中的所有中间证书
     > - 必须已启用 SHA2；受欢迎的浏览器已移除了对 SHA1 的支持
     > 
     > 将 SSL 证书导出为密码保护的 PFX 文件的步骤可能因您的证书提供商而异。 请与您的证书提供商联系以获取建议。 例如，某些提供商可能建议使用来自 [OpenSSL](https://www.openssl.org/) 或 [OpenSSL 二进制文件](https://wiki.openssl.org/index.php/Binaries)站点的 OpenSSL 第三方工具。 

4. 选择**下一步**。

5. 在**选择主机名**页上，选择以下选项之一：
    - **添加新主机名**：选择此选项以创建新的自定义域。 在**域名**字段中输入所需域名。
    - **使用现有主机名**：选择此选项以从下拉列表选择主机名。 
   
   > [!Note]
   > - 一个门户只能有一个自定义域名。 
   > - 若要创建自定义主机名称，则需要使用您的域提供程序创建 CNAME，将您的域指向您的门户的 URL。 如果刚添加了 CNAME 和域提供程序，则需要一些时间才能传播到所有 DNS 服务器。 如果未传播名称，而您在此处添加，将显示以下错误消息：请向此域名添加 CNAME 记录。 一段时间后重试。

6. 检查输入的信息，然后选择**下一步**开始创建 SSL 绑定。 应该看到消息“已为此门户成功配置自定义域名。 您现在可以转到 {Custom Domain Name} 以访问此门户。 {Custom Domain Name} 将是刚才配置的自定义门户 URL 的超链接。

7. 选择**完成**以关闭向导。

    > [!Note]
    > 如果要更改现有自定义域名，必须上传新 SSL 证书，然后按照本节的说明执行步骤。
    

