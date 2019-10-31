---
title: 在 PowerApps 中使用解决方案检查器验证应用 | Microsoft Docs
description: 可使用解决方案检查器验证解决方案。
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: article
ms.date: 07/09/2019
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-solution-checker-to-validate-your-model-driven-apps-in-powerapps"></a>在 PowerApps 中使用解决方案检查器验证模型驱动的应用

为了履行复杂的业务要求，模型驱动的应用开发者通常最终会推出极为高端的解决方案，用于自定义和扩展 Common Data Service 平台。 高级实施伴随着风险上升，并带来性能、稳定性和可靠性问题，从而影响用户的体验。 确定这些问题和了解其解决方法可能非常复杂，并且很费时间。 通过解决方案检查器，您可以使用一组最佳实践规则对解决方案执行各种静态分析检查，并快速确定这些问题模式。 检查完成后，将收到详细报告，其中列出了确定的问题，受影响的组件和代码，以及介绍各问题解决方法的文档的链接。

解决方案检查器分析以下解决方案组件： 
- Common Data Service 插件
- Common Data Service 自定义工作流活动 
- Common Data Service Web 资源（HTML 和 JavaScript）
- Common Data Service 配置，如 SDK 消息步骤 

解决方案检查器支持可从环境中导出的非托管解决方案。 

