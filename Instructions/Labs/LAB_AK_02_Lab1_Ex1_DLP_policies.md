---
lab:
  title: 练习 1 - 管理 DLP 策略
  module: Module 2 - Implement Data Loss Prevention
---
## WWL 租户 - 使用条款

如果在讲师引导式培训过程中向你提供租户，请注意，提供租户旨在支持讲师引导式培训中的动手实验室。

租户不应共享或用于动手实验室以外的用途。 本课程使用的租户为试用租户，课程结束后无法使用或访问，不符合扩展条件。

租户不得转换为付费订阅。 在本课程中获得的租户仍然是 Microsoft Corporation 的财产，我们保留随时获取访问权限和收回的权利。

# 实验室 2 - 练习 1 - 管理 DLP 策略

你是 Joni Sherman，Contoso Ltd. 新上任的合规性管理员，负责配置公司的 Microsoft 365 租户以防止数据丢失。 Contoso Ltd. 是美国的一家提供驾驶指导服务的公司，你需要确保敏感客户信息不会泄露到组织外部。

## 任务 1 - 在测试模式下创建 DLP 策略

在本练习中，你将在 Microsoft Purview 门户中创建数据丢失防护策略以防止敏感数据被用户共享。 当你的用户想共享包含信用卡信息的内容时，你创建的 DLP 策略会向他们发出通知，并让他们提供发送此信息的正当理由。 由于你目前不想用户被阻止操作影响，所以将在测试模式下实现策略。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在 Microsoft Edge 中，导航到 `https://compliance.microsoft.com` ，并以 Joni Sherman 的身份登录到 Microsoft Purview 门户  。 以 JoniS@WWLxZZZZZZ.onmicrosoft.com 身份登录（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）。  Joni 的密码应由实验室托管提供程序提供。

1. 如果出现“保持登录?”对话框，请选中“不再显示此内容”复选框，然后选择“否”  。

1. 在 Microsoft Purview 门户的左侧导航窗格中，展开“数据丢失防护”，然后选择“策略”。************

1. 在“策略”页面中，选择“+创建策略”以启动用于创建新数据丢失防护策略的向导。********

1. 在“从模板开始或创建自定义策略”页面上，向下滚动并在“类别”下选择“自定义”，在“模板”下选择“自定义策略”    。 默认情况下，这两个选项应已选中，然后选择“下一步”。

1. 在“为 DLP 策略命名”页面上输入****：

   - 名称****：信用卡 DLP 策略
   - 说明****：防止共享信用卡号

1. 选择**下一步**。

1. 在“分配管理单元”**** 页上，选择“下一步”****。

1. 在“选择应用策略的位置”页面上，仅启用“Teams 聊天和频道消息”选项，然后选择“下一步”  。

1. 在“定义策略设置”页面上，选择“创建或自定义高级 DLP 规则”，然后选择“下一步”  。

1. 在“自定义高级 DLP 规则”页面上选择“+ 创建规则” 。

1. 在“创建规则”浮出控件页面上，在“名称”字段中键入“信用卡信息”****__****。

1. 在“条件”下，选择“+ 添加条件”，然后从下拉菜单中选择“内容包含”  。

1. 在新的“内容包含”区域中，选择“添加”，然后从下拉菜单中选择“敏感信息类型”  。

1. 在“敏感信息类型”页面上，选择“信用卡号”并选择“添加”  。

1. 在“创建规则”页面上，选择“+ 添加条件”，并在下拉菜单中选择“在 Microsoft 365 中共享内容”  。

1. 在新的“从 Microsoft 365 共享内容”部分中，选择“仅与组织内的人员进行共享”选项********。

1. 在“创建规则”页面上，选择“+ 添加操作”********。 在“满足条件时使用操作保护内容。”下**** 展开“限制对 Microsoft 365 位置中内容的访问或对这些内容进行加密”复选框，然后选择“阻止所有人”。********

1. 在“创建规则”页面上的“用户通知”部分，选择开关将其切换至“开启”位置以启用用户通知************。

1. 选中相应复选框以启用“使用策略提示在 Office 365 服务中通知用户****”。

