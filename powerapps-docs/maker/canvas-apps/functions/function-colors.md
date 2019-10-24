---
title: Color 枚举与 ColorFade、ColorValue 以及 RGBA 函数 | Microsoft 文档
description: 有关 PowerApps 中的 Color 枚举与 ColorFade、ColorValue 以及 RGBA 函数的参考信息，包括语法和示例
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4af851160ea8a2add22add9f79dcc181a734e715
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "71994858"
---
# <a name="color-enumeration-and-colorfade-colorvalue-and-rgba-functions-in-powerapps"></a>PowerApps 中的 Color 枚举与 ColorFade、ColorValue 以及 RGBA 函数

使用内置颜色值，定义自定义颜色，并使用 alpha 通道。

## <a name="description"></a>描述

通过使用**颜色**枚举，你可以轻松地访问由 HTML 的级联样式表（CSS）定义的颜色。 例如， **red**返回纯红色。 可以在本主题末尾找到这些颜色的列表。

**ColorValue**函数基于 CSS 中的颜色字符串返回颜色。 该字符串可以采用以下任何形式：

- **CSS 颜色名称：** **"RoxyBrown"** 和 **"OliveDrab"** 。 这些名称不包括空格。 本主题稍后会显示支持的颜色的列表。
- **6 位十六进制值：** 例如， **"#ffd700"** 与 **"黄金"** 相同。 此字符串的格式为 "#*rrggbb*"，其中*rr*是两个十六进制数字中的红色部分， *gg*为绿色， *bb*为蓝色。
- **8 位十六进制值：** 例如， **"#ff7f5080"** 与具有 50% alpha 通道的 **"珊瑚"** 相同。 此字符串的格式为 "#*rrggbbaa*"，其中*rr*、 *gg*和*bb*与6位数字的格式相同。 Alpha 通道由*aa*： **00**表示完全透明，而**ff**表示完全不透明。

**RGBA**函数基于红色、绿色和蓝色分量返回颜色。 函数还包括一个 alpha 通道，用于混合彼此层叠的控件的颜色。 Alpha 通道的变化方式为0或0% （完全透明且不可见）到1或100% （这是完全不透明的，完全阻止控件后的任何层）。

**ColorFade** 函数返回更亮或更深的颜色版本。 淡化量的变化幅度为-1 （这会将颜色完全变暗为黑色）到0（这不会影响颜色）到1（这会将颜色完全变亮为白色）。

## <a name="alpha-channel"></a>Alpha 通道

在画布应用中，可以将控件彼此置于顶层，并为其后面的任何控件指定控件的透明度。 因此，颜色将与层混合。 例如，以下关系图显示了三种主要颜色如何混合为50%：

> [!div class="mx-imgBorder"]
> ![Three 主要颜色的 alpha 设置为 50% ](media/function-colors/alpha-primary.png)

您还可以将图像混合为支持 alpha 通道的文件格式。 例如，你无法混合 jpeg 文件，但你可以混合 .png 文件。 下图显示了上一示例中相同的红色、绿色和蓝色颜色，但红色显示为 50% alpha 通道的 .png 文件中的波形曲线（而不是圆圈）：

> [!div class="mx-imgBorder"]
> 在蓝色和绿色圆圈的前面加上50% 的 alpha 设置 ![Red 波浪线 ](media/function-colors/alpha-image.png)

如果指定了**颜色**枚举值，或者使用颜色名称或6位十六进制值生成**ColorValue**公式，则 alpha 设置为100%，这是完全不透明的。

## <a name="syntax"></a>语法

**Color**.*ColorName*

- *ColorName* - 必需。  级联样式表 (CSS) 颜色名称。 可能的枚举值列表显示在本主题的结尾。

**ColorValue**(*CSSColor*)

- *CSSColor* - 必需。  级联样式表 (CSS) 颜色定义。 可以指定名称（如**OliveDrab**）或十六进制值，例如 **#6b8e23**或 **#7fffd420**。 十六进制值可以采用 #*rrggbb*或 #*rrggbbaa*的形式。

**RGBA**(*Red*, *Green*, *Blue*, *Alpha*)

- *Red*、*Green*、*Blue* - 必需。  颜色分量值，范围从0（无饱和度）到255（完全饱和度）。
- *Alpha* - 必需。  Alpha 分量，范围为0（完全透明）到1（完全不透明）。 还可以使用百分比（0% 到 100%）。

**ColorFade**(*Color*, *FadeAmount*)

- *Color* - 必需。  颜色值（如 **Color.Red**），或者 **ColorValue** 或 **RGBA** 的输出。
- *FadeAmount* - 必需。  介于 -1 和 1 之间的数字。 -1 将颜色完全变暗为黑色，0不会影响颜色，1会将颜色完全变亮为白色。 还可以使用-100% 到100% 之间的百分比。

## <a name="built-in-colors"></a>内置颜色

