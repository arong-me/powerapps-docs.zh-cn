---
title: 启用多语言门户支持 |MicrosoftDocs
description: 有关为门户启用多种语言并使用多种语言创建内容的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f8da1ac4be7098fc712faef82f6c9566d5f10512
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552741"
---
# <a name="enable-multiple-language-portal-support"></a>启用多语言门户支持
企业并不局限于一个区域或一种语言。 单个门户可以使用多种语言显示内容，以吸引世界各地的客户。 在维护单个内容层次结构的同时，可以将门户内容翻译成多种语言。

![多语言下拉列表](../media/multi-language-dropdown.png "多语言下拉列表")  

若要为门户启用多种语言，请执行以下步骤：

1. [在 Common Data Service 环境中启用语言。](https://technet.microsoft.com/library/dn832148.aspx)  
2. 请参阅**门户** > **网站** > **网站**"。
3. 选择要将语言支持添加到的网站。
4. 在 "**常规**" 选项卡下的 "**支持的语言**" 部分中，选择 "**新建网站语言**"。
5. 填写窗体，包括**门户语言**（对组织中激活并受门户支持的语言的查找）和**发布状态**。

   ![添加新的门户语言](../media/add-new-portal-language.png "添加新的门户语言")

   ![为门户设置默认语言](../media/set-default-language-portal.png "为门户设置默认语言")

> [!Note]
> 如果在预配门户之后激活新语言，则可以[导入元数据翻译](../admin/import-metadata-translation.md)，以获取针对新激活语言翻译的元数据。

## <a name="supported-languages"></a>支持的语言

下表显示了当前可用的所有语言。 可以通过转到**门户**&gt;**内容**&gt;**门户语言**找到此列表。 在从此页中选择要更改的语言后，可以更改门户显示名称的语言。 请注意，该列表现在包含东亚语言（日语、中文和韩语）。

| **名称**                           | **语言代码** | **LCID** | **门户显示名称** |
|------------------------------------|-------------------|----------|-------------------------|
| 巴斯克语-巴斯克语                    | 欧盟             | 1069     | euskara                 |
| 保加利亚语-保加利亚               | bg-BG             | 1026     | български               |
| 加泰罗尼亚语-加泰罗尼亚语                  | ca-ES             | 1027     | català                  |
| 中文-中国                    | zh-chs-CN             | 2052     | 中文（中国）              |
| 中文-香港特别行政区            | zh-chs-HK             | 3076     | 中文（香港特別行政區）    |
| 中文-繁体              | zh-chs-幼圆             | 1028     | 中文（台灣）              |
| 克罗地亚语-克罗地亚                 | hr-HR             | 1050     | hrvatski                |
| 捷克语-捷克共和国             | cs-CZ             | 1029     | čeština                 |
| 丹麦语-丹麦                   | da-深色             | 1030     | dansk                   |
| 荷兰语-荷兰                | nl-NL             | 1043     | Nederlands              |
| 英语                            | en-us             | 1033     | 英语                 |
| 爱沙尼亚语-爱沙尼亚                 | et-EE             | 1061     | eesti                   |
| 芬兰语-芬兰                  | fi             | 1035     | suomi                   |
| 法语-法国                    | fr             | 1036     | 结算                |
| 加利西亚语-西班牙                   | 总帐             | 1110     | galego                  |
| 德语-德国                   | de             | 1031     | Deutsch                 |
| 希腊语-希腊                     | 萨尔瓦多             | 1032     | Ελληνικά                |
| 印地语-印度                      | 高清             | 1081     | हिंदी                   |
| 匈牙利语-匈牙利                | hu-HU             | 1038     | magyar                  |
| 印度尼西亚语-印度尼西亚             | id-ID             | 1057     | 巴哈萨语印度尼西亚        |
| 意大利语-意大利                    | it-IT             | 1040     | italiano                |
| 日语-日本                   | ja-jp             | 1041     | 日本語                  |
| 哈萨克语-哈萨克斯坦                | kk-KZ             | 1087     | қазақ тілі              |
| 朝鲜语-韩国                     | ko-KR             | 1042     | 한국어                  |
| 拉脱维亚语-拉脱维亚                   | lv-LV             | 1062     | latviešu                |
| 立陶宛语-立陶宛             | lt-LT             | 1063     | lietuvių                |
| 马来语-马来西亚                   | ms-MY             | 1086     | 巴哈萨语 Melayu           |
| 挪威语（博克马尔语）-挪威        | nb-否             | 1044     | norsk 博克马尔语            |
| 波兰语-波兰                    | pl-PL             | 1045     | polski                  |
| 葡萄牙语-巴西                | pt-BR             | 1046     | português （巴西）      |
| 葡萄牙语-葡萄牙              | pt-PT             | 2070     | português （葡萄牙）    |
| 罗马尼亚语-罗马尼亚                 | ro-RO             | 1048     | română                  |
| 俄文-俄罗斯                   | ru-RU             | 1049     | русский                 |
| 塞尔维亚语（西里尔文）-塞尔维亚        | Cyrl-CS        | 3098     | српски                  |
| 塞尔维亚语（拉丁语）-塞尔维亚           | Latn-CS        | 2074     | srpski                  |
| 斯洛伐克语-斯洛伐克                  | sk-SK             | 1051     | slovenčina              |
| 斯洛文尼亚语-斯洛文尼亚               | sl-SI             | 1060     | slovenščina             |
| 西班牙语（传统排序）-西班牙 | es             | 3082     | 西班牙语                 |
| 瑞典语-瑞典                   | sv-SE             | 1053     | svenska                 |
| 泰语-泰国                    | 第 th             | 1054     | ไทย                     |
| 土耳其语-土耳其                   | tr-TR             | 1055     | Türkçe                  |
| 乌克兰语-乌克兰                | uk-UA             | 1058     | українська              |
| 越南语-越南               | vi-VN             | 1066     | T Việt              |

## <a name="create-content-in-multiple-languages"></a>用多种语言创建内容

1. 登录到 Dynamics 365 门户。
2. 请参阅**门户** > **内容** > **网页**，查看内容列表。 对于每个网页，为门户激活的每个语言都将有该页的父版本和页面的子版本。
3. 若要添加新的页面本地化，请前往基本页，向下滚动到 "已**本地化内容**"。
4. 选择最右侧的 " **+** " 按钮，为本地化版本创建查找。

    ![添加新的本地化内容](../media/add-new-localized-content.png "添加新的本地化内容")  

> [!Note]
> 内容页主页上的配置字段不会继承到现有内容页。 它们仅用于创建新的内容页面。 必须单独更新内容页面配置。

仅当知识库文章已转换为用户设置要在中显示的门户时所用的语言时，才会显示这些文章。 不过，论坛和博客允许更好地控制以其他语言显示的方式。 指定论坛或博客的语言是可选的。 如果未指定语言，则将以组织的主要语言显示论坛或博客。 如果希望论坛或博客特定于某种语言，则必须创建该语言，并为其分配语言。

Web 链接集是门户顶部的导航链接。 通过导航到**门户** > **内容** > **Web 链接集**，你可以控制此内容的翻译方式。 当门户的某个语言处于活动状态时，将为新激活的语言创建一组新的链接。

![新语言的活动 web 链接](../media/active-weblink-new-language.png "新语言的活动 web 链接")