1. 在“用户替代”下，选中“允许来自 M365 服务的替代。允许 Exchange、SharePoint、OneDrive 和 Teams 中的用户替代策略限制。”复选框********。

1. 选中“需要业务理由才可替代”复选框****。

1. 在“事件报告”部分的“在管理员警报和报告中使用此严重性级别”下拉菜单中，选择“低”  。

1. 在“创建规则”页面上，选择“保存”，然后选择“下一步”************。

1. 在“策略模式”页上，选择“在模拟模式下运行策略”，并选择“在处于模拟模式时显示策略提示”************。

1. 在“查看并完成”页上查看设置，然后选择“提交”********

1. 在“新策略已创建”页上，选择“完成” 。

你现在已创建了一个 DLP 策略，该策略可扫描 Microsoft Teams 聊天和频道中的信用卡号，并允许用户在提供业务理由后替代此策略。

## 任务 2 - 修改 DLP 策略

在本任务中，你将修改在上一步中创建的现有 DLP 策略以扫描电子邮件，查看是否存在信用卡信息，并在用户尝试在电子邮件中共享此内容时告知用户。

1. 你仍然应该会使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该会以 Joni Sherman 的身份登录到 Microsoft 365。

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 `https://compliance.microsoft.com`。

1. 在 Microsoft Purview 门户的左侧导航窗格中，展开“数据丢失防护”，然后选择“策略”。************

1. 在“策略”页面上，选中最近创建的“信用卡 DLP 策略”旁边的复选框，然后选择“编辑策略”（铅笔图标）以************ 打开策略向导。

1. 在“为 DLP 策略命名”页面上，选择“下一步” 。

1. 在“分配管理单元”**** 页上，选择“下一步”****。

1. 在“选择应用策略的位置”页上，启用“Exchange 电子邮件”选项，然后选择“下一步”，直到出现“查看并完成”页****************。

1. 选择“提交”以应用在策略中进行的修改****。

1. 更新策略后，选择“完成”。

你已经修改了现有的 DLP 策略，并更改了它扫描内容的位置。

## 任务 3 - 在 PowerShell 中创建 DLP 策略

在本任务中，你将使用 PowerShell 创建一个 DLP 策略来保护 Contoso EmployeeID，并防止这些 ID 在 Exchange 中被共享。 如果用户要发送的电子邮件中包含 Contoso EmployeeID，系统则会提示用户他们正在尝试共享敏感数据，并且将阻止邮件发送操作。

1. 你仍然应该会使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在开始菜单中，选择 Windows PowerShell。

1. 在 PowerShell 窗口中，输入

   ```powershell
   Connect-IPPSSession
   ```

   然后以 Joni Sherman JoniS@WWLxZZZZZZ.onmicrosoft.com 的身份（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录。  Joni 的密码应由实验室托管提供程序提供。

1. 在 PowerShell 中输入以下命令，以创建扫描所有 Exchange 邮箱的 DLP 策略：

   ```powershell
   New-DlpCompliancePolicy -Name "EmployeeID DLP Policy" -Comment "This policy blocks sharing of Employee IDs" -ExchangeLocation All
   ```

1. 在 PowerShell 中输入以下命令，以将 DLP 规则添加到在先前步骤中创建的 DLP 策略：

   ```powershell
   New-DlpComplianceRule -Name "EmployeeID DLP rule" -Policy "EmployeeID DLP Policy" -BlockAccess $true -ContentContainsSensitiveInformation @{Name="Contoso Employee IDs"}
   ```

1. 使用以下命令查看 EmployeeID DLP 规则：

   ```powershell
   Get-DLPComplianceRule -Identity "EmployeeID DLP rule"
   ```

你已经使用 PowerShell 创建了一个在 Exchange 中扫描 Contoso EmpoloyeeID 的 DLP 策略。

## 任务 4 - 测试 DLP 策略

在此任务中，你将测试在上一个任务中创建的 DLP 策略。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并应以 Joni Sherman 的身份登录到 Microsoft 365****。

1. 打开 Microsoft Edge 浏览器窗口，导航到 `https://outlook.office.com/`****

