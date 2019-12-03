---
ms.openlocfilehash: d74254f2536b78a0951c860d803519827d31e446
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678250"
---
## <a name="delegation"></a>委派
如果可能，电源应用会将筛选器和排序操作委托给数据源，并按需查看结果。 例如，当启动显示“[库](../maker/canvas-apps/controls/control-gallery.md)”控件（已填充数据）的应用时，最初仅会将第一组记录转入设备。 用户滚动鼠标时，将从数据源中引入其他数据。 进而将加快应用启动和访问超大数据集的速度。

但是，委派并不总是可行。 数据源所支持的用于委派的函数和运算符会有所不同。 如果无法实现公式的完全委派，创作环境将出现警告，其中会标记出不能委派的部分。 如果可能，请考虑更改公式，以避免使用不能委派的函数和运算符。  [委派列表](../maker/canvas-apps/delegation-list.md)中详细说明可以委派的数据源和操作。

如果无法进行委派，则 Power Apps 将仅提取一小部分记录，以便在本地运行。 筛选和排序函数将对缩减的一组记录执行操作。 **[库](../maker/canvas-apps/controls/control-gallery.md)** 中的可用内容可能并不完整，这可能使用户感到困惑。 

请参阅[委派概述](../maker/canvas-apps/delegation-overview.md)了解详细信息。

