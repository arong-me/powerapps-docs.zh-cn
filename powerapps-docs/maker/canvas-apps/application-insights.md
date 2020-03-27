---
title: 使用 Application Insights 分析应用遥测数据 |Microsoft Docs
description: 如何使用 Application Insights 分析应用遥测
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/25/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cf7e65d395e8ad28e434cc957502a5bce52a3e6e
ms.sourcegitcommit: 77e00640a59a7db9d67d3ac52f74d264cbe3a494
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2020
ms.locfileid: "80328907"
---
# <a name="analyze-app-telemetry-using-application-insights"></a>使用 Application Insights 分析应用遥测

你可以使用[Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)的功能[Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)来连接你的应用程序。 Application Insights 包含功能强大的分析工具，可帮助你诊断问题并了解用户对你的应用程序的实际操作。 

将应用连接到 Application Insights 后，可以收集相关信息，帮助你推动更好的业务决策，并改善应用的质量。

在本快速入门中，你将检测名为 Kudos 的画布应用。 这可帮助你浏览、发现遥测概念并将其应用于你自己的画布应用。 示例 Kudos 应用是一套可从 [员工体验初学者工具包](https://powerapps.microsoft.com/blog/powerapps-employee-experience-starter-kit)下载的员工参与应用套件的一部分。

## <a name="prerequisites"></a>先决条件

- 您必须具有对[Azure 门户](https://portal.azure.com)的访问权限。
- 你必须具有[创建 Azure 资源](https://docs.microsoft.com/azure/role-based-access-control/quickstart-assign-role-user-portal)的权限。

### <a name="optional"></a>可选

- 从[Employee Experience 初学者工具包](https://powerapps.microsoft.com/blog/powerapps-employee-experience-starter-kit)下载并安装 Kudos 应用。 你还可以改为使用现有应用程序。

## <a name="create-an-application-insights-resource"></a>创建 Application Insights 资源

你需要创建一个 Azure 应用程序 Insights 资源来存储这些事件，然后才能发送应用的遥测。

1. 登录到 [Azure 门户](https://portal.azure.com/)。

1. 搜索 Application Insights：

    ![Azure Application Insights](./media/application-insights/azureappinsights.png)

1. 创建 Application Insights 资源：

    ![添加 Azure 应用程序 Insights 资源](./media/application-insights/azureappinsights-add.png)

1. 输入适当的值，然后选择 "**查看 + 创建**"。 有关更多详细信息，请阅读[创建 Application Insights 资源](https://docs.microsoft.com/azure/azure-monitor/app/create-new-resource)。 

    ![创建资源](./media/application-insights/createresource.png)

1. 创建 Application Insights 实例后，你将看到实例概述。 复制**检测密钥**。 你将需要此密钥来配置你的应用程序。

    ![复制检测密钥](./media/application-insights/instrumentation-key.png)

## <a name="connect-your-app-to-application-insights"></a>将你的应用连接到 Application Insights

1. 登录到 [Power Apps](https://make.powerapps.com)。

1. 从左侧导航栏中选择 "**应用**"。 从应用列表中，选择 " **Kudos** " 应用，然后选择 "**编辑**"：

    ![编辑 Kudos 应用](./media/application-insights/edit-kudos-app.png)

    > [!NOTE]
    > 还可以改为[创建](open-and-run-a-sample-app.md)新应用或[编辑](edit-app.md)任何现有应用。

1. 从左侧导航树视图中选择 "**应用**对象"，并粘贴**检测密钥**：

    ![添加检测密钥](./media/application-insights/add-instrumentation-key.png)

1. **保存** & **发布**应用。

1. **播放**已发布的应用程序并浏览不同的屏幕。 

浏览不同屏幕时，会自动将事件记录到 Application Insights 包括用法详细信息，如：

- 从中访问应用的位置。
- 使用的设备。
- 使用的浏览器类型。

> [!IMPORTANT]
> 必须播放已发布的应用程序，才能将事件发送到 Application Insights。 在 Power Apps Studio 中预览应用时，不会将事件发送到 Application Insights。

## <a name="view-events-in-application-insights"></a>查看 Application Insights 中的事件

1. 登录到 [Azure 门户](https://portal.azure.com/)并打开[之前](#create-an-application-insights-resource)创建的 Application Insights 资源。

1. 在左侧导航窗格中向下滚动，然后选择 "**使用情况**" 部分下的 "**用户**"。 

    > [!NOTE]
    > **用户**视图显示应用的使用详细信息，如：
    > - 查看应用的用户数。
    > - 用户对应用的会话数。
    > - 为应用记录的事件数。
    > - 用户的操作系统和浏览器版本详细信息。
    > - 用户的区域和位置。
    > 
    > 有关更多详细信息，请参阅[Application Insights 中的用户、会话和事件分析](https://docs.microsoft.com/azure/azure-monitor/app/usage-segmentation)。

1. 选择其中一个用户会话，查看具体的详细信息。 你可以查看信息，如会话长度和访问的屏幕：

    ![用户的使用情况详细信息](./media/application-insights/appinsights-users.gif)

1. 选择左侧导航窗格中 "**使用情况**" 部分下的 "**事件**" 视图。 你可以查看所有应用程序会话中所查看的所有屏幕的摘要：

    ![应用的事件详细信息](./media/application-insights/appInsights-events.gif)

> [!TIP]
> 您可以使用的一些其他 Application Insights 功能包括：  
> - [**漏斗图**](https://docs.microsoft.com/azure/azure-monitor/app/usage-funnels)
> - [**队列**](https://docs.microsoft.com/azure/azure-monitor/app/usage-cohorts)
> - [**影响分析**](https://docs.microsoft.com/azure/azure-monitor/app/usage-impact)
> - [**保留分析**](https://docs.microsoft.com/azure/azure-monitor/app/usage-retention)
> - [**使用流**](https://docs.microsoft.com/azure/azure-monitor/app/usage-flows)

## <a name="create-custom-trace-events"></a>创建自定义跟踪事件

您可以将自定义跟踪直接写入 Application Insights 并开始分析特定于您的方案的信息。 [Trace](https://docs.microsoft.com/powerapps/maker/canvas-apps/functions/function-trace)函数允许你收集：

- 屏幕上控件的精细使用情况信息。
- 哪些特定用户在访问你的应用程序。
- 发生了什么错误。

跟踪还有助于诊断问题，因为当用户浏览应用并执行不同的操作时，可以发送信息的踪迹。

从应用程序中发送自定义跟踪信息到 Application Insights 时，跟踪消息有3个严重性：

- **信息**
- **出现**
- **条**

根据你的方案，你可以选择发送具有适当严重性的跟踪消息。 您可以查询数据并根据消息严重性执行特定操作。

> [!NOTE]
> 如果您要记录任何人员数据，您将需要考虑任何可能还需要实现的数据遵从性义务（如 GDPR）。

现在，你将更新应用程序并创建新的组件，以便在应用的每个屏幕上收集反馈。 你将写入要 Application Insights 的事件。

1. 登录到 [Power Apps](https://make.powerapps.com)。

1. 从左侧导航栏中选择 "**应用**"。 从应用列表中，选择 " **Kudos** " 应用，然后选择 "**编辑**"。

    > [!NOTE]
    > 还可以改为[创建](open-and-run-a-sample-app.md)新应用或[编辑](edit-app.md)任何现有应用。

1. 选择**树视图**中的 "**组件**" 选项：

    ![组件](./media/application-insights/new-component.png)

1. 选择 "**新组件**"，然后将宽度调整为200，将 "高度" 调整为 "75"：

    ![高度和宽度](./media/application-insights/resize-component.png)

1. 从菜单中选择 "**插入**"，然后选择**图标**以添加*哭脸*和*表情符号*图标：

    ![添加图标](./media/application-insights/add-icons.png)

1. 选择 "**新建自定义属性**" 以创建自定义属性：

    ![创建自定义属性](./media/application-insights/create-custom-property.png)

1. 输入 "属性*名称*" 和 "*显示名称*"，如*FeedbackSceen*。

1. 输入属性*说明*。

1. 选择 "**属性类型**" 作为 "**输入**"，并选择 "**数据类型**" 作为**屏幕**：

    ![自定义属性](./media/application-insights/custom-input-property.png)

    > [!NOTE]
    > 输入属性允许您捕获屏幕名称及其组件，以便您可以将此信息记录到 Application Insights。

1. 选择**树视图**中的组件，然后选择 "**更多操作**（**...**）"，然后选择 "**重命名**"，使用有意义的名称（如*FeedbackComponent*）重命名该组件。

    ![重命名组件和缺点](./media/application-insights/rename-component-icons.png)

1. 选择 "图标"，选择 "**更多操作**（**...**）"，然后选择 "**重命名**"，使用有意义的名称（如*FrownIcon*和*SmileIcon*）重命名图标。

1. 选择*FrownIcon*，选择**OnSelect**属性，然后在编辑栏中输入以下表达式：

    ```
    Trace(
       "App Feedback",
       TraceSeverity.Information,
           {
             UserName: User().FullName,
             UserEmail: User().Email,
             Screen: FeedbackComponent.FeedbackScreen.Name,
             FeedbackValue: "-1"
           }
         );
    Notify("Thanks for you feedback!");
    ```

    ![哭脸图标公式](./media/application-insights/frownicon-formula.png)

    > [!NOTE]
    > 公式表达式向 Application Insights 发送*用户名*、 *sendemail*、*屏幕*和*反馈*（值为 *-1*）。

1. 选择*SmileIcon*，选择**OnSelect**属性，然后在编辑栏中输入以下表达式：
    
    ```
    Trace(
       "App Feedback",
       TraceSeverity.Information,
           {
             UserName: User().FullName,
             UserEmail: User().Email,
             Screen: FeedbackComponent.FeedbackScreen.Name,
             FeebackValue: "1"
           }
         );
    Notify("Thanks for you feedback!");
    ```

1. 将组件添加到应用中的一个屏幕：

    ![添加反馈组件](./media/application-insights/add-feedback-component.png)

1. 选择 "**保存**"，然后选择 "**发布**" 以保存 & 发布应用。

1. 播放已发布的应用，并在屏幕上发送微笑和哭脸的反馈。

    > [!IMPORTANT]
    > 必须播放已发布的应用程序，才能将事件发送到 Application Insights。 在 Power Apps Studio 中预览应用时，不会将事件发送到 Application Insights。

    ![播放已发布应用](./media/application-insights/play-published-app.png)

## <a name="analyze-data-in-application-insights"></a>分析 Application Insights 中的数据

你现在可以开始使用 App Insights 中的应用程序中的[跟踪](#create-custom-trace-events)函数来分析发送的数据。

1. 登录到 [Azure 门户](https://portal.azure.com/)并打开[之前](#create-an-application-insights-resource)创建的 Application Insights 资源：

    ![选择 application insights](./media/application-insights/select-app-insights.png)

1. 从左侧导航窗格中选择 "**监视**" 下的 "**日志**"：

    ![选择日志](./media/application-insights/select-logs.png)

1. 输入以下查询，然后选择 "**运行**"。 返回从应用收到的反馈：

    ```powerappsfl
    traces
    | where message == "App Feedback"
    | order by timestamp
    ```

    ![查看应用反馈](./media/application-insights/view-app-feedback.png)

1. 在结果中选择一行，然后展开 "*自定义维度*" 字段。 

    已记录组件中笑脸或哭脸图标**OnSelect**事件的 "**屏幕**"、"**用户名**"、" **sendemail**" 和 " **FeedbackValue** " 的值。 <br>
    还会为发送到 Application Insights 的每个事件记录其他一些值;例如**appId**、 **appName**和**appSessionId**。

    ![展开自定义维度](./media/application-insights/expand-custom-dimensions.png)

1. 利用下面的示例查询，您可以扩展 JSON 自定义维度的属性并在 "结果" 视图中项目列。

    ```powerappsfl
    traces
        | extend customdims = parse_json(customDimensions)
        | where message == "App Feedback"
        | project timestamp
            , message
            , AppName = customdims.['ms-appName']
            , AppId = customdims.['ms-appId']
            , FeedbackFrom = customdims.UserEmail
            , Screen = customdims.Screen
            , FeedbackValue = customdims.FeedbackValue
        | order by timestamp desc
    ```

    ![扩展 customDimensions 查询](./media/application-insights/custom-dimensions-extend-query.png)

    > [!TIP]
    > *日志查询*功能非常强大。 您可以使用它们来联接多个表，聚合大量数据并执行复杂的操作。 有关详细信息，请参阅[日志查询](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)。

## <a name="export-data-to-power-bi"></a>将数据导出到 Power BI

可以将 Application Insights 数据和查询结果导出到 Power BI，以便进行分析和数据显示。

1. 登录到 [Azure 门户](https://portal.azure.com/)并打开[之前](#create-an-application-insights-resource)创建的 Application Insights 资源：

1. 从左侧导航窗格中选择 "**监视**" 下的 "**日志**"：

1. 从 log analytics 查询窗口中，选择 "**导出**" 下拉菜单。

1. 选择 "**导出到 Power BI （M 查询）** " 选项。 这会将 Power BI 查询文件下载到计算机：

    ![导出 Power BI 查询](./media/application-insights/export-powerbi-query.png)

1. 在文本编辑器中打开下载的文件，并将该查询复制到剪贴板。

1. 打开 Power BI。

1. 选择 "**主页**" 功能区中的 "**获取数据**" 下拉菜单，然后选择 "**空白查询**"：

    ![Power BI 空查询](./media/application-insights/powerbi-blank-query.png)

1. 在查询窗口中，选择 "**高级编辑器**"。 将步骤5中的查询粘贴到窗口中，选择 "**完成**"，然后选择 "**关闭 & 应用**"：

    ![Power BI 高级查询](./media/application-insights/powerbi-advance-query.png)

1. 你还可以在 Power BI 中创建图表和可视化效果，以表示应用中收到的反馈。 并做出基于数据的决策和操作。

    ![图表和可视化效果](./media/application-insights/powerbi-feedback.png)

## <a name="default-trace-event-context-and-dimensions"></a>默认跟踪事件上下文和维度

还会将一组默认维度添加到每个跟踪事件的*customDimensions*属性中。 这些维度可用于标识发生事件的应用程序和应用程序会话。 如果使用 trace 函数记录其他自定义数据，则这些数据也将出现在自定义维度中。

| 维度名称  | 表示                                            |
|-----------------|-------------------------------------------------------|
| ms-appId        | 发送事件的应用的应用程序 ID     |
| ms-appName      | 发送事件的应用程序的应用程序名称   |
| ms-appSessionId | 应用程序会话 ID。                           |

