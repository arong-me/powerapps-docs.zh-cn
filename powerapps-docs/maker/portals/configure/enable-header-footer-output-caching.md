---
title: 在门户上启用页眉和页脚输出缓存 | MicrosoftDocs
description: 关于在门户上为现有用户启用页眉和页脚输出缓存的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e7a112c722e284f9060696d0fac5a3389b47b0d3
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977081"
---
# <a name="enable-header-and-footer-output-caching-on-a-portal"></a>在门户上启用页眉和页脚输出缓存

若要改善在门户中处理页眉和页脚 Web 模板的性能，可启用页眉和页脚输出缓存。 在每一次页面加载时分析和呈现页眉和页脚 Web 模板。 缓存页眉和页脚输出大大减少了页面处理时间。

对于新用户，默认已启用输出缓存。 以下站点设置可用并默认设置为 true 以支持此功能：
- Header/OutputCache/Enabled：将该值设置为 true 以启用页眉的输出缓存。
- Footer/OutputCache/Enabled：将该值设置为 true 以启用页脚的输出缓存。

对于已升级到门户新版本的用户，默认禁用输出缓存 &mdash; 这意味着在每次加载页面时对页眉和页脚 Web 模板进行分析和呈现。 若要启用输出缓存，必须更新页眉、页脚和语言下拉列表 Web 模板并创建所需的站点设置。

> [!Note]
> 如果您仅通过站点设置启用输出缓存，则页眉和页脚的有些部分不会正确呈现，并且会显示一条错误消息。

### <a name="enable-header-and-footer-output-caching-for-an-existing-user"></a>对现有用户启用页眉和页脚输出缓存

**步骤 1：更新页面 Web 模板**

1. 打开[“门户管理”应用](configure-portal.md)。
2. 转至**门户** > **Web 模板**。
3. 打开页眉 Web 模板。
4. 在**源**字段中，执行以下操作：
    - 查找以下代码和更新它：
    
        **现有代码**

        ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/Account/Login/LogOff?returnUrl={{ request.raw_url_encode | escape }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/SignIn?returnUrl={{ request.raw_url_encode }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
        
        **更新的代码**

         ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_out_url_substitution }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_in_url_substitution }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
    - 查找以下代码和更新它：

        **现有代码**
        ```
        {% assign current_page = page.adx_partialurl %}
        {% assign sr_page = sitemarkers[Search].url | remove: '/' %}
        {% assign forum_page = sitemarkers[Forums].url | remove: '/' %}
        {% if current_page == sr_page or current_page == forum_page %}
          <section class=page_section section-landing-{{ current_page }} color-inverse>
            <div class=container>
              <div class=row >
                <div class=col-md-12 text-center>
                  {% if current_page == sr_page %}
                    <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                    {% include 'Search' %}
                  {% endif %}
                </div>
              </div>
            </div>
          </section>
        {% endif %}
        ```

        **更新的代码**

        ```
        {% substitution %}
          {% assign current_page = page.id %}
          {% assign sr_page = sitemarkers[Search].id %}
          {% assign forum_page = sitemarkers[Forums].id %}
          {% if current_page == sr_page or current_page == forum_page %}
            {% assign section_class = section-landing-search %}
            {% if current_page == forum_page %}
              {% assign section_class = section-landing-forums %}
            {% endif %}
           <section class=page_section section-landing-{{ current_page }} {{ section_class | h }} color-inverse>
              <div class=container>
                <div class=row >
                  <div class=col-md-12 text-center>
                    {% if current_page == sr_page %}
                      <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                      {% include 'Search' %}
                    {% endif %}
                  </div>
                </div>
              </div>
            </section>
          {% endif %}
        {% endsubstitution %}
        ```

5. 保存 Web 模板。

**步骤 2：更新页脚 Web 模板**

1. 打开[“门户管理”应用](configure-portal.md)。
2. 转至**门户** > **Web 模板**。
3. 打开页脚 Web 模板。
4. 在**源**字段中，找到以下代码和更新它：
    
    **现有代码**
    
    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %} hidden-print>
    ```

    **更新的代码**

    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% substitution %}{% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %}{% endsubstitution %} hidden-print>
    ```

5. 保存 Web 模板。

**步骤 3：更新语言下拉列表 Web 模板**

1. 打开[“门户管理”应用](configure-portal.md)。
2. 转至**门户** > **Web 模板**。
3. 打开语言下拉列表 Web 模板。
4. 在**源**字段中，找到以下代码和更新它：
    
    **现有代码**

    ```
    <a href=/{{ language.url }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

    **更新的代码**

    ```
    <a href=/{{ language.url_substitution }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

5. 保存 Web 模板。

**步骤 4：创建站点设置**

创建以下站点设置：

|客户|值|
|----|-----|
|Header/OutputCache/Enabled|真|
|Footer/OutputCache/Enabled|真|
|||
