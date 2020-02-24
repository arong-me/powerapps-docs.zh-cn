---
title: 启用多语言门户支持 | MicrosoftDocs
description: 有关如何为门户启用多种语言和如何使用多种语言创建内容的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: a91ffe1c00b7dbcc40b786731e956bfdd8fc6d94
ms.sourcegitcommit: 4349eefb1fd788f5e27d91319bc878ee9aba7a75
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2020
ms.locfileid: "3012713"
---
# <a name="enable-multiple-language-portal-support"></a>启用多语言门户支持
业务不限于一个地区或一种语言。 一个门户可以以多种语言显示内容，以便接触全球的客户。 可将门户的内容翻译为多种语言，同时保留单一内容层次结构。

![多语言下拉列表](../media/multi-language-dropdown.png "多语言下拉列表")  

若要对门户启用多种语言，请执行以下步骤：

1. [在 Common Data Service 环境中启用语言。](https://technet.microsoft.com/library/dn832148.aspx)  
2. 转至**门户** > **网站** > **网站**。
3. 选择要向其添加语言支持的网站。
4. 在**常规**选项卡下的**支持的语言**部分，选择**新网站语言**。
5. 找到其中包含**门户语言**（组织中已激活且受门户支持的语言的查找）和**发布状态**的窗体。

   ![添加新门户语言](../media/add-new-portal-language.png "添加新门户语言")

   ![为门户设置默认语言](../media/set-default-language-portal.png "为门户设置默认语言")

   ![支持的语言](../media/supported-languages.png "支持的语言")

> [!Note]
> 如果在已设置门户后激活新语言，则可[导入元数据翻译](../admin/import-metadata-translation.md)以获取为新激活语言翻译的元数据。

## <a name="supported-languages"></a>支持语言

下表显示自带且当前可用的所有语言。 可以找到此列表，方法是转至**门户** &gt; **内容** &gt; **门户语言**。 从该页面中选择要更改的语言后，可以更改其门户显示名称。 请注意，该列表中现在包含东亚语言（日文、中文和韩文）。

| **名称**                           | **语言代码** | **LCID** | **门户显示名称** |
|------------------------------------|-------------------|----------|-------------------------|
| 巴斯克语 - 巴斯克语                    | eu-ES             | 1069     | euskara                 |
| 保加利亚语 - 保加利亚               | bg-BG             | 1026     | български               |
| 加泰罗尼亚语 - 加泰罗尼亚                  | ca-ES             | 1027     | català                  |
| 中文 - 中国                    | zh-CN             | 2052     | 中文(中国)              |
| 中文 - 香港特别行政区            | zh-HK             | 3076     | 中文(香港特別行政區)    |
| 中文 - 繁体中文              | zh-TW             | 1028     | 中文(台灣)              |
| 克罗地亚语 - 克罗地亚                 | hr-HR             | 1050     | hrvatski                |
| 捷克语 - 捷克共和国             | cs-CZ             | 1029     | čeština                 |
| 丹麦语 - 丹麦                   | da-DK             | 1030     | dansk                   |
| 荷兰语 - 荷兰                | nl-NL             | 1043     | 荷兰              |
| 英语                            | zh-CN             | 2052     | 英语                 |
| 爱沙尼亚语 - 爱沙尼亚                 | et-EE             | 1061     | eesti                   |
| 芬兰语 - 芬兰                  | fi-FI             | 1035     | suomi                   |
| 法语 - 法国                    | fr-FR             | 1036     | français                |
| 加利西亚语 - 西班牙                   | gl-ES             | 1110     | galego                  |
| 德语 - 德国                   | de-DE             | 1031     | Deutsch                 |
| 希腊语 - 希腊                     | el-GR             | 1032     | Ελληνικά                |
| 印地语 - 印度                      | hi-IN             | 1081     | हिंदी                   |
| 匈牙利语 - 匈牙利                | hu-HU             | 1038     | magyar                  |
| 印度尼西亚语 - 印度尼西亚             | id-ID             | 1057     | 印度尼西亚语        |
| 意大利语 - 意大利                    | it-IT             | 1040     | italiano                |
| 日语 - 日本                   | ja-JP             | 1041     | 日本語                  |
| 哈萨克语 - 哈萨克斯坦                | kk-KZ             | 1087     | қазақ тілі              |
| 朝鲜语 - 韩国                     | ko-KR             | 1042     | 한국어                  |
| 拉脱维亚语 - 拉脱维亚                   | lv-LV             | 1062     | latviešu                |
| 立陶宛语 - 立陶宛             | lt-LT             | 1063     | lietuvių                |
| 马来语 - 马来西亚                   | ms-MY             | 1086     | 马来语           |
| 挪威博克马尔语 - 挪威        | nb-NO             | 1044     | norsk bokmål            |
| 波兰语 - 波兰                    | pl-PL             | 1045     | polski                  |
| 葡萄牙语 - 巴西                | pt-BR             | 1046     | português (巴西)      |
| 葡萄牙语 - 葡萄牙              | pt-PT             | 2070     | português (葡萄牙)    |
| 罗马尼亚语 - 罗马尼亚                 | ro-RO             | 1048     | română                  |
| 俄语 - 俄罗斯                   | ru-RU             | 1049     | русский                 |
| 塞尔维亚语(西里尔文) - 塞尔维亚共和国        | sr-Cyrl-CS        | 3098     | српски                  |
| 塞尔维亚语(拉丁语) - 塞尔维亚共和国           | sr-Latn-CS        | 2074     | srpski                  |
| 斯洛伐克语 - 斯洛伐克                  | sk-SK             | 1051     | slovenčina              |
| 斯洛文尼亚语 - 斯洛文尼亚               | sl-SI             | 1060     | slovenščina             |
| 西班牙语(传统风格) - 西班牙 | es-ES             | 3082     | español                 |
| 瑞典语 - 瑞典                   | sv-SE             | 1053     | svenska                 |
| 泰语 - 泰国                    | th-TH             | 1054     | ไทย                     |
| 土耳其语 - 土耳其                   | tr-TR             | 1055     | Türkçe                  |
| 乌克兰语 - 乌克兰                | uk-UA             | 1058     | українська              |
| 越南语 - 越南               | vi-VN             | 1066     | Tiếng Việt              |

## <a name="create-content-in-multiple-languages"></a>创建多种语言的内容

1. 登录到 Dynamics 365 门户。
2. 转至**门户** > **内容** > **网页**以查看内容列表。 每个网页有为门户激活的每种语言的该网页父版本和子版本。
3. 若要添加页面的新本地化，请转至基本页，然后向下滚动到**本地化内容**。
4. 选择最右侧的 **+** 按钮为本地化版本创建查找。

    ![添加新的本地化内容](../media/add-new-localized-content.png "添加新的本地化内容")  

> [!Note]
> 内容页的主页上的配置字段不继承到现有内容页。 它们仅在创建新内容页时使用。 必须单独更新内容页配置。

知识文章只有在已翻译为用户设置的门户显示语言时才显示。 但是，允许加强对如何以其他语言显示论坛和博客的控制。 可以选择为论坛或博客指定语言。 如果不指定语言，论坛或博客将以组织的主语言显示。 如果需要特定于某种语言的论坛或博客，则必须创建该论坛或博客，然后为其分派语言。

Web 链接集是门户顶部的导航链接。 通过导航到**门户** > **内容** > **Web 链接集**，可以控制如何翻译此内容。 一种语言为门户的活动语言时，将为新激活的语言创建一组新链接。

![新语言的活动 Web 链接](../media/active-weblink-new-language.png "新语言的活动 Web 链接")
