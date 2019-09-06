---
title: 使用 PowerApps 禁用模型驱动应用程序中的自动保存 | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: 2e7f75dd-7a3f-4716-b995-b626929c0501
caps.latest.revision: 14
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="disable-auto-save-in-a-model-driven-app"></a>禁用模型驱动应用程序中的自动保存

自动保存可帮助应用程序用户关注其工作，而不必管理窗体中的保存数据操作。 大多数人都喜欢不必在每次更新记录时都要显式保存数据，但有些组织可能会有在设计上就要求显式保存的自定义项。 对于这些组织，可以使用选项来管理自动保存的应用方式。  
  
<a name="BKMK_HowAutoSaveWorks"></a>   

## <a name="how-auto-save-works"></a>自动保存如何工作  
 默认情况下，[更新后的实体和经典实体](create-design-forms.md#updated-versus-classic-entities)的所有的主窗体都将启用自动保存。 在创建（初始保存）了记录之后，对窗体所做的任何都会在完成更改后三十秒自动保存。 如果窗体中没有更改，则在打开窗体时不会发生自动保存。 在完成更改后，会重新计算自动保存开始前的 30 秒期间。 当前有人正在编辑的字段不会包括在自动保存中。 如果另外有人在您编辑记录的过程中更新了同一个记录，则在发生自动保存时，将会在窗体中检索和显示这些更改。  
  
 启用自动保存后，将仅为初次保存记录显示“保存”按钮。 创建记录之后，命令栏上的“保存”按钮会不显示，但在没有任何未保存的更改时会显示的右下角中，可以看到 ![“自动保存”按钮](media/auto-save-icon.png "“自动保存”按钮") 按钮。 此控件在自动保存禁用时也会显示。  
  
 可以选择此按钮以保存记录，然后立即刷新窗体中的数据。 当自动保存启用时，记录将被保存，只要您离开记录或关闭显示记录的单独窗口，都会保存记录。 对于未更新的窗体，不需要在窗体中显示**保存 & 关闭**按钮。  
  
<a name="BKMK_AutoSave"></a>   
## <a name="should-you-disable-auto-save"></a>是否应禁用自动保存？  
 如果您有在保存记录时执行的插件、工作流或窗体脚本，它们将在每次自动保存发生时运行。 如果这些扩展未设计成与自动保存一起工作，则可能导致不适宜的行为。 不管是否启用自动保存，插件、工作流和窗体脚本都应设计成查找特定的更改，不应对每个保存事件都无差别地执行。  
  
 如果您为窗体配置了审核，则将每次保存视为单独的更新。 如果有人在有未保存的更改的窗体上逗留超过三十秒，则当他们在执行自动保存后添加的其他数据，则将看到一条额外的输入。 如果您有依赖于审核数据的报告，并将每次保存视为单独的“触及”记录，则可能会看到触及的频率增加。 如果使用此方法，则应该考虑单个用户行为使其成为一个不可靠的指标，而与是否启用自动保存无关。  
  
<a name="BKMK_DisableAutoSaveOrg"></a>   
## <a name="disable-auto-save-for-the-organization"></a>为组织禁用自动保存  
 如果您确定自动保存将导致您使用的任何扩展出现总是，则可为组织将其禁用。 没有用于为单个实体或窗体禁用自动保存的设置。  
  
1. 转到**[设置](advanced-navigation.md#settings)** > **管理**。  
  
2.  选择**系统设置**。  
  
3.  对于**为所有窗体启用自动保存**选项，请选择**否**。  
  
<a name="BKMK_DisalbleAutoSaveForm"></a>   
## <a name="disable-auto-save-for-a-form"></a>为窗体禁用自动保存  
 如果要为特定实体窗体禁用自动保存，则可向实体中的 `OnSave` 添加代码。  
  
> [!NOTE]
>  窗体的自动保存将被禁用，但用户每次选择右下角的 ![“自动保存”按钮](media/auto-save-icon.png "“自动保存”按钮") 按钮时，仍将保存数据。 如果用户尝试离开或者关闭数据被更改了的窗体时，则会弹出是否需要保存更改的提示，以阻止用户离开或者关闭该窗体。  
  
1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。  
  
3.  打开要编辑的窗体。  
  
4.  创建 JavaScript Web 资源并将其添加到窗体：  
  
    1.  在窗体编辑器中的**窗体** 组下，选择**窗体属性**。  
  
    2.  在**事件**选项卡上的**窗体库**下，选择**添加**。  
  
    3.  在**查找记录**对话框中，选择**新建**。  
  
    4.  在 Web 资源窗体中，输入以下信息：  
  
        |||  
        |-|-|  
        |**姓名**|preventAutoSave|  
        |**显示名称**|阻止自动保存|  
        |**类型**|脚本(JScript)|  
  
    5.  在**类型**字段旁边，选择**文本编辑器**。  
  
    6.  在**来源**字段中，粘贴以下代码：  
  
        ```javascript  
        function preventAutoSave(econtext) {  
            var eventArgs = econtext.getEventArgs();  
            if (eventArgs.getSaveMode() == 70 || eventArgs.getSaveMode() == 2) {  
                eventArgs.preventDefault();  
            }  
        }  
  
        ```  
  
    7.  选择**确定**关闭文本编辑器。  
  
    8.  选择**保存**以保存 Web 资源，然后关闭“Web 资源”窗口。  
  
    9. 在**查找记录** 对话框中，您创建的新 Web 资源将处于选中状态。 选择**添加**关闭该对话框。  
  
5.  配置 OnSave 事件：  
  
    1.  在**窗体属性**窗口中的**事件处理程序** 分区，将**事件** 设置为**OnSave** 。  
  
    2.  选择**添加**。  
  
    3.  在**处理程序属性**窗口中，将**库**设置为在上一步中添加的 Web 资源。  
  
    4.  在**函数**字段中键入 `preventAutoSave`。 区分大小写。 不要包含引号。  
  
    5.  确保选中**已启用**。  
  
    6.  选中**将执行上下文作为第一个参数传递**。  
  
        > [!IMPORTANT]
        >  如果您不这么做，脚本将无法运行。  
  
         **处理程序属性**对话框应如下所示。 自定义前缀“new_”可能会由于为组织的默认发布商设置的自定义前缀而有差异。  
  
 ![Dynamics 365 中用于阻止自动保存的 OnSave 事件处理程序](media/prevent-auto-save-script.png "Dynamics 365 中用于阻止自动保存的 OnSave 事件处理程序")  
  
    7.  选择**确定**以关闭**处理程序属性**对话框。  
  
    8.  如果有 `OnSave` 的任何其他事件的事件处理程序，请使用绿色箭头将此处理程序移到顶部。  
  
6. 选择**确定**以关闭**窗体属性**对话框。  
  
7. 选择**保存并关闭**以关闭窗体。  
  
8. 在解决方案资源管理器中，单击**发布所有自定义项**。  
  
 在将此脚本应用于 `OnSave` 事件之后，当用户使用此窗体编辑记录时，将在窗体右下角出现**未保存的更改** 消息，就像未禁用自动保存时那样。 但是，在用户选择它旁边的 ![“自动保存”按钮](media/auto-save-icon.png "“自动保存”按钮") 按钮之前，该消息不会消失。  
  
## <a name="next-steps"></a>后续步骤  
 [创建和设计窗体](create-design-forms.md)      

 
