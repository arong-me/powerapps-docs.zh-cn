---
title: 创建自定义帮助页面 | MicrosoftDocs
description: 在 UCI 上创建自定义帮助页面
ms.custom: ''
ms.date: 09/13/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: ''
caps.latest.revision: ''
author: matthewbolanos
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0ba852565acee10fc4c853eb185f552df6399fc9
ms.sourcegitcommit: d98dd90a7dda11f434a13a7f8976459856d6142b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/29/2020
ms.locfileid: "3093892"
---
# <a name="create-guided-help-for-your-unified-interface-app"></a>为您的统一接口应用创建引导式帮助

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

使用自定义帮助窗格和向导型任务，为您的统一接口应用程序提供为您的组织定制的自定义产品内帮助体验。 使用自定义帮助窗格提供特定于实体、窗体和语言的帮助和指南，其中包括富文本、内容链接、图像和视频链接。 

> [!IMPORTANT]
> 自定义帮助窗格替代了旧版 Web 客户端应用程序使用的先前的学习路径引导式学习功能。

## <a name="custom-help-panes-and-learning-path"></a>自定义帮助窗格和学习路径
自定义帮助窗格的新的引导式帮助实现不同于以前的学习路径引导式帮助功能。 这两种功能都可以为您的应用程序创建自定义帮助。 但是，自定义帮助窗格针对最常见的引导式帮助场景进行了优化。   

自定义帮助窗格提供了学习路径未提供的以下关键功能： 
- 自由形式的富文本，包括项目符号和编号。
- 可见链接指导标记和帮助提示框。
- 更多视频源选项，包括私人源。
- 将帮助内容作为解决方案的一部分存储在 Common Data Service 中。 

自定义帮助窗格不提供学习路径提供的以下关键功能： 
- 顺序帮助提示框。
- 按角色提供帮助页面。
- 按设备外形规格提供帮助页面，如智能手机。 

