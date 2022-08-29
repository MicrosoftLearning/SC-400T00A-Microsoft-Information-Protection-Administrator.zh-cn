---
ms.openlocfilehash: fbf7dad2bb533f78527990015c8531be22894b9d
ms.sourcegitcommit: f7259dd59786836bf2ccb7f3c1a5ef37ec745a4a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/23/2022
ms.locfileid: "147629907"
---
# <a name="lab-3---exercise-4---configure-event-based-retention"></a>实验室 3 - 练习 4 - 配置基于事件的保留

在本练习中，假设你是 Joni Sherman，Contoso Ltd. 的一名合规性管理员。你的组织位于德克萨斯州，并且想要实现保留策略，从而将属于特定项目的内容在项目关闭后保留 5 年。

### <a name="task-1---create-event-type"></a>任务 1 - 创建事件类型

首先，你需要创建可以在发生特定情况时触发的事件类型。 在此例中，你将创建可以在项目关闭时触发的事件类型。

1. 你仍应使用“lon-cl1\admin”帐户登录到客户端 1 VM (LON-CL1)，并且应该以“Joni Sherman”身份 JoniS@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管服务提供程序提供的唯一租户 ID）登录到 Microsoft 365 。  Joni 的密码应由实验室托管提供程序提供。 

1. 在 Microsoft Edge 中，导航到 https://compliance.microsoft.com ，并以 Joni Sherman 的身份登录到 Microsoft Purview 门户  。

1. 在 Microsoft Purview 门户中的左侧导航窗格上，选择“记录管理”并导航到“事件”选项卡  。

1. 选择“管理事件类型”，然后选择“+ 创建” 。

1. 在“为事件类型命名”对话框中，设置以下信息：
    - 名称：项目关闭
    - 描述：当项目关闭时将触发此事件。

1. 查看“摘要”，选择“提交”，然后选择“完成”  。

你已成功创建了新的事件类型。

### <a name="task-2--create-event-driven-retention-label"></a>任务 2 - 创建事件驱动的保留标签

创建事件类型后，需要创建一个标签，此标签会在事件发生时触发其保留期。

1. 你仍应使用“lon-cl1\admin”帐户登录到客户端 1 VM (LON-CL1)，并且应该以“Joni Sherman”身份 JoniS@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管服务提供程序提供的唯一租户 ID）登录到 Microsoft 365 。  Joni 的密码应由实验室托管提供程序提供。 

1. 在 Microsoft Edge 中，导航到 https://compliance.microsoft.com ，并以 Joni Sherman 的身份登录到 Microsoft Purview 门户  。

1. 在 Microsoft Purview 门户中的左侧导航窗格上，选择“策略”，然后在“数据”下选择“保留”   。

1. 在“数据生命周期管理”页面上，选择“标签”选项卡 。

1. 选择“+ 创建标签”按钮。

1. 在“为保留标签命名”页上的“名称”、“针对用户的说明”和“针对管理员的说明”中，输入以下信息   ：

    - 名称：项目资产
    - 针对用户的说明：将此标签分配给项目文档，以确保它们的保留期为 5 年。
    - 针对管理员的说明：基于事件的保留的项目资产。

1. 选择“下一步”按钮。

1. 在“定义标签设置”页面上，启用“将项永远保留或保留特定时间段”设置 。

1. 在“定义时间段”页面上，设置以下信息：
    - 保留期有多长：5 年。
    - 此时间段应从何时开始：项目关闭

1. 选择“下一步”按钮。

1. 在“选择保留期后会发生什么情况”页面上，选择“自动删除项”，然后选择“下一步”  。

1. 在“查看并完成”页面上，选择“创建标签”按钮 。  在“已创建保留标签”页面上，选择“无操作”选项，然后选择“完成” 。

你已成功创建了标签，需要发布它。

### <a name="task-3--publish-event-driven-retention-label"></a>任务 3 - 发布事件驱动的保留标签

执行任务 2 之后，你现在需要发布项目资产保留标签，使用户可以将已发布的标签应用于 SharePoint 文档中的文档。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。 

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 https://compliance.microsoft.com。

1. 在 Microsoft Purview 门户中的左侧导航窗格上，选择“策略”，然后在“数据”下选择“保留”   。

1. 在“数据生命周期管理”页上，选择“标签”选项卡 。

1. 选择在任务 1 中创建的“项目资产”标签。

1. 选择“发布标签”图标按钮。

1. 在“选择要发布的标签”页面上，选择“下一步”按钮 。

1. 在“选择要创建的保留策略的类型”页面上，选择“静态”项。

1. 选择“下一步”按钮。

