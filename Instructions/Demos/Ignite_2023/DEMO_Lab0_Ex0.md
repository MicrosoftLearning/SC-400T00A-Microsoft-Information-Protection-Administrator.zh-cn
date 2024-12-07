---
lab:
  title: 练习 1 - 管理合规性角色
  module: Module 1 - Implement Information Protection
---
## WWL 租户 - 使用条款

如果在讲师引导式培训过程中向你提供租户，请注意，提供租户旨在支持讲师引导式培训中的动手实验室。

租户不应共享或用于动手实验室以外的用途。 本课程使用的租户为试用租户，课程结束后无法使用或访问，不符合扩展条件。

租户不得转换为付费订阅。 在本课程中获得的租户仍然是 Microsoft Corporation 的财产，我们保留随时获取访问权限和收回的权利。

# 练习 0 - 设置实验室环境

在本实验室中，你将为管理任务配置和准备环境。

## 任务 - 设置用于实验室练习的用户密码

在此任务中，你将为实验室所需的用户帐户设置密码。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。 密码应由实验室托管提供程序提供。

1. 在 Microsoft Edge**** 中，导航到 **https://admin.microsoft.com**，并使用“MOD 管理员”帐户**** admin@WWLxZZZZZZ.onmicrosoft.com 登录到 Microsoft Purview 门户。

1. 在左侧导航窗格中，展开“**用户**”，然后选择“**活动用户**”。

1. 选中“显示名称”**** 旁边的复选框以选择所有用户。

1. 取消选中“MOD 管理员”**** 和“Microsoft 服务帐户”**** 旁边的复选框。

    >[!alert] 请勿更改“MOD 管理员”**** 或“Microsoft 服务帐户”**** 密码。 这将对实验室体验产生负面影响。
    ><p>
    > ![显示“Microsoft 服务帐户”和“MOD 管理员”被取消选中的屏幕截图。](../Media/deselectserviceaccounts.png)

1. 从中间的操作功能区中选择“重置密码”****，以打开右侧的“重置密码”**** 浮出控件页。

1. 取消选中“自动创建密码”**** 和“要求此用户在首次登录时更改其密码”****。 不应选择“重置密码”页面上的任何选项。

1. 确保在“**重置密码**”浮出控件页上未选中任何复选框。

1. 在“密码”**** 字段中，输入实验室托管环境中的“资源”**** 选项卡中的“用户密码”****。 还可以将密码重置为在此实验室操作过程中记住的密码。

1. 选择“重置密码”**** 按钮以重置用户的密码。

1. 在“密码已重置”**** 页上，选择“关闭”**** 按钮以返回到“活动用户”**** 页面。