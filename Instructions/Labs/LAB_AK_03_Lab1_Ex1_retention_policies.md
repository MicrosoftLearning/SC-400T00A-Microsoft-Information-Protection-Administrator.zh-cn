---
lab:
  title: 练习 1 - 配置保留策略
  module: Module 3 - Implement Data Lifecycle and Records Management
---

## WWL 租户 - 使用条款

如果在讲师引导式培训过程中向你提供租户，请注意，提供租户旨在支持讲师引导式培训中的动手实验室。

租户不应共享或用于动手实验室以外的用途。 本课程使用的租户为试用租户，课程结束后无法使用或访问，不符合扩展条件。

租户不得转换为付费订阅。 在本课程中获得的租户仍然是 Microsoft Corporation 的财产，我们保留随时获取访问权限和收回的权利。

# 实验室 3 - 练习 1 - 配置保留策略

在本实验室中，你是德克萨斯州 Contoso Ltd. 的合规性管理员 Joni Sherman。 你的任务是实施保留策略以遵守州法规，策略允许在三年后删除记录。 你将在整个组织中配置各种保留策略，以确保根据这些法律要求管理并保留数据。

**任务**：

1. 创建公司范围内的保留策略
1. 创建具有特定用户选择的 Teams 保留策略
1. 通过 PowerShell 创建保留策略
1. 为法律和零售文档创建自适应保留策略
1. 测试自适应范围策略

## 任务 1 - 创建公司范围内的保留策略

在此任务中，你将设置一个公司范围内的保留策略，该策略涵盖关键 Microsoft 365 位置，确保所有项目都保留三年，以符合州法律。

1. 使用 **SC-400-cl1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)。

1. 在 Microsoft Edge 中，导航到 `https://purview.microsoft.com` 并以 Joni Sherman 的身份 `JoniS@WWLxZZZZZZ.onmicrosoft.com` （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户  。 Joni 的密码是在上一练习中设置的。

1. 选择“**解决方案**”，然后选择“**数据生命周期管理**”。

1. 在“**数据生命周期管理**”页上的左侧边栏中，展开“**策略**”，然后选择“**保留策略**”。

1. 在“**保留策略**”页上，选择“**+ 新建保留策略**”。

1. 在“**命名保留策略**”页上输入：

    - **名称**：`Company wide`
    - **说明**：`All locations except for teams`

1. 选择“**下一步**”按钮。  

1. 在“策略范围”页上选择“下一步”********。

1. 在“**选择要创建的保留策略的类型**”页上，选择“**静态**”，然后选择“**下一步**”。

1. 在“**选择应用此策略的位置**”中，启用以下位置：

   - Exchange 邮箱
   - SharePoint 经典和通信站点
   - OneDrive 帐户
   - Microsoft 365 组邮箱和站点

1. 选择**下一步**。

1. 在“**决定是否要保留内容、删除内容或二者均可**”页上，确保为保留配置设置以下值：

   - 选择“**将项保留特定时间段**”。
   - 在“**将项保留特定时间段**”下，从下拉列表中选择“**自定义**”
   - 将“年数”字段更改为 3
   - 保留期开始依据：上次修改项的时间
   - 保留期结束时：自动删除项

1. 选择**下一步**。

1. 在“查看并完成”页上，选择“提交”********。

1. 创建策略后，在“**已成功创建保留策略**”页上选择“**完成**”。

你已成功创建了一个保留策略，该策略从最后一次修改之日起三年内保留 Microsoft 365 关键位置上的项。 此策略可能需要长达 24 小时才能应用于你的租户，但你可以继续执行下一步。

## 任务 2 - 创建具有特定用户选择的 Teams 保留策略

接下来，你将专门为 Microsoft Teams 创建保留策略，将其应用于频道消息，并选择用户聊天，以独立于其他数据管理其保留期。 你的组织决定要求部分用户进行 Team 聊天时需要保留期。

1. 你仍然应该会使用 **SC-400-cl1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)，并且应该会以 **Joni Sherman** 的身份登录到 Microsoft Purview。

1. 在 Microsoft Edge 中，你应仍位于 Microsoft Purview 门户的“**保留策略**”页上。 如果没有，请导航到 **`https://purview.microsoft.com`**，然后依次选择“**解决方案**”、“**数据生命周期管理**”。 从左侧边栏中选择“**策略**” > “**保留策略**”。

1. 在“**保留策略**”页上，选择“**+ 新建保留策略**”。

1. 在“**命名保留策略**”页上输入：

   - **名称**：`Teams Retention`
   - **说明**：`Retention for Teams locations`

1. 选择**下一步**。

