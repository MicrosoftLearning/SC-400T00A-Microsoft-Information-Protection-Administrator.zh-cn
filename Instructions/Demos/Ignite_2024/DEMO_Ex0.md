## WWL 租户 - 使用条款

如果在讲师引导式培训过程中向你提供租户，请注意，提供租户旨在支持讲师引导式培训中的动手实验室。

租户不应共享或用于动手实验室以外的用途。 本课程使用的租户为试用租户，课程结束后无法使用或访问，不符合扩展条件。

租户不得转换为付费订阅。 在本课程中获得的租户仍然是 Microsoft Corporation 的财产，我们保留随时获取访问权限和收回的权利。

# 实验室设置：准备合规性管理的环境

在此实验室中，你将配置和准备合规性管理的环境。 你将激活关键功能、设置管理权限，并确保正确配置核心元素。

**任务**：

1. 在 Microsoft Purview 门户中启用审核
1. 设置用于实验室练习的用户密码
1. 分配合规性角色
1. 浏览 Microsoft Purview 门户

## 任务 1 - 在 Microsoft Purview 门户中启用审核

在此任务中，你将启用审核日志记录来跟踪 Microsoft 365 服务中的活动。

1. 使用**管理员**帐户登录到客户端 1 VM (SC-400-CL1)。 密码应由实验室托管提供程序提供。

1. 打开 Microsoft Edge 并导航到位于 `https://purview.microsoft.com` 的 Microsoft Purview 门户。

1. 以 MOD 管理员 `admin@WWLxZZZZZZ.onmicrosoft.com`（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）的身份登录 Microsoft Purview 门户。 可以在实验室托管窗口的“**资源**”选项卡中找到管理员的密码。

1. 在“**欢迎使用新的 Microsoft Purview 门户!**” 窗口，选中复选框以同意条款和条件，然后选择“**开始**”访问门户。

    ![显示“欢迎使用新的 Microsoft Purview 门户屏幕”的屏幕截图。](../Media/new-purview-portal-get-started.png)

1. 从左侧边栏中选择“**解决方案**”，然后选择“**审核**”。

1. 在“**搜索**”页面，选择“**开始录制用户和管理活动**”栏以启用审核日志记录。

    ![显示“开始录制用户和管理员活动”按钮的屏幕截图。](../Media/enable-audit-button.png)

1. 选择此选项后，蓝色栏将消失。

已在 Microsoft Purview 中成功启用审核。

## 任务 2 - 设置用于实验室练习的用户密码

在此任务中，你将为实验室中使用的用户帐户设置密码。

1. 在 Microsoft Edge 中，导航到 **Microsoft 365 管理中心**，网址为 **`https://admin.microsoft.com`**。

1. 在左侧导航窗格中，展开“**用户**”，然后选择“**活动用户**”。

1. 找到 **Joni Sherman** 的帐户，然后选择密钥图标以重置密码。

   在下一练习中，你将使用 Joni 的帐户。

   ![显示需要重置的用户帐户的屏幕截图。](../Media/reset-password-button-joni.png)

1. 在右侧的“**重置密码**”浮出控件页中，确保所有选项均未选中，然后在“**密码**”字段中输入要记住的密码。

1. 选择页面底部的“**重置密码**”，然后在确认页上选择“**关闭**”。

已成功重置 Joni 用于实验室练习的密码。

## 任务 3 – 分配合规性管理员角色

在此任务中，你将向 Joni Sherman 分配**合规性管理员**角色。

1. 在 Microsoft 365 管理中心，选择 Joni 的帐户。

1. 在 **Joni Sherman** 的属性浮出控件菜单中，选择“**管理角色**”。

    ![显示“欢迎使用新的 Microsoft Purview 门户屏幕”的屏幕截图。](../Media/joni-manage-roles.png)

1. 在“**管理管理员角色**”浮出控件页面上，选择“**管理中心访问权限**”，然后向下滚动以选择“**按类别显示所有内容**”。

1. 在“**安全性和合规性**”下，选择“**合规性管理员**”。

1. 选择页面底部的“保存更改”。

1. 选择右上角的“**MA**”图标，然后选择“**注销**”，以注销 MOD 管理员帐户。

   ![显示退出登录 MOD 管理员帐户的导航路径的屏幕截图。](../Media/sign-out.png)

你已成功向 Joni 分配了合规性管理员角色，需要先完成此操作才能进行接下来的练习。

## 任务 4 - 浏览 Microsoft Purview 门户

在此任务中，你将切换到 Joni Sherman 帐户并浏览 Microsoft Purview 门户。

1. 在 **Microsoft Edge** 中，导航到 Microsoft Purview 合规性门户，网址为 **`https://purview.microsoft.com`**。

1. 在出现“**选择帐户**”窗口时，选择“**使用另一个帐户**”。

1. 以 `JoniS@WWLxZZZZZZ.onmicrosoft.com` 身份登录（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）。 Joni 的密码是在上一练习中设置的。

1. 浏览 Microsoft Purview 门户，熟悉其界面。

你已成功切换到 Joni Sherman 的帐户，现在可以继续使用实验室。
