---
lab:
  title: 练习 4：配置基于服务的保留
  module: Module 3 - Implement Data Lifecycle and Records Management
---

# 实验室 3 - 练习 4 - 配置基于服务的保留

Contoso Ltd. 最近遇到了一些内部挑战，一位可能心怀不满的员工可能会尝试删除至关重要的公司数据。 作为 Contoso Ltd. 的合规性管理员 Joni Sherman，你负责保护敏感信息并确保不会丢失任何重要记录。 法律部门已确定数据可能面临风险的特定领域，你的职责是实施防止数据丢失的措施，尤其要重点关注的是电子邮件通信和 SharePoint 文档。

**任务**：

1. 配置邮箱保留
1. 恢复 SharePoint 文档

## 任务 1 - 配置邮箱保留

为了防止数据丢失，你将对 Alex Wilber 的帐户实施邮箱保留。

1. 使用 **SC-400-cl1\admin** 帐户登录到客户端 1 虚拟机 (SC-400-CL1)。

1. 在“Microsoft Edge”中，导航到 `https://admin.exchange.microsoft.com` 并以 Joni Sherman 的身份登录到 Exchange 管理中心  。 以 `JoniS@WWLxZZZZZZ.onmicrosoft.com` 身份登录（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）。

1. 关闭所有提示窗口（如果出现）。

1. 在 Exchange 管理中心的左侧边栏中，展开“**收件人**”，然后选择“**邮箱**”。

1. 从邮箱列表中选择“**Alex Wilber**”，右侧将出现一个浮出面板，其中显示了 Alex 的邮箱设置。

1. 在 **Alex Wilber** 的浮出控件页上，选择“**其他**”选项卡。

1. 在“诉讼保留”下，选择“管理诉讼保留”********。

1. 在“**管理诉讼保留**”页上，将“**诉讼保留**”设置从“**关闭**”切换为“**开启**”以显示诉讼保留设置。

1. 使用以下值为 Alex 的邮箱配置诉讼保留：

    - **保留持续时间(天)**：`90`
    - **备注(对用户可见)**： `Your mailbox has been put on hold for the next 90 days. You will not be able to delete any messages.`

1. 在面板底部，选择**保存**。 在面板中，你将收到一条消息，指出**诉讼保留已更新**。

你已成功激活环境中邮箱的邮箱保留，并阻止了所有具有访问权限的人永久删除邮箱中的任何内容。 应用保留最多需要 60 分钟。

## 任务 2 - 恢复 SharePoint 文档

在此任务中，你将删除文档并还原已删除的文档，以确保可以还原员工在得知针对其邮箱应用了诉讼保留后可能会删除的文档。

1. 使用 **SC-400-cl1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)。

1. 在 Microsoft Edge 中，导航到 `https://www.office.com` 并以 Joni Sherman 的身份登录到 Microsoft 365  。

1. 在 Microsoft Office 365 登陆页面上，选择左上角的 meatball 菜单，然后从子菜单中选择“**SharePoint**”。

   ![显示省略号位置的屏幕截图，以显示操作菜单。](../Media/show-more-actions-sharepoint.png)

1. 在 SharePoint 登陆页面上，搜索“`Benefits`”，然后从搜索结果中选择“**Benefits @ Contoso**”。

1. 在左侧边栏中，选择“**文档**”。

1. 在“文档”页上，选中“Vacation Policies.pptx”左侧的复选框，然后在操作栏中选择“删除”************。

1. 在“**删除?**”对话框中，选择“**删除**”。

1. 在左侧边栏中选择“**回收站**”。

1. 在“**回收站**”页上，右键单击“**Vacation Policies.pptx**”，然后选择“**还原**”。

1. 在左侧边栏中，选择“**文档**”并注意文件已还原。

你已经成功从 SharePoint 网站恢复了已删除的文档。
