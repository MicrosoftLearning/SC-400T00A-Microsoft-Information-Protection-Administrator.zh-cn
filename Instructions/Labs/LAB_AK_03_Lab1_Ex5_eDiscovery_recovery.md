---
lab:
  title: 练习 5 - 使用电子数据展示进行恢复
  module: Module 3 - Implement Data Lifecycle and Records Management
ms.openlocfilehash: 18e5cc590d10cdd35f2986a989b58fa07e4d472a
ms.sourcegitcommit: 53488624251b6cf8f79f2d1ff561e3f334764821
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2022
ms.locfileid: "147694948"
---
# <a name="lab-3---exercise-5---use-ediscovery-for-recovery"></a>实验室 3 - 练习 5 - 使用电子数据展示进行恢复

在本练习中，假设你是 Contoso Ltd. 的合规性管理员 Joni Sherman。 你的组织位于德克萨斯州，并且想要实现保留策略以遵守当地法律。 Uniform Preservation of Private Business Records Act 规定，记录可以在三年后销毁而不会构成违法（特例除外），为了遵守该法律，组织制定了一个保留计划，打算将组织内的所有项都保留三年。

### <a name="task-1--create-ediscovery-case"></a>任务 1 - 创建电子数据展示事例

在本练习中，你将创建电子数据展示事例并开始搜索 Megan Bowen 发送的包含标记 8 项目相关信息的邮件。 法律部门要求提供此信息以进行合规性审查。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 https://compliance.microsoft.com。

1. 在门户的左侧导航窗格中，展开“电子数据展示”，然后选择“标准” 。

1. 在“电子数据展示(标准版)”页面上，选择“+ 创建案件” 。

1. 在“新建案例”页面上，在“名称”字段中键入“Mark 8 Project 案例”，并在“说明”中键入“本案例将用于评估 Megan Bowen 的关于 Mark 8 Project 的邮件。”，然后选择“保存” 。

1. 回到“核心电子数据展示(标准)”页面上，选择“Mark 8 Project 案例”以打开此案例 。

1. 在“事例”视图中，选择“搜索”选项卡。

1. 选择“+ 新建搜索”以开始新的搜索。

1. 在“名称和说明”页面中，键入“Mark 8 Project”作为名称并选择“下一步”。

1. 在“位置”页面上，将“Exchange 邮箱”设为“开启”，然后选择“选择用户、组或团队”   。

1. 在“Exchange 邮箱”页面上，搜索 Megan Bowen 并选择 Megan 的邮箱。  选择“完成”  。

1. 在“位置”页面上，取消选中“为本地用户添加应用内容”复选框，然后选择“下一步”  。

1. 在“定义搜索条件”页面的“关键字”区域中，键入“Mark 8”并选择“下一步” 。

1. 在“查看并创建搜索”窗口中，选择“提交” 。

1. 创建搜索后，选择“完成”。

你已经成功创建了电子数据展示案件，并搜索了 Megan Bowen 发送或接收的所有包含标记 8 项目相关信息的邮件。

### <a name="task-2--assign-records-management-and-ediscovery-manager-permissions"></a>任务 2 - 分配记录管理和电子数据展示管理员权限

在此任务中，你将准备把在任务 1 中发现的数据导出到 PST 文件中，以便将该文件提供给法律部门。 首先，需要将“记录管理”角色分配给合规性管理员， 否则，他们将无法导出搜索结果。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 在右上角选择 Joni Sherman 的个人资料图片，并选择“退出登录”。随后关闭浏览器  。

1. 在 Microsoft Edge 中，导航到 https://compliance.microsoft.com 并以 MOD 管理员的身份 admin@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户  。 管理员的密码应由实验室托管提供程序提供。 

1. 在左侧导航窗格中，选择“权限”，然后在“Microsoft Purview 解决方案”下，选择“角色”  。  选择“记录管理”角色。

1. 在“记录管理”窗格中，选择“成员”类别旁边的“编辑”  。

1. 选择“选择成员”，然后选择“+ 添加” 。
 
1. 搜索 Joni Sherman 并选中其姓名前面的复选框，然后选择“添加” 。

1. 查看对成员列表所做的更改，然后选择“完成”。

1. 选择“保存”和“关闭” 。

1. 在“Microsoft Purview 解决方案的角色组”上，选择“电子数据展示管理员”角色 。

1. 在“电子数据展示管理员”窗格上，选择“电子数据展示管理员”类别旁边的“编辑”  。

1. 在“编辑选择电子数据展示管理员”窗格上，选择“选择电子数据展示管理员” 。

