---
lab:
  title: 练习 3 - 配置基于服务的保留
  module: Module 3 - Implement Data Lifecycle and Records Management
ms.openlocfilehash: b531417b4335973f9c1e3ac0950f000fa1719eab
ms.sourcegitcommit: 53488624251b6cf8f79f2d1ff561e3f334764821
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2022
ms.locfileid: "147694942"
---
# <a name="lab-3---exercise-3---configure-service-based-retention"></a>实验室 3 - 练习 3 - 配置基于服务的保留

你将扮演 Contoso Ltd 的合规管理员 Joni Sherman。法律部门要求你协助他们阻止心怀不满的员工删除公司数据。

### <a name="task-1--configure-mailbox-holds"></a>任务 1 - 配置邮箱保留

在此任务中，你将激活邮箱保留，以防止删除员工邮箱中的任何内容。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 虚拟机 (LON-CL1)。

1. 在“Microsoft Edge”中，导航到 https://outlook.office.com/ecp 并以 Joni Sherman 的身份登录到 Exchange 管理中心  。 以 JoniS@WWLxZZZZZZ.onmicrosoft.com 身份登录（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）。  Joni 的密码应由实验室托管提供程序提供。

1. 在“保持登录?”对话框上，选中“不再显示此内容”复选框，然后选择“否”  。

1. 如果显示欢迎使用屏幕，请关闭它。

1. 在“Exchange 管理中心”的左侧导航窗格中，选择“收件人”，然后选择“邮箱”  。

1. 选择 Alex Wilber 的邮箱，然后选择“铅笔”图标以编辑该邮箱。

1. 在“编辑用户邮箱”窗口中，选择“邮箱功能” 。

1. 向下滚动到“诉讼保留: 已禁用”，并选择“启用” 。

1. 在“诉讼保留”页面上，填写以下信息：

    - 诉讼保留期限(天数)：90
    - **注意**：你的邮箱的诉讼保留期限已延期至下一个 90 天。 你将无法删除任何消息。

1. 选择“保存”两次。 **注意：** 出现一条警告消息“保留设置可能需要 240 分钟才能生效”，单击该消息上的“确定”。

你已成功激活环境中邮箱的邮箱保留，并阻止了所有具有访问权限的人永久删除邮箱中的任何内容。 应用保留最多需要 4 小时。  可以立即继续执行下一个任务。

### <a name="task-2--recover-sharepoint-documents"></a>任务 2 - 恢复 SharePoint 文档

在此任务中，你将删除文档并还原已删除的文档，以确保可以还原员工在得知针对其邮箱应用了诉讼保留后可能会删除的文档。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在 Microsoft Edge 中，导航到 https://www.office.com 并以 Joni Sherman 的身份登录到 Microsoft 365  。

1. 如果显示欢迎使用屏幕，请关闭它。 如果显示 Office 365 应用通知，同样请关闭它。

1. 在 Microsoft Office 365 登陆页面上，选择左上角的“应用启动器”图标（该图标带有九个点），然后从子菜单中选择“SharePoint”。

1. 如果出现“欢迎来到 SharePoint 起始页”，请关闭它。

1. 在 SharePoint 登陆页面上，选择“Benefits @ Contoso”SharePoint 网站。

1. 在左侧导航窗格中，选择“文档”。

1. 通过选中 Vacation Policies.pptx 文件前面的复选框来将其突出显示。

1. 在操作栏中选择“删除”。

1. 在“是否删除?”对话框中，选择“删除” 。

1. 在左侧导航窗格中，选择“回收站”，然后通过选中 Vacation Policies.pptx 文件前面的复选框来将其突出显示 。

1. 在顶部操作栏中，选择“还原”。

1. 在左侧导航窗格中，选择“文档”并查看文件是否已还原。

你已经成功从 SharePoint 网站恢复了已删除的文档。

# <a name="proceed-to-lab-3---exercise-4"></a>继续进行实验室 3 - 练习 4
