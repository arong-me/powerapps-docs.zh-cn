---
title: 创建选项集 | Microsoft Docs
description: 如何创建选项集的分步说明。
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-an-option-set"></a>创建选项集

选项集让您可以为应用程序内的用户包括固定值的下拉列表，以确保数据的一致性，在其他应用程序中有时也称为选择列表或选择字段。 类似于实体，有两个标准选项集，以及创建在应用程序内使用的自定义选项集的功能。

选项集可通过两种方式创建，从门户中的选项集列表或在创建字段时直接在实体内。 有关如何创建实体的详细信息，请参阅[创建实体](data-platform-create-entity.md)。

## <a name="creating-an-option-set-while-adding-a-field"></a>在添加字段时创建选项集。

1. 在 [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**实体**。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 单击或点按现有实体或[创建新实体](data-platform-create-entity.md)

3. 单击**添加字段**向实体添加新字段。

4. 在新字段面板中，为您的字段输入**显示名称**，**名称**将自动填充并用作字段的唯一名称。 **显示名称**在将此字段呈现给您的用户时使用，**名称**在生成应用程序时使用，使用表达式和公式形式。

    ![新建字段](./media/data-platform-cds-create-entity/newfieldpanel.png "新建字段面板")

5. 单击**数据类型**下拉列表并选择**选项集**或**多选选项集**。

6. 单击**选项集**下拉列表并选择**新建选项集**

    > [!NOTE]
    > 如果现有选项集可以用于您的实体，可以从此列表中选择，而无需创建新选项集。

    ![选项集列表](./media/data-platform-cds-newoptionset/fieldpanel-1.png "选项集列表")

7. 新面板将打开以创建选项集，**显示名称**和**名称**将默认为字段的名称，但如果需要可以更改。 单击**添加新项目**开始创建选项列表。 重复此步骤，直到您的所有项目全部创建。

    ![新建选项集](./media/data-platform-cds-newoptionset/field-optionsetpanel.png "新建选项集")

8. 一旦您输入了项目，单击**保存**创建您的选项集。

    ![新建选项集](./media/data-platform-cds-newoptionset/field-optionsetpanel-values.png "新建选项集")

9. 单击**完成**关闭字段面板，然后**保存实体**将实体保存到 Common Data Service。

    > [!NOTE]
    > 您可以选择其中一个项目作为此字段的**默认值**，它将在用户在实体中创建新记录时默认选项。

    ![新建字段](./media/data-platform-cds-newoptionset/fieldpanel-2.png "新建字段面板")

## <a name="creating-an-option-set-from-the-option-set-list"></a>从选项集列表创建选项集

1. 在 [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**选项集**。

    ![选项集](./media/data-platform-cds-newoptionset/optionsetlist.png "选项集列表")

2. 单击**新建选项集**

3. 新面板将打开以创建选项集，输入**显示名称**和**名称**。 单击**添加新项目**开始创建选项列表。 重复此步骤，直到您的所有项目全部创建。

    ![选项集创建](./media/data-platform-cds-newoptionset/optionset-create.png "选项集创建")

4. 一旦您输入了项目，单击**保存**创建您的选项集。

    ![新建选项集](./media/data-platform-cds-newoptionset/optionset-create-values.png "新建选项集")

5. 现在您可以通过在实体上创建新字段来使用此选项集。

## <a name="global-and-local-option-sets"></a>全局和本地选项集

默认情况下，选项集创建为全局选项集，这让它们可以在多个实体中重复使用。 在创建您可以选择来将选项集设置为**本地**的新选项集时，位于**查看更多**选项下。 此选项只可用于添加字段时创建选项集时，且不通过选项集列表。 本地选项集只能由其创建时所基于的实体和字段，不能在其他实体上重复使用。 此方法仅向对本地选项集有特定需求的高级用户。

> [!IMPORTANT]
> 在将选项集创建为本地或全局后将无法更改。
