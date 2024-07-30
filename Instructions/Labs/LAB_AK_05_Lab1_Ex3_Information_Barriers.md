---
lab:
  title: 练习 3 - 配置信息屏障
  module: Module 5 - Manage insider and privacy risk in Microsoft 365
---

# 实验室 5 - 练习 3 - 配置信息屏障

作为 Contoso 有限公司的合规性管理员 Joni，你的职责是在 Microsoft 365 中配置和管理信息屏障。 信息屏障在保持明确的界限和防止组织中的特定组或个人之间进行未经授权的通信方面发挥着关键作用。 通过实施信息屏障，可以确保遵守法规、保护敏感信息并最大限度地减少利益冲突。 此设置将创建一个安全的工作环境，保护数据机密性并支持 Contoso 有限公司的合规性承诺。

## 任务 1：验证 Microsoft Teams 中是否启用了按名称搜索

在此任务中，你将验证 Microsoft Teams 中是否启用了“按名称搜索”功能。 此功能允许用户轻松搜索和查找其组织中的特定个人。 你将按照提供的步骤配置并激活此功能，以增强组织的 Microsoft Teams 环境中的协作并简化通信。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 如果你仍使用 Joni 的帐户登录，请退出此帐户并关闭所有浏览器窗口。

1. 在 Microsoft Edge 中，导航到 `https://admin.teams.microsoft.com` 并以 MOD 管理员的身份 admin@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户 。

1. 在左侧导航窗格中的“Teams”下拉菜单下，选择“Teams 设置”

1. 向下滚动到“按名称搜索”。 如果此功能设置为“关”，请将此功能切换为“开”，然后选择“保存”以保存此设置 。

1. 在“更改生效需要时间”弹出窗口中，选择“确认”

    >注意：此更改可能需要几个小时才会生效。

## 任务 2：将组织中的用户分群

在此任务中，你将使用 PowerShell 连接到安全与合规性模块，并为法律部门和市场营销部门创建组织段 。

1. 提升的 PowerShell 窗口应仍处于打开状态。

1. 在“PowerShell”窗口中，输入 cmdlet 以连接到安全与合规性 PowerShell，

    ````powershell
    Connect-IPPSSession
    ````

    以 Joni Sherman JoniS@WWLxZZZZZZ.onmicrosoft.com 的身份（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录。  Joni 的密码应由实验室托管提供程序提供。

1. 使用 UserGroupFilter 参数运行 New-OrganizationSegment cmdlet 以创建“法律”段  ：

    ````powershell
    New-OrganizationSegment -Name "Legal" -UserGroupFilter "Department -eq 'Legal'"
    ````

1. 再次运行 New-OrganizationSegment cmdlet 以创建“市场营销”段 ：

    ````powershell
    New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"
    ````

1. 运行 Get-OrganizationSegment cmdlet 以查看已创建的段。

    ````powershell
    Get-OrganizationSegment
    ````

你已成功连接到安全与合规性 PowerShell，为法律部门和市场营销部门创建了组织段，并使用 Get-OrganizationSegment cmdlet 查看了这些段。

## 任务 3：创建信息屏障策略

在此任务中，你将使用 PowerShell 创建信息屏障策略，以阻止法律部门和市场营销部门之间的通信。

1. 提升的 PowerShell 窗口应仍处于打开状态。

1. 使用 SegmentsBlocked 参数运行 New-InformationBarrierPolicy cmdlet 以创建新的“法律-市场营销”策略  ：

    ````powershell
    New-InformationBarrierPolicy -Name "Legal-Marketing" -AssignedSegment "Legal" -SegmentsBlocked "Marketing" -State Active
    ````

1. 当 PowerShell 中显示有关信息屏障策略警告的通知时，请键入 Y，然后按 Enter 以继续创建策略 。

1. 现在，必须创建一项信息屏障策略，以阻止相反方向。 使用 SegmentsBlocked 参数运行 New-InformationBarrierPolicy cmdlet 以创建新的“市场营销-法律”策略  ：

    ````powershell
    New-InformationBarrierPolicy -Name "Marketing-Legal" -AssignedSegment "Marketing" -SegmentsBlocked "Legal" -State Active
    ````

1. 运行 Get-InformationBarrierPolicy cmdlet 以查看已创建的策略。

    ````powershell
    Get-InformationBarrierPolicy
    ````

    >注意：查看创建的策略时，请确保策略被标记为“活动” 。 在应用信息屏障策略之前，这些策略必须处于活动状态。

你已使用 PowerShell 成功创建“法律-市场营销”和“市场营销-法律”信息屏障策略，并通过运行 Get-InformationBarrierPolicy cmdlet 验证了其状态为活动状态。

## 任务 4：应用信息屏障策略

在此任务中，你将使用 PowerShell 应用活动的信息屏障策略并检查其应用状态。

1. 提升的 PowerShell 窗口应仍处于打开状态。

1. 运行 Start-InformationBarrierPoliciesApplication cmdlet 以应用活动的信息屏障策略：

    ````powershell
    Start-InformationBarrierPoliciesApplication
    ````

1. 运行 Get-InformationBarrierPoliciesApplicationStatus cmdlet 以查看应用的策略。

    ````powershell
    Get-InformationBarrierPoliciesApplicationStatus
    ````

    >注意：请留出 30 分钟，让系统开始应用策略。

1. 应用策略后，“状态”将从“未启动”更新为“已完成”  。

你已通过运行 Start-InformationBarrierPoliciesApplication cmdlet 成功应用了信息屏障策略，并使用 Get-InformationBarrierPoliciesApplicationStatus cmdlet 验证了其应用状态。
