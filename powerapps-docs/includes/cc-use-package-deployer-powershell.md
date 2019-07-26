---
ms.openlocfilehash: 215a6d9fb0890bd6d93843b0b649ada4203e5600
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224203"
---
适用于 Package Deployer 工具的 PowerShell 文件以 [NuGet 包](https://go.microsoft.com/fwlink/?linkid=859211)的形式提供。 若要使用它们，必须使用 nuget.exe 下载并将其解压缩到本地计算机。<br/><br/>

从 <https://www.nuget.org/downloads> 下载 nuget.exe，并将其保存到计算机，例如 d:\\。 然后在命令提示符处运行以下命令以将包内容解压缩到计算机上的文件夹中，例如 PD-PowerShell：<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell -Version [VERSION] -O d:\PD-PowerShell`<br/><br/>
    
解压缩适用于 Package Deployer 工具的 PowerShell 文件后，浏览到 `[ExtractedLocation]\tools` 文件夹以查找所需文件。 