| Color 枚举 | ColorValue | RGBA | 颜色样本 |
| --- | --- | --- | --- |
| **Color.AliceBlue** |**ColorValue （"#f0f8ff" &nbsp;）**<br>**ColorValue （"aliceblue" &nbsp;）** |**RGBA （&nbsp;240、&nbsp;248、&nbsp;255 &nbsp;1 &nbsp;）** |![艾丽斯蓝](./media/function-colors/color-aliceblue.png) |
| **Color.AntiqueWhite** |**ColorValue （"#faebd7" &nbsp;）**<br>**ColorValue （"AntiqueWhite" &nbsp;）** |**RGBA （&nbsp;250、&nbsp;235、&nbsp;215 &nbsp;1 &nbsp;）** |![古董白](./media/function-colors/color-antiquewhite.png) |
| **Color.Aqua** |**ColorValue （"#00ffff" &nbsp;）**<br>**ColorValue （"水绿色" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;255、&nbsp;255 &nbsp;1 &nbsp;）** |![浅绿色](./media/function-colors/color-aqua.png) |
| **Color.Aquamarine** |**ColorValue （"#7fffd4" &nbsp;）**<br>**ColorValue （"碧绿色" &nbsp;）** |**RGBA （&nbsp;127、&nbsp;255、&nbsp;212 &nbsp;1 &nbsp;）** |![水绿色](./media/function-colors/color-aquamarine.png) |
| **Color.Azure** |**ColorValue （"#f0ffff" &nbsp;）**<br>**ColorValue （"azure" &nbsp;）** |**RGBA （&nbsp;240、&nbsp;255、&nbsp;255 &nbsp;1 &nbsp;）** |![天蓝色](./media/function-colors/color-azure.png) |
| **Color.Beige** |**ColorValue （"#f5f5dc" &nbsp;）**<br>**ColorValue （"米色" &nbsp;）** |**RGBA （&nbsp;245、&nbsp;245、&nbsp;220 &nbsp;1 &nbsp;）** |![米黄色](./media/function-colors/color-beige.png) |
| **Color.Bisque** |**ColorValue （"#ffe4c4" &nbsp;）**<br>**ColorValue （"BISQUE" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;228、&nbsp;196 &nbsp;1 &nbsp;）** |![橘黄色](./media/function-colors/color-bisque.png) |
| **Color.Black** |**ColorValue （"#000000" &nbsp;）**<br>**ColorValue （"黑色" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;0、&nbsp;0 &nbsp;1 &nbsp;）** |![黑色](./media/function-colors/color-black.png) |
| **Color.BlanchedAlmond** |**ColorValue （"#ffebcd" &nbsp;）**<br>**ColorValue （"blanchedalmond" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;235、&nbsp;205 &nbsp;1 &nbsp;）** |![白杏色](./media/function-colors/color-blanchedalmond.png) |
| **Color.Blue** |**ColorValue （"#0000ff" &nbsp;）**<br>**ColorValue （"Blue" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;0、&nbsp;255 &nbsp;1 &nbsp;）** |![蓝色](./media/function-colors/color-blue.png) |
| **Color.BlueViolet** |**ColorValue （"#8a2be2" &nbsp;）**<br>**ColorValue （"BLUEVIOLET" &nbsp;）** |**RGBA （&nbsp;138、&nbsp;43、&nbsp;226 &nbsp;1 &nbsp;）** |![蓝紫色](./media/function-colors/color-blueviolet.png) |
| **Color.Brown** |**ColorValue （"#a52a2a" &nbsp;）**<br>**ColorValue （"棕色" &nbsp;）** |**RGBA （&nbsp;165、&nbsp;42、&nbsp;42 &nbsp;1 &nbsp;）** |![棕色](./media/function-colors/color-brown.png) |
| **Color.Burlywood** |**ColorValue （"#deb887" &nbsp;）**<br>**ColorValue （"color.burlywood" &nbsp;）** |**RGBA （&nbsp;222、&nbsp;184、&nbsp;135 &nbsp;1 &nbsp;）** |![实木色](./media/function-colors/color-burlywood.png) |
| **Color.CadetBlue** |**ColorValue （"#5f9ea0" &nbsp;）**<br>**ColorValue （"CadetBlue" &nbsp;）** |**RGBA （&nbsp;95、&nbsp;158、&nbsp;160 &nbsp;1 &nbsp;）** |![军蓝色](./media/function-colors/color-cadetblue.png) |
| **Color.Chartreuse** |**ColorValue （"#7fff00" &nbsp;）**<br>**ColorValue （"CHARTREUSE" &nbsp;）** |**RGBA （&nbsp;127、&nbsp;255、&nbsp;0 &nbsp;1 &nbsp;）** |![黄绿色](./media/function-colors/color-chartreuse.png) |
| **Color.Chocolate** |**ColorValue （"#d2691e" &nbsp;）**<br>**ColorValue （"巧克力" &nbsp;）** |**RGBA （&nbsp;210、&nbsp;105、&nbsp;30 &nbsp;1 &nbsp;）** |![巧克力色](./media/function-colors/color-chocolate.png) |
| **Color.Coral** |**ColorValue （"#ff7f50" &nbsp;）**<br>**ColorValue （"珊瑚" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;127、&nbsp;80 &nbsp;1 &nbsp;）** |![珊瑚色](./media/function-colors/color-coral.png) |
| **Color.CornflowerBlue** |**ColorValue （"#6495ed" &nbsp;）**<br>**ColorValue （"CornflowerBlue" &nbsp;）** |**RGBA （&nbsp;100、&nbsp;149、&nbsp;237 &nbsp;1 &nbsp;）** |![菊蓝色](./media/function-colors/color-cornflowerblue.png) |
| **Color.Cornsilk** |**ColorValue （"#fff8dc" &nbsp;）**<br>**ColorValue （"CORNSILK" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;248、&nbsp;220 &nbsp;1 &nbsp;）** |![玉米丝色](./media/function-colors/color-cornsilk.png) |
| **Color.Crimson** |**ColorValue （"#dc143c" &nbsp;）**<br>**ColorValue （"Crimson" &nbsp;）** |**RGBA （&nbsp;220、&nbsp;20、&nbsp;60 &nbsp;1 &nbsp;）** |![深红色](./media/function-colors/color-crimson.png) |
| **Color.Cyan** |**ColorValue （"#00ffff" &nbsp;）**<br>**ColorValue （"青色" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;255、&nbsp;255 &nbsp;1 &nbsp;）** |![蓝绿色](./media/function-colors/color-cyan.png) |
| **Color.DarkBlue** |**ColorValue （"#00008b" &nbsp;）**<br>**ColorValue （"DarkBlue" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;0、&nbsp;139 &nbsp;1 &nbsp;）** |![深蓝色](./media/function-colors/color-darkblue.png) |
| **Color.DarkCyan** |**ColorValue （"#008b8b" &nbsp;）**<br>**ColorValue （"DARKCYAN" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;139、&nbsp;139 &nbsp;1 &nbsp;）** |![深青绿](./media/function-colors/color-darkcyan.png) |
| **Color.DarkGoldenRod** |**ColorValue （"#b8860b" &nbsp;）**<br>**ColorValue （"DarkGoldenRod" &nbsp;）** |**RGBA （&nbsp;184、&nbsp;134、&nbsp;11 &nbsp;1 &nbsp;）** |![暗金黄色](./media/function-colors/color-darkgoldenrod.png) |
| **Color.DarkGray** |**ColorValue （"#a9a9a9" &nbsp;）**<br>**ColorValue （"深灰" &nbsp;）** |**RGBA （&nbsp;169、&nbsp;169、&nbsp;169 &nbsp;1 &nbsp;）** |![深灰色](./media/function-colors/color-darkgray.png) |
| **Color.DarkGreen** |**ColorValue （"#006400" &nbsp;）**<br>**ColorValue （"DarkGreen" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;100、&nbsp;0 &nbsp;1 &nbsp;）** |![深绿色](./media/function-colors/color-darkgreen.png) |
| **Color.DarkGrey** |**ColorValue （"#a9a9a9" &nbsp;）**<br>**ColorValue （"DARKGREY" &nbsp;）** |**RGBA （&nbsp;169、&nbsp;169、&nbsp;169 &nbsp;1 &nbsp;）** |![深灰色](./media/function-colors/color-darkgrey.png) |
| **Color.DarkKhaki** |**ColorValue （"#bdb76b" &nbsp;）**<br>**ColorValue （"DarkKhaki" &nbsp;）** |**RGBA （&nbsp;189、&nbsp;183、&nbsp;107 &nbsp;1 &nbsp;）** |![深褐色](./media/function-colors/color-darkkhaki.png) |
| **Color.DarkMagenta** |**ColorValue （"#8b008b" &nbsp;）**<br>**ColorValue （"darkmagenta" &nbsp;）** |**RGBA （&nbsp;139、&nbsp;0、&nbsp;139 &nbsp;1 &nbsp;）** |![深洋红色](./media/function-colors/color-darkmagenta.png) |
| **Color.DarkOliveGreen** |**ColorValue （"#556b2f" &nbsp;）**<br>**ColorValue （"DarkOliveGreen" &nbsp;）** |**RGBA （&nbsp;85、&nbsp;107、&nbsp;47 &nbsp;1 &nbsp;）** |![深橄榄绿色](./media/function-colors/color-darkolivegreen.png) |
| **Color.DarkOrange** |**ColorValue （"#ff8c00" &nbsp;）**<br>**ColorValue （"DARKORANGE" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;140、&nbsp;0 &nbsp;1 &nbsp;）** |![深橙色](./media/function-colors/color-darkorange.png) |
| **Color.DarkOrchid** |**ColorValue （"#9932cc" &nbsp;）**<br>**ColorValue （"DarkOrchid" &nbsp;）** |**RGBA （&nbsp;153、&nbsp;50、&nbsp;204 &nbsp;1 &nbsp;）** |![深紫色](./media/function-colors/color-darkorchid.png) |
| **Color.DarkRed** |**ColorValue （"#8b0000" &nbsp;）**<br>**ColorValue （"darkred" &nbsp;）** |**RGBA （&nbsp;139、&nbsp;0、&nbsp;0 &nbsp;1 &nbsp;）** |![深红色](./media/function-colors/color-darkred.png) |
| **Color.DarkSalmon** |**ColorValue （"#e9967a" &nbsp;）**<br>**ColorValue （"DarkSalmon" &nbsp;）** |**RGBA （&nbsp;233、&nbsp;150、&nbsp;122 &nbsp;1 &nbsp;）** |![深橙红色](./media/function-colors/color-darksalmon.png) |
| **Color.DarkSeaGreen** |**ColorValue （"#8fbc8f" &nbsp;）**<br>**ColorValue （"DARKSEAGREEN" &nbsp;）** |**RGBA （&nbsp;143、&nbsp;188、&nbsp;143 &nbsp;1 &nbsp;）** |![深海绿色](./media/function-colors/color-darkseagreen.png) |
| **Color.DarkSlateBlue** |**ColorValue （"#483d8b" &nbsp;）**<br>**ColorValue （"DarkSlateBlue" &nbsp;）** |**RGBA （&nbsp;72、&nbsp;61、&nbsp;139 &nbsp;1 &nbsp;）** |![深石板蓝色](./media/function-colors/color-darkslateblue.png) |
| **Color.DarkSlateGray** |**ColorValue （"#2f4f4f" &nbsp;）**<br>**ColorValue （"darkslategray" &nbsp;）** |**RGBA （&nbsp;47、&nbsp;79、&nbsp;79 &nbsp;1 &nbsp;）** |![深石板灰色](./media/function-colors/color-darkslategray.png) |
| **Color.DarkSlateGrey** |**ColorValue （"#2f4f4f" &nbsp;）**<br>**ColorValue （"DarkSlateGrey" &nbsp;）** |**RGBA （&nbsp;47、&nbsp;79、&nbsp;79 &nbsp;1 &nbsp;）** |![深石板灰色](./media/function-colors/color-darkslategrey.png) |
| **Color.DarkTurquoise** |**ColorValue （"#00ced1" &nbsp;）**<br>**ColorValue （"DARKTURQUOISE" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;206、&nbsp;209 &nbsp;1 &nbsp;）** |![深宝石绿色](./media/function-colors/color-darkturquoise.png) |
| **Color.DarkViolet** |**ColorValue （"#9400d3" &nbsp;）**<br>**ColorValue （"DarkViolet" &nbsp;）** |**RGBA （&nbsp;148、&nbsp;0、&nbsp;211 &nbsp;1 &nbsp;）** |![深紫色](./media/function-colors/color-darkviolet.png) |
| **Color.DeepPink** |**ColorValue （"#ff1493" &nbsp;）**<br>**ColorValue （"deeppink" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;20、&nbsp;147 &nbsp;1 &nbsp;）** |![深粉色](./media/function-colors/color-deeppink.png) |
| **Color.DeepSkyBlue** |**ColorValue （"#00bfff" &nbsp;）**<br>**ColorValue （"DeepSkyBlue" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;191、&nbsp;255 &nbsp;1 &nbsp;）** |![深天蓝色](./media/function-colors/color-deepskyblue.png) |
| **Color.DimGray** |**ColorValue （"#696969" &nbsp;）**<br>**ColorValue （"DIMGRAY" &nbsp;）** |**RGBA （&nbsp;105、&nbsp;105、&nbsp;105 &nbsp;1 &nbsp;）** |![暗灰色](./media/function-colors/color-dimgray.png) |
| **Color.DimGrey** |**ColorValue （"#696969" &nbsp;）**<br>**ColorValue （"DimGrey" &nbsp;）** |**RGBA （&nbsp;105、&nbsp;105、&nbsp;105 &nbsp;1 &nbsp;）** |![暗灰色](./media/function-colors/color-dimgrey.png) |
| **Color.DodgerBlue** |**ColorValue （"#1e90ff" &nbsp;）**<br>**ColorValue （"dodgerblue" &nbsp;）** |**RGBA （&nbsp;30、&nbsp;144、&nbsp;255 &nbsp;1 &nbsp;）** |![闪蓝色](./media/function-colors/color-dodgerblue.png) |
| **Color.FireBrick** |**ColorValue （"#b22222" &nbsp;）**<br>**ColorValue （"FireBrick" &nbsp;）** |**RGBA （&nbsp;178、&nbsp;34、&nbsp;34 &nbsp;1 &nbsp;）** |![火砖色](./media/function-colors/color-firebrick.png) |
| **Color.FloralWhite** |**ColorValue （"#fffaf0" &nbsp;）**<br>**ColorValue （"FLORALWHITE" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;250、&nbsp;240 &nbsp;1 &nbsp;）** |![花白色](./media/function-colors/color-floralwhite.png) |
| **Color.ForestGreen** |**ColorValue （"#228b22" &nbsp;）**<br>**ColorValue （"ForestGreen" &nbsp;）** |**RGBA （&nbsp;34、&nbsp;139、&nbsp;34 &nbsp;1 &nbsp;）** |![森林绿](./media/function-colors/color-forestgreen.png) |
| **Color.Fuchsia** |**ColorValue （"#ff00ff" &nbsp;）**<br>**ColorValue （"fuchsia" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;0、&nbsp;255 &nbsp;1 &nbsp;）** |![紫红色](./media/function-colors/color-fuchsia.png) |
| **Color.Gainsboro** |**ColorValue （"#dcdcdc" &nbsp;）**<br>**ColorValue （"Gainsboro" &nbsp;）** |**RGBA （&nbsp;220、&nbsp;220、&nbsp;220 &nbsp;1 &nbsp;）** |![亮灰色](./media/function-colors/color-gainsboro.png) |
| **Color.GhostWhite** |**ColorValue （"#f8f8ff" &nbsp;）**<br>**ColorValue （"GHOSTWHITE" &nbsp;）** |**RGBA （&nbsp;248、&nbsp;248、&nbsp;255 &nbsp;1 &nbsp;）** |![幽灵白色](./media/function-colors/color-ghostwhite.png) |
| **Color.Gold** |**ColorValue （"#ffd700" &nbsp;）**<br>**ColorValue （"黄金" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;215、&nbsp;0 &nbsp;1 &nbsp;）** |![金色](./media/function-colors/color-gold.png) |
| **Color.GoldenRod** |**ColorValue （"#daa520" &nbsp;）**<br>**ColorValue （"金黄色" &nbsp;）** |**RGBA （&nbsp;218、&nbsp;165、&nbsp;32 &nbsp;1 &nbsp;）** |![金麒麟色](./media/function-colors/color-goldenrod.png) |
| **Color.Gray** |**ColorValue （"#808080" &nbsp;）**<br>**ColorValue （"灰色" &nbsp;）** |**RGBA （&nbsp;128、&nbsp;128、&nbsp;128 &nbsp;1 &nbsp;）** |![灰色](./media/function-colors/color-gray.png) |
| **Color.Green** |**ColorValue （"#008000" &nbsp;）**<br>**ColorValue （"绿色" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;128、&nbsp;0 &nbsp;1 &nbsp;）** |![绿色](./media/function-colors/color-green.png) |
| **Color.GreenYellow** |**ColorValue （"#adff2f" &nbsp;）**<br>**ColorValue （"GreenYellow" &nbsp;）** |**RGBA （&nbsp;173、&nbsp;255、&nbsp;47 &nbsp;1 &nbsp;）** |![黄绿色](./media/function-colors/color-greenyellow.png) |
| **Color.Grey** |**ColorValue （"#808080" &nbsp;）**<br>**ColorValue （"灰色" &nbsp;）** |**RGBA （&nbsp;128、&nbsp;128、&nbsp;128 &nbsp;1 &nbsp;）** |![灰色](./media/function-colors/color-grey.png) |
| **Color.Honeydew** |**ColorValue （"#f0fff0" &nbsp;）**<br>**ColorValue （"甜瓜" &nbsp;）** |**RGBA （&nbsp;240、&nbsp;255、&nbsp;240 &nbsp;1 &nbsp;）** |![蜜色](./media/function-colors/color-honeydew.png) |
| **Color.HotPink** |**ColorValue （"#ff69b4" &nbsp;）**<br>**ColorValue （"HOTPINK" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;105、&nbsp;180 &nbsp;1 &nbsp;）** |![艳粉色](./media/function-colors/color-hotpink.png) |
| **Color.IndianRed** |**ColorValue （"#cd5c5c" &nbsp;）**<br>**ColorValue （"IndianRed" &nbsp;）** |**RGBA （&nbsp;205、&nbsp;92、&nbsp;92 &nbsp;1 &nbsp;）** |![印度红](./media/function-colors/color-indianred.png) |
| **Color.Indigo** |**ColorValue （"#4b0082" &nbsp;）**<br>**ColorValue （"靛蓝色" &nbsp;）** |**RGBA （&nbsp;75、&nbsp;0、&nbsp;130 &nbsp;1 &nbsp;）** |![靛蓝色](./media/function-colors/color-indigo.png) |
| **Color.Ivory** |**ColorValue （"#fffff0" &nbsp;）**<br>**ColorValue （"象牙塔" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;255、&nbsp;240 &nbsp;1 &nbsp;）** |![乳白色](./media/function-colors/color-ivory.png) |
| **Color.Khaki** |**ColorValue （"#f0e68c" &nbsp;）**<br>**ColorValue （"深褐色" &nbsp;）** |**RGBA （&nbsp;240、&nbsp;230、&nbsp;140 &nbsp;1 &nbsp;）** |![卡其色](./media/function-colors/color-khaki.png) |
| **Color.Lavender** |**ColorValue （"#e6e6fa" &nbsp;）**<br>**ColorValue （"紫色" &nbsp;）** |**RGBA （&nbsp;230、&nbsp;230、&nbsp;250 &nbsp;1 &nbsp;）** |![淡紫色](./media/function-colors/color-lavender.png) |
| **Color.LavenderBlush** |**ColorValue （"#fff0f5" &nbsp;）**<br>**ColorValue （"lavenderblush" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;240、&nbsp;245 &nbsp;1 &nbsp;）** |![浅紫红色](./media/function-colors/color-lavenderblush.png) |
| **Color.LawnGreen** |**ColorValue （"#7cfc00" &nbsp;）**<br>**ColorValue （"LawnGreen" &nbsp;）** |**RGBA （&nbsp;124、&nbsp;252、&nbsp;0 &nbsp;1 &nbsp;）** |![草绿色](./media/function-colors/color-lawngreen.png) |
| **Color.LemonChiffon** |**ColorValue （"#fffacd" &nbsp;）**<br>**ColorValue （"LEMONCHIFFON" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;250、&nbsp;205 &nbsp;1 &nbsp;）** |![柠檬绸色](./media/function-colors/color-lemonchiffon.png) |
| **Color.LightBlue** |**ColorValue （"#add8e6" &nbsp;）**<br>**ColorValue （"LightBlue" &nbsp;）** |**RGBA （&nbsp;173、&nbsp;216、&nbsp;230 &nbsp;1 &nbsp;）** |![淡蓝色](./media/function-colors/color-lightblue.png) |
| **Color.LightCoral** |**ColorValue （"#f08080" &nbsp;）**<br>**ColorValue （"lightcoral" &nbsp;）** |**RGBA （&nbsp;240、&nbsp;128、&nbsp;128 &nbsp;1 &nbsp;）** |![浅珊瑚色](./media/function-colors/color-lightcoral.png) |
| **Color.LightCyan** |**ColorValue （"#e0ffff" &nbsp;）**<br>**ColorValue （"LightCyan" &nbsp;）** |**RGBA （&nbsp;224、&nbsp;255、&nbsp;255 &nbsp;1 &nbsp;）** |![浅青色](./media/function-colors/color-lightcyan.png) |
| **Color.LightGoldenRodYellow** |**ColorValue （"#fafad2" &nbsp;）**<br>**ColorValue （"lightgoldenrodyellow" &nbsp;）** |**RGBA （&nbsp;250、&nbsp;250、&nbsp;210 &nbsp;1 &nbsp;）** |![浅金黄色](./media/function-colors/color-lightgoldenrodyellow.png) |
| **Color.LightGray** |**ColorValue （"#d3d3d3" &nbsp;）**<br>**ColorValue （"LightGray" &nbsp;）** |**RGBA （&nbsp;211、&nbsp;211、&nbsp;211 &nbsp;1 &nbsp;）** |![浅灰色](./media/function-colors/color-lightgray.png) |
| **Color.LightGreen** |**ColorValue （"#90ee90" &nbsp;）**<br>**ColorValue （"lightgreen" &nbsp;）** |**RGBA （&nbsp;144、&nbsp;238、&nbsp;144 &nbsp;1 &nbsp;）** |![浅绿色](./media/function-colors/color-lightgreen.png) |
| **Color.LightGrey** |**ColorValue （"#d3d3d3" &nbsp;）**<br>**ColorValue （"LightGrey" &nbsp;）** |**RGBA （&nbsp;211、&nbsp;211、&nbsp;211 &nbsp;1 &nbsp;）** |![浅灰色](./media/function-colors/color-lightgrey.png) |
| **Color.LightPink** |**ColorValue （"#ffb6c1" &nbsp;）**<br>**ColorValue （"LIGHTPINK" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;182、&nbsp;193 &nbsp;1 &nbsp;）** |![浅粉色](./media/function-colors/color-lightpink.png) |
| **Color.LightSalmon** |**ColorValue （"#ffa07a" &nbsp;）**<br>**ColorValue （"LightSalmon" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;160、&nbsp;122 &nbsp;1 &nbsp;）** |![浅肉色](./media/function-colors/color-lightsalmon.png) |
| **Color.LightSeaGreen** |**ColorValue （"#20b2aa" &nbsp;）**<br>**ColorValue （"color.lightseagreen" &nbsp;）** |**RGBA （&nbsp;32、&nbsp;178、&nbsp;170 &nbsp;1 &nbsp;）** |![浅海蓝色](./media/function-colors/color-lightseagreen.png) |
| **Color.LightSkyBlue** |**ColorValue （"#87cefa" &nbsp;）**<br>**ColorValue （"LightSkyBlue" &nbsp;）** |**RGBA （&nbsp;135、&nbsp;206、&nbsp;250 &nbsp;1 &nbsp;）** |![浅天蓝色](./media/function-colors/color-lightskyblue.png) |
| **Color.LightSlateGray** |**ColorValue （"#778899" &nbsp;）**<br>**ColorValue （"LIGHTSLATEGRAY" &nbsp;）** |**RGBA （&nbsp;119、&nbsp;136、&nbsp;153 &nbsp;1 &nbsp;）** |![浅石板灰色](./media/function-colors/color-lightslategray.png) |
| **Color.LightSlateGrey** |**ColorValue （"#778899" &nbsp;）**<br>**ColorValue （"LightSlateGrey" &nbsp;）** |**RGBA （&nbsp;119、&nbsp;136、&nbsp;153 &nbsp;1 &nbsp;）** |![浅石板灰色](./media/function-colors/color-lightslategrey.png) |
| **Color.LightSteelBlue** |**ColorValue （"#b0c4de" &nbsp;）**<br>**ColorValue （"lightsteelblue" &nbsp;）** |**RGBA （&nbsp;176、&nbsp;196、&nbsp;222 &nbsp;1 &nbsp;）** |![浅钢蓝色](./media/function-colors/color-lightsteelblue.png) |
| **Color.LightYellow** |**ColorValue （"#ffffe0" &nbsp;）**<br>**ColorValue （"LightYellow" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;255、&nbsp;224 &nbsp;1 &nbsp;）** |![浅黄色](./media/function-colors/color-lightyellow.png) |
| **Color.Lime** |**ColorValue （"#00ff00" &nbsp;）**<br>**ColorValue （"酸橙色" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;255、&nbsp;0 &nbsp;1 &nbsp;）** |![酸橙色](./media/function-colors/color-lime.png) |
| **Color.LimeGreen** |**ColorValue （"#32cd32" &nbsp;）**<br>**ColorValue （"LimeGreen" &nbsp;）** |**RGBA （&nbsp;50、&nbsp;205、&nbsp;50 &nbsp;1 &nbsp;）** |![橙绿色](./media/function-colors/color-limegreen.png) |
| **Color.Linen** |**ColorValue （"#faf0e6" &nbsp;）**<br>**ColorValue （"linen" &nbsp;）** |**RGBA （&nbsp;250、&nbsp;240、&nbsp;230 &nbsp;1 &nbsp;）** |![亚麻色](./media/function-colors/color-linen.png) |
| **Color.Magenta** |**ColorValue （"#ff00ff" &nbsp;）**<br>**ColorValue （"品红" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;0、&nbsp;255 &nbsp;1 &nbsp;）** |![洋红色](./media/function-colors/color-magenta.png) |
| **Color.Maroon** |**ColorValue （"#800000" &nbsp;）**<br>**ColorValue （"褐紫红色" &nbsp;）** |**RGBA （&nbsp;128、&nbsp;0、&nbsp;0 &nbsp;1 &nbsp;）** |![褐红色](./media/function-colors/color-maroon.png) |
| **Color.MediumAquamarine** |**ColorValue （"#66cdaa" &nbsp;）**<br>**ColorValue （"MediumAquamarine" &nbsp;）** |**RGBA （&nbsp;102、&nbsp;205、&nbsp;170 &nbsp;1 &nbsp;）** |![中碧绿色](./media/function-colors/color-mediumaquamarine.png) |
| **Color.MediumBlue** |**ColorValue （"#0000cd" &nbsp;）**<br>**ColorValue （"mediumblue" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;0、&nbsp;205 &nbsp;1 &nbsp;）** |![中蓝色](./media/function-colors/color-mediumblue.png) |
| **Color.MediumOrchid** |**ColorValue （"#ba55d3" &nbsp;）**<br>**ColorValue （"MediumOrchid" &nbsp;）** |**RGBA （&nbsp;186、&nbsp;85、&nbsp;211 &nbsp;1 &nbsp;）** |![中兰花紫](./media/function-colors/color-mediumorchid.png) |
| **Color.MediumPurple** |**ColorValue （"#9370db" &nbsp;）**<br>**ColorValue （"MEDIUMPURPLE" &nbsp;）** |**RGBA （&nbsp;147、&nbsp;112、&nbsp;219 &nbsp;1 &nbsp;）** |![中紫色](./media/function-colors/color-mediumpurple.png) |
| **Color.MediumSeaGreen** |**ColorValue （"#3cb371" &nbsp;）**<br>**ColorValue （"MediumSeaGreen" &nbsp;）** |**RGBA （&nbsp;60、&nbsp;179、&nbsp;113 &nbsp;1 &nbsp;）** |![中海绿色](./media/function-colors/color-mediumseagreen.png) |
| **Color.MediumSlateBlue** |**ColorValue （"#7b68ee" &nbsp;）**<br>**ColorValue （"mediumslateblue" &nbsp;）** |**RGBA （&nbsp;123、&nbsp;104、&nbsp;238 &nbsp;1 &nbsp;）** |![中灰蓝色](./media/function-colors/color-mediumslateblue.png) |
| **Color.MediumSpringGreen** |**ColorValue （"#00fa9a" &nbsp;）**<br>**ColorValue （"MediumSpringGreen" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;250、&nbsp;154 &nbsp;1 &nbsp;）** |![中春绿色](./media/function-colors/color-mediumspringgreen.png) |
| **Color.MediumTurquoise** |**ColorValue （"#48d1cc" &nbsp;）**<br>**ColorValue （"MEDIUMTURQUOISE" &nbsp;）** |**RGBA （&nbsp;72、&nbsp;209、&nbsp;204 &nbsp;1 &nbsp;）** |![中蓝绿色](./media/function-colors/color-mediumturquoise.png) |
| **Color.MediumVioletRed** |**ColorValue （"#c71585" &nbsp;）**<br>**ColorValue （"MediumVioletRed" &nbsp;）** |**RGBA （&nbsp;199、&nbsp;21、&nbsp;133 &nbsp;1 &nbsp;）** |![中紫罗兰色](./media/function-colors/color-mediumvioletred.png) |
| **Color.MidnightBlue** |**ColorValue （"#191970" &nbsp;）**<br>**ColorValue （"midnightblue" &nbsp;）** |**RGBA （&nbsp;25、&nbsp;25、&nbsp;112 &nbsp;1 &nbsp;）** |![午夜蓝色](./media/function-colors/color-midnightblue.png) |
| **Color.MintCream** |**ColorValue （"#f5fffa" &nbsp;）**<br>**ColorValue （"MintCream" &nbsp;）** |**RGBA （&nbsp;245、&nbsp;255、&nbsp;250 &nbsp;1 &nbsp;）** |![薄荷奶油色](./media/function-colors/color-mintcream.png) |
| **Color.MistyRose** |**ColorValue （"#ffe4e1" &nbsp;）**<br>**ColorValue （"MISTYROSE" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;228、&nbsp;225 &nbsp;1 &nbsp;）** |![雾中玫瑰色](./media/function-colors/color-mistyrose.png) |
| **Color.Moccasin** |**ColorValue （"#ffe4b5" &nbsp;）**<br>**ColorValue （"Moccasin" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;228、&nbsp;181 &nbsp;1 &nbsp;）** |![鹿皮色](./media/function-colors/color-moccasin.png) |
| **Color.NavajoWhite** |**ColorValue （"#ffdead" &nbsp;）**<br>**ColorValue （"navajowhite" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;222、&nbsp;173 &nbsp;1 &nbsp;）** |![纳瓦白色](./media/function-colors/color-navajowhite.png) |
| **Color.Navy** |**ColorValue （"#000080" &nbsp;）**<br>**ColorValue （"深蓝色" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;0、&nbsp;128 &nbsp;1 &nbsp;）** |![深蓝色](./media/function-colors/color-navy.png) |
| **Color.OldLace** |**ColorValue （"#fdf5e6" &nbsp;）**<br>**ColorValue （"OLDLACE" &nbsp;）** |**RGBA （&nbsp;253、&nbsp;245、&nbsp;230 &nbsp;1 &nbsp;）** |![老花色](./media/function-colors/color-oldlace.png) |
| **Color.Olive** |**ColorValue （"#808000" &nbsp;）**<br>**ColorValue （"橄榄色" &nbsp;）** |**RGBA （&nbsp;128、&nbsp;128、&nbsp;0 &nbsp;1 &nbsp;）** |![橄榄色](./media/function-colors/color-olive.png) |
| **Color.OliveDrab** |**ColorValue （"#6b8e23" &nbsp;）**<br>**ColorValue （"olivedrab" &nbsp;）** |**RGBA （&nbsp;107、&nbsp;142、&nbsp;35 &nbsp;1 &nbsp;）** |![橄榄土褐色](./media/function-colors/color-olivedrab.png) |
| **Color.Orange** |**ColorValue （"#ffa500" &nbsp;）**<br>**ColorValue （"橙色" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;165、&nbsp;0 &nbsp;1 &nbsp;）** |![橙色](./media/function-colors/color-orange.png) |
| **Color.OrangeRed** |**ColorValue （"#ff4500" &nbsp;）**<br>**ColorValue （"ORANGERED" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;69、&nbsp;0 &nbsp;1 &nbsp;）** |![橙红色](./media/function-colors/color-orangered.png) |
| **Color.Orchid** |**ColorValue （"#da70d6" &nbsp;）**<br>**ColorValue （"兰花" &nbsp;）** |**RGBA （&nbsp;218、&nbsp;112、&nbsp;214 &nbsp;1 &nbsp;）** |![兰花紫](./media/function-colors/color-orchid.png) |
| **Color.PaleGoldenRod** |**ColorValue （"#eee8aa" &nbsp;）**<br>**ColorValue （"palegoldenrod" &nbsp;）** |**RGBA （&nbsp;238、&nbsp;232、&nbsp;170 &nbsp;1 &nbsp;）** |![淡菊黄色](./media/function-colors/color-palegoldenrod.png) |
| **Color.PaleGreen** |**ColorValue （"#98fb98" &nbsp;）**<br>**ColorValue （"PaleGreen" &nbsp;）** |**RGBA （&nbsp;152、&nbsp;251、&nbsp;152 &nbsp;1 &nbsp;）** |![苍绿色](./media/function-colors/color-palegreen.png) |
| **Color.PaleTurquoise** |**ColorValue （"#afeeee" &nbsp;）**<br>**ColorValue （"PALETURQUOISE" &nbsp;）** |**RGBA （&nbsp;175、&nbsp;238、&nbsp;238 &nbsp;1 &nbsp;）** |![苍宝石绿色](./media/function-colors/color-paleturquoise.png) |
| **Color.PaleVioletRed** |**ColorValue （"#db7093" &nbsp;）**<br>**ColorValue （"PaleVioletRed" &nbsp;）** |**RGBA （&nbsp;219、&nbsp;112、&nbsp;147 &nbsp;1 &nbsp;）** |![苍紫罗蓝色](./media/function-colors/color-palevioletred.png) |
| **Color.PapayaWhip** |**ColorValue （"#ffefd5" &nbsp;）**<br>**ColorValue （"papayawhip" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;239、&nbsp;213 &nbsp;1 &nbsp;）** |![番木色](./media/function-colors/color-papayawhip.png) |
| **Color.PeachPuff** |**ColorValue （"#ffdab9" &nbsp;）**<br>**ColorValue （"PeachPuff" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;218、&nbsp;185 &nbsp;1 &nbsp;）** |![桃肉色](./media/function-colors/color-peachpuff.png) |
| **Color.Peru** |**ColorValue （"#cd853f" &nbsp;）**<br>**ColorValue （"秘鲁" &nbsp;）** |**RGBA （&nbsp;205、&nbsp;133、&nbsp;63 &nbsp;1 &nbsp;）** |![秘鲁棕色](./media/function-colors/color-peru.png) |
| **Color.Pink** |**ColorValue （"#ffc0cb" &nbsp;）**<br>**ColorValue （"粉色" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;192、&nbsp;203 &nbsp;1 &nbsp;）** |![粉红色](./media/function-colors/color-pink.png) |
| **Color.Plum** |**ColorValue （"#dda0dd" &nbsp;）**<br>**ColorValue （"plum" &nbsp;）** |**RGBA （&nbsp;221、&nbsp;160、&nbsp;221 &nbsp;1 &nbsp;）** |![梅红色](./media/function-colors/color-plum.png) |
| **Color.PowderBlue** |**ColorValue （"#b0e0e6" &nbsp;）**<br>**ColorValue （"PowderBlue" &nbsp;）** |**RGBA （&nbsp;176、&nbsp;224、&nbsp;230 &nbsp;1 &nbsp;）** |![粉蓝色](./media/function-colors/color-powderblue.png) |
| **Color.Purple** |**ColorValue （"#800080" &nbsp;）**<br>**ColorValue （"紫色" &nbsp;）** |**RGBA （&nbsp;128、&nbsp;0、&nbsp;128 &nbsp;1 &nbsp;）** |![紫色](./media/function-colors/color-purple.png) |
| **Color.Red** |**ColorValue （"#ff0000" &nbsp;）**<br>**ColorValue （"Red" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;0、&nbsp;0 &nbsp;1 &nbsp;）** |![红色](./media/function-colors/color-red.png) |
| **Color.RosyBrown** |**ColorValue （"#bc8f8f" &nbsp;）**<br>**ColorValue （"rosybrown" &nbsp;）** |**RGBA （&nbsp;188、&nbsp;143、&nbsp;143 &nbsp;1 &nbsp;）** |![玫瑰棕色](./media/function-colors/color-rosybrown.png) |
| **Color.RoyalBlue** |**ColorValue （"#4169e1" &nbsp;）**<br>**ColorValue （"RoyalBlue" &nbsp;）** |**RGBA （&nbsp;65、&nbsp;105、&nbsp;225 &nbsp;1 &nbsp;）** |![宝蓝色](./media/function-colors/color-royalblue.png) |
| **Color.SaddleBrown** |**ColorValue （"#8b4513" &nbsp;）**<br>**ColorValue （"SADDLEBROWN" &nbsp;）** |**RGBA （&nbsp;139、&nbsp;69、&nbsp;19 &nbsp;1 &nbsp;）** |![重褐色](./media/function-colors/color-saddlebrown.png) |
| **Color.Salmon** |**ColorValue （"#fa8072" &nbsp;）**<br>**ColorValue （"橙红" &nbsp;）** |**RGBA （&nbsp;250、&nbsp;128、&nbsp;114 &nbsp;1 &nbsp;）** |![鲑肉色](./media/function-colors/color-salmon.png) |
| **Color.SandyBrown** |**ColorValue （"#f4a460" &nbsp;）**<br>**ColorValue （"sandybrown" &nbsp;）** |**RGBA （&nbsp;244、&nbsp;164、&nbsp;96 &nbsp;1 &nbsp;）** |![沙棕色](./media/function-colors/color-sandybrown.png) |
| **Color.SeaGreen** |**ColorValue （"#2e8b57" &nbsp;）**<br>**ColorValue （"SeaGreen" &nbsp;）** |**RGBA （&nbsp;46、&nbsp;139、&nbsp;87 &nbsp;1 &nbsp;）** |![海绿色](./media/function-colors/color-seagreen.png) |
| **Color.SeaShell** |**ColorValue （"#fff5ee" &nbsp;）**<br>**ColorValue （"SEASHELL" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;245、&nbsp;238 &nbsp;1 &nbsp;）** |![海贝色](./media/function-colors/color-seashell.png) |
| **Color.Sienna** |**ColorValue （"#a0522d" &nbsp;）**<br>**ColorValue （"Sienna" &nbsp;）** |**RGBA （&nbsp;160、&nbsp;82、&nbsp;45 &nbsp;1 &nbsp;）** |![赭色](./media/function-colors/color-sienna.png) |
| **Color.Silver** |**ColorValue （"#c0c0c0" &nbsp;）**<br>**ColorValue （"白银" &nbsp;）** |**RGBA （&nbsp;192、&nbsp;192、&nbsp;192 &nbsp;1 &nbsp;）** |![银色](./media/function-colors/color-silver.png) |
| **Color.SkyBlue** |**ColorValue （"#87ceeb" &nbsp;）**<br>**ColorValue （"SkyBlue" &nbsp;）** |**RGBA （&nbsp;135、&nbsp;206、&nbsp;235 &nbsp;1 &nbsp;）** |![天蓝色](./media/function-colors/color-skyblue.png) |
| **Color.SlateBlue** |**ColorValue （"#6a5acd" &nbsp;）**<br>**ColorValue （"SLATEBLUE" &nbsp;）** |**RGBA （&nbsp;106、&nbsp;90、&nbsp;205 &nbsp;1 &nbsp;）** |![石板蓝色](./media/function-colors/color-slateblue.png) |
| **Color.SlateGray** |**ColorValue （"#708090" &nbsp;）**<br>**ColorValue （"石板灰" &nbsp;）** |**RGBA （&nbsp;112、&nbsp;128、&nbsp;144 &nbsp;1 &nbsp;）** |![石板灰色](./media/function-colors/color-slategray.png) |
| **Color.SlateGrey** |**ColorValue （"#708090" &nbsp;）**<br>**ColorValue （"slategrey" &nbsp;）** |**RGBA （&nbsp;112、&nbsp;128、&nbsp;144 &nbsp;1 &nbsp;）** |![石板灰色](./media/function-colors/color-slategrey.png) |
| **Color.Snow** |**ColorValue （"#fffafa" &nbsp;）**<br>**ColorValue （"雪" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;250、&nbsp;250 &nbsp;1 &nbsp;）** |![雪白色](./media/function-colors/color-snow.png) |
| **Color.SpringGreen** |**ColorValue （"#00ff7f" &nbsp;）**<br>**ColorValue （"SPRINGGREEN" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;255、&nbsp;127 &nbsp;1 &nbsp;）** |![春绿色](./media/function-colors/color-springgreen.png) |
| **Color.SteelBlue** |**ColorValue （"#4682b4" &nbsp;）**<br>**ColorValue （"Color.steelblue" &nbsp;）** |**RGBA （&nbsp;70、&nbsp;130、&nbsp;180 &nbsp;1 &nbsp;）** |![钢蓝色](./media/function-colors/color-steelblue.png) |
| **Color.Tan** |**ColorValue （"#d2b48c" &nbsp;）**<br>**ColorValue （"tan" &nbsp;）** |**RGBA （&nbsp;210、&nbsp;180、&nbsp;140 &nbsp;1 &nbsp;）** |![棕褐色](./media/function-colors/color-tan.png) |
| **Color.Teal** |**ColorValue （"#008080" &nbsp;）**<br>**ColorValue （"青色" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;128、&nbsp;128 &nbsp;1 &nbsp;）** |![水鸭色](./media/function-colors/color-teal.png) |
| **Color.Thistle** |**ColorValue （"#d8bfd8" &nbsp;）**<br>**ColorValue （"THISTLE" &nbsp;）** |**RGBA （&nbsp;216、&nbsp;191、&nbsp;216 &nbsp;1 &nbsp;）** |![蓟色](./media/function-colors/color-thistle.png) |
| **Color.Tomato** |**ColorValue （"#ff6347" &nbsp;）**<br>**ColorValue （"番茄色" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;99、&nbsp;71 &nbsp;1 &nbsp;）** |![番茄色](./media/function-colors/color-tomato.png) |
| **Color。透明** |**ColorValue （"#00000000" &nbsp;）**<br>**ColorValue （"透明" &nbsp;）** |**RGBA （&nbsp;0、&nbsp;0、&nbsp;0 &nbsp;0 &nbsp;）** |![透过](./media/function-colors/color-transparent.png) |
| **Color.Turquoise** |**ColorValue （"#40e0d0" &nbsp;）**<br>**ColorValue （"青绿色" &nbsp;）** |**RGBA （&nbsp;64、&nbsp;224、&nbsp;208 &nbsp;1 &nbsp;）** |![宝石绿色](./media/function-colors/color-turquoise.png) |
| **Color.Violet** |**ColorValue （"#ee82ee" &nbsp;）**<br>**ColorValue （"紫色" &nbsp;）** |**RGBA （&nbsp;238、&nbsp;130、&nbsp;238 &nbsp;1 &nbsp;）** |![紫罗兰色](./media/function-colors/color-violet.png) |
| **Color.Wheat** |**ColorValue （"#f5deb3" &nbsp;）**<br>**ColorValue （"COLOR.WHEAT" &nbsp;）** |**RGBA （&nbsp;245、&nbsp;222、&nbsp;179 &nbsp;1 &nbsp;）** |![小麦色](./media/function-colors/color-wheat.png) |
| **Color.White** |**ColorValue （"#ffffff" &nbsp;）**<br>**ColorValue （"白色" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;255、&nbsp;255 &nbsp;1 &nbsp;）** |![白色](./media/function-colors/color-white.png) |
| **Color.WhiteSmoke** |**ColorValue （"#f5f5f5" &nbsp;）**<br>**ColorValue （"烟白色" &nbsp;）** |**RGBA （&nbsp;245、&nbsp;245、&nbsp;245 &nbsp;1 &nbsp;）** |![烟白色](./media/function-colors/color-whitesmoke.png) |
| **Color.Yellow** |**ColorValue （"#ffff00" &nbsp;）**<br>**ColorValue （"黄色" &nbsp;）** |**RGBA （&nbsp;255、&nbsp;255、&nbsp;0 &nbsp;1 &nbsp;）** |![黄色](./media/function-colors/color-yellow.png) |
| **Color.YellowGreen** |**ColorValue （"#9acd32" &nbsp;）**<br>**ColorValue （"YELLOWGREEN" &nbsp;）** |**RGBA （&nbsp;154、&nbsp;205、&nbsp;50 &nbsp;1 &nbsp;）** |![黄绿色](./media/function-colors/color-yellowgreen.png) |
