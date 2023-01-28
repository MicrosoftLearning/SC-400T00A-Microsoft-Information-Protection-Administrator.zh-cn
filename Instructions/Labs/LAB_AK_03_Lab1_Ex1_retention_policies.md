---
lab:
  title: 练习 1 - 配置保留策略
  module: Module 3 - Implement Data Lifecycle and Records Management
---

# <a name="lab-3---exercise-1---configure-retention-policies"></a>实验室 3 - 练习 1 - 配置保留策略

在本练习中，假设你是 Contoso Ltd. 的系统管理员 Joni Sherman。 你的组织位于德克萨斯州，并且想要实现保留策略以遵守州法律，该法律规定，记录可以在在三年后删除，而不会构成违法。 

为了遵守该法，你的组织制定了一个保留计划，打算将组织内的所有项都保留三年。


### <a name="task-1--create-company-wide-retention-policy"></a>任务 1 - 创建公司范围内的保留策略

在本练习中，你将创建公司范围内的保留策略，应用保留期，并设置策略应用位置。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在 Microsoft Edge 中，导航到 https://compliance.microsoft.com 并以 Joni Sherman 的身份 JoniS@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户  。  Joni 的密码应由实验室托管提供程序提供。

1. 在 Microsoft Purview 门户中的左侧导航窗格中，选择“策略”，然后在“数据”下选择“保留”   。

1. 在“数据生命周期管理”页面的“保留策略”选项卡中，选择“+ 新建保留策略”  。

1. 在“为保留策略命名”页上的“名称”和“说明”中输入以下信息  ：

    - 名称：公司范围
    - 说明：所有位置（Teams 除外）

1. 选择“下一步”按钮。  

1. 在“选择要创建的保留策略的类型”区域中，选择“静态”，然后选择“下一步”。  

1. 在“选择应用策略的位置”区域中，确保选择了“Exchange 电子邮件”、“SharePoint 网站”、“OneDrive 帐户”和“Microsoft 365 组”，然后选择“下一步” 。

1. 在“确定是想要保留内容还是删除内容或两者兼而有之”页上的“将项保留特定时间段”部分中，输入以下信息 ：

    - 将项保留特定时间段：从下拉列表中选择“自定义” 
    - 将“年数”字段更改为 3
    - 保留期开始依据：上次修改项的时间
    - 保留期结束时：自动删除项

1. 选择“下一步”按钮。

1. 在“查看并完成”页面上，选择“提交”按钮 。

1. 创建策略后，选择“完成”按钮。

你已成功为 Exchange 电子邮件、Microsoft 365 组、OneDrive 和 SharePoint 网站位置创建了保留策略。 此保留策略将自上次修改日期起将这些项保留在这些位置 3 年。 此策略可能需要长达 24 小时才能应用于你的租户，但你可以继续执行下一步。

### <a name="task-2--create-location-based-retention-policies-with-filter"></a>任务 2 - 使用筛选器创建基于位置的保留策略

你现在将为 Teams 位置创建保留策略。 由于 Teams 频道可以包含文档，因此它们将全部保留。 你的组织决定要求部分用户进行 Team 聊天时需要保留期。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。 

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 https://compliance.microsoft.com。

1. 在 Microsoft Purview 门户中的左侧导航窗格中，选择“策略”，然后在“数据”下选择“保留”   。

1. 在“数据生命周期管理”页面的“保留策略”选项卡中，选择“+ 新建保留策略”  。

1. 在“为保留策略命名”页上的“名称”和“说明”中输入以下信息  ：

    - **名称**：Teams 保留
    - **说明**：针对 Teams 的保留位置

1. 选择“下一步”按钮。

1. 在“选择要创建的保留策略的类型”区域中，选择“静态”，然后选择“下一步”。  

1. 在“选择应用策略的位置”页面上，输入以下设置：

    - “Teams 频道消息”位置 -“状态”： 启用 
    - Teams 聊天位置 - 状态：开启 
    - 所有其他位置都应自动“关闭”。
    

1. 对于“Teams 聊天”位置，选择“所有用户”下的“编辑”文本链接  

1. 在“Teams 聊天”窗格中，添加用户： 
    - Adele Vance
    - Pradeep Gupta

    注意：通过添加这两名用户，Teams 聊天中的包括设置从“所有团队”更改为了仅添加的这两名用户。

1. 选择“完成”，然后选择“下一步” 。

1. 在“确定是想要保留内容还是删除内容或两者兼而有之”页上的“将项保留特定时间段”部分中，输入以下信息 ：

    - 将项保留特定时间段：从下拉列表中选择“自定义” 
    - 将“年数”字段更改为 3
    - 保留期开始依据：上次修改项的时间
    - 保留期结束时：自动删除项


1. 选择“下一步”按钮。

1. 在“查看并完成”页面上，选择“提交”按钮 。

1. 成功创建策略后，选择“完成”。

你已成功为 Teams 位置创建了保留策略。 你为所有 Teams 频道位置设置了 3 年保留期。 你已为“Teams 聊天”位置设置了一个筛选器，以便仅应用于特定用户。

