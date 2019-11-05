---
title: 在门户中搜索文件附件内容 |MicrosoftDocs
description: 了解如何配置门户以在门户中的文件附件内容内进行搜索。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 52d7701ac84072c84886ea86969f28809d0e7960
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551637"
---
# <a name="search-within-file-attachment-content"></a>在文件附件内容内搜索

您可以使用注释附件在知识库文章中包含可下载文件。 你还可以使用 web 文件创建包含可下载内容的常见问题页面。

你可以配置门户以允许门户用户在知识库文章的附件内容中搜索。 这可以帮助用户找到所需的信息。

在知识库文章中，将对具有定义的前缀的任何注释附件编制索引。 在 "web 文件" 中，将为最新的注释附件编制索引。

若要为附件编制索引，必须创建以下网站设置并将其值设置为**True**：

|站点设置|描述|
|------------|-----------|
|搜索/IndexNotesAttachments|指示是否应对知识库文章和 web 文件中的 notes 附件内容进行索引。 默认情况下，它设置为**False**。|
|KnowledgeManagement/DisplayNotes|指示是否为知识库文章的附件编制索引。 默认情况下，它设置为**False**。|
|||

> [!NOTE]
> 只能搜索附加到知识库文章中的文件。 不能搜索附加到 web 文件的文件。

搜索字词时，搜索结果还会包含附件。 如果搜索词与注释附件匹配，还将提供指向相应知识库文章的链接。 若要查看可下载的附件，请在左窗格中选择 "**记录类型**" 下的 "**下载**"。 若要修改**下载**标签，请编辑搜索/分面/下载内容片段。 默认情况下，此值设置为 "**下载**"。

![下载附件](../media/search-attachment-content.png "下载附件") 

> [!NOTE]
> - 若要使用此功能，必须[启用 "相关性搜索](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization)"。 详细信息：[相关性搜索](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>更新门户配置

如果你已有2018年4月之前的门户，并已将门户升级到最新版本，则必须使用以下配置才能获得与新门户安装相同的用户体验。

**内容片段**

若要修改注释和 web 文件下载的搜索结果中显示的标签，请创建内容片段搜索/分面/下载，然后根据需要设置其值。 默认值为 "**下载**"。

**Web 文件**

现在可以为与 web 文件关联的文件附件的内容编制索引。 可以更新要从搜索中排除的 CSS 文件和图像文件（例如，homehero、web.config 和）的现有 web 文件。 

1. 打开[门户管理应用](configure-portal.md)，并 > **Web Files**中转到**门户**。
2. 打开要从搜索中排除的文件。
3. 在 "**杂项**" 下的 "**从搜索中排除**" 字段中选择 **"是"** 。

**Web 模板**

对分面搜索结果模板 web 模板进行修订，以将与知识库文章关联的文件显示为带有相关文章链接的主搜索结果项。 必须将分面搜索结果模板 web 模板更新为以下源：

```
{% assign openTag = '{{' %}
{% assign closingTag = '}}' %}
{%raw%}
  <script id=search-view-results type=text/x-handlebars-template>
   {{#if items}}
    <div class=page-header>
     <h3>{%endraw%}{{openTag}} stringFormat {{ resx.Search_Results_Format_String }} firstResultNumber lastResultNumber itemCount {{closingTag}}{%raw%}
      <em class=querytext>{{{query}}}</em>
      {{#if isResetVisible}}
       <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
      {{/if}}
     </h3>
    </div>
   <ul>
    {{#each items}}
     <li>
      <h3><a title={{title}} href={{url}}>{{#if parent}}<span class=glyphicon glyphicon-file pull-left text-muted aria-hidden=true></span>{{/if}}{{title}}</a></h3>
      <p class=fragment>{{{fragment}}}</p>
      {{#if parent}}
       <p class=small related-article>{%endraw%}{{ resx.Related_Article }}{%raw%}: <a title={{parent.title}} href={{parent.absoluteUrl}}>{{parent.title}}</a></p>
      {{/if}}
      <ul class=note-group small list-unstyled>
       {{#if relatedNotes}}
        {{#each relatedNotes}}
         <li class=note-item>
         {{#if isImage}}
          <a target=_blank title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{else}}
          <a title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{/if}}
         <p class=fragment text-muted>{{{fragment}}}</p>
         </li>
        {{/each}}
        {{/if}}
      </ul>
     </li>
    {{/each}}
   </ul>
   {{else}}
    <h2>{%endraw%}{{ resx.Search_No_Results_Found }}{%raw%}<em class=querytext>{{{query}}}</em>
     {{#if isResetVisible}}
      <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
     {{/if}}
    </h2>
   {{/if}}
  </script>
{%endraw%}
```

**站点设置**

您必须将 `\_logicalname:annotation~0.9^0.25` 值添加到搜索/查询站点设置。 添加后，该值应如下所示：
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

若要配置 facet，以将与知识库文章和 web 文件关联的批注分组到单个方面，请编辑 Search/RecordTypeFacetsEntities 站点设置名称并将 `;Downloads:annotation,adx_webfile` 追加到其值。

若要允许与知识库文章关联的附件显示在门户和搜索结果中，请编辑**KnowledgeManagement/DisplayNotes**站点设置并将其值设置为**True**。 站点设置**KnowledgeManagement/NotesFilter**包含必须以注释文本字段为前缀的前缀值;门户上只显示带有指定前缀值的注释。 默认情况下，此值为 \*WEB\*，但你可以通过站点设置对其进行更改。

若要启用对与注释关联的文件附件的索引，请创建**Search/IndexNotesAttachments**站点设置并将其值设置为**True**。
