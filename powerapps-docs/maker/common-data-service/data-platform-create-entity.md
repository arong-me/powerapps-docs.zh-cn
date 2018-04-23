---
title: 创建自定义实体的快速入门 | Microsoft Docs
description: 创建以其他实体为基础的自定义实体或从头开始创建自定义实体的快速入门。
services: powerapps
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: e22a18bacb258ca46c8f36d647f9ebcc45282929
ms.sourcegitcommit: aa2d0166dccb38100183c093f293233b46f3669d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2018
---
# <a name="quickstart-create-a-custom-entity"></a>快速入门：创建自定义实体
可以创建自定义实体来存储特定于组织的数据。 然后可通过开发引用该实体的应用来显示该数据。 创建实体后，可以[创建或修改实体的一个或多个字段](data-platform-manage-fields.md)，以及 [构建实体之间的关系](data-platform-entity-lookup.md)。

这些说明将展示如何手动创建自定义实体，还可以使用 Power Query 以现有数据为基础创建实体。 有关详细信息，请参阅[使用 Power Query 新建实体](data-platform-cds-newentity-pq.md)

> [!NOTE]
> 创建实体前，请先参阅[实体参考](../../developer/common-data-service/reference/about-entity-reference.md)。 这些实体涵盖典型的方案，如客户和联系人。 如果有符合你要求的现成实体或仅需稍加更改的实体，可使用该实体以节省时间。

## <a name="create-an-entity"></a>创建实体
1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“实体”。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 从命令栏中，单击或点击“新建实体”。
3. 在“显示名称”字段中，输入一个易于识别的名称，以便在将来引用该实体。 这也用于使用该实体创建的窗体、图表和其他对象。 注意还会填充另外两个字段：

    * 复数显示名称 - 从 PowerApps 或 Flow 中与此实体交互时使用，并通过 Common Data Service WebAPI 作为实体的名称使用。 复数名称应自动生成，但可以更改。
    * 名称 - 这是实体的唯一名称，不得包含特殊字符或空格，且必须唯一。 此名称还包含在创建环境时设置的前缀，用于确保所创建的实体可以在其他环境中导出和导入，而不会与其他实体名称发生冲突。 可以通过为 Common Data Service 默认解决方案更新发布服务器上的前缀来更改此前缀。

    > [!NOTE]
    > 可以随时更新“显示名称”字段以在应用中以不同方式显示，在保存实体后，“名称”字段不能更改，因为这可能导致现有应用中断。

    ![新建实体](./media/data-platform-cds-create-entity/newentitypanel.png "新建实体面板")

4. 单击“下一步”，将转至实体详细信息页。 默认情况下，每个实体都以一个字段开头，在针对该实体创建查找时使用“主名称”字段。 它通常应该用于实体中存储的数据的名称或主描述。

    > [!NOTE]
    > 在第一次保存实体之前，可以更新“主名称”字段的名称和显示名称。 例如，如果想调用“学生名”字段而不是“主名称”

    ![实体详细信息](./media/data-platform-cds-create-entity/newentitydetails.png "新实体详细信息")

5. 可选：通过单击“添加字段”将文本字段添加到实体。 在“新字段”面板中，为字段输入“显示名称”并选择数据类型。 有关详细信息，请参阅 [管理实体中的字段](data-platform-manage-fields.md)。

    ![新字段](./media/data-platform-cds-create-entity/newfieldpanel-2.png "新字段面板")


6. 单击“完成”以添加字段，然后重复步骤 5 以添加其他字段。
7. 单击“保存实体”以保存实体并使它在应用中可用。

    实体将出现在数据库的实体列表中。 若要查看已创建的实体，可以将命令栏中的筛选器从“默认”更改为“自定义”

## <a name="system-fields"></a>系统字段
所有实体均包含系统字段。 这些字段为只读。 因此，无法更改或删除这些字段，且无法为它们赋值。 默认情况下，系统字段不会显示在字段列表中，即使它们存在于实体上。 若要查看所有字段，可以在命令栏上将筛选器从“默认”更改为“所有”。

若要详细了解与实体相关的元数据，请参阅[实体元数据](../../developer/common-data-service/entity-metadata.md)

## <a name="next-steps"></a>后续步骤
* [管理实体中的字段](data-platform-manage-fields.md)
* [定义实体之间的关系](data-platform-entity-lookup.md)
* [使用 Common Data Service 数据库生成应用](../canvas-apps/data-platform-create-app.md)
* [使用 Common Data Service 数据库从头开始创建应用](../canvas-apps/data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，我们收集自定义实体和字段名称并将其存储在诊断系统中。  我们利用这一知识来改进我们客户的通用数据模型。 创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区中的常见方案，并确定服务标准实体范围中的缺口，如与组织相关的架构。 Microsoft 无法访问或使用数据库表中与这些实体相关联的数据，此类数据也无法在预配了数据库的区域之外进行复制。 不过，请注意，自定义实体和字段名称可能可以进行跨区域复制，并根据我们的数据保留策略进行删除。 Microsoft 致力于保护你的隐私安全，我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)对此进行了详述。