1. 在“策略范围”页上选择“下一步”********。

1. 在“**选择要创建的保留策略的类型**”页上，选择“**静态**”，然后选择“**下一步**”。

1. 在“**选择应用策略的位置**”页上，启用以下位置：

   - Teams 渠道消息
   - Teams 聊天和 Copilot 交互
   - 将所有其他位置保留为禁用状态。

1. 对于“**Teams 聊天和 Copilot 交互**”位置，选择“**所有用户**”下的“**编辑**”文本链接

1. 在 **Teams 聊天和 Copilot 交互**浮出面板中添加用户：

    - Adele Vance
    - Pradeep Gupta

    >注意：添加这两名用户后，Teams 聊天中的“包括”设置从“所有团队”更改为“2 位用户”****************。

1. 在浮出面板底部选择“**完成**”。

1. 返回到“**选择应用此策略的位置**”页上，选择“**下一步**”。

1. 在“**决定是否要保留内容、删除内容或二者均可**”页上，确保为保留配置设置以下值：

   - 选择“**将项保留特定时间段**”。
   - 在“**将项保留特定时间段**”下，从下拉列表中选择“**自定义**”
   - 将“年数”字段更改为 3
   - 保留期开始依据：上次修改项的时间
   - 保留期结束时：自动删除项

1. 选择**下一步**。

1. 在“查看并完成”页上，选择“提交”********。

1. 创建策略后，在“**已成功创建保留策略**”页上选择“**完成**”。

1. 关闭浏览器窗口。

你已成功为 Microsoft Teams 配置保留策略，确保频道消息和特定用户聊天内容保留三年。

## 任务 3 - 通过 PowerShell 创建保留策略

在此任务中，你将使用 PowerShell 创建相同的保留策略，演示如何自动执行策略设置过程。

1. 使用 **SC-400-cl1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)。

1. 右键单击任务栏中的“Windows”按钮，然后选择“**终端(管理员)**”，打开提升的 PowerShell 窗口。 如果出现“**用户帐户控制**”对话框，请选择“**是**”。

1. 运行 **Connect-IPPSSession** cmdlet 以连接到租户中的“安全与合规中心”：

    ```powershell
    Connect-IPPSSession
    ```

1. 如果出现登录对话框提示，请以 **MOD 管理员**`admin@WWLxZZZZZZ.onmicrosoft.com`（其中 ZZZZZZ 是实验室托管服务提供程序提供的唯一租户 ID）身份登录。 管理员的密码应由实验室托管提供程序提供。

1. 运行 **New-RetentionCompliancePolicy** cmdlet 为所有位置（Teams 除外）创建第一个保留策略：

    ```powershell
    New-RetentionCompliancePolicy -Name "Company Wide PS" -ExchangeLocation All -ModernGroupLocation All -SharePointLocation All -OneDriveLocation All
    ```

1. 运行 **New-RetentionComplianceRule** cmdlet，基于修改日期将保留期设为 3 年（以天为单位）：

    ```powershell
    New-RetentionComplianceRule -Name "Company Wide PS Rule" -Policy "Company Wide PS" -RetentionDuration 1095 -ExpirationDateOption ModificationAgeInDays -RetentionComplianceAction Keep
    ```

1. 运行 **New-RetentionCompliancePolicy** cmdlet，为 Teams 位置创建第二个保留策略：

    ```powershell
    New-RetentionCompliancePolicy -Name "Teams Retention PS" -TeamsChannelLocation All -TeamsChatLocation "Adele Vance", "Pradeep Gupta"
    ```

1. 运行 **New-RetentionComplianceRule** cmdlet，将保留期设为 3 年（以天为单位）：

    ```powershell
    New-RetentionComplianceRule -Name "Teams Retention PS Rule" -Policy "Teams Retention PS" -RetentionDuration 1095 -RetentionComplianceAction Keep
    ```

1. 关闭终端窗口。

你已成功使用 PowerShell 创建保留策略，通过 Microsoft Purview 门户对设置的策略进行镜像。

## 任务 4 - 为法律和零售文档创建自适应保留策略

现在，你将为财务和法务部门创建自适应保留策略，确保所有与法律相关的文档保留五年。

1. 你应仍使用 **SC-400-cl1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)，并且应该会以 **Joni Sherman** 的身份登录到 Microsoft 365。

1. 打开 Microsoft Edge 并导航到 `https://purview.microsoft.com`****。 验证是否仍在使用 Joni 的帐户登录，然后从左侧边栏中选择“**设置**”。

1. 在“**设置**”页上，展开左侧边栏中的“**角色和范围**”，然后选择“**自适应范围**”。

