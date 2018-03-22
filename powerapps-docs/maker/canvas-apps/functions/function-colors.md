---
title: Color 枚举与 ColorFade、ColorValue 以及 RGBA 函数 | Microsoft 文档
description: 有关 PowerApps 中的 Color 枚举与 ColorFade、ColorValue 以及 RGBA 函数的参考信息，包括语法和示例
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2015
ms.author: gregli
ms.openlocfilehash: da456de295f3b4fe38c98d4482e57372e3fc59a3
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="color-enumeration-and-colorfade-colorvalue-and-rgba-functions-in-powerapps"></a>PowerApps 中的 Color 枚举与 ColorFade、ColorValue 以及 RGBA 函数
使用内置颜色值，定义自定义颜色以及 Alpha 值混合处理。

## <a name="description"></a>说明
通过 **Color** 枚举可轻松访问 HTML 的级联样式表 (CSS) 定义的颜色。  例如，**Color.Red** 返回纯红色。  本文末尾提供了这些颜色的列表。   

**ColorValue** 函数基于 CSS 颜色字符串返回颜色。  CSS 颜色的名称（如“RosyBrown”）和十六进制值（如“#bc8f8f”）均可以使用。

**RGBA** 函数基于红色、绿色和蓝色颜色组件返回颜色。  它还包括一个 Alpha 组件，该组件用于混合在彼此之上层叠的对象的颜色。  Alpha 可从 0 或 0%（完全透明且不可见）到 1 或 100%（完全不透明，完全遮蔽了下面的图层）变化。

**ColorFade** 函数返回更亮或更深的颜色版本。  淡化量可从 -1（使颜色完全变暗为黑色）到 0（对颜色没有影响）到 1（使颜色完全变亮为白色）变化。  

## <a name="syntax"></a>语法
**Color**.*ColorName*

* *ColorName* - 必需。  级联样式表 (CSS) 颜色名称。  请参阅下面可能的枚举值的列表。

**ColorValue**(*CSSColor*)

* *CSSColor* - 必需。  级联样式表 (CSS) 颜色定义。  颜色的名称（如“OliveDrab”）和十六进制值（如“#6b8e23”）均可以使用。  

**RGBA**(*Red*, *Green*, *Blue*, *Alpha*)

* *Red*、*Green*、*Blue* - 必需。  颜色组件值，范围从 0（无饱和度）到 255（完全饱和度）。
* *Alpha* - 必需。  Alpha 组件，范围从 0（完全透明）到 1（完全不透明）。  还可以使用百分比（0% 到 100%）。

**ColorFade**(*Color*, *FadeAmount*)

* *Color* - 必需。  颜色值（如 **Color.Red**），或者 **ColorValue** 或 **RGBA** 的输出。
* *FadeAmount* - 必需。  介于 -1 和 1 之间的数字。  -1（使颜色完全变暗为黑色）、0（对颜色没有影响）和 1（使颜色完全变亮为白色）。  

