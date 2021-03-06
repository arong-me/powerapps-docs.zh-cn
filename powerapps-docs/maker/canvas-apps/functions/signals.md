---
title: Acceleration、App、Compass、Connection 和 Location 信号 | Microsoft Docs
description: Power Apps 中的加速、应用、指南针、连接和位置传感器的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1cd90e345b41f8316e8cd8c50f4077ee1f64ee91
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "79212621"
---
# <a name="acceleration-app-compass-connection-and-location-signals-in-power-apps"></a>Power Apps 中的加速、应用、指南针、连接和位置信号

返回关于应用环境的信息，例如用户的全球所在位置，以及所显示的是哪个屏幕。

## <a name="description-and-syntax"></a>说明和语法

信号是可随时更改的值，与用户可能与应用交互的方式无关。 基于信号的公式将在这些值更改时自动重新计算。

信号通常返回信息的[记录](../working-with-tables.md#records)。 可以使用此信息并将其存储为记录，也可提取单个属性，其方式是使用“.” [运算符](operators.md)。

> [!NOTE]
> **加速**和**罗盘**函数在本机播放机（如 iOS 或 Android）中返回准确的值，但在浏览器中创建或修改应用时，这些函数将返回零值。

### <a name="acceleration"></a>Acceleration

**Acceleration** 信号以相对于设备屏幕的三维方式返回设备的加速度。 Acceleration 的测量单位为 g（9.81 m/s<sup>2</sup> 或 32.2 ft/s<sup>2</sup>）（地球由于重力而在其表面对物体产生的加速度）。

| 属性 | 说明 |
| --- | --- |
| **Acceleration.X** |右侧和左侧。  右侧为正数。 |
| **Acceleration.Y** |前方和后方。  前方为正数。 |
| **Acceleration.Z** |上方和下方。  上方为正数。 |

### <a name="app"></a>应用程序

除了其他属性，**应用程序**对象还包含指示所显示屏幕的信号。

| 属性 | 说明 |
| --- | --- |
| **App.ActiveScreen** |显示的屏幕。 返回一个屏幕对象，您可以使用该对象引用屏幕的属性，或与另一个屏幕进行比较以确定要显示的屏幕。 您可以使用 "**[后退](function-navigate.md)**" 或 "**[导航](function-navigate.md)**" 功能更改显示的屏幕。 |

详细信息： [**应用**对象](object-app.md)文档。

### <a name="compass"></a>Compass
**Compass** 信号返回屏幕顶部的指南针标题。 该标题以磁北方为基础。

| 属性 | 说明 |
| --- | --- |
| **Compass.Heading** |标题以度为单位。  返回一个介于 0 到 360 之间的数值，0 表示北方。 |

### <a name="connection"></a>连接
**Connection** 信号返回网络连接的相关信息。 如果连接按流量计费，建议限制通过网络发送或接受数据的量。

| 属性 | 说明 |
| --- | --- |
| **Connection.Connected** |返回一个布尔值 **true** 或 **false**，指示设备是否已连接到网络。 |
| **Connection.Metered** |返回一个布尔值 **true** 或 **false**，指示连接是否按流量计费。 |

### <a name="location"></a>Location
**Location** 信号基于全球定位系统 (GPS) 和其他设备信息（如手机基站通信和 IP 地址）返回设备的位置。

用户首次访问位置信息时，设备可能会提示该用户，以允许访问此信息。

随着位置在不断改变，位置上的依赖项将不断被重新计算，这将消耗设备电池的电量。 要维护电池寿命，可使用 **[Enable](function-enable-disable.md)** 和 **[Disable](function-enable-disable.md)** 函数打开或关闭位置更新。 如果显示的屏幕不依赖于位置信息，位置将自动关闭。

| 属性 | 说明 |
| --- | --- |
| **Location.Altitude** |返回一个指示海拔高度的数值（用英尺表示）。 |
| **Location.Latitude** |返回一个从-90 到90的数字，它指示纬度，从赤道的角度来度量。 正数表示赤道以北的位置。 |
| **Location.Longitude** |返回一个数字，从–180到180，指示经度，单位为英国的格林尼治度。  正数指示 Greenwhich 的东部位置。 |

## <a name="examples"></a>示例
在棒球域中，罐状指针从罐间球场到 home 盘子上的收集者。 该手机相对于地面是平行移动的，手机的屏幕顶端指向捕手，且投手在投掷过程中未使手机发生旋转。 在该位置，这部手机连接的是按流量计费的移动网络服务，没有 WiFi。 将显示 **PlayBall** 屏幕。   

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Location.Latitude** |返回当前位置的纬度。 此字段位于地图坐标 47.591 N，122.333 W。 |47.591<br><br>纬度将随球在投手和捕手之间的移动而不断更改。 |
| **Location.Longitude** |返回当前位置的经度。 |122.333<br><br>经度将随球在投手和捕手之间的移动而不断更改。 |
| **位置** |返回当前位置的经度和纬度作为记录。 |{&nbsp;纬度：&nbsp;47.591，经度：&nbsp;122.333&nbsp;} |
| **Compass.Heading** |返回屏幕顶部的指南针标题。 在此字段中，主盘子大致来自罐杯杯的球场。 |230.25 |
| **Acceleration.X** |返回并排设备的加速度。 由于投手直接向前相对屏幕的顶端投掷手机，因此设备不会并排加速。 |0 |
| **Acceleration.Y** |返回设备从前到后的加速度。 在投掷设备之初，投手为设备提供了一个较大的加速度，在半秒中内达到从 0 增至 90 英里/小时（132 英尺/秒）。 设备在空中运动时，忽略空气阻力，设备不会进一步加速。 捕手接住设备时，设备将减速至停止。 |8.2，投手投掷设备时。<br><br>0，设备在空中时。<br><br>-8.2，捕手接住设备时。 |
| **Acceleration.Z** |返回设备从上到下的加速度。 设备在空中运动时会受重力影响。 |0，投手投掷设备前。<br><br>1，设备在空中运动时。<br><br>0，捕手接住设备后。 |
| **Acceleration** |将加速度作为记录返回。 |{ X: 0, Y: 264, Z: 0 }，投手投掷设备时。 |
| **Connection.Connected** |返回一个布尔值，它指示设备是否已连接到网络 |**true** |
| **Connection.Metered** |返回一个布尔值，它指示连接是否按流量计费 |**true** |
| **App.ActiveScreen = PlayBall** |返回一个布尔值，它指示是否显示了 **PlayBall**。 |**true** |
| **App.ActiveScreen.Fill** |返回所显示的屏幕的背景色。 |**Color.Green** |

