---
title: 在门户的文件附件内容中搜索 | MicrosoftDocs
description: 了解如何配置门户以在门户中的文件附件内容中搜索。
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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760142"
---
# <a name="search-within-file-attachment-content"></a>在文件附件内容中搜索

您可以使用注释附件在知识库文章中包含可下载文件。 您还可以使用 Web 文件创建包含可下载内容的常见问题页面。

您可以配置门户以允许门户用户在知识库文章的附件内容中搜索。 这可以帮助用户查找他们要找的信息。

在知识库文章中，任何带定义前缀的注释附件都编入索引。 在 Web 文件中，最新的注释附件编入索引。

若要将附件编入索引，必须创建以下站点设置并将其值设置为 **True**：

|站点设置|说明|
|------------|-----------|
|Search/IndexNotesAttachments|指示知识库文章和 Web 文件中注释附件的内容是否应编入索引。 默认情况下，它设置为 **False**。|
|KnowledgeManagement/DisplayNotes|指示是否将知识库文章的附件编入索引。 默认情况下，它设置为 **False**。|
|||

> [!NOTE]
> 仅可搜索附加到知识文章的文件。 附加到 Web 文件的文件不可搜索。

在搜索词语时，搜索结果也包含附件。 如果搜索词语包含注释附件，还将提供相应知识库文章的链接。 若要查看可下载附件，在左窗格中的**记录类型**下选择**下载**。 若要修改**下载**标签，请编辑搜索/分面/下载内容片段。 默认情况下，该值被设置为**下载**。

![下载附件](../media/search-attachment-content.png "下载附件") 

> [!NOTE]
> - 若要使用此功能，您必须[启用相关性搜索](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization)。 更多信息：[相关性搜索](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>更新门户配置

如果您已经有 2018 年 4 月之前的门户，并已将您的门户升级到最新版本，则必须使用以下配置来获得与新门户安装相同的用户体验。

**内容代码段**

若要修改搜索结果中显示的标签以用于注释和 Web 文件下载，请创建一个内容片段搜索/分面/下载，然后将其值设置为所需值。 默认值为**下载**。

**Web 文件**

与 Web 文件关联的文件附件的内容现在可以编入索引。 您可以更新 CSS 文件和图像文件的现有 Web 文件（例如，bootstrap.min.css、theme.css 和 homehero.jpg）以从搜索中排除。 

1. 打开[门户管理应用](configure-portal.md)并转到**门户** > **Web 文件**。
2. 打开要从搜索中排除的文件。
3. 在**其他**下，在**从搜索中排除**字段中选择**是**。

**Web 模板**

分面搜索 - 结果模板 Web 模板已修改以作为包含相关文章链接的主要搜索结果项目显示与知识库文章关联的文件。 您必须将分面搜索 - 结果模板 Web 模板更新为下列源：

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

您必须将 `\_logicalname:annotation~0.9^0.25` 值添加到“搜索/查询”站点设置。 添加后，此值应该如下所示：
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

若要配置分面以在单一分面中分组与知识库文章和 Web 文件关联的注释，编辑 Search/RecordTypeFacetsEntities 站点设置名称并将 `;Downloads:annotation,adx_webfile` 追加到它的值中。

若要允许与知识文章关联的附件出现在门户和搜索结果中，编辑 **KnowledgeManagement/DisplayNotes** 站点设置并将其值设置为 **True**。 站点设置 **KnowledgeManagement/NotesFilter** 包含必须添加为注释中注释文本字段的前缀的前缀值；仅具有指定前缀值的注释将出现在门户中。 默认情况下，值为 \*WEB\*，但可以通过站点设置更改。

若要启用与注释关联的文件附件的索引，创建 **Search/IndexNotesAttachments** 站点设置并将其值设置为 **True**。
