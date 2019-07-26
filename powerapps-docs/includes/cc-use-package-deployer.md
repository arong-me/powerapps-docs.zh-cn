---
ms.openlocfilehash: a108a9ee6f9033851b2f55beb071a1e7cae254dd
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224246"
---
Package Deployer 工具以 [NuGet 包](https://go.microsoft.com/fwlink/?linkid=859205)的形式提供。 若要使用 Package Deployer，必须使用 nuget.exe 将其下载并解压缩到本地计算机。<br/><br/>

从 <https://www.nuget.org/downloads> 下载 nuget.exe，并将其保存到计算机，例如 d:\\。 然后在命令提示符处运行以下命令，将包内容解压缩到计算机上的文件夹中，例如 PD：<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf -Version [VERSION] -O d:\PD`<br/><br/>
    
解压缩 Package Deployer 工具后，浏览到 `[ExtractedLocation]\tools` 文件夹以查找 PackageDeployer.exe 文件。 
