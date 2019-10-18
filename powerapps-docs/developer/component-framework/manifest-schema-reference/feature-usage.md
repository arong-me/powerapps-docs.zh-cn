---
title: 功能使用 |Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87f5e921-4114-4710-a362-db741426a69b
ms.openlocfilehash: 21e76a2a17910fe36967364f063ff2fc9b25e153
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "72339623"
---
# <a name="feature-usage-element"></a>功能使用情况元素

功能使用情况元素用作围绕 `uses-feature` 元素的包装，它们本身允许开发人员声明其组件要使用哪些功能。 如果未定义任何使用-功能元素，则不需要使用此功能元素。

## <a name="available-for"></a>适用于

模型驱动应用

## <a name="child-elements"></a>子元素

|元素|描述|适用于|
|--|--|-----|
|[使用-功能](uses-feature.md)|指示要使用的组件的功能。|模型驱动应用|


## <a name="example"></a>示例

```XML
<feature-usage>
    <uses-feature name="Device.captureAudio" required="true" />
    <uses-feature name="Device.captureImage" required="true" />
    <uses-feature name="Device.captureVideo" required="true" />
    <uses-feature name="Device.getBarcodeValue" required="true" />
    <uses-feature name="Device.getCurrentPosition" required="true" />
    <uses-feature name="Device.pickFile" required="true" />
    <uses-feature name="Utility" required="true" />
    <uses-feature name="WebAPI" required="true" />
 </feature-usage>
```
