# 实验室 3 - 练习 4 - 使用电子数据展示进行恢复

在本练习中，假设你是 Joni Sherman，Contoso Ltd. 的合规性管理员。你的组织位于德克萨斯州，并且想要实现保留策略以遵守当地法律。Uniform Preservation of Private Business Records Act 规定，记录可以在三年后销毁而不会构成违法（特例除外），为了遵守该法，组织制定了一个保留计划，打算将组织内的所有项都保留三年。

### 任务 1 - 创建电子数据展示事例

在本练习中，你将创建电子数据展示事例并开始搜索 Megan Bowen 发送的包含标记 8 项目相关信息的邮件。法律部门要求提供此信息以进行合规性审查。

1. 你仍应使用 **lon-cl1\admin** 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 **Joni Sherman** 身份 JoniS@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管服务提供程序提供的唯一租户 ID）登录到 Microsoft 365。  Joni 的密码应由实验室托管提供程序提供。 

2. 在 **Microsoft Edge** 中，导航到 **https://compliance.microsoft.com** 并以 **Joni Sherman** 的身份登录到 Microsoft 365 合规性门户。

3. 在门户的左侧导航窗格上，展开“**电子数据展示**”，然后选择“**核心**”。

4. 在“**核心电子数据展示**”页面上，选择“**+ 创建资源**”。

5. 在 **“事例名称”** 字段中，键入 *“标记 8 项目事例”*，然后在 **“事例说明”** 中键入 *“本事例将用于评估 Megan Bowen 的关于标记 8 项目的邮件”*，然后选择 **“保存”**。

6. 在“**核心电子数据展示**”页面上，双击“**标记 8 项目事例**”以打开事例。

7. 在“事例”视图中，选择 **“搜索”** 选项卡。

8. 选择“**+ 新搜索**”以开始新的搜索。

9. 在“**名称和说明**”页中，键入“**标记 8 项目**”用作名称，然后选择“**下一步**”。

10. 在“**位置**”页面中，将“**Exchange 邮箱**”设为“**开**”，然后选中“**选择用户、组或团队**”。

11. 在 **“Exchange 邮箱”** 对话框中，搜索 *Megan Bowen* 并选择 Megan 的邮箱。  选择 **“完成”**。

12. 在 **“位置”** 页面中，取消选中 **“为本地用户添加应用内容”** 复选框，然后选择 **“下一步”**。

13. 在 **“定义搜索条件”** 页面的 **“关键字”** 区域中，键入 **“标记 8”** 并选择 **“下一步”**。

14. 在 **“查看并创建搜索”** 窗口中，选择 **“提交”**。

15. 创建搜索后，选择 **“完成”**。

你已经成功创建了电子数据展示事例，并搜索了 Megan Bowen 发送或接收的所有包含标记 8 项目相关信息的邮件。

### 任务 2 - 分配记录管理权限和电子数据展示管理器权限

在此任务中，你将准备把在任务 1 中发现的数据导出到 PST 文件中，以便将该文件提供给法律部门。首先，需要将“记录管理”角色分配给合规性管理员，否则，他们将无法导出搜索结果。

1. 使用 **“lon-cl1\admin”** 帐户登录到客户端 1 VM (LON-CL1)。

2. 在 **Microsoft Edge** 中，导航到 **https://compliance.microsoft.com** 并以 **MOD 管理员**的身份登录到 Microsoft 365 合规性门户。  你可能需要注销 Joni Sherman 的登录。

3. 在左侧导航窗格中，选择“**权限**”，然后**在合规中心下**选择“**角色**”。  选择“**记录管理**”角色。

4. 在角色概述窗格中，选择 **“成员”** 类别旁边的 **“编辑”**。

5. 选择“**选择成员**”，然后选择“**+ 添加**”。
 
6. 搜索 **Joni Sherman** 并选中其姓名前面的复选框，然后选择 **“添加”**。

7. 查看对成员列表所做的更改，然后选择 **“完成”**。

8. 选择“**保存**”。  

9. 对“**电子数据展示管理器**”角色重复步骤 3-8，这样 Joni 就可以在未来的实验室中导出电子数据展示数据。

你已成功为合规性管理员授予了导出搜索结果和执行记录管理任务的权限。可能需要长达 60 分钟的时间才能对用户应用权限，但你可以继续执行下一个任务。

