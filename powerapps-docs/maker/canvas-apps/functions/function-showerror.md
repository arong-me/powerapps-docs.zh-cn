---
title: 通知函数 |Microsoft Docs
description: Power Apps 中 Notify 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/28/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9a4facf4689ed09e7628411f1c55739f8980336f
ms.sourcegitcommit: 129d004e3d33249b21e8f53e0217030b5c28b53f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78265469"
---
# <a name="notify-function-in-power-apps"></a>在 Power Apps 中通知功能
向用户显示横幅消息。

## <a name="description"></a>说明
Notify 函数在屏幕顶部向用户显示一条横幅消息，覆盖当前显示的内容。  通知将保留，直到用户将其关闭，另一个通知替换它，或者默认为10秒的超时过期。

根据消息的类型，使用适当的颜色和图标。   该类型由该函数的第二个参数指定：

| NotificationType 参数 | 说明 |
| --- | --- |
| **NotificationType.Error** | 显示该消息表示错误。 |
| **NotificationType.Information**（默认） | 显示该消息表示信息。  |
| **NotificationType.Success** | 显示该消息表示成功。 |
| **NotificationType.Warning** | 显示该消息表示警告。 |

当你创作应用和终端用户使用应用时，均会显示消息。

Notify 只能在[行为公式](../working-with-formulas-in-depth.md)中使用。

Notify 可以搭配 [IfError](function-iferror.md) 函数使用，以检测错误并使用自定义错误消息报告错误。

Power Apps 还可以使用完全不同的机制从**通知**发送推送通知。  有关详细信息，请参阅[在 Power Apps 中发送通知](../add-notifications.md)。

Notify 始终返回“true”。

注意:如果此函数只能显示错误消息，则该函数以前名为**ShowError** 。

## <a name="syntax"></a>语法
**通知**（ *Message* [， *NotificationType* [， *Timeout* ]]）

* *Message* - 必需。  要向用户显示的消息。
* *NotificationType* - 可选。  从上表中显示的消息类型。  默认值为 NotificationType.Information。  
* *Timeout* –可选。  自动关闭通知之前要等待的毫秒数。  默认值为10秒（或10000毫秒）。  通知将会无限期显示，*超时*为0。

## <a name="examples"></a>示例

### <a name="step-by-step"></a>分步操作

1. 向屏幕添加“按钮”控件。

2. 将该**按钮**的**OnSelect**属性设置为公式：

    ```powerapps-dot
    Notify( "Hello, World" )
    ```

3. 单击或按下该按钮。  

    每次单击该按钮时，会将消息“Hello, World”作为信息显示给用户。  如果用户不取消或再次按下此按钮，它将在10秒（默认超时）内自动取消。

    ![在创作环境中，显示 Button.OnSelect、调用 Notify 并将生成的“Hello, World”消息作为蓝色横幅消息显示给用户](media/function-showerror/hello-world.png)

4. 更改消息的类型以指示错误。  将第二个参数添加到公式中：

    ```powerapps-dot
    Notify( "Hello, World", NotificationType.Error )
    ```

5. 单击或按下该按钮。

    现在，每次单击该按钮时，会将消息“Hello, World”作为错误显示给用户。  如果用户不取消或再次按下此按钮，它将在10秒（默认超时）内自动取消。

    ![在创作环境中，显示 Button.OnSelect、调用 Notify 并将生成的“Hello, World”消息作为红色横幅消息显示给用户](media/function-showerror/hello-world-error.png)

4. 更改消息的类型以指示警告。  更改公式中的第二个参数：

    ```powerapps-dot
    Notify( "Hello, World", NotificationType.Warning, 4000 )
    ```

5. 单击或按下该按钮。

    现在，每次单击该按钮时，会将消息“Hello, World”作为警告显示给用户。  如果用户不取消或再次按下此按钮，它将在4秒（4000毫秒）内自动取消。

    ![在创作环境中，显示 Button.OnSelect、调用 Notify 并将生成的“Hello, World”消息作为橙色横幅消息显示给用户](media/function-showerror/hello-world-warning.png)

4. 更改消息的类型以指示成功。  更改公式中的第二个参数：

    ```powerapps-dot
    Notify( "Hello, World", NotificationType.Success, 0 )
    ```

5. 单击或按下该按钮。

    现在，每次单击该按钮时，会将消息“Hello, World”显示给用户表示成功。  如果为**0** ，则仅用户或按下该按钮时，通知将被消除。

    ![在创作环境中，显示 Button.OnSelect、调用 Notify 并将生成的“Hello, World”消息作为绿色横幅消息显示给用户](media/function-showerror/hello-world-success.png)
