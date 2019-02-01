---
title: 在 PowerApps 中使用解决方案检查器验证应用 | Microsoft Docs
description: 可使用解决方案检查器验证解决方案。
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: article
ms.date: 12/04/2018
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-solution-checker-to-validate-your-model-driven-apps-in-powerapps"></a>在 PowerApps 中使用解决方案检查器验证模型驱动的应用

为了履行复杂的业务要求，模型驱动的应用开发者通常最终会推出极为高端的解决方案，用于自定义和扩展面向应用的 Common Data Service (CDS) 平台。 高级实施伴随着风险上升，并带来性能、稳定性和可靠性问题，从而影响用户的体验。 确定这些问题和了解其解决方法可能非常复杂，并且很费时间。 通过解决方案检查器，您可以使用一组最佳实践规则对解决方案执行各种静态分析检查，并快速确定这些问题模式。 检查完成后，将收到详细报告，其中列出了确定的问题，受影响的组件和代码，以及介绍各问题解决方法的文档的链接。

解决方案检查器分析以下解决方案组件： 
- 面向应用程序的 CDS 插件
- 面向应用程序的 CDS 自定义工作流活动 
- 面向应用程序的 CDS Web 资源（HTML 和 JavaScript）
- 面向应用程序的 CDS 配置，如 SDK 消息步骤 

解决方案检查器支持可从环境中导出的非托管解决方案。 解决方案检查器*不*支持以下解决方案： 


<!--from editor: Should it be Common Data Service (singular) below, rather than Services? -->

- 系统默认解决方案（默认解决方案和 Common Data Services 默认解决方案）。
- 包含使用 ECMAScript 6 (2015) 或更高版本的 JavaScript 的解决方案。 如果检测到使用这些版本之一的 JavaScript，将报告 Web 资源发生了 JS001 语法问题。


## <a name="enable-the-solution-checker"></a>启用解决方案检查器
安装 PowerApps 检查器解决方案之后，PowerApps 的“解决方案”区域中将提供解决方案检查器。 请注意，在 Microsoft AppSource 中浏览或搜索找不到此功能。 若要安装，请执行以下步骤：  

1. 登录 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后选择要启用解决方案检查器的 Common Data Service 环境。 
2. 在左侧导航窗格中，选择**解决方案**。
3. 在工具栏上，选择**解决方案检查器**，然后选择 **安装** – 这将打开 Microsoft AppSource 页面。 如果浏览器阻止页面打开，需要允许弹出窗口。 

   > [!div class="mx-imgBorder"]
   > ![安装解决方案检查器](media/solution-checker-install.png "安装解决方案检查器")

4. 在 AppSource 页面中选择**免费试用**。 


<!--from editor: Should it be "solution checker" rather than "checker solution" in the following step?

