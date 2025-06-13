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

<!------ Commenting out until tenant bug issues are resolved
## Task 4 – Create an adaptive retention policy for legal and retail documents

Now, you'll create an adaptive retention policy for the finance and legal departments, ensuring that all legal-related documents are retained for five years.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. Open Microsoft Edge and navigate to **`https://purview.microsoft.com`**. Verify you're still logged in with Joni's account, then select **Settings** from the left sidebar.

1. On the **Settings** page, expand **Roles and scopes** from the left sidebar, then select **Adaptive scopes**.

1. On the **Adaptive scopes** page select **+ Create scope**.

1. On the **Name your adaptive policy scope** page enter:

    - **Name**: `Legal Documents Retention`
    - **Description**: `Retention for legal related documents`

1. Select **Next**.

1. On the **Assign admin unit** page select **Next**.

1. On the **What type of scope do you want to create?** page select **Users** then select **Next**.

1. On the **Create the query to define users** page, in the **User attributes** section, ensure these values are selected for the user attribute configuration:

   - Select the **Attribute** dropdown then select **Department**
   - Leave the default **is equal to** value in the next field
   - Enter `Legal` as the **Value**

1. Add a second attribute by selecting **+ Add attribute** on the **Create the query to define users** page. In the new field under the one we just configured, configure these values:

   - Select the dropdown for the query operator and update it from And to **Or**
   - Select the **Attribute** dropdown then select **Department**
   - Leave the default **is equal to** value in the next field
   - Enter `Retail` as the **Value**

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your adaptive scope is created select **Done** on the **Your scope was created** page.

1. Back on the **Adaptive scopes** page, select **Solutions** from the bottom of the left sidebar.

1. Select the tab for **Data Governance** from the top filter buttons.

1. Select the **Data Lifecycle Management** card.

1. On the **Data Lifecycle Management** page, expand **Policies** then select **Retention policies**.

1. On the **Retention policies** page, select **+ New retention policy**.

1. On the **Name your retention policy** page enter:

    - **Name**: `Legal Data Retention`
    - **Description**: `Retention of all documents within the legal and retail departments.`

1. Select **Next**.

1. On the **Policy Scope** page select **Next**.

1. On the **Choose the type of retention policy to create** page select **Adaptive** then select **Next**.

1. On the **Choose adaptive policy scopes and locations** page select **+ Add scopes**.

1. On the **Choose adaptive policy scopes** flyout panel select the checkbox for **Legal Documents Retention** then select **Add** at the bottom of the panel.

1. Back on the **Choose locations to apply the policy** enable:

    - Exchange mailboxes
    - OneDrive accounts
    - Leave all other locations disabled.

1. Select **Next**.

1. On the **Decide if you want to retain content, delete it, or both** page, ensure these values are set for the retention configuration:

   - Select **Retain items for a specific period**.
   - Under **Retain items for a specific period**, select **5 years** from the dropdown list
   - **Start the retention period based on**: When items were last modified
   - **At the end of the retention period**: Do nothing

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your policy is created, select the **Done** button.

1. Once your policy is created select **Done** on the **You successfully created a retention policy** page.

You have successfully applied an adaptive scope to a retention policy, covering legal and retail department documents for five years.

## Task 5 – Test the adaptive scope policy

In this final task, you'll verify the users affected by the adaptive scope and test the new retention policy to ensure it is functioning as expected.

>**Note**: When you create and submit a retention policy, it can take up to seven days for the retention policy to be applied.

1. Open an elevated PowerShell window by right clicking the Windows button in the task bar, then select **Terminal (Admin)**. Select **Yes** if the **User Account Control** dialogue pops up.

1. Run the **Connect-IPPSSession** cmdlet to the Security & Compliance Center in your tenant:

    ```powershell
    Connect-IPPSSession
    ```

1. When prompted with a sign in dialog box, sign in with Joni Sherman's account, `JoniS@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's account was set in a previous exercise.

1. Run the **Get-RetentionCompliancePolicy** cmdlet to view all details of the adaptive scope policy:

    ```powershell
    Get-RetentionCompliancePolicy -Identity "Legal Data Retention" -DistributionDetail | Format-List
    ```

1. Review the results and search for these details:

    - **Enabled**: True
    - **Mode**: Enforce
    - **DistributionStatus**: Success

    ![Screenshot of the results of the Get-RetentionCompliancePolicy cmdlet.](../Media/results-getretentioncompliancepolicy.png)

You have verified the successful implementation of the adaptive scope retention policy, confirming that it is correctly applied and operational.
--->