1. 选择“+ 添加”，搜索 Joni Sherman 并选中其姓名前面的复选框，然后选择“添加”  。

1. 查看对成员列表所做的更改，然后选择“完成”。

1. 选择“保存”和“关闭” 。

你已成功为合规性管理员授予了导出搜索结果和执行记录管理任务的权限。 可能需要长达 60 分钟的时间才能将权限应用到用户，但你可以继续执行下一个任务。

### <a name="task-3--export-data-from-ediscovery-case"></a>任务 3 - 从电子数据展示案件中导出数据

在此任务中，你将准备导出在任务 1 中发现的数据，以便可以将其提供给法律部门。  请记住，权限可能需要 60 分钟才会在租户中可用。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 在右上角选择 MOD 管理员的个人资料图片，并选择“退出登录”。随后关闭浏览器  。

1. 打开 Microsoft Edge，导航到 https://compliance.microsoft.com 并以 Joni Sherman 的身份 JoniS@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户  。  Joni 的密码应由实验室托管提供程序提供。

1. 在 Microsoft Purview 门户的左侧导航窗格中，展开“电子数据展示”，然后选择“标准”  。

1. 选择“Mark 8 Project 案例”以打开此案例。

1. 选择“搜索”选项卡，然后选择“标记 8 项目”搜索 。

    >[!TIP]
    如果你的电子数据展示搜索没有数据，请考虑搜索参数。 Megan 的邮箱应该包含一些关于 Mark 8 项目的邮件。  如果没有，请考虑将搜索中的关键字更改为 Megan 邮箱中任何现有电子邮件中的任何术语。  例如，“planner”一词通常出现在 Megan 现有的几封电子邮件中。  搜索必须具有数据，以便导出具有任何进程。

1. 在“标记 8 项目”对话框中，选择“操作”按钮下拉菜单，然后选择“导出结果”  。

1. 在“导出结果”窗格的“输出选项”下，查看选项 。  单击“导出”按钮。

    [//]: <> (在 LOD 租户中请求失败，状态代码为 500 - 之前在 M365 Dev 租户中有效)

1. 在“合规性”窗口弹出后，选择“确定” 。

1. 从事例屏幕中选择“导出”选项卡。  双击刚刚创建的导出。

1. 在导出窗格的“导出密钥”下，选择“复制到剪贴板”，然后选择“下载结果”  。
  
1. 系统出现提示时，在浏览器中选择“打开”以安装电子数据展示导出工具，然后选择“安装”。

1. 在出现的对话框中，粘贴之前复制到剪贴板的密钥。  选择一个合适的位置以下载文件。 选择“开始”。 

你已成功导出发现的数据。

### <a name="task-4--perform-search--purge-on-mailboxes"></a>任务 4 - 对邮箱执行搜索和清除操作

一项调查显示，用户收到一些钓鱼邮件，你的任务是删除环境中所有邮箱中的钓鱼邮件。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 https://compliance.microsoft.com。

1. 在 Purview 门户的左侧导航窗格中，选择“内容搜索”。

1. 选择“+ 新建搜索”。

1. 在“名称和说明”窗口中，键入“删除钓鱼邮件”作为“名称”并选择“下一步” 。

1. 在“位置”部分中，选择“Exchange 邮箱”，然后选择“下一步”  。

1. 在“定义搜索条件”页面的“关键字”字段中，键入“From:phishingmail@outlook.com AND subject:"Password changed"”并选择“下一步” 。

1. 在“查看并创建搜索”窗口中，选择“提交” 。 然后选择“完成”。

1. 创建搜索后，需要使用“安全与合规 PowerShell”进行清除。 在开始菜单中，选择以管理员身份运行 Windows PowerShell。

1. 在 PowerShell 窗口中，使用以下 cmdlet，然后以 MOD 管理员身份登录 ：

    ```powershell
    Connect-IPPSSession
    ```

1. 在“PowerShell”窗口中，使用以下命令：

    ```powershell
    New-ComplianceSearchAction -SearchName "Phishing mail removal" -Purge -PurgeType HardDelete
    ```

1. 在 PowerShell 中，键入表示“是”的 Y 并按 Enter 键以确认操作 。

你已经成功创建了新的内容搜索来查找特定电子邮件，然后使用清除操作从用户的邮箱中删除了钓鱼邮件。 只能以“组织管理”角色的成员身份运行清除操作，而“合规性管理员”不属于该角色。

# <a name="proceed-to-lab-3---exercise-6"></a>继续进行实验室 3 - 练习 6
