---
ms.openlocfilehash: fbe01554dfbbf77ae7e284b1eeb49ec7c4f6c688
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212715"
---
如果使用 Microsoft Dynamics 365（联机），那么将数据导出至静态工作表时将创建该导出数据的本地副本，并在计算机中存储该副本。 数据通过安全连接从 Dynamics 365（联机）传输到计算机，且不会在本地副本和 Dynamics 365（联机）之间保持连接。  
  
 若导出至动态工作表或数据透视表，则会在 Excel 工作表和 Dynamics 365（联机）之间保持链接。 每次动态工作表或数据透视表刷新后，都需使用自己的凭据向 Dynamics 365（联机）进行身份验证。 可以查看自己有权查看的数据。  
  
 管理员使用安全角色确定是否允许组织的用户将数据导出至 Excel。