1. 在“选择位置”页面上，启用“让我选择特定位置”选项 。

1. 输入以下信息：
    - Exchange 电子邮件位置 - 状态：关闭 
    - “SharePoint 网站”位置 -“状态”：启用
    - “OneDrive 帐户”位置 -“状态”：启用
    - Microsoft 365 组位置 - 状态：关闭   

1. 选择“下一步”按钮。

1. 在“为策略命名”页上的“名称”和“说明”中输入以下信息  ：

    - 名称：项目资产保留标签
    - 描述：项目资产保留标签、保留期 5 年、SharePoint 网站位置。

1. 选择“下一步”按钮。

1. 在“完成”页面上，选择“提交”按钮 。  创建策略后，选择“完成”。

你已成功将项目资产的保留标签发布到用户。

### <a name="task-4--apply-label-and-add-assetid"></a>任务 4 - 应用标签并添加 AssetID

发布标签后，用户需要应用标签，并将项目的正确资产 ID 分配给要标记的文档。 在本任务中，你将测试此功能。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。 

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 https://compliance.microsoft.com。

1. 在左上角选择九点图标，然后在“应用”下选择“SharePoint” 。

1. 在左侧导航窗格中，选择“我的网站”，然后在“已关注”下选择“操作”  。

1. 在左侧导航窗格中，选择“文档”。

1. 在“文档”页面上，选择“Bug List.xlsx”，方法是选中它前面的复选框，然后选择三个垂直点 。

1. 在上下文菜单中，选择“详细信息”。

1. 在右侧菜单中，在“属性”下选择“应用标签”，然后选择“项目资产”标签  。

    注意：由于发布保留标签可能需要一些时间，因此可能无法立即使用该选项。

1. 将新出现的“资产 ID”字段设置为“BostonOfficeLaunch”，然后选择右上角的“X”关闭右侧菜单  。

你已成功将标签和资产 ID 分配给文档。 当触发资产 ID BostonOfficeLaunch 的项目关闭事件时，这将激活 5 年的保留期。

### <a name="task-5--create-specific-event"></a>任务 5 - 创建特定事件

事件发生后，你需要触发它，使所标记的内容能够启动强制保留期。

1. 你仍应使用“lon-cl1\admin”帐户登录到客户端 1 VM (LON-CL1)，并且应该以“Joni Sherman”身份 JoniS@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管服务提供程序提供的唯一租户 ID）登录到 Microsoft 365 。  Joni 的密码应由实验室托管提供程序提供。 

1. 在 Microsoft Edge 中，导航到 https://compliance.microsoft.com ，并以 Joni Sherman 的身份登录到 Microsoft Purview 门户  。

1. 在 Microsoft Purview 门户中的左侧导航窗格上，选择“记录管理”并导航到“事件”选项卡  。

1. 选择“+ 新建”。 

1. 在“为事件命名”页面上，设置以下信息：
    - 名称：项目 Boston Office Launch 已关闭
    - 描述：具有项目资产标签和 AssetID BostonOfficeLaunch 的资产将进入其保留期。

1. 选择“下一步”  。

1. 在“事件设置”页上，选择“使用事件类型”，然后选择“选择事件类型”  。

1. 在“选择事件类型”页上，选择“项目关闭”，然后选择“添加”  。

1. 选择“下一步”  。

1. 在“事件设置”页上，将“SharePoint 和 OneDrive 中项的资产 ID”设置为“BostonOfficeLaunch”，然后选择今天的日期  。

1. 选择“下一步”，选择“提交”，然后选择“完成”  。

你已成功触发了事件，并启动了具有项目资产标签和资产 ID BostonOfficeLaunch 的所有文档的保留期。

### <a name="task-6--observe-results-of-event-trigger"></a>任务 6 - 观察事件触发器的结果

若要验证所指定的保留期是否已启动，需要尝试删除文件。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。 

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 https://compliance.microsoft.com。

1. 在左上角选择九点图标，然后在“应用”下选择“SharePoint” 。

1. 在左侧导航窗格中，选择“我的网站”，然后在“已关注”下选择“操作”  。

1. 在左侧导航窗格中，选择“文档”。

1. 在“文档”页面上，选择“Bug List.xlsx”，方法是选中它前面的复选框，然后选择三个垂直点 。

1. 在上下文菜单中，选择“删除”并观察结果。

你已成功确认文档的保留期已启动。 如果你仍然可以删除文档，则表示事件的同步期尚未完成，保留策略的触发仍在进行中。 与其他保留标签一样，此过程最多可能需要 7 天才能完成。

# <a name="proceed-to-lab-3---exercise-5"></a>继续进行实验室 3 - 练习 5
