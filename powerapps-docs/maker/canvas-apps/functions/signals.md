---
title: Acceleration、App、Compass、Connection 和 Location 信号 | Microsoft Docs
description: PowerApps 中 Acceleration、App、Compass、Connection 和 Location 传感器的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 147766eb9e9b17698882241e8eb3bd0ae7ba7e78
ms.sourcegitcommit: 0dbbf53aea319e53edadc1d3a9efa5728856ebd8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58172624"
---
# <a name="acceleration-app-compass-connection-and-location-signals-in-powerapps"></a>PowerApps 中的 Acceleration、App、Compass、Connection 和 Location 信号
返回关于应用环境的信息，例如用户的全球所在位置，以及所显示的是哪个屏幕。  

## <a name="description-and-syntax"></a>说明和语法
所有信号都将返回信息的[记录](../working-with-tables.md#records)。 可以使用此信息并将其存储为记录，也可提取单个属性，其方式是使用“.” [运算符](operators.md)。

> [!NOTE]
> **加速**并**指南针**函数返回准确的值在 iOS 或 Android，如本机播放器，但在你创建或修改应用程序，在浏览器中的，这些函数将返回零值。

### <a name="acceleration"></a>Acceleration
**Acceleration** 信号以相对于设备屏幕的三维方式返回设备的加速度。 Acceleration 的测量单位为 g（9.81 m/s<sup>2</sup> 或 32.2 ft/s<sup>2</sup>）（地球由于重力而在其表面对物体产生的加速度）。

| 属性 | 描述 |
| --- | --- |
| **Acceleration.X** |右侧和左侧。  右侧为正数。 |
| **Acceleration.Y** |前方和后方。  前方为正数。 |
| **Acceleration.Z** |上方和下方。  上方为正数。 |

### <a name="app"></a>App
**App** 信号返回正在运行的应用的相关信息。

| 属性 | 描述 |
| --- | --- |
| **App.ActiveScreen** | 所显示的屏幕。 返回一个屏幕对象，可用于引用屏幕属性，或与其他屏幕进行比较，以判断显示的是哪个屏幕。 若要更改所显示的屏幕，请使用 **[回](function-navigate.md)** 或 **[Navigate](function-navigate.md)** 函数。 |
| **App.Width** | 返回在其中运行应用程序窗口的宽度。 设置时，可以在公式中使用此属性**宽度**屏幕来构建响应性应用的属性。  |
| **App.Height** | 返回在其中运行应用程序窗口的高度。 设置时，可以在公式中使用此属性**高度**屏幕来构建响应性应用的属性。 |
| **App.DesignWidth** | 返回在 PowerApps Studio 中的应用程序的宽度。 设置时，可以在公式中使用此属性**宽度**屏幕来确保响应性应用中的最小宽度的属性。  |
| **App.DesignHeight** | 返回在 PowerApps Studio 中的应用程序的高度。 设置时，可以在公式中使用此属性**高度**屏幕来确保在响应性应用最小高度属性。  |

**应用程序**对象还具有[行为公式](../working-with-formulas-in-depth.md)，可以设置。

| 属性  | 说明 |
| --- | --- |
| **OnStart** | 应用用户启动它时的行为。 此属性通常用于检索并缓存数据到集合**[收集](function-clear-collect-clearcollect.md)** 函数，设置变量**[设置](function-set.md)** 函数，并导航到包含初始屏幕**[Navigate](function-navigate.md)** 函数。 第一屏出现之前，会计算此公式。 加载没有屏幕，因此不能设置与上下文变量**[UpdateContext](function-updatecontext.md)** 函数。 但是，可以传递与上下文变量**Navigate**函数。 |

**应用**对象显示在左侧的导航窗格中控件的层次结构列表的顶部，你可以选择类似于在屏幕上控件的此对象。 选择的对象后，你可以查看和编辑其属性之一，如果您在公式栏的左侧的下拉列表中选择该属性。  

更改后**OnStart**属性，可以测试它悬停**应用**对象在左侧的导航窗格中，选择显示的省略号 （...），然后选中**运行OnStart**。 当首次加载应用，与现有集合和变量已设置。 使用**[ClearCollect](function-clear-collect-clearcollect.md)** 函数而不是**收集**函数开始空集合。

 ![与运行 OnStart 应用项上下文菜单](media/appobject-runonstart.png)

### <a name="compass"></a>Compass
**Compass** 信号返回屏幕顶部的指南针标题。 该标题以磁北方为基础。

| 属性 | 描述 |
| --- | --- |
| **Compass.Heading** |标题以度为单位。  返回一个介于 0 到 360 之间的数值，0 表示北方。 |

### <a name="connection"></a>Connection
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
| **Location.Latitude** |返回一个介于 - 90 至 90 之间的数值，该值指示从赤道起以度数表示的纬度。 正数表示赤道以北的位置。 |
| **Location.Longitude** |返回一个介于 0 至 180 之间的数值，该值指示从英国格林威治以西起用度数表示的经度。 |

## <a name="examples"></a>示例
在棒球字段中，投手投掷手机从投球区向本垒的捕手。 该手机相对于地面是平行移动的，手机的屏幕顶端指向捕手，且投手在投掷过程中未使手机发生旋转。 在该位置，这部手机连接的是按流量计费的移动网络服务，没有 WiFi。 将显示 **PlayBall** 屏幕。   

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Location.Latitude** |返回当前位置的纬度。 字段位于地图上的坐标 N，122.333 w。 |47.591<br><br>纬度将随球在投手和捕手之间的移动而不断更改。 |
| **Location.Longitude** |返回当前位置的经度。 |122.333<br><br>经度将随球在投手和捕手之间的移动而不断更改。 |
| **位置** |返回当前位置的经度和纬度作为记录。 |{&nbsp;纬度：&nbsp;47.591，经度：&nbsp;122.333&nbsp;} |
| **Compass.Heading** |返回屏幕顶部的指南针标题。 在此字段中，本垒大致西南部从才投手区。 |230.25 |
| **Acceleration.X** |返回并排设备的加速度。 由于投手直接向前相对屏幕的顶端投掷手机，因此设备不会并排加速。 |0 |
| **Acceleration.Y** |返回设备从前到后的加速度。 在投掷设备之初，投手为设备提供了一个较大的加速度，在半秒中内达到从 0 增至 90 英里/小时（132 英尺/秒）。 设备在空中运动时，忽略空气阻力，设备不会进一步加速。 捕手接住设备时，设备将减速至停止。 |8.2，投手投掷设备时。<br><br>0，设备在空中时。<br><br>-8.2，捕手接住设备时。 |
| **Acceleration.Z** |返回设备从上到下的加速度。 设备在空中运动时会受重力影响。 |0，投手投掷设备前。<br><br>1，设备在空中运动时。<br><br>0，捕手接住设备后。 |
| **Acceleration** |将加速度作为记录返回。 |{X:0，Y:264，Z:0} 作为投手投掷设备。 |
| **Connection.Connected** |返回一个布尔值，它指示设备是否已连接到网络 |**true** |
| **Connection.Metered** |返回一个布尔值，它指示连接是否按流量计费 |**true** |
| **App.ActiveScreen = PlayBall** |返回一个布尔值，它指示是否显示了 **PlayBall**。 |**true** |
| **App.ActiveScreen.Fill** |返回所显示的屏幕的背景色。 |**Color.Green** |