## <a name="built-in-colors"></a>内置颜色
| Color 枚举 | 带有十六进制代码的 ColorValue | RGBA | 颜色样本 |
| --- | --- | --- | --- |
| **Color.AliceBlue** |**ColorValue("#f0f8ff")** |**RGBA(240, 248, 255, 1)** |![艾丽斯蓝](./media/function-colors/color-aliceblue.png) |
| **Color.AntiqueWhite** |**ColorValue("#faebd7")** |**RGBA(7, "250, 235,215, 1)** |![古董白](./media/function-colors/color-antiquewhite.png) |
| **Color.Aqua** |**ColorValue("#00ffff")** |**RGBA(0, 255, 255, 1)** |![浅绿色](./media/function-colors/color-aqua.png) |
| **Color.Aquamarine** |**ColorValue("#7fffd4")** |**RGBA(127, 255, 212, 1)** |![水绿色](./media/function-colors/color-aquamarine.png) |
| **Color.Azure** |**ColorValue("#f0ffff")** |**RGBA(240, 255, 255, 1)** |![天蓝色](./media/function-colors/color-azure.png) |
| **Color.Beige** |**ColorValue("#f5f5dc")** |**RGBA(245, 245, 220, 1)** |![米黄色](./media/function-colors/color-beige.png) |
| **Color.Bisque** |**ColorValue("#ffe4c4")** |**RGBA(255, 228, 196, 1)** |![橘黄色](./media/function-colors/color-bisque.png) |
| **Color.Black** |**ColorValue("#000000")** |**RGBA(0, 0, 0, 1)** |![黑色](./media/function-colors/color-black.png) |
| **Color.BlanchedAlmond** |**ColorValue("#ffebcd")** |**RGBA(255, 235, 205, 1)** |![白杏色](./media/function-colors/color-blanchedalmond.png) |
| **Color.Blue** |**ColorValue("#0000ff")** |**RGBA(0, 0, 255, 1)** |![蓝色](./media/function-colors/color-blue.png) |
| **Color.BlueViolet** |**ColorValue("#8a2be2")** |**RGBA(138, 43, 226, 1)** |![蓝紫色](./media/function-colors/color-blueviolet.png) |
| **Color.Brown** |**ColorValue("#a52a2a")** |**RGBA(165, 42, 42, 1)** |![棕色](./media/function-colors/color-brown.png) |
| **Color.Burlywood** |**ColorValue("#deb887")** |**RGBA(222, 184, 135, 1)** |![实木色](./media/function-colors/color-burlywood.png) |
| **Color.CadetBlue** |**ColorValue("#5f9ea0")** |**RGBA(95, 158, 160, 1)** |![军蓝色](./media/function-colors/color-cadetblue.png) |
| **Color.Chartreuse** |**ColorValue("#7fff00")** |**RGBA(127, 255, 0, 1)** |![黄绿色](./media/function-colors/color-chartreuse.png) |
| **Color.Chocolate** |**ColorValue("#d2691e")** |**RGBA(210, 105, 30, 1)** |![巧克力色](./media/function-colors/color-chocolate.png) |
| **Color.Coral** |**ColorValue("#ff7f50")** |**RGBA(255, 127, 80, 1)** |![珊瑚色](./media/function-colors/color-coral.png) |
| **Color.CornflowerBlue** |**ColorValue("#6495ed")** |**RGBA(100, 149, 237, 1)** |![菊蓝色](./media/function-colors/color-cornflowerblue.png) |
| **Color.Cornsilk** |**ColorValue("#fff8dc")** |**RGBA(255, 248, 220, 1)** |![玉米丝色](./media/function-colors/color-cornsilk.png) |
| **Color.Crimson** |**ColorValue("#dc143c")** |**RGBA(220, 20, 60, 1)** |![深红色](./media/function-colors/color-crimson.png) |
| **Color.Cyan** |**ColorValue("#00ffff")** |**RGBA(0, 255, 255, 1)** |![蓝绿色](./media/function-colors/color-cyan.png) |
| **Color.DarkBlue** |**ColorValue("#00008b")** |**RGBA(0, 0, 139, 1)** |![深蓝色](./media/function-colors/color-darkblue.png) |
| **Color.DarkCyan** |**ColorValue("#008b8b")** |**RGBA(0, 139, 139, 1)** |![深青绿](./media/function-colors/color-darkcyan.png) |
| **Color.DarkGoldenRod** |**ColorValue("#b8860b")** |**RGBA(184, 134, 11, 1)** |![暗金黄色](./media/function-colors/color-darkgoldenrod.png) |
| **Color.DarkGray** |**ColorValue("#a9a9a9")** |**RGBA(169, 169, 169, 1)** |![深灰色](./media/function-colors/color-darkgray.png) |
| **Color.DarkGreen** |**ColorValue("#006400")** |**RGBA(0, 100, 0, 1)** |![深绿色](./media/function-colors/color-darkgreen.png) |
| **Color.DarkGrey** |**ColorValue("#a9a9a9")** |**RGBA(169, 169, 169, 1)** |![深灰色](./media/function-colors/color-darkgrey.png) |
| **Color.DarkKhaki** |**ColorValue("#bdb76b")** |**RGBA(189, 183, 107, 1)** |![深褐色](./media/function-colors/color-darkkhaki.png) |
| **Color.DarkMagenta** |**ColorValue("#8b008b")** |**RGBA(139, 0, 139, 1)** |![深洋红色](./media/function-colors/color-darkmagenta.png) |
| **Color.DarkOliveGreen** |**ColorValue("#556b2f")** |**RGBA(85, 107, 47, 1)** |![深橄榄绿色](./media/function-colors/color-darkolivegreen.png) |
| **Color.DarkOrange** |**ColorValue("#ff8c00")** |**RGBA(255, 140, 0, 1)** |![深橙色](./media/function-colors/color-darkorange.png) |
| **Color.DarkOrchid** |**ColorValue("#9932cc")** |**RGBA(153, 50, 204, 1)** |![深紫色](./media/function-colors/color-darkorchid.png) |
| **Color.DarkRed** |**ColorValue("#8b0000")** |**RGBA(139, 0, 0, 1)** |![深红色](./media/function-colors/color-darkred.png) |
| **Color.DarkSalmon** |**ColorValue("#e9967a")** |**RGBA(233, 150, 122, 1)** |![深橙红色](./media/function-colors/color-darksalmon.png) |
| **Color.DarkSeaGreen** |**ColorValue("#8fbc8f")** |**RGBA(143, 188, 143, 1)** |![深海绿色](./media/function-colors/color-darkseagreen.png) |
| **Color.DarkSlateBlue** |**ColorValue("#483d8b")** |**RGBA(72, 61, 139, 1)** |![深石板蓝色](./media/function-colors/color-darkslateblue.png) |
| **Color.DarkSlateGray** |**ColorValue("#2f4f4f")** |**RGBA(47, 79, 79, 1 )** |![深石板灰色](./media/function-colors/color-darkslategray.png) |
| **Color.DarkSlateGrey** |**ColorValue("#2f4f4f")** |**RGBA(47, 79, 79, 1 )** |![深石板灰色](./media/function-colors/color-darkslategrey.png) |
| **Color.DarkTurquoise** |**ColorValue("#00ced1")** |**RGBA(0, 206, 209, 1)** |![深宝石绿色](./media/function-colors/color-darkturquoise.png) |
| **Color.DarkViolet** |**ColorValue("#9400d3")** |**RGBA(148, 0, 211, 1)** |![深紫色](./media/function-colors/color-darkviolet.png) |
| **Color.DeepPink** |**ColorValue("#ff1493")** |**RGBA(255, 20, 147, 1)** |![深粉色](./media/function-colors/color-deeppink.png) |
| **Color.DeepSkyBlue** |**ColorValue("#00bfff")** |**RGBA(0, 191, 255, 1)** |![深天蓝色](./media/function-colors/color-deepskyblue.png) |
| **Color.DimGray** |**ColorValue("#696969")** |**RGBA(105, 105, 105, 1)** |![暗灰色](./media/function-colors/color-dimgray.png) |
| **Color.DimGrey** |**ColorValue("#696969")** |**RGBA(105, 105, 105, 1)** |![暗灰色](./media/function-colors/color-dimgrey.png) |
| **Color.DodgerBlue** |**ColorValue("#1e90ff")** |**RGBA(30, 144, 255, 1)** |![闪蓝色](./media/function-colors/color-dodgerblue.png) |
| **Color.FireBrick** |**ColorValue("#b22222")** |**RGBA(178, 34, 34, 1)** |![火砖色](./media/function-colors/color-firebrick.png) |
| **Color.FloralWhite** |**ColorValue("#fffaf0")** |**RGBA(255, 250, 240, 1)** |![花白色](./media/function-colors/color-floralwhite.png) |
| **Color.ForestGreen** |**ColorValue("#228b22")** |**RGBA(34, 139, 34, 1)** |![森林绿](./media/function-colors/color-forestgreen.png) |
| **Color.Fuchsia** |**ColorValue("#ff00ff")** |**RGBA(255, 0, 255, 1)** |![紫红色](./media/function-colors/color-fuchsia.png) |
| **Color.Gainsboro** |**ColorValue("#dcdcdc")** |**RGBA(220, 220, 220, 1)** |![亮灰色](./media/function-colors/color-gainsboro.png) |
| **Color.GhostWhite** |**ColorValue("#f8f8ff")** |**RGBA(248, 248, 255, 1)** |![幽灵白色](./media/function-colors/color-ghostwhite.png) |
| **Color.Gold** |**ColorValue("#ffd700")** |**RGBA(255, 215, 0, 1)** |![金色](./media/function-colors/color-gold.png) |
| **Color.GoldenRod** |**ColorValue("#daa520")** |**RGBA(218, 165, 32, 1)** |![金麒麟色](./media/function-colors/color-goldenrod.png) |
| **Color.Gray** |**ColorValue("#808080")** |**RGBA(128, 128, 128, 1)** |![灰色](./media/function-colors/color-gray.png) |
| **Color.Green** |**ColorValue("#008000")** |**RGBA(0, 128, 0, 1)** |![绿色](./media/function-colors/color-green.png) |
| **Color.GreenYellow** |**ColorValue("#adff2f")** |**RGBA(173, 255, 47, 1)** |![黄绿色](./media/function-colors/color-greenyellow.png) |
| **Color.Grey** |**ColorValue("#808080")** |**RGBA(128, 128, 128, 1)** |![灰色](./media/function-colors/color-grey.png) |
| **Color.Honeydew** |**ColorValue("#f0fff0")** |**RGBA(240, 255, 240, 1)** |![蜜色](./media/function-colors/color-honeydew.png) |
| **Color.HotPink** |**ColorValue("#ff69b4")** |**RGBA(255, 105, 180, 1)** |![艳粉色](./media/function-colors/color-hotpink.png) |
| **Color.IndianRed** |**ColorValue ("#cd5c5c")** |**RGBA(205, 92, 92, 1)** |![印度红](./media/function-colors/color-indianred.png) |
| **Color.Indigo** |**ColorValue("#4b0082")** |**RGBA(75, 0, 130, 1)** |![靛蓝色](./media/function-colors/color-indigo.png) |
| **Color.Ivory** |**ColorValue("#fffff0")** |**RGBA(255, 255, 240, 1)** |![乳白色](./media/function-colors/color-ivory.png) |
| **Color.Khaki** |**ColorValue("#f0e68c")** |**RGBA(240, 230, 140, 1)** |![卡其色](./media/function-colors/color-khaki.png) |
| **Color.Lavender** |**ColorValue("#e6e6fa")** |**RGBA(230, 230, 250, 1)** |![淡紫色](./media/function-colors/color-lavender.png) |
| **Color.LavenderBlush** |**ColorValue("#fff0f5")** |**RGBA(255, 240, 245, 1)** |![浅紫红色](./media/function-colors/color-lavenderblush.png) |
| **Color.LawnGreen** |**ColorValue("#7cfc00")** |**RGBA(124, 252, 0, 1)** |![草绿色](./media/function-colors/color-lawngreen.png) |
| **Color.LemonChiffon** |**ColorValue("#fffacd")** |**RGBA(255, 250, 205, 1)** |![柠檬绸色](./media/function-colors/color-lemonchiffon.png) |
| **Color.LightBlue** |**ColorValue("#add8e6")** |**RGBA(173, 216, 230, 1)** |![淡蓝色](./media/function-colors/color-lightblue.png) |
| **Color.LightCoral** |**ColorValue("#f08080")** |**RGBA(240, 128, 128, 1)** |![浅珊瑚色](./media/function-colors/color-lightcoral.png) |
| **Color.LightCyan** |**ColorValue("#e0ffff")** |**RGBA(224, 255, 255, 1)** |![浅青色](./media/function-colors/color-lightcyan.png) |
| **Color.LightGoldenRodYellow** |**ColorValue("#fafad2")** |**RGBA(250, 250, 210, 1)** |![浅金黄色](./media/function-colors/color-lightgoldenrodyellow.png) |
| **Color.LightGray** |**ColorValue("#d3d3d3")** |**RGBA(211, 211, 211, 1)** |![浅灰色](./media/function-colors/color-lightgray.png) |
| **Color.LightGreen** |**ColorValue("#90ee90")** |**RGBA(144, 238, 144, 1)** |![浅绿色](./media/function-colors/color-lightgreen.png) |
| **Color.LightGrey** |**ColorValue("#d3d3d3")** |**RGBA(211, 211, 211, 1)** |![浅灰色](./media/function-colors/color-lightgrey.png) |
| **Color.LightPink** |**ColorValue("#ffb6c1")** |**RGBA(255, 182, 193, 1)** |![浅粉色](./media/function-colors/color-lightpink.png) |
| **Color.LightSalmon** |**ColorValue("#ffa07a")** |**RGBA(255, 160, 122, 1)** |![浅肉色](./media/function-colors/color-lightsalmon.png) |
| **Color.LightSeaGreen** |**ColorValue("#20b2aa")** |**RGBA(32, 178, 170, 1)** |![浅海蓝色](./media/function-colors/color-lightseagreen.png) |
| **Color.LightSkyBlue** |**ColorValue("#87cefa")** |**RGBA(135, 206, 250, 1)** |![浅天蓝色](./media/function-colors/color-lightskyblue.png) |
| **Color.LightSlateGray** |**ColorValue("#778899")** |**RGBA(119, 136, 153, 1)** |![浅石板灰色](./media/function-colors/color-lightslategray.png) |
| **Color.LightSlateGrey** |**ColorValue("#778899")** |**RGBA(119, 136, 153, 1)** |![浅石板灰色](./media/function-colors/color-lightslategrey.png) |
| **Color.LightSteelBlue** |**ColorValue("#b0c4de")** |**RGBA(176, 196, 222, 1)** |![浅钢蓝色](./media/function-colors/color-lightsteelblue.png) |
| **Color.LightYellow** |**ColorValue("#ffffe0")** |**RGBA(255, 255, 224, 1)** |![浅黄色](./media/function-colors/color-lightyellow.png) |
| **Color.Lime** |**ColorValue("#00ff00")** |**RGBA(0, 255, 0, 1)** |![酸橙色](./media/function-colors/color-lime.png) |
| **Color.LimeGreen** |**ColorValue("#32cd32")** |**RGBA(50, 205, 50, 1)** |![橙绿色](./media/function-colors/color-limegreen.png) |
| **Color.Linen** |**ColorValue("#faf0e6")** |**RGBA(250, 240, 230, 1)** |![亚麻色](./media/function-colors/color-linen.png) |
| **Color.Magenta** |**ColorValue("#ff00ff")** |**RGBA(255, 0, 255, 1)** |![洋红色](./media/function-colors/color-magenta.png) |
| **Color.Maroon** |**ColorValue("#800000")** |**RGBA(128, 0, 0, 1)** |![褐红色](./media/function-colors/color-maroon.png) |
| **Color.MediumAquamarine** |**ColorValue("#66cdaa")** |**RGBA(102, 205, 170, 1)** |![中碧绿色](./media/function-colors/color-mediumaquamarine.png) |
| **Color.MediumBlue** |**ColorValue("#0000cd")** |**RGBA(0, 0, 205, 1)** |![中蓝色](./media/function-colors/color-mediumblue.png) |
| **Color.MediumOrchid** |**ColorValue("#ba55d3")** |**RGBA(186, 85, 211, 1)** |![中兰花紫](./media/function-colors/color-mediumorchid.png) |
| **Color.MediumPurple** |**ColorValue("#9370db")** |**RGBA(147, 112, 219, 1)** |![中紫色](./media/function-colors/color-mediumpurple.png) |
| **Color.MediumSeaGreen** |**ColorValue("#3cb371")** |**RGBA(60, 179, 113, 1)** |![中海绿色](./media/function-colors/color-mediumseagreen.png) |
| **Color.MediumSlateBlue** |**ColorValue("#7b68ee")** |**RGBA(123, 104, 238, 1)** |![中灰蓝色](./media/function-colors/color-mediumslateblue.png) |
| **Color.MediumSpringGreen** |**ColorValue("#00fa9a")** |**RGBA(0, 250, 154, 1)** |![中春绿色](./media/function-colors/color-mediumspringgreen.png) |
| **Color.MediumTurquoise** |**ColorValue("#48d1cc")** |**RGBA(72, 209, 204, 1)** |![中蓝绿色](./media/function-colors/color-mediumturquoise.png) |
| **Color.MediumVioletRed** |**ColorValue("#c71585")** |**RGBA(199, 21, 133, 1)** |![中紫罗兰色](./media/function-colors/color-mediumvioletred.png) |
| **Color.MidnightBlue** |**ColorValue("#191970")** |**RGBA(25, 25, 112, 1)** |![午夜蓝色](./media/function-colors/color-midnightblue.png) |
| **Color.MintCream** |**ColorValue("#f5fffa")** |**RGBA(245, 255, 250, 1)** |![薄荷奶油色](./media/function-colors/color-mintcream.png) |
| **Color.MistyRose** |**ColorValue("#ffe4e1")** |**RGBA(255, 228, 225, 1)** |![雾中玫瑰色](./media/function-colors/color-mistyrose.png) |
| **Color.Moccasin** |**ColorValue("#ffe4b5")** |**RGBA(255, 228, 181, 1)** |![鹿皮色](./media/function-colors/color-moccasin.png) |
| **Color.NavajoWhite** |**ColorValue("#ffdead")** |**RGBA(255, 222, 173, 1)** |![纳瓦白色](./media/function-colors/color-navajowhite.png) |
| **Color.Navy** |**ColorValue("#000080")** |**RGBA(0, 0, 128, 1)** |![深蓝色](./media/function-colors/color-navy.png) |
| **Color.OldLace** |**ColorValue("#fdf5e6")** |**RGBA(253, 245, 230, 1)** |![老花色](./media/function-colors/color-oldlace.png) |
| **Color.Olive** |**ColorValue("#808000")** |**RGBA(128, 128, 0, 1)** |![橄榄色](./media/function-colors/color-olive.png) |
| **Color.OliveDrab** |**ColorValue("#6b8e23")** |**RGBA(107, 142, 35, 1)** |![橄榄土褐色](./media/function-colors/color-olivedrab.png) |
| **Color.Orange** |**ColorValue("#ffa500")** |**RGBA(255, 165, 0, 1)** |![橙色](./media/function-colors/color-orange.png) |
| **Color.OrangeRed** |**ColorValue("#ff4500")** |**RGBA(255, 69, 0, 1)** |![橙红色](./media/function-colors/color-orangered.png) |
| **Color.Orchid** |**ColorValue("#da70d6")** |**RGBA(218, 112, 214, 1)** |![兰花紫](./media/function-colors/color-orchid.png) |
| **Color.PaleGoldenRod** |**ColorValue("#eee8aa")** |**RGBA(238, 232, 170, 1)** |![淡菊黄色](./media/function-colors/color-palegoldenrod.png) |
| **Color.PaleGreen** |**ColorValue("#98fb98")** |**RGBA(152, 251, 152, 1)** |![苍绿色](./media/function-colors/color-palegreen.png) |
| **Color.PaleTurquoise** |**ColorValue("#afeeee")** |**RGBA(175, 238, 238, 1)** |![苍宝石绿色](./media/function-colors/color-paleturquoise.png) |
| **Color.PaleVioletRed** |**ColorValue("#db7093")** |**RGBA(219, 112, 147, 1)** |![苍紫罗蓝色](./media/function-colors/color-palevioletred.png) |
| **Color.PapayaWhip** |**ColorValue("#ffefd5")** |**RGBA(255, 239, 213, 1)** |![番木色](./media/function-colors/color-papayawhip.png) |
| **Color.PeachPuff** |**ColorValue("#ffdab9")** |**RGBA(255, 218, 185, 1)** |![桃肉色](./media/function-colors/color-peachpuff.png) |
| **Color.Peru** |**ColorValue("#cd853f")** |**RGBA(205, 133, 63, 1)** |![秘鲁棕色](./media/function-colors/color-peru.png) |
| **Color.Pink** |**ColorValue("#ffc0cb")** |**RGBA(255, 192, 203, 1)** |![粉红色](./media/function-colors/color-pink.png) |
| **Color.Plum** |**ColorValue("#dda0dd")** |**RGBA(221, 160, 221, 1)** |![梅红色](./media/function-colors/color-plum.png) |
| **Color.PowderBlue** |**ColorValue("#b0e0e6")** |**RGBA(176, 224, 230, 1)** |![粉蓝色](./media/function-colors/color-powderblue.png) |
| **Color.Purple** |**ColorValue("#800080")** |**RGBA(128, 0, 128, 1)** |![紫色](./media/function-colors/color-purple.png) |
| **Color.Red** |**ColorValue("#ff0000")** |**RGBA(255, 0, 0, 1)** |![红色](./media/function-colors/color-red.png) |
| **Color.RosyBrown** |**ColorValue("#bc8f8f")** |**RGBA(188, 143, 143, 1)** |![玫瑰棕色](./media/function-colors/color-rosybrown.png) |
| **Color.RoyalBlue** |**ColorValue("#4169e1")** |**RGBA(65, 105, 225, 1)** |![宝蓝色](./media/function-colors/color-royalblue.png) |
| **Color.SaddleBrown** |**ColorValue("#8b4513")** |**RGBA(139, 69, 19, 1)** |![重褐色](./media/function-colors/color-saddlebrown.png) |
| **Color.Salmon** |**ColorValue("#fa8072")** |**RGBA(250, 128, 114, 1)** |![鲑肉色](./media/function-colors/color-salmon.png) |
| **Color.SandyBrown** |**ColorValue("#f4a460")** |**RGBA(244, 164, 96, 1)** |![沙棕色](./media/function-colors/color-sandybrown.png) |
| **Color.SeaGreen** |**ColorValue("#2e8b57")** |**RGBA(46, 139, 87, 1)** |![海绿色](./media/function-colors/color-seagreen.png) |
| **Color.SeaShell** |**ColorValue("#fff5ee")** |**RGBA(255, 245, 238, 1)** |![海贝色](./media/function-colors/color-seashell.png) |
| **Color.Sienna** |**ColorValue("#a0522d")** |**RGBA(160, 82, 45, 1)** |![赭色](./media/function-colors/color-sienna.png) |
| **Color.Silver** |**ColorValue("#c0c0c0")** |**RGBA(192, 192, 192, 1)** |![银色](./media/function-colors/color-silver.png) |
| **Color.SkyBlue** |**ColorValue("#87ceeb")** |**RGBA(135, 206, 235, 1)** |![天蓝色](./media/function-colors/color-skyblue.png) |
| **Color.SlateBlue** |**ColorValue("#6a5acd")** |**RGBA(106, 90, 205, 1)** |![石板蓝色](./media/function-colors/color-slateblue.png) |
| **Color.SlateGray** |**ColorValue("#708090")** |**RGBA(112, 128, 144, 1)** |![石板灰色](./media/function-colors/color-slategray.png) |
| **Color.SlateGrey** |**ColorValue("#708090")** |**RGBA(112, 128, 144, 1)** |![石板灰色](./media/function-colors/color-slategrey.png) |
| **Color.Snow** |**ColorValue("#fffafa")** |**RGBA(255, 250, 250, 1)** |![雪白色](./media/function-colors/color-snow.png) |
| **Color.SpringGreen** |**ColorValue("#00ff7f")** |**RGBA(0, 255, 127, 1)** |![春绿色](./media/function-colors/color-springgreen.png) |
| **Color.SteelBlue** |**ColorValue("#4682b4")** |**RGBA(70, 130, 180, 1)** |![钢蓝色](./media/function-colors/color-steelblue.png) |
| **Color.Tan** |**ColorValue("#d2b48c")** |**RGBA(210, 180, 140, 1)** |![棕褐色](./media/function-colors/color-tan.png) |
| **Color.Teal** |**ColorValue("#008080")** |**RGBA(0, 128, 128, 1)** |![水鸭色](./media/function-colors/color-teal.png) |
| **Color.Thistle** |**ColorValue("#d8bfd8")** |**RGBA(216, 191, 216, 1)** |![蓟色](./media/function-colors/color-thistle.png) |
| **Color.Tomato** |**ColorValue("#ff6347")** |**RGBA(255, 99, 71, 1)** |![番茄色](./media/function-colors/color-tomato.png) |
| **Color.Turquoise** |**ColorValue("#40e0d0")** |**RGBA(64, 224, 208, 1)** |![宝石绿色](./media/function-colors/color-turquoise.png) |
| **Color.Violet** |**ColorValue("#ee82ee")** |**RGBA(238, 130, 238, 1)** |![紫罗兰色](./media/function-colors/color-violet.png) |
| **Color.Wheat** |**ColorValue("#f5deb3")** |**RGBA(245, 222, 179, 1)** |![小麦色](./media/function-colors/color-wheat.png) |
| **Color.White** |**ColorValue("#ffffff")** |**RGBA(255, 255, 255, 1)** |![白色](./media/function-colors/color-white.png) |
| **Color.WhiteSmoke** |**ColorValue("#f5f5f5")** |**RGBA(245, 245, 245, 1)** |![烟白色](./media/function-colors/color-whitesmoke.png) |
| **Color.Yellow** |**ColorValue("#ffff00")** |**RGBA(255, 255, 0, 1)** |![黄色](./media/function-colors/color-yellow.png) |
| **Color.YellowGreen** |**ColorValue("#9acd32")** |**RGBA(154, 205, 50, 1)** |![黄绿色](./media/function-colors/color-yellowgreen.png) |