1. 选择左上角的“新建邮件”按钮以撰写新电子邮件****。

1. 在“收件人”字段中，输入“Megan”，然后选择 Megan Bowen 的电子邮件地址****__****。

1. 在“主题”字段中，输入“有关员工信息的帮助__”。

1. 在电子邮件正文中输入：

   ``` text
   Please help me with the start dates for the following employees:
   ABC123456
   DEF678901
   GHI234567

   Thank you, 
   Joni Sherman
   ```

1. 选择邮件窗口右上角的“发送”按钮以发送电子邮件****。

1. 你应该会收到一条消息，指出电子邮件无法送达并被 DLP 策略阻止。

      ![“管理角色”选项的屏幕截图](../Media/dlp-email-blocked.png)

你已成功测试自己的 DLP 策略。

## 任务 5 - 在模拟模式下激活策略

在本任务中，你将激活在测试模式中创建的信用卡信息 DLP 策略，使该策略执行其保护操作。

1. 你仍然应该会使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该会以 Joni Sherman 的身份登录到 Microsoft 365。

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 `https://compliance.microsoft.com`。

1. 在 Microsoft Purview 门户的左侧导航窗格中，展开“数据丢失防护”，然后选择“策略”。************

1. 在“策略”页面上，选中“信用卡 DLP 策略”旁边的复选框，然后选择“编辑策略”（铅笔图标）以************ 打开策略向导。

1. 选择“下一步”，直到出现“策略模式”页，然后选择“立即打开策略”************。

1. 在“查看并完成”页上，选择“提交”********。

1. 在“策略已更新”页面上，选择“完成”********。

你已成功激活该 DLP 策略。 如果策略检测到有人试图共享信用卡信息，它将阻止该操作，并允许用户提供业务正当理由来覆盖该阻止操作。

## 任务 6 - 修改策略优先级

在创建两个 DLP 策略之后，你希望确保限制性更高的策略在处理时能得到比限制性较低的策略更高的优先级。 因此，你需要将 EmployeeID DLP 策略移动至更高的优先级。

1. 你仍然应该会使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该会以 Joni Sherman 的身份登录到 Microsoft 365。

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 `https://compliance.microsoft.com`。

1. 在 Microsoft Purview 门户的左侧导航窗格中，展开“数据丢失防护”，然后选择“策略”。************

1. 在“策略”选项卡中，选择“EmployeeID DLP 策略”旁边三个垂直分布的点以打开“操作”选择并选择“移动到顶部”****************。

1. 在“数据丢失防护”窗口中，选择“刷新”，然后查看策略表的“顺序”列中的优先级  。

你已成功修改 DLP 策略的优先级。 如果两个策略匹配到相同的内容，则将执行高优先级策略的操作。

## 任务 7 - 在 Microsoft 365 Defender 中启用文件监视

你需要使用 Microsoft 365 Defender 中的文件策略来保护 OneDrive 和 SharePoint Online 位置中的文件。 在创建文件策略之前，你需要启用文件监视，从而让 Microsoft 365 Defender 扫描组织中的文件。

1. 你仍然应该会使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 在右上角选择 Joni Sherman 的个人资料图片，并选择“退出登录”，然后关闭浏览器 。

1. 打开 Microsoft Edge，导航到 `https://security.microsoft.com` 并以 MOD 管理员身份 admin@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft 365 Defender 门户************。 管理员的密码应由实验室托管提供程序提供。

1. 在左侧导航窗格中，展开“系统”，然后选择“设置”********。

1. 在“设置”页面中，选择“云应用”********。

1. 在“云应用”窗口的左窗格中，向下滚动到“信息保护”部分，然后选择“文件”************。

1. 选中“启用文件监视”复选框，然后选择“保存”（如果尚未标记）********。

你已成功在 Microsoft 365 Defender 中启用了文件监视，现在可以使用文件策略扫描文件，以查看是否存在敏感内容。

## 任务 8 - 为 Microsoft 365 Defender 创建文件策略

在本任务中，你需要在 Microsoft 365 Defender 中创建一个文件策略，用于扫描 OneDrive 和 SharePoint Online 中的文件，并在共享文件时自动隔离包含信用卡信息的文件。

