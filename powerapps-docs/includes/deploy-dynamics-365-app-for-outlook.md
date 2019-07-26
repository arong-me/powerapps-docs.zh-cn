---
title: 部署 Dynamics 365 App for Outlook | MicrosoftDocs
ms.custom: ''
ms.date: 2017-04-20
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
ms.assetid: 09736e14-e744-48ca-a755-1b05bb55340e
caps.latest.revision: 39
author: jimholtz
ms.author: jimholtz
manager: brycho
ms.openlocfilehash: d75ec08a1d4d594136ca3339daa819cf89ee910a
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456778"
---
# <a name="deploy-dynamics-365-app-for-outlook"></a>部署 Dynamics 365 App for Outlook
在桌面、Web 或平板电脑上使用 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 时，用户可以通过使用 [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] 来充分利用 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 的强大功能。 例如，查看有关电子邮件或约会收件人的信息，或将 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 电子邮件或约会链接到 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 记录（如商机、帐户或案例）。 若要详细了解 [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] 提供的内容，请参阅 [Dynamics 365 App for Outlook 用户指南](http://go.microsoft.com/fwlink/p/?LinkID=613099)。  
  
> [!IMPORTANT]
>  [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 与 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] 不同。 自 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] 起，将 [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] 与 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] 配对是将 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 与 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 集成的首选方式。 请注意，当同一用户同时使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 和 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] 时，跟踪活动不受支持。 有关 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] 外接程序的信息，请参阅 [Dynamics 365 for Outlook 用户指南](http://go.microsoft.com/fwlink/p/?LinkID=524751)。  
>   
>  [委托用户](https://support.office.com/article/Allow-someone-else-to-manage-your-mail-and-calendar-9684B670-7588-4EEA-8717-9E5799047540)不能使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 来跟踪电子邮件。 对于委托用户，建议使用[文件夹级别跟踪或自动跟踪](https://www.microsoft.com/en-us/dynamics/crm-customer-center/overview-of-tracking-records-in-dynamics-365-for-outlook.aspx)。  
  
<a name="BKMK_Compare"></a>   
## <a name="comparing-dynamics-365-app-for-outlook-with-dynamics-365-for-outlook"></a>比较 Dynamics 365 App for Outlook 与 Dynamics 365 for Outlook  
 下表对 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 功能与 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]（也称为 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 客户端或外接程序）进行了比较（自 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] 起）。  
  
||||  
|-|-|-|  
|**功能**|**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**|**[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]**|  
|跟踪和设置电子邮件相关项|是|是|  
|跟踪和设置约会相关项|是|是|  
|跟踪和设置联系人相关项|是|是|  
|跟踪和设置任务相关项|否|是|  
|一键设置相关项|是|否|  
|显示收件人的摘要|是|否|  
|显示电子邮件/约会中的相关记录摘要|是|否|  
|适用于 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]|是|否|  
|适用于 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 桌面版|是|是|  
|适用于 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] for Mac|是|否|  
|适用于手机|是|否|  
|直接打开并创建 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 记录|是|是|  
|应用自定义窗体和业务逻辑|是|是|  
|脱机工作|否|是|  
|应用电子邮件模板|是|是|  
|应用销售宣传资料|是|是|  
|应用知识文章|是|是|  
|发送电子邮件后进行监视的功能|是|否|  
|对视图进行排序、筛选、格式设置、分组和分类|否|是|  
|创建 Word 邮件合并文档|否|是|  
|控制字段同步|否|是|  
  
<a name="BKMK_Requirements"></a>   
## <a name="requirements"></a>要求  
 使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 需要以下内容：  
  
-   [!INCLUDE[pn_crm_online_2016_update](../includes/pn-crm-online-2016-update.md)] 或 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]  
  
-   通过服务器端同步实现传入电子邮件的同步。 [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][设置电子邮件、约会、联系人和任务的服务器端同步](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)  
  
-   以下是所需特权  
  
> [!NOTE]
>  [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] 功能支持的配置和要求已在我们的文档中列出。 未记录的特定配置应视为不受支持。  
  
### <a name="required-privileges"></a>所需特权  
 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 通过“使用 Dynamics 365 App for Outlook”特权提供对 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 的访问权限。 如果用户不具备此特权，将收到以下错误：  
  
