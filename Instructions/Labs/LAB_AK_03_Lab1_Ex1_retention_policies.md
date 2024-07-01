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

在本练习中，假设你是 Contoso Ltd. 的系统管理员 Joni Sherman。 你的组织位于德克萨斯州，并且想要实现保留策略以遵守州法律，该法律规定，记录可以在在三年后删除，而不会构成违法。

为了遵守该法，你的组织制定了一个保留计划，打算将组织内的所有项都保留三年。

## 任务 1 - 创建公司范围内的保留策略

在本练习中，你将创建公司范围内的保留策略，应用保留期，并设置策略应用位置。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在 Microsoft Edge 中，导航到 `https://compliance.microsoft.com` 并以 Joni Sherman 的身份 JoniS@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户  。  Joni 的密码应由实验室托管提供程序提供。

1. 在“Microsoft Purview”门户的左侧导航窗格中，展开“数据生命周期管理”，然后选择“Microsoft 365”************。

1. 在“数据生命周期管理”页的“保留策略”选项卡中，选择“+ 新建保留策略”************。

1. 在“为保留策略命名”页上的“名称”和“说明”中输入以下信息  ：

    - **名称**：公司范围
    - **说明**：所有位置（Teams 除外）

1. 选择“下一步”按钮。  

1. 在“策略范围”页上选择“下一步”********。

1. 在“选择要创建的保留策略的类型”区域中，选择“静态”，然后选择“下一步”************。

1. 在“选择应用此策略的位置”中，启用****：

   - Exchange 邮箱****
   - SharePoint 经典和通信站点****
   - **OneDrive 帐户**
   - Microsoft 365 组邮箱和站点****

1. 选择**下一步**。

1. 在“确定是想要保留内容还是删除内容或两者兼而有之”页上的“将项保留特定时间段”部分中，输入以下信息 ：

   - 将项保留特定时间段：从下拉列表中选择“自定义”********
   - 将“年数”字段更改为 3
   - 保留期开始依据：上次修改项的时间
   - 保留期结束时：自动删除项

1. 选择**下一步**。

1. 在“查看并完成”页上，选择“提交”********。

1. 创建策略后，选择“完成”****。

你已成功为 Exchange 电子邮件、Microsoft 365 组、OneDrive 和 SharePoint 网站位置创建了保留策略。 此保留策略将自上次修改日期起将这些项保留在这些位置 3 年。 此策略可能需要长达 24 小时才能应用于你的租户，但你可以继续执行下一步。

## 任务 2 - 使用筛选器创建基于位置的保留策略

你现在将为 Teams 位置创建保留策略。 由于 Teams 频道可以包含文档，因此它们将全部保留。 你的组织决定要求部分用户进行 Team 聊天时需要保留期。

1. 你仍然应该会使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该会以 Joni Sherman 的身份登录到 Microsoft 365。

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 `https://compliance.microsoft.com`。

1. 在“Microsoft Purview”门户的左侧导航窗格中，展开“数据生命周期管理”，然后选择“Microsoft 365”************。

1. 在“数据生命周期管理”页面的“保留策略”选项卡中，选择“+ 新建保留策略”  。

1. 在“为保留策略命名”页上的“名称”和“说明”中输入以下信息  ：

   - **名称**：Teams 保留
   - **说明**：针对 Teams 的保留位置

1. 选择**下一步**。

1. 在“策略范围”页上选择“下一步”********。

1. 在“选择要创建的保留策略的类型”区域中，选择“静态”，然后选择“下一步”。************

1. 在“选择应用策略的位置”页上，启用****：

   - **Teams 渠道消息**
   - **Teams 聊天**
   - 将所有其他位置保留为禁用状态。

1. 对于“Teams 聊天”位置，选择“所有用户”下的“编辑”文本链接

1. 在“Teams 聊天”浮出控件页上添加用户****：

    - Adele Vance
    - Pradeep Gupta

    >注意：添加这两名用户后，Teams 聊天中的“包括”设置从“所有团队”更改为“2 位用户”****************。

1. 选择“完成”，然后选择“下一步”********。

1. 在“确定是想要保留内容还是删除内容或两者兼而有之”页上的“将项保留特定时间段”部分中，输入以下信息 ：

   - 将项保留特定时间段：从下拉列表中选择“自定义”********
   - 将“年数”字段更改为 3
   - 保留期开始依据：上次修改项的时间
   - 保留期结束时：自动删除项

1. 选择**下一步**。

1. 在“查看并完成”页上，选择“提交”********。

1. 在“已成功创建保留策略”页上，选择“完成”********。

你已成功为 Teams 位置创建了保留策略。 你为所有 Teams 频道位置设置了 3 年保留期。 你已为“Teams 聊天”位置设置了一个筛选器，以便仅应用于特定用户。

## 任务 3 - 通过 PowerShell 创建保留策略

你将使用 PowerShell 创建相同的保留策略

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 通过使用鼠标右键来选择 Windows 按钮，然后选择“Windows PowerShell(管理员)”来打开提升的 PowerShell 窗口，如果遇到“用户帐户控制”窗口，则选择“是” 。

1. 使用以下 cmdlet 连接到租户中的“安全与合规中心”：

    ```powershell
    Connect-IPPSSession
    ```