> [!NOTE]
> - 本主题介绍如何从 PowerApps 开发者门户运行解决方案检查器。 另外还提供 PowerShell 模块，您可以使用它来直接与服务交互。 Microsoft.PowerApps.Checker.PowerShell 模块可用于对支持的本地和在线环境版本的托管和非托管解决方案进行分析，或自动化服务并将服务集成到您的版本和发布管道中。 详细信息：[Microsoft.PowerApps.Checker.PowerShell 概述]( /powershell/powerapps/overview?view=pa-ps-latest#get-started-using-the-microsoftpowerappscheckerpowershell-module) 
> - 解决方案检查器不使用 ECMAScript 6 (2015) 或更高版本处理包含 JavaScript 的解决方案。 如果检测到使用这些版本之一的 JavaScript，将报告 Web 资源发生了 JS001 语法问题。

## <a name="enable-the-solution-checker"></a>启用解决方案检查器
默认情况下，所有 Common Data Service 环境中均已启用解决方案检查器。 在 PowerApps 的**解决方案**区域中选择非托管解决方案时，**解决方案检查器**菜单项可用。 如果**解决方案检查器**菜单中的**运行**选项不可用时，可以通过安装 PowerApps 检查器解决方案启用。 若要安装，请执行以下步骤：   

1. 登录 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后选择要启用解决方案检查器的 Common Data Service 环境。 
2. 在左侧导航窗格中，选择**解决方案**。
3. 在工具栏上，选择**解决方案检查器**，然后选择**安装** – 这将打开 Microsoft AppSource 页面。 如果浏览器阻止页面打开，需要允许弹出窗口。 

   > [!div class="mx-imgBorder"]
   > ![安装解决方案检查器](media/solution-checker-install.png "安装解决方案检查器")

4. 在 AppSource 页面中选择**免费试用**。 

5. 如果您同意，请接受条款和条件，然后选择环境以安装 PowerApps 检查器解决方案。 
6. 安装完毕后，在 PowerApps 站点上刷新**解决方案**列表以验证解决方案检查器是否可用。  
7. 若要检查解决方案，请[运行解决方案检查器](#run-the-solution-checker)。


<!-- ### Components created with the PowerApps checker
When you install the PowerApps checker these solution specific components are created. 
- Entities: The entities that are created are required to store the results of solution analysis and the status of analysis jobs in your environment.
   - Analysis Component
   - Analysis Job
   - Analysis Result
- System job: A system job is created so admins can remove solution analysis data from the environment. The job contains a configuration value, currently set to remove the solution analysis data after 60 days, which an administrator can override. 
- Security Roles: Two security roles, **Export Customizations**, and **Solution Checker** are created. These roles are required to export the solution for analysis, and storing the analysis results to the entities in your environment.
- User principle: The **PowerApps Advisor** user is created that allows the checker to authenticate with your Common Data Service environment and assign the two security roles, Export Customizations and Solution Checker. The PowerApps Advisor is an application user and does not consume a license.  -->

## <a name="run-the-solution-checker"></a>运行解决方案检查器
在环境中安装 PowerApps 检查器之后，如果在 PowerApps 的**解决方案**区域中选择非托管解决方案，将提供**解决方案检查器**菜单项。 

1. 登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 
2. 在左侧窗格中选择**解决方案**。 
3. 在要分析的非托管解决方案旁边，选择 **...**，指向**解决方案检查器**，然后选择**运行**。 

   > [!div class="mx-imgBorder"]
   > ![运行解决方案检查器命令](media/solution-checker-run.png "运行解决方案检查器命令")

4.  **解决方案**页面右上角的状态窗格显示**正在运行解决方案检查器**。 

    > [!div class="mx-imgBorder"]
    > ![解决方案检查器状态](media/solution-checker-status.png "解决方案检查器状态")
   
    请注意以下事项：
    - 解决方案检查器可能需要几分钟才能完成分析。 
    
    - 此时**解决方案**列表的 **解决方案检查**列中的状态为**正在运行...**。 
    
    - 检查完成后，您将收到电子邮件通知，PowerApps 站点的**通知**区域中也会显示通知。  

5.  检查完成后[查看报告](#review-the-solution-checker-report)。

## <a name="cancel-a-check"></a>取消检查

在环境中提交解决方案检查之后，可以通过**解决方案**页面右上区域中的状态窗格取消检查。 

如果取消检查，将停止运行解决方案检查，而解决方案检查状态将恢复为之前的状态。 

## <a name="solution-checker-states"></a>解决方案检查器状态
在环境中安装解决方案检查器之后，**解决方案**列表中将提供**解决方案检查**列。 此列显示解决方案的解决方案分析状态。 

|状态  |说明  |
|---------|---------|
|尚未运行    | 从未分析解决方案。        |
|正在运行     | 正在分析解决方案。       |
|无法完成     |  已请求分析解决方案，但是未成功完成。       |
|截止*日期和时间*的结果   | 解决方案分析完成，可下载结果。      |
|无法完成。 截止*日期和时间*的结果     | 最近的分析请求未成功完成。 可以下载最近的成功结果。         |
|由 Microsoft 检查     | 这是 Microsoft 托管解决方案。 不允许对这些解决方案进行解决方案分析。         |
|由发布方检查     | 这是第三方管理的解决方案。 现在不能对这些解决方案进行解决方案分析。        |


## <a name="review-the-solution-checker-report"></a>查看解决方案检查器报告
完成解决方案检查之后，可以在门户中查看分析报告，也可以从 Web 浏览器下载该报告。 门户中有用于筛选，按**问题**、**位置**或**严重性**为结果分组，以及查看解决方案中检测到的问题的详细信息的选项。 

1. 在左侧窗格中选择**解决方案**。
2. 在要查看解决方案检查器报告的非托管解决方案旁边，选择 **...**，指向**解决方案检查器**，然后选择**查看报告**。  
3. 选择问题以查看详细信息和有关如何解决的说明。

    > [!div class="mx-imgBorder"] 
    > ![](media/solution-checker-viewresults.png "解决方案检查器查看结果")

也可以下载解决方案检查结果。 将把解决方案检查器 zip 文件下载到您的 Web 浏览器指定的文件夹。下载报告为 [!INCLUDE [pn-excel-short](../../includes/pn-excel-short.md)] 格式，其中包含多个可视化项和列，用于帮助您识别解决方案中检测到的每个问题的影响、类型和位置。 还提供了有关如何解决问题的详细指示信息的链接。 

1. 在左侧窗格中选择**解决方案**。
2. 在要下载解决方案检查器报告的非托管解决方案旁边，选择 **...**，指向**解决方案检查器**，然后选择**下载报告**。  
3. 将把解决方案检查器 zip 文件下载到 Web 浏览器指定的文件夹。

下面是报告中每列的摘要。

|报告字段 |说明  |适用于组件   |
|---------|---------|---------|
|问题     |   解决方案中确定的问题的标题。      | 所有        |
|类别     | 确定的问题的分类，如**性能**、**使用情况**或**支持能力**。      |  所有     |
|严重性     | 表示确定的问题的潜在影响。 可用影响类型为**高**、**中**、**低**、**参考**。         |  所有       |
|指导     |  详细说明问题、影响和建议操作的文章的链接。       |  所有       |
|组件     |  确定有问题的解决方案组件。        |   所有      |
|Location     |  确定发生了问题的组件的位置和/或源文件，如程序集或 JavaScript 文件名。        |  所有       |
|行号     |  问题在受影响 Web 资源组件中的行号参考。       |  Web 资源       |
|模块     | 在程序集中检测到了问题的模块的名称。     |   插件或自定义工作流活动      |
|类型      | 在程序集中确定的问题的类型。        | 插件或自定义工作流活动        |
|成员     |  在程序集中确定的问题的编号。      | 插件或自定义工作流活动        |
|语句     | 导致问题的代码语句或配置。        |  所有       |
|注释     | 包含高级别解决方法步骤的问题相关详细信息。         |  所有       |


## <a name="best-practice-rules-used-by-solution-checker"></a>解决方案检查器使用的最佳实践规则

|解决方案组件  |规则名称  |规则说明  |
|---------|---------|---------|
|插件或工作流活动   | [il-specify-column](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-specify-column&client=PAChecker&source=featuredocs)  | 避免通过 Common Data Service 查询 API 选择所有列。     |
|插件或工作流活动   | [meta-remove-dup-reg](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-dup-reg&client=PAChecker&source=featuredocs)     | 避免重复的 Common Data Service 插件注册。     |
|插件或工作流活动   | [il-turn-off-keepalive](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-turn-off-keepalive&client=PAChecker&source=featuredocs)   | 在 Common Data Service 插件中与外部主机交互时，请将 KeepAlive 设置为 false。     |
|插件或工作流活动   | [il-avoid-unpub-metadata](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-unpub-metadata&client=PAChecker&source=featuredocs)   | 避免检索未发布的 Common Data Service 元数据。     |
|插件或工作流活动   | [il-avoid-batch-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-batch-plugin&client=PAChecker&source=featuredocs)   | 避免在 Common Data Service 插件和工作流活动中使用批处理请求类型。    |
|插件或工作流活动   | [meta-avoid-reg-no-attribute](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-no-attribute&client=PAChecker&source=featuredocs)  | 包括使用 Common Data Service 插件注册筛选属性。    |
|插件或工作流活动   | [meta-avoid-reg-retrieve](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-retrieve&client=PAChecker&source=featuredocs)  | 使用为 Retrieve 和 RetrieveMultiple 消息注册的 Common Data Service 插件时，请务必小心谨慎。    |
|插件或工作流活动   | [meta-remove-inactive](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-inactive&client=PAChecker&source=featuredocs)    | 删除 Common Data Service 中已停用的配置    |
|插件或工作流活动   | [il-meta-avoid-crm2011-depr-message](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm2011-depr-message&client=PAChecker&source=featuredocs)  | 请勿使用 Microsoft Dynamics CRM 2011 弃用的消息。     |
|插件或工作流活动   | [meta-avoid-crm4-event](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-crm4-event&client=PAChecker&source=featuredocs) | 请勿使用 Microsoft Dynamics CRM 4.0 插件注册插件。    |
|插件或工作流活动   | [il-avoid-specialized-update-ops](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-specialized-update-ops&client=PAChecker&source=featuredocs)  | 请勿在 Common Data Service 中使用特制更新操作请求。    | 
| 插件或工作流活动 |  [il-use-autonumber-feature](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-use-autonumber-feature&client=PAChecker)  |使用自动编号功能，而不是自定义的自动编号解决方案。 | 
| 插件或工作流活动  | [il-avoid-parallel-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-parallel-plugin&client=PAChecker)  | 应避免在插件中使用并行模式。  |
| 插件或工作流活动  | [il-avoid-lock-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-lock-plugin&client=PAChecker)  | 避免在插件中锁定静态成员。  |
| 插件或工作流活动  | [meta-avoid-retrievemultiple-annotation](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-retrievemultiple-annotation&client=PAChecker)  | 避免在批注 RetrieveMultiple 上注册插件。  |
|Web 资源  | [web-use-async](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-async&client=PAChecker&source=featuredocs)  |  与 HTTP 和 HTTPS 资源异步交互。   |
|Web 资源  | [meta-remove-invalid-form-handler](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-invalid-form-handler&client=PAChecker&source=featuredocs)  | 更正或删除无效的 Common Data Service 窗体事件注册。   |
|Web 资源  | [meta-remove-orphaned-form-element](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-orphaned-form-element&client=PAChecker&source=featuredocs)  | 更正或删除孤立的 Common Data Service 窗体事件注册。   |
|Web 资源  | [web-avoid-modals](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-modals&client=PAChecker&source=featuredocs)  | 避免使用模式对话框。   |
|Web 资源  | [web-avoid-crm2011-service-odata](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-odata&client=PAChecker&source=featuredocs)   | 请勿以 Microsoft Dynamics CRM 2011 OData 2.0 端点为目标。     |
|Web 资源  | [web-avoid-crm2011-service-soap](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-soap&client=PAChecker&source=featuredocs)  | 请勿以 Microsoft Dynamics CRM 2011 SOAP 服务为目标。   |
|Web 资源  | [web-avoid-browser-specific-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-browser-specific-api&client=PAChecker&source=featuredocs) | 请勿使用 Internet Explorer 旧 API 或浏览器插件。   |
|Web 资源  | [web-avoid-2011-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-2011-api&client=PAChecker&source=featuredocs)  | 请勿使用已弃用的 Microsoft Dynamics CRM 2011 对象模型。  |
|Web 资源  | [web-use-relative-uri](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-relative-uri&client=PAChecker&source=featuredocs)   | 请勿使用绝对 Common Data Service 端点 URL。    |
|Web 资源  | [web-use-client-context](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-client-context&client=PAChecker&source=featuredocs)  | 使用客户端上下文。   |
|Web 资源  | [web-use-dialog-api-param](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-dialog-api-param&client=PAChecker&source=featuredocs)   | 使用对话框 API 参数。   |
|Web 资源  | [web-use-org-setting](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-org-setting&client=PAChecker&source=featuredocs)   | 使用组织设置。   |
|Web 资源  | [web-use-grid-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-grid-api&client=PAChecker&source=featuredocs)   | 使用网格 API。    |
|Web 资源  | [web-avoid-isActivityType](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-isActivityType&client=PAChecker&source=featuredocs)   | 将 Xrm.Utility.isActivityType 方法替换为新的 Xrm.Utility.getEntityMetadata，并且在功能区规则中不使用。    |
|Web 资源  | [meta-avoid-silverlight](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-silverlight&client=PAChecker&source=featuredocs)   | 已弃用 Silverlight Web 资源。   |
| Web 资源  | [web-remove-debug-script](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-remove-debug-script&client=PAChecker)  | 避免在非开发环境中包含调试脚本。  | 
| Web 资源  | [web-use-strict-mode](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-strict-mode&client=PAChecker)  | 如果可能，使用严格模式。  | 
| Web 资源  | [web-use-strict-equality-operators](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-strict-equality-operators&client=PAChecker)  | 使用绝对相同的运算符。  | 
| Web 资源  | [web-avoid-eval](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-eval&client=PAChecker)  | 请勿使用“eval”函数或其等效项。  | 


### <a name="see-also"></a>另请参阅
[Common Data Service 的最佳实践和指南](../../developer/common-data-service/best-practices/index.md)<br />
[模型驱动应用的最佳实践和指南](../../developer/model-driven-apps/best-practices/index.md)<br />
[解决方案检查器的常见问题和解决](common-issues-resolutions-solution-checker.md)<br />
