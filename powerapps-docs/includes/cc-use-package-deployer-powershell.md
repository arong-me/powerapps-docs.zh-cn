适用于 Package Deployer 工具的 PowerShell 文件可用作 [NuGet 包](https://go.microsoft.com/fwlink/?linkid=859211)。 要使用这些文件，您必须使用 **nuget.exe** 下载文件并将其提取到您的本地计算机。<br/><br/>

从 <https://www.nuget.org/downloads> 下载 **nuget.exe**，然后将其保存到您的计算机，例如目录 **d:\\**。 然后，在命令提示符处运行以下命令以将程序包内容提取到计算机上的某个文件夹，例如 **PD-PowerShell**：<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell -Version [VERSION] -O d:\PD-PowerShell`<br/><br/>
    
在提取适用于 Package Deployer 工具的 PowerShell 文件后，浏览到 `[ExtractedLocation]\tools` 文件夹以查找所需的文件。 
