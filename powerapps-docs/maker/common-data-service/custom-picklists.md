---
title: 创建选项集 | Microsoft Docs
description: 有关如何创建选项集的分步说明。
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: b2b472ae33bd16761d25fc965f24afc6bb9b957e
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218409"
---
# <a name="create-an-option-set"></a>创建选项集

选项集可以将固定值的下拉列表包含到应用的用户，以确保数据一致性，有时在其他应用程序中将它称为选择列表或选择字段。 与实体相似，存在两个标准的选项集，并可以创建自定义选项集以便在应用中使用。

可以通过两种方式创建选项集，一种方式是从门户中的选项集列表创建，另一种方式是在创建字段时直接在实体中创建。 有关如何创建实体的详细信息，请参阅[创建实体](data-platform-create-entity.md)。

## <a name="creating-an-option-set-while-adding-a-field"></a>在添加字段时创建选项集。

1. 在 [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“实体”。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 单击或点击现有实体，或者[创建新实体](data-platform-create-entity.md)

3. 通过单击“添加字段”将新建字段添加到实体。

4. 在新建字段面板中，输入字段的“显示名称”，“名称”将自动填充，并用作字段的唯一名称。 在向用户显示此字段时使用“显示名称”，在生成应用时，在表达式和公式中使用“名称”。

    ![新建字段](./media/data-platform-cds-create-entity/newfieldpanel.png "新建字段面板")

5. 单击“数据类型”下拉列表，选择“选项集”，或“多选选项集”。

6. 单击“选项集”下拉列表，选择“新建选项集”

    > [!NOTE]
    > 如果可以为实体使用现有的选项集，则可以从此列表中选择它，而无需创建新的选项集。

    ![选项集列表](./media/data-platform-cds-newoptionset/fieldpanel-1.png "选项集列表")

7. 将打开一个新的面板以创建选项集，“显示名称”和“名称”将默认自该字段的名称，但可以根据需要更改。 单击“添加新项”以开始创建选项列表。 重复此步骤，直到创建所有项。

    ![新建选项集](./media/data-platform-cds-newoptionset/field-optionsetpanel.png "新建选项集")

8. 输入项之后，单击“保存”以创建选项集。

    ![新建选项集](./media/data-platform-cds-newoptionset/field-optionsetpanel-values.png "新建选项集")

9. 单击“完成”以关闭字段面板，然后单击“保存实体”以将实体保存到 Common Data Service。

    > [!NOTE]
    > 可以为此字段选择其中一个项作为“默认”，当用户在实体中创建新记录时，默认情况下将选择该项。

    ![新建字段](./media/data-platform-cds-newoptionset/fieldpanel-2.png "新建字段面板")

## <a name="creating-an-option-set-from-the-option-set-list"></a>从选项集列表创建选项集

1. 在 [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“选项集”。

    ![选项集](./media/data-platform-cds-newoptionset/optionsetlist.png "选项集列表")

2. 单击“新建选项集”

3. 将打开一个新面板以创建选项集，输入“显示名称”和“名称”。 单击“添加新项”以开始创建选项列表。 重复此步骤，直到创建所有项。

    ![选项集创建](./media/data-platform-cds-newoptionset/optionset-create.png "选项集创建")

4. 输入项之后，单击“保存”以创建选项集。

    ![新建选项集](./media/data-platform-cds-newoptionset/optionset-create-values.png "新建选项集")

5. 现在可以通过在实体上创建新字段来使用此选项集。

## <a name="global-and-local-option-sets"></a>全局和本地选项集

默认情况下，选项集作为全局选项集创建，这使它们可以在多个实体之间进行重用。 在“查看更多”选项下，创建新的选项集时，可以选择在“本地”创建选项集。 只有在添加字段时创建选项集（而不是通过选项集列表）时，此选项才可用。 本地选项集只能由它们所针对的实体和字段使用，不能在其他实体上重用。 此方法仅适用于需要本地选项集的高级用户。

> [!IMPORTANT]
> 一旦将选项集创建为本地或全局，则不能更改。