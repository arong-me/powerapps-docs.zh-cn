---
title: 使用经典编辑器自动使用 Azure 管道进行测试 |Microsoft Docs
description: 介绍如何使用 Azure 管道中的经典编辑器自动执行测试套件和事例。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/16/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ecfeeb1f62032008d7ada618afb56e6da8589f40
ms.sourcegitcommit: 223c3d19ec4fbe43fcc7a16b76423c00f8602ecd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81490881"
---
# <a name="automate-tests-with-azure-pipeline-using-classic-editor"></a>使用经典编辑器自动使用 Azure 管道进行测试

在本文中，你将了解如何在[Azure DevOps Services](https://docs.microsoft.com/azure/devops/user-guide/what-is-azure-devops?view=azure-devops)中使用[Azure Pipelines 经典编辑器](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops#define-pipelines-using-the-classic-interface)来设置和运行在测试工作室中生成的画布应用测试。

您可以使用 GitHub 上的公共项目- [Microsoft/PowerAppsTestAutomation](https://github.com/microsoft/PowerAppsTestAutomation)来执行以下操作：

- 自动登录到应用程序的操作。
- 在生成代理上打开浏览器，并执行一组测试用例和套件。
- 查看 Azure DevOps 管道中的测试执行状态。

## <a name="prerequisites"></a>先决条件

在开始之前，必须完成以下步骤：

- 在 GitHub 上[分叉](#step-1---fork-the-powerappstestautomation-project) [Microsoft/PowerAppsTestAutomation](https://github.com/microsoft/PowerAppsTestAutomation)项目。

    > [!NOTE]
    > 不能将公共叉设为私有。 如果要创建专用[存储库，请复制存储库](https://help.github.com/github/creating-cloning-and-archiving-repositories/duplicating-a-repository)。

- 在存储库中创建新的[*测试 url*](#step-2---create-test-url-json-file) ，其中包含要从管道运行的应用测试 url。

### <a name="step-1---fork-the-powerappstestautomation-project"></a>步骤 1-将 PowerAppsTestAutomation 项目分叉

[分叉](https://help.github.com/github/getting-started-with-github/fork-a-repo)是存储库的副本。 通过分支存储库，可以在不影响原始项目的情况下进行更改。

1. 登录到[GitHub](https://github.com/)。

1. 请参阅[microsoft/PowerAppsTestAutomation](https://github.com/microsoft/PowerAppsTestAutomation)存储库。 你还可以改为搜索**microsoft/PowerAppsTestAutomation** ，然后选择存储库：

    ![搜索 GitHub](media/test-studio-classic-pipeline-editor/search-github.png)

1. 选择**分叉**：

    ![分叉](media/test-studio-classic-pipeline-editor/fork.png)

1. 选择想要分叉的位置：

    ![分叉帐户](media/test-studio-classic-pipeline-editor/fork-account.png)

你的分叉存储库现在将可用。

### <a name="step-2---create-test-url-json-file"></a>步骤 2-创建测试 URL json 文件

测试 URL json 文件将包含用于验证应用程序的测试套件和测试用例 Url。 可以通过在测试中心中选择 "[复制播放" 链接](working-with-test-studio.md#playing-tests-in-a-browser)来检索应用测试套件和测试用例 url。

你可以在之前创建的存储库中找到 ```Samples/TestAutomationURLs.json``` 的示例文件。

1. 在存储库中创建新的 ```TestURLs.json``` 文件，或使用任何其他文件名。 <br> 稍后将在文档中的管道变量中映射文件名和位置。

1. 复制 ```Samples/TestAutomationURLs.json``` 文件中的格式。

1. 将测试 Url 部分与你要在应用程序中验证的测试进行更新。

1. 将更改提交到存储库：

    ![JSON 更新](media/test-studio-classic-pipeline-editor/json-update.png)

## <a name="create-a-pipeline"></a>创建管道

1. 登录到 Azure DevOps 实例。

1. 选择现有项目或创建新项目。

1. 在左侧菜单中选择 "**管道**"。

1. 选择 "**创建管道**"：

    ![创建管道](media/test-studio-classic-pipeline-editor/create-pipeline.png)

1. 选择 **"使用经典编辑器"** ：

    ![经典编辑器](media/test-studio-classic-pipeline-editor/use-classic-editor.png)

1. 选择 "GitHub" 作为 "源"。

1. 如有必要，请使用 OAuth 或个人访问令牌授权 GitHub 连接：

    ![管道-GitHub](media/test-studio-classic-pipeline-editor/pipeline-github.png)

1. 如果需要，编辑连接名称。

1. 从 "**存储库**" 输入右侧选择 " **...** （省略号）"。

1. 在 GitHub 上输入项目的名称，然后**选择**该名称：

    ![选择存储库](media/test-studio-classic-pipeline-editor/select-repo.png)

1. 选择“继续”。

1. 在 "选择模板" 屏幕中，选择 "**空作业**"：

    ![空作业](media/test-studio-classic-pipeline-editor/empty-job.png)

1. **保存**管道。

## <a name="add-tasks-to-the-pipeline"></a>向管道添加任务

现在，你将添加新的作业任务并将任务配置为按此顺序在管道中运行测试：

1. [使用 PowerShell 配置屏幕分辨率。](#step-1---configure-screen-resolution-using-powershell)

1. [还原 PowerAppsTestAutomation 解决方案的 NuGet 包。](#step-2---restore-nuget-packages)

1. [生成 PowerAppsTestAutomation 解决方案。](#step-3---build-the-powerappstestautomation-solution)

1. [添加适用于 Google Chrome 的 Visual Studio 测试。](#step-4---add-visual-studio-tests-for-google-chrome)

1. [为 Mozilla Firefox 添加 Visual Studio 测试。](#step-5---add-visual-studio-tests-for-mozilla-firefox)

### <a name="step-1---configure-screen-resolution-using-powershell"></a>步骤 1-使用 PowerShell 配置屏幕分辨率

1. 选择 "*代理作业 1*" 旁边的 **+** 。

1. 搜索**PowerShell**。

1. 选择 "**添加**"，将 PowerShell 任务添加到作业：

    ![PowerShell](media/test-studio-classic-pipeline-editor/powershell.png)

1. 选择该任务。 <br>
    还可以更新显示名称，*将代理屏幕分辨率设置为 1920x1080*或类似。

1. 选择 "**内联**" 作为脚本类型，然后在 "脚本" 窗口中输入以下内容：

    ```powershell
    # Set agent screen resolution to 1920x1080 to avoid sizing issues with Portal  
    Set-DisplayResolution -Width 1920 -Height 1080 -Force
    # Wait 10 seconds  
    Start-Sleep -s 10
    # Verify Screen Resolution is set to 1920x1080  
    Get-DisplayResolution
    ```

    ![Script](media/test-studio-classic-pipeline-editor/script.png)

### <a name="step-2---restore-nuget-packages"></a>步骤 2-还原 NuGet 包

1. 选择代理作业1旁边 **+** 。

1. 搜索 " **NuGet**"。

1. 选择 "添加"，将 NuGet 任务添加到作业。

1. 选择该任务。
    <br> 还可以更新显示名称以**还原 NuGet 包**或类似。

1. 选择 **...** "解决方案"、"**包" 或 "项目 json**配置" 字段的路径中的（省略号）。

1. 选择 PowerAppsTestAutomation 解决方案文件。

1. 选择 **"确定"** ：

    ![NuGet 包](media/test-studio-classic-pipeline-editor/nuget.png)

### <a name="step-3---build-the-powerappstestautomation-solution"></a>步骤 3-生成 PowerAppsTestAutomation 解决方案

1. 选择 "代理作业 1" 旁边的 **+** 。

1. 搜索**Visual Studio 生成**。

1. 选择 "**添加**"，将 Visual Studio 生成任务添加到作业。

1. 选择该任务。
    <br> 还可以更新显示名称以**生成电源应用测试自动化解决方案**或类似的。

1. 选择 **...** "**解决方案**配置" 字段中的 "（省略号）"。

1. 选择 PowerAppsTestAutomation 解决方案文件。

1. 选择“确定”。

### <a name="step-4---add-visual-studio-tests-for-google-chrome"></a>步骤 4-添加适用于 Google Chrome 的 Visual Studio 测试

1. 选择 "代理作业 1" 旁边的 **+** 。

1. 搜索 " **Visual Studio 测试**"。

1. 选择 "添加"，将 Visual Studio 测试任务添加到作业。

1. 选择该任务。
    <br> 还可以通过 \$（BrowserTypeChrome）或类似更新显示名称以*运行 Power Apps 测试自动化测试*。

1. 删除 "测试文件" 文本字段中的默认项并添加以下内容：

    ```**\Microsoft.PowerApps.TestAutomation.Tests\bin\\Debug\Microsoft.PowerApps.TestAutomation.Tests.dll```

1. 在 "**测试筛选条件" 字段**中输入 ```TestCategory=PowerAppsTestAutomation```。

1. 选择 "**测试组合包含 UI 测试**"。

    ![Chrome](media/test-studio-classic-pipeline-editor/chrome.png)

1. 选择 **...** （省略号）在 "**设置文件**" 字段中。

1. 展开**TestAutomation**，选择**patestautomation**文件，然后选择 **"确定"** ：

    ![运行设置](media/test-studio-classic-pipeline-editor/runsettings.png)

1. 在 "**替代测试运行参数**" 字段中复制以下。

    ```
    -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -BrowserType $(BrowserTypeChrome) -OnlineUrl $(OnlineUrl) -UsePrivateMode $(UsePrivateMode) -TestAutomationURLFilePath $(TestAutomationURLFilePath) -DriversPath $(ChromeWebDriver)
    ```

    > [!NOTE]
    > 这是管道中的变量的配置位置，以 \$（VariableName）的形式表示。

1. 在 "测试运行标题" 字段中输入 "**运行电源应用测试自动化测试 \$（BrowserTypeChrome）** " 或 "类似"。

    ![测试运行](media/test-studio-classic-pipeline-editor/test-run.png)

### <a name="step-5---add-visual-studio-tests-for-mozilla-firefox"></a>步骤 5-为 Mozilla Firefox 添加 Visual Studio 测试

1. 右键单击 "**添加适用于 Chrome 的 Visual Studio 测试**" 任务，然后选择 "**克隆任务**"。

1. 选择任务并更新以下区域。

    1. **标题**：通过 \$（BrowserTypeFirefox）复制运行 Power Apps 测试自动化测试

    1.  **替代测试运行参数**

        ```
        -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -BrowserType $(BrowserTypeFirefox) -OnlineUrl $(OnlineUrl) -UsePrivateMode $(UsePrivateMode) -TestAutomationURLFilePath $(TestAutomationURLFilePath) -DriversPath $(GeckoWebDriver)
        ```

    1.  **测试运行标题**：通过 \$（BrowserTypeFirefox）运行电源应用测试自动化测试

## <a name="configure-pipeline-variables"></a>配置管道变量

现在，你将配置[前面](#add-tasks-to-the-pipeline)添加的任务中定义的管道变量。

1. 选择 "**变量**" 选项卡。

2. 选择 "**添加**"，然后重复此步骤以配置以下变量：

| 变量名称             | 变量值                                                                                                                 |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| BrowserTypeChrome         | Chrome                                                                                                                         |
| BrowserTypeFirefox        | Firefox                                                                                                                        |
| OnlineUrl                 | <https://make.powerapps.com>                                                                                                   |
| TestAutomationURLFilePath | ```$(Build.SourcesDirectory)\<test URL file>.json``` <br>**注意：** 这是之前创建的[*测试 url 文件*](#step-2---create-test-url-json-file)。                      |
| UsePrivateMode            | true                                                                                                                           |
| OnlineUsername            | 输入将登录到应用程序的用户上下文的 Azure Active Directory 电子邮件地址。 测试将在此用户帐户的上下文中运行。\> |

1. 选择 "添加"，然后在变量名称中输入**OnlinePassword** 。

1. 检查锁定图像，使此变量成为机密变量。

    ![变量](media/test-studio-classic-pipeline-editor/variables.png)

1. **保存**管道配置。

## <a name="run-and-analyze-tests"></a>运行和分析测试

若要验证是否成功执行了测试，请选择 "**队列**"，然后选择 "**运行**"。 作业将开始运行。

![运行作业](media/test-studio-classic-pipeline-editor/run-job.png)

作业运行时，选择作业以查看每个运行的任务的详细状态：

![作业详细信息](media/test-studio-classic-pipeline-editor/job-details.png)

作业完成后，可以查看高级作业摘要，以及任何错误或警告。 通过选择 "测试" 选项卡，可以查看有关已执行的测试用例的特定详细信息。

下面的示例指示，使用 Chrome 浏览器执行测试时，至少有一个测试用例失败：

![Chrome-失败](media/test-studio-classic-pipeline-editor/chrome-failed.png)

选择 " **RunTestAutomation**测试" 以深入了解有关哪些测试用例已失败的详细信息。 在 "*附件" 选项卡*中，可以查看测试执行的摘要，以及测试套件中发生故障或通过的测试用例：

![附件选项卡](media/test-studio-classic-pipeline-editor/attachments-tab.png)

> [!NOTE]
> 如果执行测试套件，将会看到通过和失败的测试用例的摘要。 如果执行测试用例，将看到有关任何跟踪信息（如果有）的失败的特定详细信息。

## <a name="known-limitations"></a>已知限制

- 不支持多重身份验证。

- Internet Explorer 11 和 Microsoft Edge 不支持浏览器。

- 测试摘要将报告每个浏览器的单个测试结果。 测试结果将包含1个或多个测试用例或测试套件结果。   

- Azure Active Directory 登录流程以外的任何身份验证过程都需要在**PowerAppsTestAutomation**解决方案中自定义登录过程。

### <a name="see-also"></a>另请参阅

- [Test Studio 概述](test-studio.md)
- [使用 Test Studio](working-with-test-studio.md)