### <a name="task-3--create-retention-policy-via-powershell"></a>任务 3 - 通过 PowerShell 创建保留策略

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

### <a name="task-4--create-retention-policy-with-adaptive-scope"></a>任务 4 - 使用自适应范围创建保留策略

在本练习中，你将为财务和法律部门创建保留策略。 该策略的目的是遵守法律，将所有法律相关文档保留 5 年。 首先，你将创建一个自适应范围，包括法律和零售部门，然后使用此范围创建保留策略。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。 

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 https://compliance.microsoft.com。

1. 在 Microsoft Purview 门户中的左侧导航窗格中，选择“数据生命周期管理” 。
1. 在“数据生命周期管理”上的“自适应范围”选项卡中，选择“+ 创建范围”  。
1. 在“为自适应策略范围命名”页上的“名称”和“说明”中输入以下信息  ：

    - 名称：法律文档保留
    - 说明：法律相关文档的保留

1. 选择“下一步”按钮。
1. 在“想要创建哪种类型的范围?”页面上，选择“用户” 。
1. 选择“下一步”按钮。
1. 在“创建查询以定义用户”页面上，在“用户属性”下打开该属性的下拉菜单，然后选择“部门”  。
1. 直接在属性字段旁边，选择“等于”作为运算符。
1. 对于值，输入“法律”
1. 若要添加第二个属性，请在“创建查询以定义用户”页面上选择“+ 添加属性” 。
1. 对于“查询运算符”、“属性”、“运算符”和“值”，请输入以下信息   ：
    - 查询运算符：或
    - 属性：部门
    - 运算符：等于
    - 值：零售

1. 选择“下一步”按钮。
1. 在“查看并完成”页面上，选择“提交”按钮 。
1. 成功提交后，单击“完成”按钮以关闭页面。

1. 在 Microsoft Purview 门户中的左侧导航窗格中，选择“策略”，然后在“数据”下选择“保留”   。

1. 在“数据生命周期管理”页面的“保留策略”选项卡中，选择“+ 新建保留策略”  。

1. 在“为保留策略命名”页上的“名称”和“说明”中输入以下信息  ：

    - 名称：法律数据保留
    - 说明：保留法律和零售部门内的所有文档。

1. 选择“下一步”按钮。

1. 在“选择要创建的保留策略的类型”区域中，选择“自适应”，然后选择“下一步”  。

1. 在“选择自适应策略范围和位置”页面上，选择“+ 添加范围” 。
2. 在新的“选择自适应策略范围”页上，选择“法律文档保留”，然后选择“添加”按钮  。

1. 在“选择应用策略的位置”下，输入以下信息：

    - Exchange 电子邮件 - 状态：开启 
    - OneDrive - 状态：开启 
    - 所有其他位置都应自动“关闭”。
    
1. 选择“下一步”按钮。
1. 在“确定是想要保留内容还是删除内容或两者兼而有之”页上的“将项保留特定时间段”部分中，输入以下信息 ：

    - 将项保留特定期限：5 年
    - 保留期开始依据：项创建时间
    - 保留期结束时：无操作

1. 选择“下一步”按钮。

1. 在“查看并完成”页面上，选择“提交”按钮 。

1. 创建策略后，选择“完成”按钮。
### <a name="task-5--test-adaptive-scope-policy"></a>任务 5 - 测试自适应范围策略

在本练习中，你将验证受自适应范围影响的用户，并测试新的自适应保留策略。

注意：创建并提交保留策略后，最多可能需要 7 天才能应用保留策略。

 1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。 

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 https://compliance.microsoft.com。

1. 在 Microsoft Purview 门户中的左侧导航窗格中，选择“策略”，然后在“数据”下选择“保留”   。

1. 在“数据生命周期管理”页面上的“自适应范围”选项卡中，选择“法律文档保留”  。

1. 在新的“法律文档保留”页面上，选择“范围详细信息” 。
1. 在“法律文档保留”页面上，应能够看到受范围影响的所有位置。

[//]: <> (实验室租户中的错误：无法加载数据。请重试)

1. 若要查看自适应范围保留策略的详细信息，请打开 PowerShell 窗口，方法是右键选择 Windows 按钮，然后选择 Windows PowerShell。

1. 使用以下 cmdlet 连接到租户中的“安全与合规中心”：

    ```powershell
    Connect-IPPSSession
    ```
1. 如果出现登录对话框的提示，请以 MOD 管理员的身份 admin@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管服务提供程序提供的唯一租户 ID）登录。 管理员的密码应由实验室托管提供程序提供。
1. 运行以下 cmdlet 以查看自适应范围策略的所有详细信息：
    ```powershell
    Get-RetentionCompliancePolicy -Identity "Legal Data Retention" -DistributionDetail | Format-List
    ```
1. 查看详细信息。 某些参数应具有以下状态：

    - Enabled: True
    - Mode: Enforce
    - DistributionStatus: Success