5. If you agree, accept the terms and conditions and select the environment to install the PowerApps checker solution. 
6. When the installation is complete, refresh the **Solution** list on the PowerApps site to verify that the solution checker is available.  
7. To check a solution, [Run the solution checker](#run-the-solution-checker).


<!-- ### Components created with the PowerApps checker
When you install the PowerApps checker these solution specific components are created. 
- Entities: The entities that are created are required to store the results of solution analysis and the status of analysis jobs in your environment.
   - Analysis Component
   - Analysis Job
   - Analysis Result
- System job: A system job is created so admins can remove solution analysis data from the environment. The job contains a configuration value, currently set to remove the solution analysis data after 60 days, which an administrator can override. 
- Security Roles: Two security roles, **Export Customizations**, and **Solution Checker** are created. These roles are required to export the solution for analysis, and storing the analysis results to the entities in your environment.
- User principle: The **PowerApps Advisor** user is created that allows the checker to authenticate with your CDS for Apps environment and assign the two security roles, Export Customizations and Solution Checker. The PowerApps Advisor is an application user and does not consume a license.  -->

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
解决方案检查完成后，可从 Web 浏览器下载分析报告。 报告的格式为 [!INCLUDE [pn-excel-short](../../includes/pn-excel-short.md)]，其中包含若干可视化效果和列，可帮助您确定解决方案中检测到的每个问题的影响、类型和位置。 还提供了有关如何解决问题的详细指示信息的链接。 

1. 在左侧窗格中选择**解决方案**。
2. 在要下载解决方案检查器报告的非托管解决方案旁边，选择 **...**，指向**解决方案检查器**，然后选择**下载最近的报告**。  
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
|插件或工作流活动   | [il-specify-column](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-specify-column&client=PAChecker&source=featuredocs)  | 避免通过 Dynamics 365 for Customer Engagement 查询 APIs 选择所有列。     |
|插件或工作流活动   | [meta-remove-dup-reg](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-dup-reg&client=PAChecker&source=featuredocs)     | 避免重复注册 Dynamics 365 for Customer Engagement 插件。     |
|插件或工作流活动   | [il-turn-off-keepalive](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-turn-off-keepalive&client=PAChecker&source=featuredocs)   | 在 Dynamics 365 for Customer Engagement 插件中与外部主机交互时，请将 KeepAlive 设置为 false。     |
|插件或工作流活动   | [il-avoid-unpub-metadata](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-unpub-metadata&client=PAChecker&source=featuredocs)   | 避免检索未经发布的 Dynamics 365 for Customer Engagement 元数据。     |
|插件或工作流活动   | [il-avoid-batch-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-batch-plugin&client=PAChecker&source=featuredocs)   | 避免在 Dynamics 365 Customer Engagement 插件和工作流活动中使用批处理请求类型。    |
|插件或工作流活动   | [meta-avoid-reg-no-attribute](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-no-attribute&client=PAChecker&source=featuredocs)  | 包括使用 Dynamics 365 for Customer Engagement 插件注册过滤属性。    |
|插件或工作流活动   | [meta-avoid-reg-retrieve](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-retrieve&client=PAChecker&source=featuredocs)  | 使用为 Retrieve 和 RetrieveMultiple 消息注册的 Dynamics 365 for Customer Engagement 插件时，请务必小心谨慎。    |
|插件或工作流活动   | [meta-remove-inactive](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-inactive&client=PAChecker&source=featuredocs)    | 删除 Dynamics 365 for Customer Engagement 中的已停用配置。    |
|插件或工作流活动   | [避免使用 window.top](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-window-top&client=PAChecker&source=featuredocs)   | 避免使用 window.top。    |
|插件或工作流活动   | [il-meta-avoid-crm2011-depr-message](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm2011-depr-message&client=PAChecker&source=featuredocs)  | 请勿使用 Microsoft Dynamics CRM 2011 弃用的消息。     |
|插件或工作流活动   | [meta-avoid-crm4-event](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-crm4-event&client=PAChecker&source=featuredocs) | 请勿使用 Microsoft Dynamics CRM 4.0 插件注册插件。    |
|插件或工作流活动   | [il-avoid-specialized-update-ops](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-specialized-update-ops&client=PAChecker&source=featuredocs)  | 请勿在 Dynamics 365 for Customer Engagement 中使用特制更新操作请求。        |
|Web 资源  | [web-use-async](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-async&client=PAChecker&source=featuredocs)  |  与 HTTP 和 HTTPS 资源异步交互。   |
|Web 资源  | [meta-remove-invalid-form-handler](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-invalid-form-handler&client=PAChecker&source=featuredocs)  | 更正或删除无效的 Dynamics 365 for Customer Engagement 窗体事件注册。   |
|Web 资源  | [meta-remove-orphaned-form-element](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-orphaned-form-element&client=PAChecker&source=featuredocs)  | 更正或删除孤立的 Dynamics 365 for Customer Engagement 窗体事件注册。   |
|Web 资源  | [web-avoid-modals](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-modals&client=PAChecker&source=featuredocs)  | 避免使用模式对话框。   |
|Web 资源  | [web-avoid-crm2011-service-odata](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-odata&client=PAChecker&source=featuredocs)   | 请勿以 Microsoft Dynamics CRM 2011 OData 2.0 端点为目标。     |
|Web 资源  | [web-avoid-crm2011-service-soap](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-soap&client=PAChecker&source=featuredocs)  | 请勿以 Microsoft Dynamics CRM 2011 SOAP 服务为目标。   |
|Web 资源  | [web-avoid-browser-specific-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-browser-specific-api&client=PAChecker&source=featuredocs) | 请勿使用 Internet Explorer 旧 API 或浏览器插件。   |
|Web 资源  | [web-avoid-2011-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-2011-api&client=PAChecker&source=featuredocs)  | 请勿使用已弃用的 Microsoft Dynamics CRM 2011 对象模型。  |
|Web 资源  | [web-use-relative-uri](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-relative-uri&client=PAChecker&source=featuredocs)   | 请勿使用面向应用程序的绝对 CDS 端点 URL。    |
|Web 资源  | [web-use-client-context](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-client-context&client=PAChecker&source=featuredocs)  | 使用客户端上下文。   |
|Web 资源  | [web-use-dialog-api-param](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-dialog-api-param&client=PAChecker&source=featuredocs)   | 使用对话框 API 参数。   |
|Web 资源  | [web-use-org-setting](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-org-setting&client=PAChecker&source=featuredocs)   | 使用组织设置。   |
|Web 资源  | [web-use-grid-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-grid-api&client=PAChecker&source=featuredocs)   | 使用网格 API。    |
|Web 资源  | [web-avoid-isActivityType](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-isActivityType&client=PAChecker&source=featuredocs)   | 将 Xrm.Utility.isActivityType 方法替换为新的 Xrm.Utility.getEntityMetadata，并且在功能区规则中不使用。    |
|Web 资源  | [meta-avoid-silverlight](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-silverlight&client=PAChecker&source=featuredocs)   | 已弃用 Silverlight Web 资源。   |


## <a name="see-also"></a>另请参阅
[有关构建 PowerApps 解决方案的指南和最佳实践](https://docs.microsoft.com/dynamics365/customer-engagement/guidance/)