1. 你仍然应该会使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在“Microsoft Edge”中，“Microsoft Defender for Cloud Apps 门户”选项卡应该仍处于打开状态。 在右上角选择 MOD 管理员的个人资料图片，并选择齿轮旁边的“退出登录”，然后关闭浏览器********。

1. 打开 Microsoft Edge，导航到 `https://security.microsoft.com` 并以 Joni Sherman 的身份 JoniS@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft 365 Defender 门户************。 Joni Sherman 的密码应由实验室托管提供程序提供。

1. 在 Microsoft 365 Defender 门户的左侧导航栏中，向下滚动到“云应用”部分，然后选择“文件”。************

1. 在“文件”页面上，选择“+ 从搜索新建策略”。********

1. 在“创建文件策略”页面上，将“策略模板”选项保留为“无模板”。************

1. 在“创建文件策略”页面上输入以下信息****

   - 策略名称****：文件的信用卡信息
   - 说明****：防止在文件中共享信用卡号

1. 将“策略严重性”保持为“低”（一个点亮的图标），并确保将“类别”设置为“DLP”   。 这些应该是文件策略的默认设置。

1. 在“与以下所有项匹配的文件”区域中，展开下拉菜单“公开(Internet)、外部、公开”并添加“内部”  。

1. 在“检查方法”下拉菜单中，选择“数据分类服务”********。

1. 在“选择检查类型…”下拉菜单中，选择“敏感信息类型…” 。

1. 在“选择敏感信息类型”对话框中，选择“信用卡号”，然后选择右上角的“完成”************。

1. 在“警报”下，勾选“为每个匹配的文件创建警报”复选框，并查看你的选项 。 通过选择“另存为默认设置”，将设置保留为默认设置****。

1. 在“治理操作”部分，展开“Microsoft OneDrive for Business”并选择“放入用户隔离”  。

1. 在“治理操作”部分，展开“Microsoft SharePoint Online”并选中“放入用户隔离”复选框************。

1. 在页面底部选择“创建”  。

你现在已经创建了一个文件策略，该策略将持续扫描保存在 OneDrive 和 SharePoint 中的文件，以查看是否存在信用卡信息，并在组织内部共享这些文件时隔离它们。

## 任务 9 - 为 Power Platform 创建 DLP 策略

贵公司使用 Power Automate 流在 SharePoint Online 和 Salesforce 之间共享数据。 在本任务中，你将为 Power Platform 创建一个 DLP 策略，该策略允许现有的流继续工作，但会阻止创建将在 SharePoint Online 和定义为非业务类的应用之间共享数据的流。

1. 使用 lon-cl2\admin 帐户登录到客户端 2 VM (LON-CL1)****。

1. 在“Microsoft Edge”中，导航到 `https://admin.powerplatform.microsoft.com` 并以“MOD 管理员”身份 admin@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Power Platform 管理中心  。  管理员的密码应由实验室托管提供程序提供。

1. 在“Power Platform 管理中心”的左侧导航窗格中，选择“策略”下拉菜单，然后选择“数据策略”  。

1. 在“数据策略”页面上，选择“+ 新建策略” 。

1. 在“为策略命名”页面上，输入“租户范围 SharePoint 策略”，然后选择“下一步”****__****。

1. 在“分配连接器”页面上的“非业务类|默认”选项卡上，选择“SharePoint”和“Salesforce”，然后选择页面顶部的“移动至业务类”    。

1. 在“分配连接器”页面中，选择“业务类”选项卡以确保现在同时显示 SharePoint 和 Salesforce，然后选中“下一步”************。

1. 在“自定义连接器模式”页面上，选择“下一步”********。

1. 在“定义范围”页面上，选择“添加所有环境”，然后选择“下一步”************。

1. 在“查看并创建策略”页面上，查看策略设置并选择“创建策略”********。

你现在已经创建了一个 PowerPlatform DLP 策略，该策略阻止用户创建涉及 SharePoint Online 连接器和任何非 Salesforce 连接器的流。
