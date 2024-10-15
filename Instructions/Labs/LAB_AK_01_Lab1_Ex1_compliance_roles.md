---
lab:
  title: 练习 1 - 管理合规性角色
  module: Module 1 - Implement Information Protection
---
## WWL 租户 - 使用条款

如果在讲师引导式培训过程中向你提供租户，请注意，提供租户旨在支持讲师引导式培训中的动手实验室。

租户不应共享或用于动手实验室以外的用途。 本课程使用的租户为试用租户，课程结束后无法使用或访问，不符合扩展条件。

租户不得转换为付费订阅。 在本课程中获得的租户仍然是 Microsoft Corporation 的财产，我们保留随时获取访问权限和收回的权利。

# 实验室 1 - 练习 1 - 管理合规性角色

作为近期受雇于 Contoso Ltd.的合规性管理员，你 (Joni Sherman) 需要确保新的 Microsoft 365 租户符合各种法律和法规标准。 Contoso Ltd. 正在发展壮大，你的角色对于保持不同区域的合规性至关重要。

**任务**：

1. 分配合规性角色
1. 浏览 Microsoft Purview 门户

## 任务 1 - 分配合规性角色

在此任务中，你将向 Joni Sherman 分配合规性管理员角色。

1. 使用 SC-400-CL1\admin**** 帐户登录客户端 1 VM (SC-400-CL1)。 密码应由实验室托管提供程序提供。

1. 打开 Microsoft Edge**** 并导航到 Microsoft Purview 门户 `https://admin.microsoft.com`，然后以 MOD 管理员****`admin@WWLxZZZZZZ.onmicrosoft.com` 身份登录（其中 ZZZZZZ 是实验室托管提供商提供的唯一租户 ID）。 管理员的密码应由实验室托管提供程序提供。

1. 在左侧边栏中，展开“**用户**”，然后选择“**活动用户**”。

1. 在“**活动用户**”页上，搜索 `Joni`，然后选择“**Joni Sherman**”。

1. Joni 帐户的属性显示在右侧浮出控件面板中。 在浮出控件面板中选择“**管理角色**”。

1. 在“**管理管理员角色**”面板上，选择“**管理中心访问**”选项，然后向下滚动以展开“**按类别显示所有内容**”。

1. 在“**安全性与合规性**”类别下，选中“**合规性管理员**”的复选框，然后选择浮出控件面板底部的“**保存更改**”。

1. 应收到一条消息，指出**管理员角色已更新**。

1. 在“**管理管理员角色**”页上，选择浮出控件面板右上角的 **X** 以关闭面板。

1. 选择右上角的“**MA**”图标，然后选择“**注销**”，以注销 MOD 管理员帐户。

   ![显示退出登录 MOD 管理员帐户的导航路径的屏幕截图。](../Media/sign-out.png)

你已成功向 Joni Sherman 分配合规性管理员角色，需要先完成此操作才能执行本实验室的不同练习。

## 任务 2 - 浏览 Microsoft Purview 门户

在此任务中，你将以 Joni Sherman 身份登录，以浏览 Microsoft Purview 门户。

1. 仍应使用 SC-400-CL1\admin**** 帐户登录到客户端 1 VM (SC-400-CL1)。

1. 在“Microsoft Edge”中，导航到 `https://purview.microsoft.com`。

1. 显示“选择帐户”窗口时，请选择“使用其他帐户” 。

1. 显示“登录”窗口时，以 `JoniS@WWLxZZZZZZ.onmicrosoft.com`（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录。 Joni 的密码是在上一练习中设置的。

1. 熟悉新的 Microsoft Purview 门户。 完成后，让浏览器窗口保持打开状态。

你已成功切换到 Joni Sherman 的帐户，现在可以开始使用实验室。