1. 如果出现登录对话框提示，请以 MOD 管理员身份 admin@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管服务提供程序提供的唯一租户 ID）登录。  管理员的密码应由实验室托管提供程序提供。

1. 运行以下 cmdlet 为所有位置（Teams 除外）创建第一个保留策略：

    ```powershell
    New-RetentionCompliancePolicy -Name "Company Wide PS" -ExchangeLocation All -ModernGroupLocation All -SharePointLocation All -OneDriveLocation All
    ```

1. 运行以下 cmdlet 以基于修改的日期设置保留期（以天为单位）：

    ```powershell
    New-RetentionComplianceRule -Name "Company Wide PS Rule" -Policy "Company Wide PS" -RetentionDuration 1095 -ExpirationDateOption ModificationAgeInDays -RetentionComplianceAction Keep
    ```

1. 运行以下 cmdlet，为 Teams 位置创建第二个保留策略：

    ```powershell
    New-RetentionCompliancePolicy -Name "Teams Retention PS" -TeamsChannelLocation All -TeamsChatLocation "Adele Vance", "Pradeep Gupta"
    ```

1. 运行以下 cmdlet，以天为单位设置保留期：

    ```powershell
    New-RetentionComplianceRule -Name "Teams Retention PS Rule" -Policy "Teams Retention PS" -RetentionDuration 1095 -RetentionComplianceAction Keep
    ```

你已通过 PowerShell 成功创建了保留策略，其保留期为 3 年。

<!-- ## Task 4 – Create Retention Policy with adaptive scope

In this exercise you will create a retention policy for the finance and legal department. The purpose of the policy is to comply with the law, retaining all legal related documents for 5 years. First you will create an adaptive scope including the legal and the retail department, then you will create a retention policy using this scope.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **`https://compliance.microsoft.com`**.

1. In the **Microsoft Purview** portal on the left navigation pane expand **Roles & scopes** then select **Adaptive scopes**.

1. On the **Adaptive scopes** page select **+ Create scope**.

1. On the **Name your adaptive policy scope** page input:

    - **Name**: Legal Documents Retention
    - **Description**: Retention for legal related documents

1. Select **Next**.

1. On the **Assign admin unit** page select **Next**.

1. On the **What type of scope do you want to create?** page select **Users** then select **Next**.

1. On the **Create the query to define users** page, under **User attributes** select the drop-down menu for **Attribute** then select **Department**.

1. Directly next to the attribute field select **is equal to** as the operator.

1. Input **Legal** in the **Value** field.

1. To add a second attribute, select **+ Add attribute** on the **Create the query to define users** page.

1. For the **Query operator**, **Attribute**, **Operator**, and **Value** input:

   - **Query operator**: Or
   - **Attribute**: Department
   - **Operator**: is equal to
   - **Value**: Retail

1. Ensure the checkboxes are selected next to each attribute then select **Next**.

1. On the **Review and finish** page select **Submit**.

1. On the **Your scope was created page** select **Done**.

1. In the **Microsoft Purview** portal, in the left navigation pane, expand **Data lifecycle management** then select **Microsoft 365**.

1. On the **Data lifecycle management** page select the **Retention policies** tab then select **+ New retention policy**.

1. On the **Name your retention policy** page input:

    - **Name**: Legal Data Retention
    - **Description**: Retention of all documents within the legal and retail departments.

1. Select **Next**.

1. On the **Policy Scope** page select **Next**.

1. On the **Choose the type of retention policy to create** page select **Adaptive** then select **Next**.

1. On the **Choose adaptive policy scopes and locations** page select **+ Add scopes**.

1. In the right flyout **Choose adaptive policy scopes** page select the checkbox for **Legal Documents Retention** then select the **Add** button.

1. Back on the **Choose locations to apply the policy** enable:

    - **Exchange mailboxes**
    - **OneDrive accounts**
    - Leave all other locations disabled.

1. Select **Next**.

1. On the **Decide if you want to retain content, delete it, or both** page, for the **Retain items for a specific period** section input:

    - **Retain items for a specific period**: 5 years
    - **Start the retention period based on**: When items were created
    - **At the end of the retention period**: Do nothing

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your policy is created, select the **Done** button.

1. On the **You successfully created a retention policy** page select **Done**.

You have successfully applied an adaptive scope to a retention policy.

## Task 5 – Test adaptive scope policy

In this exercise you will verify the users affected by the adaptive scope and test the new adaptive retention policy.

>**Note**: When you create and submit a retention policy, it can take up to seven days for the retention policy to be applied.

1. To review the details of the adaptive scope retention policy, logged into  **lon-cl1\admin**, open a PowerShell window by selecting the Windows button with the right mouse button and then select Windows PowerShell.

1. Connect to the Security & Compliance Center in your tenant with the following cmdlet:

    ```powershell
    Connect-IPPSSession
    ```

1. If prompted with a sign in dialog box, sign in with Joni Sherman's account,  JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. Run the following cmdlet to view all details of the adaptive scope policy:

    ```powershell
    Get-RetentionCompliancePolicy -Identity "Legal Data Retention"     -DistributionDetail | Format-List
    ```

1. Review the details. Certain parameters should have following statuses:

    - **Enabled**: True
    - **Mode**: Enforce
    - **DistributionStatus**: Success

You have verified the success of your adaptive scope.-->