> “你尚未获得使用此应用的授权。 请与系统管理员联系，以更新设置。”  
  
 用户还必须具有以下实体的读取/写入特权。  
  
 “业务管理”选项卡：  
  
-   **Mailbox**  
  
 “自定义”选项卡：  
  
-   **实体**  
  
-   **字段**  
  
-   **关系**  
  
-   **系统应用程序元数据**  
  
-   **系统窗体**  
  
-   **用户应用程序元数据**  
  
-   **视图**  
  
##### <a name="set-the-privileges-for-a-security-role"></a>设置安全角色的特权  
  
1.  [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2.  单击“安全角色”。  
  
3.  选择一个安全角色，然后单击“业务管理”选项卡。  
  
4.  在“实体”部分中，查看“邮箱”特权设置。 安全角色应具有“用户”或更高级别的设置。  
  
5.  在“隐私相关特权”部分中，验证“使用 Dynamics 365 App for Outlook”是否已设置为“组织”。 如果没有，请单击“使用 Dynamics 365 App for Outlook”。  
  
### <a name="supported-configurations-with-microsoft-exchange"></a>Microsoft Exchange 支持的配置  
 自 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] 起，可以将应用与任何 [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] 或 [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] 和 [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] 或 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (on-premises) 的任意组合结合使用，包括混合配置。 这意味着可以在以下任何配置中使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]：  
  
|||  
|-|-|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (on-premises)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (on-premises)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
  
> [!NOTE]
>  如果使用 [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]，则需要使用 IFD 身份验证进行身份验证，如下所述。  
  
### <a name="supported-browsers-for-outlook-on-the-web"></a>Web 版 Outlook 支持的浏览器  
 可以在以下浏览器上配合使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 与 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]：  
  
-   [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)]、 [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)]或[!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]  
  
     支持以下配置：  
  
    -   为“Internet”安全区域启用了保护模式。 若要启用保护模式：在 IE 10 或 11 中，请转到“工具” > “Internet 选项” > “安全”选项卡 > “Internet”。  
  
    -   为“本地 Intranet”安全区域启用了保护模式。 若要启用保护模式：在 IE 10 或 11 中，请转到“工具” > “Internet 选项” > “安全”选项卡 > “本地 Internet”。  
  
    -   [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] URL 位于“本地 Intranet”安全区域的受信任网站列表中。 在 IE 10 或 11 中，请转到“工具” > “Internet 选项” > “安全”选项卡 > “本地 Internet” > “站点” > “高级”。  
  
-   [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)] 上的 [!INCLUDE[tn_Google_Chrome](../includes/tn-google-chrome.md)]（最新版本）  
  
-   [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)] 上的 [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)]（最新版本）  
  
-   Mac 或 OSX 上的 [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_Safari](../includes/tn-safari.md)]（版本 9 或版本 10）  
  
### <a name="supported-operating-systems-for-outlook-on-the-desktop"></a>桌面版 Outlook 支持的操作系统  
 可以在以下版本的 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 桌面版上使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]：  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2013 和 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016。  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] for Mac*。  
  
     *需要 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 版本 15.0.847.32 或更高版本。  
  
### <a name="supported-mobile-devices"></a>支持的移动设备  
 可以在以下任何手机和操作系统的移动浏览器中将 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 与 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] 结合使用：  
  
-   运行 iOS 版本 8、9 或 10 的 [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_iphone](../includes/tn-iphone.md)] 设备。  
  
-   运行 [!INCLUDE[tn_android](../includes/tn-android.md)] 4.4 (KitKat) 或 5.0 (Lollipop)、6 (Marshmallow) 或 7 (Nougat) 的 [!INCLUDE[tn_android](../includes/tn-android.md)] 手机。  
  
-   运行 [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)] 或 [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)] 的 [!INCLUDE[pn_windows_phone](../includes/pn-windows-phone.md)] 设备。  
  
