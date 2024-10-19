---
lab:
  title: 练习 3 - 管理 DLP 报告
  module: Module 2 - Implement Data Loss Prevention
---

# 实验室 2 - 练习 3 - 管理 DLP 报告

你是 Joni Sherman，Contoso Ltd. 的合规性管理员，负责配置公司的 Microsoft 365 租户以防止数据丢失。 Contoso Ltd. 是美国的一家提供驾驶指导服务的公司，你需要确保敏感客户信息不会泄露到组织外部。 你已获悉新的合规官将帮助你查看 DLP 报告。

**任务**：

1. 授予对 DLP 报告的访问权限
1. 在活动管理器中查看 DLP 数据
1. 使用 PowerShell 浏览 DLP 数据

## 任务 1 - 授予对 DLP 报告的访问权限

在本练习中，你将授予新的合规官 Megan Bowen 对 DLP 报告的访问权限。 作为非技术用户，该合规部主管将只读取报告，而不会更改 DLP 配置。

1. 使用 **SC-400-cl1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)。

1. 在 Microsoft Edge 中，导航到 `https://purview.microsoft.com` 并以 MOD 管理员的身份 `admin@WWLxZZZZZZ.onmicrosoft.com` （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户  。 管理员的密码应由实验室托管提供程序提供。

1. 从左侧边栏中选择“**设置**”。

1. 在“**设置**”页上，展开左侧边栏中的“**角色和范围**”，然后选择“**角色组**”。

1. 在“**Microsoft Purview 解决方案的角色组**”页上，选中“**信息保护分析师**”复选框，然后从顶部导航栏中选择“**编辑**”选项卡。

1. 在“编辑角色组的成员”页上，选择“+ 选择用户” 。

1. 在“**选择用户**”浮出面板上，搜索 `Megan` 以查找 Megan Bowen 的帐户。 选中 **Megan Bowen** 帐户的复选框，然后选择面板底部的“**选择**”按钮。

1. 返回到“**编辑角色组的成员**”页，验证是否显示 Megan 的帐户，然后选择“**下一步**”。

1. 在“查看角色组并完成”页上，选择“保存” 。

1. 在“已成功更新角色组”页上，选择“完成” 。

1. 选择右上角的“**MA**”，然后选择“**注销**”，以注销 MOD 管理员帐户。

你现在已为新的合规部主管授予了对 Microsoft 365 合规门户中的 DLP 报告的访问权限。

## 任务 2 - 在活动管理器中查看 DLP 数据

在此任务中，你将测试是否正确应用了在任务 1 中授予的对 DLP 报告的访问权限。

1. 使用 **SC-400-cl2\admin** 帐户登录到客户端 1 VM (SC-400-CL1)。

1. 在 Microsoft Edge 中，导航到 `https://purview.microsoft.com` 并以 Megan Bowen 的身份 `MeganB@WWLxZZZZZZ.onmicrosoft.com` （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户  。 上一练习中已设置 Megan 的密码。

1. 从左侧边栏中选择“**解决方案**”，然后选择“**数据丢失防护**”。

1. 在左侧边栏中，选择“**活动管理器**”。

1. 在“活动资源管理器”页上，选择“内置筛选器”下拉菜单 。

1. 浏览“检测到活动的 DLP 策略”筛选器和“检测到活动的 DLP 策略规则”筛选器 。

1. 选择右上角的“**MB**”图标，然后选择“**注销**”，从 Megan 的帐户注销。

你现在验证了已配置访问权限，新的合规官可以在 Purview 门户中查看报告。

## 任务 3 - 使用 PowerShell 浏览 DLP 数据

在此任务中，你将通过 PowerShell 查看 DLP 活动。

1. 你仍然应该会使用 **SC-400-cl1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)。

1. 右键单击任务栏中的“Windows”按钮，然后选择“**终端(管理员)**”，打开提升的 PowerShell 窗口。

1. 运行 **Connect-IPPSSession** cmdlet 以连接到“信息保护”PowerShell 会话：

   ``` powershell
   Connect-IPPSSession
   ```

1. 在“**登录到你的帐户**”对话框中，选择“**+ 使用另一帐户**”，然后使用帐户“**Megan Bowen**”`MeganB@WWLxZZZZZZ.onmicrosoft.com`（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录。

1. 运行 **Export-ActivityExplorerData** PowerShell cmdlet，从 PowerShell 浏览活动管理器。 下面的脚本示例将显示最近一周的活动的网格视图：

   ``` powershell
   $StartTime = (Get-Date).AddDays(-7)
   $EndTime = (Get-Date).AddDays(1)
   $Results = Export-ActivityExplorerData -StartTime $StartTime -EndTime $EndTime -OutputFormat JSON
   ($Results.ResultData) | ConvertFrom-Json | select -ExpandProperty SyncRoot | ogv
   ```

1. 浏览从以前的实验室收集的数据，然后关闭网格视图窗口。

1. 下面的脚本示例使用 **Filter1** 参数显示最近一周的终结点活动：

   ``` powershell
   $StartTime = (Get-Date).AddDays(-7)
   $EndTime = (Get-Date).AddDays(1)
   $Results = Export-ActivityExplorerData -StartTime $StartTime -EndTime $EndTime -Filter1 @("Workload","Endpoint")-OutputFormat JSON
   ($Results.ResultData) | ConvertFrom-Json | select -ExpandProperty SyncRoot | ogv
   ```

1. 浏览从以前的实验室收集的数据，然后关闭网格视图窗口。

你已成功以新任合规官 Megan Bowen 的身份查看了 DLP 活动。
