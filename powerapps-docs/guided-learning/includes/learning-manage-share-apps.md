虽然可以使用 PowerApps 轻松生成可满足你自己的业务需求的应用，但能够与其他人共享这些应用才是它的真正魅力所在。 至此，你已经知道如何生成应用，此主题将介绍如何共享应用。 可以与特定的用户或组共享应用，也可以与整个组织共享应用。 与其他人共享应用后，他们可以在浏览器中使用 Dynamics 365 运行应用，也可以使用适用于 Windows、iOS 或 Android 的 PowerApps Mobile 运行应用。 若向某人授予参与者权限，他/她还可以更新应用。

## <a name="prepare-to-share-an-app"></a>准备共享应用
必须先将应用保存到云中，然后才能与其他人共享。 为应用指定一个有意义的名称和提要，让其他人知道这是一个什么应用，并能在列表中快速找到它。 在 PowerApps Studio 中，单击或点击“**文件**”，然后输入提要。

![应用提要](./media/learning-manage-share-apps/app-description.png)

请注意，你对共享应用做出的任何更改一经保存，便会与共享对象同步。 如果你改进应用，便会发现这样非常棒；但如果你删除或大幅改动相关功能，也可能会对其他人造成影响。

## <a name="share-an-app"></a>共享应用
访问 web.powerapps.com，依次单击应用磁贴上的省略号 (. 。 .) 和“**共享**”。

![通过 web.powerapps.com 共享应用](./media/learning-manage-share-apps/share-app.png)

在这里，不仅可以共享应用，还可以控制应用版本（下一主题将对此进行介绍）。 指定要与之共享应用的用户和组，并指定每个共享对象应具有的角色（**用户**或**参与者**）。 单击或点击“**保存**”。

![选择用户和组](./media/learning-manage-share-apps/select-users.png)

若选择通过电子邮件通知用户，应用的每个共享对象都会收到包含 Dynamics 365 链接的电子邮件。 应用参与者收到的电子邮件中还包含 web.powerapps.com 链接。如果不单击 Dynamics 365 链接，共享对象就看不到应用。 虽然应用位于 AppSource 中，但共享对象仍必须自行将其添加到 Dynamics 365 中。

![Dynamics 365 中的应用](./media/learning-manage-share-apps/dynamics-365.png)

## <a name="permissions-and-licensing"></a>权限和授权
我们不会详细介绍权限和授权，但会介绍一些与共享相关的基础知识：

* 用户和参与者需要获得对共享应用使用的任何数据连接和网关的访问权限。 虽然应用隐式附带某些权限，但仍必须明确授予其他权限。
* 如果应用使用 Common Data Service 实体，用户和参与者需要获得对 Common Data Service 数据库的访问权限。 若要直接处理实体，参与者还需要获得 PowerApps "P2" 许可证。

共享应用非常简单，可以轻松挑选出你认为有用的应用，以供整个组织的其他用户使用。 下一主题将介绍如何在使用和共享应用时控制有效的应用版本。

