---
ms.openlocfilehash: 29226cfe8ab5c0ad01b785cfdaeec2e12a230dd7
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225320"
---
通过让 Social Engagement 连接到 [Azure 事件中心](https://azure.microsoft.com/documentation/articles/event-hubs-overview/)，可允许使用自动化规则将社交数据流式传输到事件中心。 Azure 事件中心会将从 Social Engagement 中流式传输的社交数据存储[预先配置的一段时间](https://azure.microsoft.com/documentation/articles/event-hubs-availability-and-support-faq/)，任何可侦听事件中心的应用程序均可访问、存储和/或处理此数据。  
  
 请注意，从 Social Engagement 中发送的社交数据包括有关社交帖子（作者和文本）的信息，以及语言、位置、情绪、标记等诸多信息。有关发送到事件中心的社交帖子内容的完整信息，请参阅 [JSON 架构定义](http://go.microsoft.com/fwlink/p/?LinkId=786643)。