### <a name="supported-clients-per-feature"></a>支持的客户端（按功能）  
 支持的 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 功能取决于所运行的客户端。 下表总结了 [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] 和 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 的每个客户端/配置支持哪些功能。  
  
 ![每个 Dynamics 365 App for Outlook 功能支持的客户端](media/clients-supported-for-each-dynamics-365-app-for-outlook-feature.png "Clients supported for each Dynamics 365 App for Outlook feature")  
  
 （1）[!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] 支持 [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)]、[!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)]、[!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]、[!INCLUDE[tn_Safari](../includes/tn-safari.md)] 9、[!INCLUDE[tn_Safari](../includes/tn-safari.md)] 10、[!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] 和 [!INCLUDE[tn_chrome](../includes/tn-chrome.md)]。  
  
 （2）移动 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]支持 [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)]、[!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)]、[!INCLUDE[tn_ios](../includes/tn-ios.md)] 8、[!INCLUDE[tn_ios](../includes/tn-ios.md)] 9、[!INCLUDE[tn_ios](../includes/tn-ios.md)] 10、[!INCLUDE[tn_android](../includes/tn-android.md)] KitKat (4.4)、[!INCLUDE[tn_android](../includes/tn-android.md)] Lollipop、[!INCLUDE[tn_android](../includes/tn-android.md)] Marshmallow 和 [!INCLUDE[tn_android](../includes/tn-android.md)] Nougat。  
  
 （3）跟踪撰写模式中的电子邮件和跟踪约会需要 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2013 CU14 或 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016。  
  
 （4）仅 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]2016 CU3 和 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.6741.1000 及更高版本支持跟踪联系人。  
  
 （5）Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] 中不支持添加电子邮件模板、知识管理文章和销售宣传资料。  
  
 （6）仅支持 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.7426.1049 及更高版本。  
  
 （7）仅支持 16.0.6741.1000 及更高版本。  
  
> [!NOTE]
>  目前（2017 日历年）不支持平板电脑。  
  
 [在这篇博客中阅读了解更多关于受支持的客户端的信息：Dynamics 365 App for Outlook 支持矩阵](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)  
  
### <a name="supported-servers"></a>支持的服务器  
 [使用 Office 外接程序的服务器要求](https://dev.office.com/docs/add-ins/overview/requirements-for-running-office-add-ins)有 [!INCLUDE[pn_Exchange_Server_2013_short](../includes/pn-exchange-server-2013-short.md)]、[!INCLUDE[pn_exchange_server_2016_short](../includes/pn-exchange-server-2016-short.md)] 或 [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]。  
  
### <a name="supported-languages"></a>支持的语言  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 支持以下语言：  
  
||||  
|-|-|-|  
|白俄罗斯语(保加利亚) - 1026|印地语(印度) - 1081|葡萄牙语(葡萄牙) - 2070|  
|中文(中华人民共和国) - 2052|匈牙利语 - 1038|罗马尼亚语 - 1048|  
|中文(台湾) - 1028|印度尼西亚语 - 1057|俄语 - 1049|  
|克罗地亚语(克罗地亚) - 1050|意大利语 - 1040|塞尔维亚语 - 2074|  
|捷克语(捷克共和国) - 1029|日语 - 1041|斯洛伐克语 - 1051|  
|丹麦语 - 1030|哈萨克语 - 1087|斯洛文尼亚语 - 1060|  
|荷兰语 - 1043|韩语 - 1042|西班牙语 - 3082|  
|英语 - 1033|Latvian - 1062|瑞典语 - 1053|  
|爱沙尼亚语 - 1061|立陶宛语 - 1063|泰语 - 1054|  
|芬兰语 - 1035|马来西亚语 - 1086|土耳其语 - 1055|  
|法语 - 1036|挪威语 - 1044|乌克兰语 - 1058|  
|德语 - 1031|波兰语 - 1045|越南语 - 1066|  
|希腊语- 1032|葡萄牙语(巴西) - 1046||  
  
<a name="BKMK_Deploy"></a>   
## <a name="deploy-dynamics-365-app-for-outlook"></a>部署 Dynamics 365 App for Outlook  
 设置 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] 并设置所需特权后，便可以将 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 推送到部分或所有用户，也可以让用户根据需要自行安装。  
  
> [!NOTE]
>  如果使用的是[!INCLUDE[pn_dyn_365_op](../includes/pn-dyn-365-op.md)]，请参阅下面的部分：[部署到 Dynamics 365 本地用户](#BKMK_DeployOnprem)  
  
#### <a name="to-push-the-app-to-users"></a>如何将应用推送给用户  
  
1.  转到“设置” >  “Dynamics 365 App for Outlook”。  
  
2.  如果希望让用户自动获得应用，请在“Dynamics 365 App for Outlook 入门”屏幕中，在“为符合条件的用户添加”下（如果是第二次或后续再打开此屏幕，可能需要单击“设置”），选择“自动将应用添加到 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]”复选框。 如果用户具有所需特权且电子邮件已通过 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] 同步，则无需再执行任何操作即可将应用推送给他们。 例如，如果向销售人员角色添加所需特权，然后将此角色分配给新用户，新用户将自动获得该应用。  
  
