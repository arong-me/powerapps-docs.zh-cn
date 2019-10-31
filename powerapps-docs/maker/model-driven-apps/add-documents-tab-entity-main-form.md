---
title: 将“文档”选项卡添加到实体的主窗体 | MicrosoftDocs
description: 了解如何将“文档”选项卡添加到实体的主窗体
s.custom: null
ms.date: 09/05/2019
ms.reviewer: null
ms.service: crm-online
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
author: Mattp123
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
search.audienceType:
  - customizer
search.app:
  - D365CE
---
# <a name="add-the-sharepoint-documents-tab-to-the-main-form-for-an-entity"></a>将“SharePoint 文档”选项卡添加到实体的主窗体
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

在实体主窗体上添加选项卡以显示 SharePoint 文档可帮助用户发现和使用模型驱动应用中可用的 SharePoint 集成功能。 

![文档文件选项卡](media/document-files-tab.png)

> [!IMPORTANT]
> 要使用此功能，必须启用文档管理。 详细信息：[使用 SharePoint 管理您的文档](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)

## <a name="add-the-documents-tab-in-the-formxml"></a>在 FormXML 中添加文档选项卡 
1.  新建解决方案。 登录 PowerApps 并转到**解决方案**，选择**新建解决方案**，然后输入必填信息和可选信息。 详细信息：[创建解决方案](../common-data-service/create-solution.md)
2. 将实体添加到要在主窗体上添加“文档”选项卡的解决方案中。 支持所有标准和自定义实体。 详细信息：[向解决方案添加现有组件](/powerapps/maker/common-data-service/use-solution-explorer#add-an-existing-component-to-a-solution)
3. 在解决方案中包括实体的窗体，例如客户实体的主窗体。 在实体旁边，选择 **...**，然后选择**编辑**。 选择**窗体**选项卡。如果缺少所需的窗体，请添加它。   

4. 将一列式选项卡添加到主窗体。 为此，在窗体设计器中选择窗体区域上的一个区域，选择**添加组件**，然后选择**一列式选项卡**。  
   ![插入一列式选项卡](media/insert-one-column-tab.png)

5. 在窗体设计器中，选择窗体设计器区域上的**新建选项卡**，选择**添加字段**，然后在左窗格中添加诸如*地址 1: 市/县*之类的字段。 您可以为选项卡使用任何文本或数字字段。![向选项卡添加字段](media/add-field-to-tab.png)
6. 重命名选项卡标签。 为此，选择**新建选项卡**，然后在右侧的属性窗格中用更具描述性的内容替换**新建选项卡**，例如*文件*。
7. 选择**保存**，选择**发布**，然后关闭窗体设计器。 
8. 在 PowerApps 开发者主页上，选择**解决方案**，选择该解决方案，然后选择**导出**将解决方案导出为非托管解决方案。 详细信息：[导出解决方案](../common-data-service/import-update-export-solutions.md#export-solutions) 
9. 提取解决方案，并使用 XML 或文本编辑器打开 customization.xml 文件。 
10. 在 customization.xml 中搜索 **label description="Files"**（或您在上一步中为选项卡标签指定的任何名称）。
11. 向下滚动到 control id="*field name*" 元素，例如 **control id="address1_city"**，然后将整个元素替换为本主题中的 [XML 示例](#xml-sample-for-adding-the-documents-tab-to-a-form)。 

    > [!div class="mx-imgBorder"] 
    > ![](media/form-xml.png "XML 示例插入点")

12. 对 XML 示例进行以下修改。 
    
     a. 找到 **RelationshipName** 元素，并将其替换为显示为 *entityLogicalName*_SharePointDocument 的架构名称。 例如，对于客户实体，关系的架构名称是 Account_SharePointDocument，这是本主题中 XML 示例的架构名称。 要查找其他实体的名称，请转到**设置** > **自定义** > **自定义系统** > **实体** > 选择实体 > 选择 **1:N 关系**。 找到类型为 **SharePointDocument** 的**相关实体**。 

      ![客户关系 SharePoint 文档](media/account-sharepointdocument.png)

     b. 创建一个全局唯一标识符 (guid)，并替换上一步中粘贴的**控件**元素中的现有 **uniqueid** guid，同时保留大括号 {}。  
       ![控件元素的唯一 ID](media/control-unique-id.png) c。 保存对 customizations.xml 进行的更改。 
13. 打开 solution.xml 文件，并增大**版本**元素值。 例如，从 *1.1.0.0* 到 *1.2.0.0*。 
14. 将所有解决方案文件打包到压缩 (zipped) 文件夹中，然后导入到您的环境中。 如果收到错误，您必须删除以前的解决方案，请这样做。 详细信息：[导入、更新和升级解决方案](../common-data-service/import-update-export-solutions.md) 

## <a name="xml-sample-for-adding-the-documents-tab-to-a-form"></a>将“文档”选项卡添加到窗体的 XML 示例
```xml
  <control id="DocumentSubGrid" classid="{E7A81278-8635-4d9e-8D4D-59480B391C5B}" indicationOfSubgrid="true" uniqueid="{9cd66b5c-8b7a-6433-c5a5-46a7245dd534}"> 
    <parameters> 
      <ViewId>{0016F9F3-41CC-4276-9D11-04308D15858D}</ViewId> 
      <IsUserView>false</IsUserView>         
      <RelationshipName>Account_SharepointDocument</RelationshipName>
      <TargetEntityType>sharepointdocument</TargetEntityType> 
      <AutoExpand>Fixed</AutoExpand> 
      <EnableQuickFind>false</EnableQuickFind> 
      <EnableViewPicker>true</EnableViewPicker> 
      <ViewIds /> 
      <EnableJumpBar>false</EnableJumpBar> 
      <ChartGridMode>Grid</ChartGridMode> 
      <VisualizationId /> 
      <IsUserChart>false</IsUserChart> 
      <EnableChartPicker>false</EnableChartPicker> 
      <RecordsPerPage>10</RecordsPerPage> 
      <HeaderColorCode>#F3F3F3</HeaderColorCode> 
    </parameters> 
  </control> 
```

### <a name="see-also"></a>另请参阅
[使用 SharePoint 管理您的文档](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)