## <a name="prerequisites"></a>必备条件 
要创作自定义帮助窗格，您需要： 
- 版本 9.1.0.10300 或更高版本。
- **帮助页面**特权的全局创建、读取、写入、删除、追加和追加到权限。 默认情况下，系统管理员和系统定制员安全角色均具有此特权。  
- [您的环境必须启用了自定义帮助窗格。](#enable-custom-help-panes-for-your-environment)

## <a name="enable-custom-help-panes-for-your-environment"></a>为您的环境启用自定义帮助窗格
1. 打开模型驱动应用，然后在命令栏上，选择**设置** ![设置](../model-driven-apps/media/powerapps-gear.png) > **高级设置**。
2. 转到**设置** > **系统** > **管理**。  
3. 在**管理**页上，选择**系统设置**。
4. 在**常规**选项卡上的**设置自定义帮助 URL** 下，为**启用自定义帮助窗格和向导型任务**选择**是**，然后选择**确定**。

    > [!div class="mx-imgBorder"] 
    > ![启用自定义帮助窗格](media/enable-custom-help-panes.png "启用自定义帮助窗格")

> [!IMPORTANT]
> 您可以启用自定义帮助窗格或可自定义帮助，但不能同时启用。 确认**使用可自定义实体的自定义帮助**和**将参数追加到 URL**是否均设置为**否**。  
 
## <a name="context-sensitive-custom-help"></a>上下文相关的自定义帮助
每个帮助窗格对于以下上下文是唯一的： 
- 应用程序 
- 实体
- 表单 
- Language   

## <a name="help-pane-navigation"></a>帮助窗格导航
默认情况下，帮助窗格保持打开状态并位于您使用它第一次打开的帮助内容上，即使您导航到其他窗体。 这样，当您将用户定向到应用的不同部分时，帮助内容将保持不变。 

### <a name="to-author-help-pane-content"></a>创作帮助窗格的内容
1.  要查看帮助窗格，请打开模型驱动应用，然后在命令栏上选择**帮助**。 

    ![帮助](media/help-command.png)   
2.  在“帮助”窗格上，选择垂直省略号，然后选择**编辑**。 

    ![编辑帮助](media/help-edit-command.png)
    
    帮助窗格现在处于编辑模式，光标位于帮助窗格标题上。
3.  在编辑窗格中，您可以执行以下任务： 
    - 通过直接在帮助窗格区域键入来输入文本。 
    - 使用富文本命令（如粗体、斜体、删除线和创建列表）来为文本设置格式。 
    - 选择**插入**选项卡添加部分、视频、图像、链接、指导标记和提示框帮助。 
<!-- confirm the image is safe for use
    > [!div class="mx-imgBorder"] 
    > ![Custom help pane edit](media/custom-help-pane-edit.png)  -->
4.  要保存更改，请选择**保存**。  

### <a name="free-form-text"></a>自由形式的文本
文本可以放在帮助窗格中的任何位置。 在各部分之前、之中或之后输入自由形式的文本。 文本支持粗体、斜体、下划线和删除线字体格式。 可以使用剪切、复制和粘贴以及多级撤消。 

### <a name="bullets-and-numbered-lists"></a>项目符号和编号列表
选择项目符号或编号图标可切换当前行，使其加上项目符号或编号。 如果您在列表中选择了多行，则每行都将加上项目符号或编号。 移动列表中的一行并缩进其下级编号。  

### <a name="sections"></a>部分
部分是可折叠的文本框。  您可以在其中放置链接或自由形式的文本。 使用部分可以将相似的项目分组。 部分可以默认打开或折叠。 

### <a name="video-and-static-images"></a>视频和静态图像
您可以将视频和静态图像插入帮助窗格。 视频和图像是 Internet 上内容的链接。 自定义帮助窗格不会在您的帮助窗格中存储视频和图像文件。 打开帮助窗格时，自定义帮助窗格会将内容从链接引入以显示它。 如果要引用企业专用内容，可以使用指向 Microsoft Stream 视频的链接。 

> [!TIP]
> 请记住复制所需视频或图像的链接 URL，以便将其粘贴到帮助窗格中。 

自定义帮助窗格支持以下视频源：
- Microsoft Stream（用于专用内容） 
- YouTube
- Facebook
- Vimeo


### <a name="links"></a>链接
链接可以指向网站，并且可以在同一窗口（默认）中打开，也可以在单独的窗口中打开。 链接到现有帮助页面的功能尚未启用。   

### <a name="balloons-and-coach-marks"></a>提示框和指导标记
提示框和指导标记可用于指向特定的 UI 元素。 提示框可以包含文本。 指导标记只是使用指导指针突出显示一个元素。 按顺序说明几个 UI 元素的一种方法是简单地收集用户可以选择的列表中的链接。 例如：

1. 带有说明或注释的第一个 UI 元素的链接。
2. 带有说明或注释的第二个 UI 元素的链接。
3. 带有说明或注释的第三个 UI 元素的链接。

用户可以按顺序选择一个元素，也可以返回到特定元素并突出显示它。

## <a name="solutions-and-custom-help-pane-content"></a>解决方案和自定义帮助窗格的内容
所有帮助内容都作为解决方案的一部分存储在 Common Data Service 的帮助页面组件中。 当您将解决方案从一个环境迁移到另一个环境（例如从测试到生产）时，可以定义导出帮助记录，以便将它们包含在解决方案中。 这使您可以在解决方案移到其他环境时将帮助内容与解决方案中的功能同步。 作为解决方案的一部分，自定义帮助窗格支持所有标准解决方案应用程序生命周期管理 (ALM) 功能。

### <a name="moving-content-via-solutions"></a>通过解决方案移动内容
默认情况下，所有新的帮助页面都会显示在默认解决方案中。 如果要将内容移动到另一个环境，请先将现有帮助页面添加到非托管解决方案中，然后再导出它们。 要将帮助页面添加到非托管解决方案，请按照下列步骤操作：

1. 导航到非托管解决方案。
2. 从命令栏上的省略号选择**切换到经典**。
3. 选择**添加现有**。
4. 选择**帮助页面**。
5. 选择想要添加的帮助页面，然后选择**确定**。

> [!NOTE]
> 当前，您无法在现代解决方案资源管理器中将现有的帮助窗格添加到非托管解决方案中。 


## <a name="help-page-documentation-automation"></a>帮助页面文档自动化
您可能希望将内容备份或存储在源代码控制系统中。 您可能还希望在帮助窗格内容上使用文档自动化工具，例如翻译工具或检查器。 自定义帮助窗格数据直接存储在 Common Data Service 中，并且可以为此目的导出和导入。  

自定义帮助窗格支持自定义 XML 格式。 此格式在下面有记录。 详细信息：[自定义帮助 XML 定义](#custom-help-xml-definition)  

导出后，每个帮助页面都将导出为单独的文件。   

## <a name="frequently-asked-questions"></a>常见问题
本节讨论有关自定义帮助页面的常见问题。 

### <a name="are-custom-help-pages-the-same-as-customizable-help"></a>自定义帮助页面与可自定义帮助相同吗？

自定义帮助窗格和向导型任务是系统设置的**设置自定义帮助 URL** 部分的一个选项。 自定义帮助窗格和向导型任务支持可自定义的帮助窗格，该窗格就显示在用户窗体的旁边。  此系统设置的“设置自定义帮助”部分中的其他选项包括可自定义的帮助功能。 它们使您可以替代默认的应用帮助，并将组织中的用户指向其他 URL 以获得帮助。 或者，可以替代高度自定义实体的帮助，以便可以更好地描述您的工作流。

有关可自定义帮助的更多信息，请参阅[启用和使用可自定义帮助](../model-driven-apps/use-customizable-help.md)。


### <a name="how-do-i-migrate-my-data-from-learning-path-to-custom-help-pages"></a>如何将数据从学习路径迁移到自定义帮助页面？ 
学习路径有两种类型的帮助：帮助窗格和顺序帮助提示框。 顺序帮助提示框位置已与旧版 Web 客户端 UI 深度集成，无法转移到新的自定义帮助窗格。  

根据您的引导式帮助中包含多少文本，只是将信息直接从学习路径用户界面复制到新的自定义帮助窗格用户界面中可能是最简单的。 不过，您也可以导出学习路径帮助内容。  最简单的方法是使用**学习路径** > **内容库** > **本地化** > **导出**功能导出您的内容。 选择所需的记录，然后将其导出。 这将为每个帮助窗格和向导型任务创建一个 XLIFF 文件。  然后，使用公开可用的 XLIFF 编辑器或 XLIFF 到 HTML 转换器检索您的内容。 

## <a name="custom-help-xml-definition"></a>自定义帮助 XML 定义
本节介绍自定义帮助 XML 定义。 

### <a name="pphml"></a>PPHML

```
<pphml>
    <h1>FAQ</h1>
    <collapsible title="What is PPHML?">
        <p>PPHML is a domain specific language for help content. It is used to create help content that includes elements such as images, videos, balloons, coach marks, etc.</p>
    </collapsible>
    <collapsible title="What does PPHML stand for?">
        <p>PPHML stands for Power Platform Help Markup Language</p>
    </collapsible>
</pphml>
```

#### <a name="definition-and-usage"></a>定义和使用

`<pphml>` 元素告诉帮助浏览器这是一个 PPHML 文档。

`<pphml>` 元素表示 PPHML 文档的根。

`<pphml>` 元素是所有其他 PPHML 元素的容器。

### <a name="title"></a>标题
在帮助页面中显示标题。

```
<h1>This will be displayed at the top of the help page</h1>
```

#### <a name="definition-and-usage"></a>定义和使用
**`<h1>`** 元素定义帮助页面的标题。

`<h1>` 这必须是 `<pphml>` 中的第一个元素。

### <a name="image"></a>图像
在帮助页面中显示图像。

```
<img src="smiley.gif" alt="Smiley face" title="Smiley face"/>
```

#### <a name="definition-and-usage"></a>定义和使用
**`<img>`** 元素将图像嵌入帮助页面。

#### <a name="attributes"></a>属性
- `src`：指定图像的 URL。 此属性是必需的。

- `title`：指定标题和图像一起显示，通常作为悬停工具提示。

- `alt`：指定图像的替换文本。 屏幕阅读器使用此文本。

### <a name="video"></a>视频
在帮助页面中显示视频。

```
<video src="https://www.youtube.com/watch?v=WSWmn7WM3i4" />
```

#### <a name="definition-and-usage"></a>定义和使用

**`<video>`** 元素将视频（例如教程或培训视频）嵌入帮助页面。

##### <a name="supported-sources"></a>支持的源

- Microsoft Stream
- YouTube
- Facebook
- Vimeo

#### <a name="attributes"></a>属性
- `src`：指定视频的 URL。 此属性是必需的。

- `allowFullScreen`：指定用户是否可以将视频切换到全屏。 可能的值为“true”或“false”。 并非所有视频源都支持此属性。

- `autoplay`：指定视频将在加载帮助页面后立即开始播放。 可能的值为“true”或“false”。 并非所有视频源都支持此属性。

- `startTime`：指定从何时开始播放视频，以秒为单位。

### <a name="paragraph"></a>段落
在帮助页面中显示段落。

```
<p>This is some text in a paragraph.</p>
```

#### <a name="definition-and-usage"></a>定义和使用
**`<p>`** 元素定义段落。

段落中的文本可以通过以下方式修饰：
- 粗体，使用 `<strong>` 元素
- 斜体，使用 `<em>` 元素
- 删除线，使用 `<del>` 元素
- 下划线，使用 `<u>` 元素

这些修饰可以组合。 例如，创建一段既为粗体又带下划线的文本。

### <a name="bulleted-list"></a>项目符号列表
在帮助页面中显示项目符号列表。

```
<ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ul>
```

#### <a name="definition-and-usage"></a>定义和使用
**`<ul>`** 元素定义项目符号列表。

将 `<ul>` 元素与 `<li>` 元素一起使用可以创建项目符号列表。

### <a name="numbered-list"></a>编号列表
在帮助页面中显示编号列表。

```
<ol>
    <li>First step</li>
    <li>Second step</li>
    <li>Third step</li>
</ol>
```

#### <a name="definition-and-usage"></a>定义和使用
**`<ol>`** 元素定义已排序（已编号）列表。
将 `<ol>` 标记与 `<li>` 元素一起使用可以创建编号列表。

### <a name="collapsible"></a>可折叠
在帮助页面中显示可折叠部分。

```
<collapsible title="This is a Section">
    <p>This is a paragraph inside a section</p>
    <img src=smiley.gif" title="This is an image inside a section" />
</collapsible>
```

#### <a name="definition-and-usage"></a>定义和使用
**`<collapsible>`** 元素定义一部分内容，用户可以按需查看或隐藏。

#### <a name="attributes"></a>属性
- `collapsed`：指定该部分是最初折叠还是展开。 可能的值为“true”（已折叠）或“false”（已展开）。

### <a name="link"></a>链接
在帮助页面中显示链接。

在新的浏览器窗口中打开的网站的链接：

```
<a href="https://www.microsoft.com" target="_blank">Microsoft Home Page</a>
```

另一个帮助页面的链接：

```
<a href="./LearnMore">Learn More</a>
```

#### <a name="definition-and-usage"></a>定义和使用
`<a>` 标记定义一个链接，该链接允许用户从帮助页面导航到网站或另一个帮助页面。

#### <a name="attributes"></a>属性

- `href`：指定要导航到的网站或帮助页面的 URL。 此属性是必需的。
- `target`：指定在何处打开链接的 URL。
   - 如果不存在或是 `_self`，则假定该链接指向另一个帮助页面，并在帮助浏览器中打开。
   - 如果是 `_blank`，则在新的浏览器窗口中打开链接。
   - 如果是 `_top`，则在当前的浏览器窗口中打开链接。
   - 如果值为 `iframe` 的名称，则在该 iframe 中打开链接。

### <a name="coach-mark"></a>指导标记
在帮助页面中显示指导标记。

```
<coachmark target="#my-html-button">Click to highlight the HTML element with id [my-html-button]</coachmark>
```

#### <a name="definition-and-usage"></a>定义和使用
指导标记是一个交互式元素，可用于将用户的注意力吸引到托管帮助浏览器的应用程序 UI 中的特定点。

#### <a name="attributes"></a>属性

- `target`：指定在其上显示指导标记的 HTML 元素的 [CSS 选择器](https://www.w3schools.com/cssref/css_selectors.asp)。 此属性是必需的。

### <a name="balloon"></a>提示框
在帮助页面中显示提示框。

```
<balloon target="#my-html-button" title="This button submits the form" details="Please click this button to continue and submit the form">Click to show a balloon over the HTML element with id [my-html-button]</balloon>
```

#### <a name="definition-and-usage"></a>定义和使用
提示框是一个交互式元素，可用于帮助用户在托管帮助浏览器的应用程序的 UI 中执行操作。

#### <a name="attributes"></a>属性
- `target`：指定在其上显示指导提示框链接的 HTML 元素的 CSS 选择器。 此属性是必需的。
- `title`：指定提示框的标题。
- `details`：指定要在提示框内显示的内容。