3.  执行下列操作之一:  
  
    -   若要将应用推送给所有符合条件的用户，请单击“为所有符合条件的用户添加应用”。  
  
    -   若要将应用推送给某些用户，在列表中选择这些用户，然后单击“将应用添加到 Outlook”。  
  
    > [!TIP]
    >  如果列表显示用户处于挂起状态或尚未添加，则可以单击该用户旁边的“了解详细信息”链接，查找状态的详细信息。  
  
4.  完成时，单击“保存”。  
  
#### <a name="to-have-users-install-the-app-themselves"></a>如何让用户自行安装应用  
  
1.  用户单击“设置”按钮![“设置”按钮](media/mp-ua-r16-settings.png "Settings button")，然后点击“Apps for Dynamics 365”。  
  
2.  在“Apps for Dynamics 365”屏幕中上，在“[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]”下，用户单击“将应用添加到 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]”。  
  
> [!NOTE]
>  必要时，用户还可自行禁用或删除外接程序。 有关详细信息，请参阅 [Dynamics 365 App for Outlook 用户指南](http://go.microsoft.com/fwlink/p/?LinkID=613099)。  
  
<a name="BKMK_DeployOnprem"></a>   
## <a name="to-deploy-to-dynamics-365-on-premises-users"></a>如何部署到 Dynamics 365 on-premises 用户  
 如果使用的是 Dynamics 365 on-premises，请执行以下步骤。  
  
-   为面向 Internet 的部署配置 Dynamics 365 服务器。 请参阅 [Configure IFD for Microsoft Dynamics 365](https://technet.microsoft.com/library/dn609803.aspx)（为 Microsoft Dynamics 365 配置 IFD）。  
  
-   如果要连接到 Exchange 内部部署，请配置 OAuth 提供程序并注册客户端应用。 请参阅[为使用 OAuth 的 Dynamics 365 应用程序配置 Windows Server 2012 R2](https://technet.microsoft.com/library/hh699726.aspx)。  
  
<a name="BKMK_Troubleshoot"></a>   
## <a name="troubleshooting-installation-problems"></a>安装问题疑难解答  
 如果你或用户在安装 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 时遇到问题，这可能是因为他们的 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 邮箱当前链接到了另一个 [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] 组织。 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 邮箱（电子邮件地址）仅可以在一个组织中同步约会、联系人和任务，隶属于该组织的用户仅可以使用一个 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 邮箱同步约会、联系人和任务。  如果想要更改主要同步组织，则可以覆盖存储在 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 中的设置。 有关详细信息，请参阅[此 KB 文章](https://support.microsoft.com/en-gb/help/3211627/incomingemailrejected-error-when-attempting-to-install-dynamics-365-app-for-outlook)。  
  
<a name="BKMK_Explore"></a>   
## <a name="explore-the-users-guide-and-train-your-users"></a>浏览用户指南和培训用户  
 如要了解如何使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]，[请参阅 Dynamics 365 App for Outlook 用户指南](http://go.microsoft.com/fwlink/p/?LinkID=613099)。  
  
 ![“Dynamics 365 App for Outlook 用户指南”页](media/dynamics-365-app-for-outlook-user-s-guide-page.png "Dynamics 365 App for Outlook User's Guide page")  
  
## <a name="see-also"></a>请参阅  
 [Dynamics 365 App for Outlook 用户指南](http://go.microsoft.com/fwlink/p/?LinkID=613099)   
 [在这篇博客中阅读了解更多关于受支持的客户端的信息：Dynamics 365 App for Outlook 支持矩阵](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)   
 [设置电子邮件、约会、联系人和任务的服务器端同步](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)   
 [添加用户、许可证和安全角色](https://msdn.microsoft.com/23612155-f92d-4871-a109-186419d5c19d)   
 [向 Microsoft Dynamics 365（联机）添加互操作功能](../DocSets/CRMIGv9_Admin/Toc/Add%20interoperation%20features%20to%20Microsoft%20Dynamics%20365%20\(online\).md)