### 任务 3 - 从电子数据展示事例中导出数据

在此任务中，你将准备导出在任务 1 中发现的数据，以便可以将其提供给法律部门。  请记住，权限可能需要 60 分钟才会在租户中可用。

1. 你仍应使用 **“lon-cl1\admin”** 帐户登录到客户端 1 VM (LON-CL1)。

2. 在 **Microsoft Edge** 中，导航到 **https://compliance.microsoft.com** 并以 **Joni Sherman** 的身份登录到 Microsoft 365 合规性门户。

3. 在 **Microsoft 365 合规性**门户的左侧导航窗格中，展开“**电子数据展示**”，然后选择“**核心**”。

4. 单击“**标记 8 项目事例**”来打开该事例。

5. 选择“**搜索**”选项卡，然后选择“**标记 8 项目**”搜索。

**提示：** 如果电子数据展示搜索没有数据，请考虑使用搜索参数。  在之前的实验室中，你是否让 Megan 发送了一封关于“*标记 8*”项目的电子邮件？  如果没有，请考虑将搜索中的关键字更改为 Megan 邮箱中任何一封现有电子邮件中的字词。  例如，“planner”一词通常出现在 Megan 现有的几封电子邮件中。  为了使导出有内容处理，搜索必须有数据。

6. 在“**标记 8 项目**”对话框中，选择“**操作**”按钮下拉列表，然后选择“**导出结果**”。

7. 在“**导出结果**”窗格的“**输出选项**”下，查看选项。  选择“**导出**”按钮。

8. 关闭“**标记 8 项目**”搜索窗格。  

9. 在案件屏幕上选择“**导出**”选项卡。  双击刚刚创建的导出。

10.  在导出窗格的“**导出密钥**”下，选择“**复制到剪切板**”，然后选择“**下载结果**”。
  
11.  出现提示时，请在浏览器中选择“**打开**”来安装电子数据展示导出工具，然后选择“**安装**”。

12.  在出现的对话框中，粘贴之前复制到剪切板的密钥。  选择合适的位置来下载文件。  选择“**启动**”。

你已成功导出发现的数据。

### 任务 4 - 对邮箱执行搜索和清除操作

一项调查显示，用户收到一些钓鱼邮件，你的任务是删除环境中所有邮箱中的钓鱼邮件。

1. 你仍应使用 **“lon-cl1\admin”** 帐户登录到客户端 1 VM (LON-CL1)。

2. 在 **Microsoft Edge** 中，导航到 **https://compliance.microsoft.com** 并以 **Joni Sherman** 的身份登录到 Microsoft 365 合规中心门户。

3. 在合规中心的左侧导航窗格中，选择 **“内容搜索”**。

4. 选择 **“+”** 图标/按钮以新建搜索。

5. 在 **“名称和说明”** 窗口中，键入 **“删除钓鱼邮件”** 并选择 **“下一步”**。

6. 在 **“位置”** 部分中，选择 **“特定位置”**，然后选择 **“Exchange 邮箱”** 以将其打开，再选择 **“下一步”**。

7. 在 **“定义搜索条件”** 页面的 **“关键字”** 字段中，键入 *“From:phishingmail@outlook.com AND subject:"Password changed"”* 并选择 **“下一步”**。

8. 在“**查看并创建搜索**”窗口中，选择“**提交**”。单击“**完成**”。

9. 创建搜索后，需要使用 **“安全与合规 PowerShell”** 进行清除。在开始菜单中，选择以管理员身份运行 **Windows PowerShell**。

10. 在 **PowerShell** 窗口中，使用以下 cmdlet，然后以 **MOD 管理员**身份登录：

	`Connect-IPPSSession`

11. 在 **PowerShell** 窗口中，使用以下命令：

	`New-ComplianceSearchAction -SearchName "Phishing mail removal" -Purge -PurgeType HardDelete`

12. 在 PowerShell 中，键入 **“Y”** 代表“是”以确认操作。

你已经成功创建了新的内容搜索来查找特定电子邮件，然后使用清除操作从用户的邮箱中删除了钓鱼邮件。只能以“组织管理”角色的成员身份运行清除操作，而“合规性管理员”不属于该角色。

# 继续进行实验室 3 - 练习 5
