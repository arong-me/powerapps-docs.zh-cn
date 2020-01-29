---
title: 使用 Test Studio 测试画布应用 | Microsoft Docs
description: 通过示例介绍如何使用 Test Studio 测试画布应用。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/18/2019
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: afd2427a0c24461fa79e363787a7ec6c28bb4038
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541603"
---
# <a name="working-with-test-studio-experimental"></a>使用 Test Studio（实验性功能）

在本快速入门中，你将为名为 Kudos 的画布应用创建测试。 你还可以浏览和发现测试概念，并将其应用于为自己的画布应用编写测试。 示例 Kudos 应用是员工参与应用套件的一部分，可从[员工体验初学者套件](https://powerapps.microsoft.com/en-us/blog/powerapps-employee-experience-starter-kit)中下载。

> [!NOTE]
> 此功能仍为实验性功能，我们建议使用它来编写非生产应用的测试。 有关详细信息，请参阅[实验性功能和预览功能](working-with-experimental-preview.md)。

## <a name="open-test-studio"></a>打开 Test Studio

与其他实验性功能不同，你无需在应用中启用此功能。 Test Studio 默认适用于所有画布应用。

1. 登录到 [Power Apps](https://make.powerapps.com)。

2. 创建[新应用](get-started-test-drive.md)或[编辑现有应用](edit-app.md)。

3. 将应用保存到 Power Apps 以打开 Test Studio。 
    
    > [!NOTE]
    > 必须先保存应用，然后才能为应用编写测试。

4. 在左侧导航栏中，选择“高级工具”  。

5. 选择“打开测试”，为此应用程序打开 Test Studio  。 这会在新的浏览器选项卡中打开 Test Studio。

    ![打开 Test Studio](./media/working-with-test-studio/open-tests.png)

## <a name="create-a-test-suite"></a>创建测试套件

默认将在 Test Studio 中为你创建测试套件和测试用例。 测试套件用于将测试用例组织到一起。 一个应用可以包含一个或多个测试套件。 你可以使用默认测试套件和测试用例来立即开始编写测试，也可以创建新的测试套件。

1. 选择“新建套件”  。
2. 在主网格中选择字段，更新“测试套件名称和描述”  。

    ![新测试套件](./media/working-with-test-studio/new-test-suite.png)

## <a name="create-a-test-case"></a>创建测试用例

根据测试的组织或分组方式，你可以在测试套件中创建多个测试用例。 每个用例都可以测试应用中的特定功能或功能子集。

1. 选择测试套件。
2. 在顶部菜单中选择“新建用例”，创建一个新用例  。
3. 在主网格中选择字段，更新“测试用例名称和描述”  。

 ![新测试用例](./media/working-with-test-studio/new-test-case.png)

## <a name="record-a-test-case"></a>录制测试用例

测试用例由包含各种操作的测试步骤组成。 测试操作使用执行任务的 Power Apps 表达式编写。 与应用交互时，可以使用录制器自动生成测试步骤。 记录后，可以更新测试用例，添加新步骤，删除步骤，以及编写验证测试结果的测试断言。

> [!NOTE]
> 仅在录制模式下播放已发布的应用。 在开始录制测试用例之前，应向应用发布任何最近的更改。 录制而不发布最近的更改会导致上次发布的应用版本在录制模式下播放。

1. 在顶部菜单中选择“录制”  。 这会在新的浏览器选项卡中使用录制模式打开已发布的应用。

    > [!IMPORTANT]
    > 在现有测试用例上进行录制会覆盖已存在的任何现有测试步骤。

    ![录制测试](./media/working-with-test-studio/record-tests.png)

2. 与应用交互。 你的操作在左侧窗格中录制  。

3. 交互完成后，选择“完成”  。 （可选）可以选择“取消”返回 Test Studio，这将不会录制交互  。 

    ![保存录制](./media/working-with-test-studio/save-recording.png)

4. 查看在 Test Studio 中自动生成的测试步骤和表达式。
5. 如果需要，编辑主网格中的步骤描述文本。 你还可以通过在主网格中选择公式来更新测试步骤操作。

    ![更新测试用例](./media/working-with-test-studio/update-test-case.png)

### <a name="add-test-steps-and-test-assertions"></a>添加测试步骤和测试断言

每个测试用例都应有预期结果。 在 Kudos 示例中，发送 Kudo 的一个预期结果是在 Common Data Service (CDS) 数据库中创建一条新记录。 现在，你将更新测试用例并添加其他测试步骤来验证记录是否创建成功。

你需要执行以下步骤来验证记录是否创建成功：

- 在测试用例开始时，初始化数据库中 Kudo 记录计数的变量。
- 在测试用例结束时，初始化数据库中 Kudo 记录计数的变量。
- 编写测试断言表达式，验证计数是否递增。 如果计数不递增，则测试断言失败，并且你的测试用例会失败。

要在 Kudos 应用中添加测试步骤和测试断言，请执行以下操作：

1. 选择步骤 1 或要在其上方插入新步骤的步骤。 

2. 在顶部菜单中选择“在上方插入一个步骤”或从活动行中选择选项  。 这将创建一个空步骤。

    ![插入步骤](./media/working-with-test-studio/insert-step-above.png)

    > [!NOTE]
    > 选择“在上方插入一个步骤”后，将在当前步骤的上方添加一个新的空步骤  。 你还可以改用 Assert、SetProperty、Select 或 Trace 操作     。 这会添加带有可编辑的相应操作公式的步骤。

3. 更新步骤描述。 例如，“在数据库中对 Kudo 记录计数”。

4. 在执行测试前，在操作输入中输入表达式或公式以对数据库中的记录进行计数。

    你可以使用支持的任何表达式。 还可以查询应用中包含的任何数据源、集合、变量或运行流，以及创建要在测试中使用的新的全局变量或集合。

    ```Set(kudosBeforeTest, CountRows(Filter(Kudos, Receiver.Email = "someone@example.com")))```

5. 选择步骤 2 或要在其上方插入新步骤的步骤。

6. 在顶部菜单中选择“在上方插入一个步骤”或从活动行中选择选项  。 这将创建一个空步骤。

7. 在 [Trace](./functions/function-trace.md) 的操作输入中输入表达式或公式，并将 kudosBeforeTest 值写入测试结果记录  。

    ```Trace("kudosBeforeTest : " & kudosBeforeTest);```

    ![测试前的 Kudo 计数](./media/working-with-test-studio/kudos-before-test.png)

8. 测试完成后，转到测试用例的底部并插入一个新步骤，以对数据中的记录进行计数。

    ```Set(kudosAfterTest, CountRows(Filter(Kudos, Receiver.Email = "someone@example.com")))```

9. 添加最后一步，以验证数据库中的记录计数是否增加 1，然后输入以下断言操作验证这一点：

    ```Assert(kudosAfterTest = kudosBeforeTest + 1, "Kudos count incorrect. Expected : " & kudosBeforeTest + 1  & " Actual :" & kudosAfterTest)```

    ![测试断言后的 Kudo 计数](./media/working-with-test-studio/kudos-after-test-assert.png)

10. 在 Test Studio 的右上方菜单中保存测试用例。 

## <a name="play-back-your-test"></a>播放测试

你可以播放录制的测试来验证应用功能。 你可以播放单个测试套件或单个测试用例中的所有测试。 

在播放包含最近更改的录制之前，必须发布该应用：

![播放但不发布](./media/working-with-test-studio/publish-test-studio-changes.png)

> [!IMPORTANT]
> 如果跳过，录制播放将不包含最新的测试更改。 将对应用播放最近发布的测试用例或测试套件。

1. 单击“发布”  。 这会自动保存并发布你的测试。

    ![发布更改](./media/working-with-test-studio/publish-button.png)

2. 选择测试套件或单个测试用例。

3. 单击“播放”  。 已发布的应用将在“播放”模式下打开，并且你可以看到测试步骤自动播放  。 绿色的复选标记指示测试步骤执行成功。 如果某个步骤失败，将显示一个红色失败指示器以及一条失败消息

    ![播放模式](./media/working-with-test-studio/play-mode.png)

4. 单击“完成”返回 Test Studio。

### <a name="failed-assertion"></a>失败的断言

在本部分中，你将更改测试断言以体验失败的测试：

1. 选择表达式框，以编辑断言步骤。

2. 在测试操作中将 ```+ 1``` 更新为 ```+ 2```。 这意味着测试需要创建 2 条记录，这是不正确的。 如果测试成功，则只应在数据库中创建一条记录。

    ```Assert(kudosAfterTest = kudosBeforeTest + 2, "Kudos count incorrect. Expected : " & kudosBeforeTest + 2  & " Actual :" & kudosAfterTest)```

    ![断言计数更新](./media/working-with-test-studio/assert-count-update.png)

3. 选择“发布”  。

4. 选择“播放”  。

5. 查看正在播放的测试。 最后一个步骤会失败，并显示一个错误以及在断言步骤中提供的消息。  

    ![播放错误](./media/working-with-test-studio/playback-error.png)

### <a name="playing-tests-in-a-browser"></a>在浏览器中播放测试

你可以选择复制链接，以在 Test Studio 外的单独浏览器中播放测试。 这有助于在持续生成和发布管道（如 Azure DevOps）中集成测试  。

选定测试的播放链接保持不变。 它不会因测试套件或测试用例而更改。 你可以更新测试，而无需修改生成和发布过程。

要在浏览器中播放测试，请执行以下步骤：

1. 在右窗格中选择测试套件或测试用例。

2. 单击“复制播放链接”  。

    ![复制播放链接](./media/working-with-test-studio/copy-play-link.png)

3. 如果有任何未发布的更改，系统会提示你发布测试。

    ![复制之前发布链接](./media/working-with-test-studio/publish-before-copy-link.png)

4. 你可以选择跳过发布过程并复制播放链接。 如果跳过，新的测试更改将不会播放。

    ![复制播放链接](./media/working-with-test-studio/copy-play-link-ack.png)

5. 打开浏览器并将 URL 粘贴到地址栏中，以播放测试。

6. 查看正在播放的测试。

## <a name="processing-test-results"></a>处理测试结果

使用浏览器时，在 Test Studio 中播放测试时可见的测试面板将不可见。 因此，不能确定执行的特定测试步骤，也不能确定测试是通过还是失败。

要确定 Test Studio 外的测试结果，可以在测试对象中使用名为 OnTestCaseComplete 和 OnTestSuiteComplete 的两个属性，你可以使用这些属性来处理测试结果   。 将测试集成到持续生成和发布管道（如 Azure DevOps）中时，可使用这些属性确定是否应继续进行应用部署  。

每个用例或套件完成时，将触发为这些属性输入的表达式。 你可以自定义这些属性，以处理测试结果并将其发送到各种数据源或服务，例如：

- SQL Server。
- Common Data Service。
- Power Automate。
- 使用 Office 365 的电子邮件。

这些设置适用于应用中的每个测试套件或测试用例。 每个测试套件或测试用例完成后，可在 TestCaseResult 和 TestSuiteResult 记录中获得测试结果和测试中包含的任何 Trace 消息   。

TestCaseResult 记录包含以下属性  ：

- TestCaseName - 测试用例的名称  。
- TestCaseId - 测试用例的 ID  。
- TestSuiteName - 用例所属的测试套件名称  。
- TestSuiteId - 用例所属的测试套件 ID  。
- StartTime - 测试的开始执行时间  。
- EndTime - 测试的结束执行时间  。
- Traces - 任何测试断言的结果和来自 Trace 函数的任何消息  。
- Success -指示测试用例成功完成  。
- TestFailureMessage - 如果用例失败，则为失败消息  。

TestSuiteResult 记录包含以下属性  ： 

- TestSuiteName - 测试套件名称  。
- TestSuiteId - 测试套件 ID  。
- StartTime - 测试套件的开始执行时间  。
- EndTime - 测试套件的结束执行时间  。
- TestsPassed - 套件中成功完成的测试用例数  。
- TestsFailed - 套件中失败的测试用例数  。

在本快速入门中，你将在 Common Data Service 数据库中创建两个自定义实体，以通过自定义 OnTestCaseComplete 和 OnTestSuiteComplete 属性来存储测试结果   ：

1. 在左侧窗格中单击“测试”，或单击套件标头上的“查看”   。

    ![测试或查看设置的属性](./media/working-with-test-studio/test-or-view-to-set-property.png)

2. 选择 OnTestCaseComplete 操作  。

3. 输入用于处理测试结果的表达式。 下面的示例将每个测试用例的结果保存到 Common Data Service 中的自定义 AppTestResults 实体。 可以选择将测试结果存储到 SQL、SharePoint 或任何其他数据源。 可能需要根据需要在数据源中设置或增加 Trace 字段。

    > [!NOTE]
    > 以下示例需要 [Common Data Service 连接](https://docs.microsoft.com/connectors/commondataservice/)。 你可以创建[简单应用](data-platform-create-app.md)或使用 Common Data Service [从头开始生成应用](data-platform-create-app-scratch.md)。 另外，请参阅 [Patch](./functions/function-patch.md) 函数引用，详细了解如何修改以下示例中使用的数据源记录。

    ```
    //Save to Common Data Service
    Patch(AppTestResults
    , Defaults(AppTestResults)
    , {
             TestPass: TestCaseResult.TestCaseName & ":" & Text(Now())
             ,TestSuiteId: TestCaseResult.TestSuiteId
             ,TestSuiteName: TestCaseResult.TestSuiteName
             ,TestCaseId: TestCaseResult.TestCaseId
             ,TestCaseName: TestCaseResult.TestCaseName
             ,StartTime: TestCaseResult.StartTime
             ,EndTime: TestCaseResult.EndTime
             ,TestSuccess: TestCaseResult.Success
             ,TestTraces: JSON(TestCaseResult.Traces)
             ,TestFailureMessage: TestCaseResult.TestFailureMessage
    }
    );
    ```
    ![OnTestCaseComplete example.png](./media/working-with-test-studio/ontestcasecomplete-example.png)

4. 选择 OnTestSuiteComplete 操作  。

5. 输入用于处理测试结果的表达式。 在下面的示例中，你将每个测试用例的结果保存到 Common Data Service 中的自定义 AppTestSuiteResults 实体。 

    ```
    //Save to Common Data Service
    Patch(AppTestSuiteResults
        , Defaults(AppTestSuiteResults)
        , {
             TestSuiteId: TestSuiteResult.TestSuiteId
             ,TestSuiteName: TestSuiteResult.TestSuiteName
             ,StartTime: TestSuiteResult.StartTime
             ,EndTime: TestSuiteResult.EndTime
             ,TestPassCount: TestSuiteResult.TestsPassed
             ,TestFailCount: TestSuiteResult.TestsFailed
        }
    );
    ```

    ![OnTestSuiteComplete example.png](./media/working-with-test-studio/ontestsuitecomplete-example.png)

可以在这些属性中使用的其他表达式示例包括：

- 将结果发送到 Power Automate 中的流。

    ```MyTestResultsFlow.Run(JSON(TestCaseResult))```

- 通过电子邮件发送结果：

    ```Office365.SendMailV2(“someone@example.com”, “Test case results”, JSON(TestCaseResult, JSONFormat.IndentFour))```

- 接收测试结果的应用通知：

  例如，在 Test Studio 外的浏览器中播放测试时，测试完成后会收到通知。

    ```
    Notify(TestCaseResult.TestCaseName & " : "
            & If( TestCaseResult.Success
                , " Passed"
                , TestCaseResult.TestFailureMessage)
            ,If(  TestCaseResult.Success
                , NotificationType.Success
                , NotificationType.Error)
    )
    ```

## <a name="test-functions"></a>测试函数

除 Power Apps 中可用的[函数](formula-reference.md)外，以下是编写测试时通常会使用的常用函数。

- [选择](./functions/function-select.md)
- [SetProperty](./functions/function-setproperty.md)
- [ActualRebinds](./functions/function-assert.md)
- [Trace](./functions/function-trace.md)