1. 在“自适应范围”页上，选择“+ 创建范围”********。

1. 在“**命名自适应策略范围**”页上，输入：

    - **名称**：`Legal Documents Retention`
    - **说明**：`Retention for legal related documents`

1. 选择**下一步**。

1. 在“分配管理单元”页上，选择“下一步”********。

1. 在“想要创建哪种类型的范围?”页上，选择“用户”，然后选择“下一步”************。

1. 在“**创建查询以定义用户**”页的“**用户属性**”部分中，确保为用户属性配置选择这些值：

   - 选择“**属性**”下拉列表，然后选择“**部门**”
   - 保留下一个字段中的默认值“**等于**”
   - 输入 `Legal` 作为“**值**”

1. 在“**创建查询以定义用户**”页上选择“**+ 添加属性**”，添加第二个属性。 在刚刚配置的字段下方的新字段中，配置以下值：

   - 选择查询运算符下拉列表，并将其从 And 更新为 **Or**
   - 选择“**属性**”下拉列表，然后选择“**部门**”
   - 保留下一个字段中的默认值“**等于**”
   - 输入 `Retail` 作为“**值**”

1. 选择**下一步**。

1. 在“查看并完成”页上，选择“提交”********。

1. 创建自适应范围后，请在“**已创建范围**”页上选择“**完成**”。

1. 返回“**自适应范围**”页，从左侧边栏底部选择“**解决方案**”。

1. 从顶部筛选器按钮中选择“**数据管理**”选项卡。

1. 选择“**数据生命周期管理**”卡。

1. 在“**数据生命周期管理**”页上，展开“**策略**”，然后选择“**保留策略**”。

1. 在“**保留策略**”页上，选择“**+ 新建保留策略**”。

1. 在“**命名保留策略**”页上输入：

    - **名称**：`Legal Data Retention`
    - **说明**：`Retention of all documents within the legal and retail departments.`

1. 选择**下一步**。

1. 在“策略范围”页上选择“下一步”********。

1. 在“选择要创建的保留策略的类型”页上，选择“自适应”，然后选择“下一步”************。

1. 在“选择自适应策略范围和位置”页上，选择“+ 添加范围”********。

1. 在“**选择自适应策略范围**”浮出面板上，选中“**法律文档保留**”复选框，然后在面板底部选择“**添加**”。

1. 回到“选择应用策略的位置”，启用****：

    - Exchange 邮箱
    - OneDrive 帐户
    - 将所有其他位置保留为禁用状态。

1. 选择**下一步**。

1. 在“**决定是否要保留内容、删除内容或二者均可**”页上，确保为保留配置设置以下值：

   - 选择“**将项保留特定时间段**”。
   - 在“**将项保留特定时间段**”下，从下拉列表中选择“**5 年**”
   - 保留期开始依据：上次修改项的时间
   - 保留期结束时：无操作

1. 选择**下一步**。

1. 在“查看并完成”页上，选择“提交”********。

1. 创建策略后，选择“完成”按钮。

1. 创建策略后，在“**已成功创建保留策略**”页上选择“**完成**”。

你已成功将自适应范围应用于保留策略，涵盖法律和零售部门文档五年。

## 任务 5 - 测试自适应范围策略

在此最终任务中，你将验证受自适应范围影响的用户，并测试新的保留策略，以确保其按预期运行。

>注意：创建并提交保留策略后，最多可能需要 7 天才能应用保留策略****。

1. 右键单击任务栏中的“Windows”按钮，然后选择“**终端(管理员)**”，打开提升的 PowerShell 窗口。 如果出现“**用户帐户控制**”对话框，请选择“**是**”。

1. 运行 **Connect-IPPSSession** cmdlet，以连接到租户中的“安全与合规中心”：

    ```powershell
    Connect-IPPSSession
    ```

1. 如果出现登录对话框的提示，请使用 Joni Sherman 的帐户“`JoniS@WWLxZZZZZZ.onmicrosoft.com`”（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录。 Joni 的帐户已在上一练习中设置。

1. 运行 **Get-RetentionCompliancePolicy** cmdlet 以查看自适应范围策略的所有详细信息：

    ```powershell
    Get-RetentionCompliancePolicy -Identity "Legal Data Retention" -DistributionDetail | Format-List
    ```

1. 查看结果并搜索以下详细信息：

    - Enabled: True
    - Mode: Enforce
    - DistributionStatus: Success

    ![Get-RetentionCompliancePolicy cmdlet 结果的屏幕截图。](../Media/results-getretentioncompliancepolicy.png)

你已验证自适应范围保留策略的成功实施，确认它已正确应用并正常运行。
