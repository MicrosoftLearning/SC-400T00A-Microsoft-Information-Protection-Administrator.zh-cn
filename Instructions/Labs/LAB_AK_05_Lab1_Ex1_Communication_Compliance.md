---
lab:
  title: 练习 1 - 配置通信合规性
  module: Module 5 - Manage insider and privacy risk in Microsoft 365
---
## WWL 租户 - 使用条款

如果在讲师引导式培训过程中向你提供租户，请注意，提供租户旨在支持讲师引导式培训中的动手实验室。

租户不应共享或用于动手实验室以外的用途。 本课程使用的租户为试用租户，课程结束后无法使用或访问，不符合扩展条件。

租户不得转换为付费订阅。 在本课程中获得的租户仍然是 Microsoft Corporation 的财产，我们保留随时获取访问权限和收回的权利。

# 实验室 5 - 练习 1 - 配置通信合规性

作为组织的合规性管理员，你负责配置 Microsoft 通信合规性，以帮助确保组织满足其合规性要求。 Microsoft 通信合规性允许你监视各种渠道（例如电子邮件、Microsoft Teams 以及其他聊天和协作工具）中的通信活动，以帮助检测和缓和违反策略的行为和其他不当行为。

## 任务 1：分配合规性管理员角色

在本练习中，你将向 Joni 分配通信合规性角色，以授予在 Microsoft Purview 门户中执行通信合规性任务的权限。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在 Microsoft Edge 中，导航到 `https://compliance.microsoft.com` ，以 MOD 管理员身份 admin@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户 。 管理员的密码应由实验室托管提供程序提供。

1. 导航到“角色和范围”，然后从下拉菜单中选择“权限” 。

1. 在“权限”页上，选择“Microsoft Purview 解决方案”下的“角色”  。

1. 在“Microsoft Purview 解决方案的角色组”页上，选择“通信合规性” 。

1. 从右侧的“通信合规性”弹出页中选择“编辑” 。

1. 在“编辑角色组的成员”页上，选择“+ 选择用户” 。

1. 在“选择用户”页上，选中 Joni Sherman 旁边的复选框，然后选择“选择” 。

1. 在“编辑角色组的成员”页上，选择“下一步” 。

1. 在“查看角色组并完成”页上，选择“保存” 。

1. 在“已成功更新角色组”页上，选择“完成” 。

1. 退出登录“MOD 管理员”帐户并关闭所有浏览器窗口。

你已成功将通信合规性角色分配给 Joni Sherman，授予她在 Microsoft Purview 门户中执行通信合规性任务的权限。

## 任务 2 - 配置自定义策略

在本练习中，你将在 Microsoft 通信合规性中配置自定义策略，以监视通信中的敏感财务信息。 按照以下步骤配置策略：

1. 在 Microsoft Edge 中，导航到 `https://compliance.microsoft.com` 并以 JoniS@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户 。

1. 在左侧导航窗格中选择“通信合规性”。

1. 关闭出现的任何提示菜单。

1. 在“通信合规性”页上的顶部导航栏中，选择“策略” 。

1. 在“策略”选项卡中选择“+ 创建策略”，然后从下拉列表中选择“自定义策略”  。

1. 在“命名和描述策略”页上输入：

    - 名称：检测财务机密
    - 说明：检测共享财务机密的情况

1. 选择**下一步**。

1. 在“选择用户和审阅者”页上的“选择用户和组”下，将“全部用户”保留为选中状态  。

1. 在“审阅者”字段中选择“Joni Sherman”和“MOD 管理员”，然后选择“下一步”   。

1. 在“选择要检测通信的位置”页上选择“Exchange”，然后选择“下一步”  。

1. 在“选择条件并查看百分比”页上的“通信定向”下，将默认值保留为选中状态 。

1. 在“条件”下选择“+ 添加条件”，然后选择“消息包含任何这些字词”  。

1. 在“消息包含任何这些字词”下的字段中，输入“机密”。

    >注意：若要根据邮件中的特定字词或短语应用策略，请输入这些字词或短语并用逗号分隔。 用逗号分隔的项之间没有空格。 对包含两个或两个以上字词的短语使用引号。 独立应用每个字词或短语（只需要一个字词即可触发策略）。

1. 在“查看百分比”下，将滑块调至“100%”，然后选择“下一步”  。

1. 在“查看并完成”页上，选择“创建策略” 。

1. 在“已创建策略”页上，选择“完成” 。

1. 已创建通信合规性策略。

    >注意：在测试策略之前，请确保为策略提供激活时间。 策略可能需要大约 24 小时才能完全处理电子邮件消息。 策略可能需要大约 48 小时才能完全处理 Microsoft Teams、Yammer 和第三方平台中的通信。

## 任务 3 - 测试自定义策略

在此任务中，你将验证配置的自定义策略的有效性。 通过测试不同的场景，你将评估策略识别和标记敏感财务信息的能力。 这些测试提供对策略行为的有价值的实际见解。

>注意：在测试策略之前，请确保为策略提供激活时间。 策略可能需要大约 24 小时才能完全处理电子邮件消息。 策略可能需要大约 48 小时才能完全处理 Microsoft Teams、Yammer 和第三方平台中的通信。

1. 退出登录 Joni 的帐户并关闭所有浏览器窗口。

1. 在 Microsoft Edge 中，导航到 `https://outlook.office.com` 并以 LynneR@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录 Outlook 网页版。

1. 从 Outlook 网页版的左上角选择“新建邮件”。

1. 在“收件人”行中，输入不在租户域中的个人或其他第三方电子邮件地址。 在主题行中输入“新机密邮件”，并在正文中输入“我的超级机密邮件。” 。

1. 选择“发送”发送该消息。

1. 发送邮件后，再次从 Outlook 网页版的左上角选择“新建邮件”。

1. 在“收件人”行中输入“Megan Bowen”，并选择建议的电子邮件地址 。 在主题行中输入“大秘密！”， 在电子邮件正文中输入“我们将为 Debra 举办一场惊喜的婴儿派对！ 保密！”。

1. 选择“发送”

1. 在“收件人”行中输入“Joni Sherman”，并选择建议的电子邮件地址 。 在主题行中输入“惊喜派对！”， 在电子邮件正文中输入“Joni！我们正在计划办公室里的几个大秘密！别忘了本月 Debra 的婴儿派对 和 Megan 的惊喜生日派对！”。

1. 选择“发送”

1. Lynne 想发送最后一封电子邮件。 在“收件人”行中输入“Debra Berger”，并选择建议的电子邮件地址 。 在电子邮件正文中输入“Debra！我刚刚听说了一个关于 Northwind 收购的巨大财务秘密！ 让我们在午餐时聚在一起讨论。”。

1. 选择“发送”

1. 退出登录 Lynne 的帐户并关闭所有浏览器窗口。

你已成功测试自定义策略，以验证其在识别和标记敏感财务信息方面的有效性。

## 任务 4 - 管理通信合规性策略

在此任务中，你将在 Microsoft Purview 门户中管理通信合规性策略。你将查看“检测财务机密”策略的待处理项目并对其采取操作，以确保策略有效识别和处理任何潜在的合规性问题。

1. 在 Microsoft Edge 中，导航到 `https://compliance.microsoft.com` 并以 JoniS@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户 。 Joni 的密码应由实验室托管提供程序提供。

1. 从左侧导航栏导航到“通信合规性”。

1. 选择“策略”。

1. 查看“检测财务机密”策略的“待审阅的项目”。

    >注意：请注意，如果“待审阅的项目”计数为 0，则策略可能需要额外的时间才能完全处理测试 。 请记住，策略可能需要大约 24 小时才能完全处理电子邮件消息。

1. 选择“检测财务机密”策略以查看待处理的项目。 三封测试电子邮件将位于此视图中。

1. 选择主题为“大秘密！”的项目。

1. 由于此邮件是简单的参与方通知，因此请选择“解决”。 在“解决”窗格中的“注释”字段中输入“所需的策略修改”，然后选择“解决”   。

1. 现在，“检测财务机密”策略将有 2 个待处理的项目。 选择主题为“新机密邮件”的项目。

1. 在右侧显示的邮件下，选择“标记为”。

1. 在“标记项”窗格中，选择“有疑问” 。 在“注释”字段中，输入“可疑机密项”，然后选择“保存”  。

1. 在“检测财务机密”策略中，选择主题为“Northwind 收购”的项目。

1. 选择“Northwind 收购”项目下的“通知”。

1. 在“发送通知”窗格中，选择“选择通知模板”的下拉菜单 。 选择“+创建新通知”以创建新的通知模板。

1. 在“创建通知模板”窗格中的“模板名称”字段中输入“违规邮件”  。

1. 在“发件人:”字段中输入“Joni Sherman”并选择建议的用户 。

1. 在“主题”字段中，输入“检测到违规邮件” 。 在“邮件正文”中，输入“这是为了通知检测到违规邮件并将呈报该邮件。”

1. 选择“创建”。

1. 在“已创建通知模板‘违规邮件’”窗格中，选择“关闭” 。

1. 在“发送通知”窗格中的“选择通知模板”下，选择新创建的“违规邮件”通知模板，然后选择“保存”   。

1. 在“通知已发送”窗格中，选择“关闭” 。

1. 在“检测财务机密”策略中，选择主题为“Northwind 收购”的项目。

1. 选择“Northwind 收购”项目下的“呈报”。

1. 在“呈报此项目的修正”中，选择“MOD 管理员”作为其他审阅者 。 在“呈报原因”字段中，输入“检测到数据泄漏计划。” ， 然后选择“呈报”。

1. 在“呈报已发送”窗格中，选择“关闭” 。

1. 返回到“Northwind 收购”邮件消息的视图，选择“标记为”。 在“标记项”窗格中，选择“不合规” 。 在“注释”字段中输入“不合规邮件”，然后选择“保存”  。

你已通过查看和解决待处理的项目成功管理了通信合规性策略。

## 任务 5 - 修改通信合规性策略

在此任务中，你将修改通信合规性策略。 你将微调策略设置并添加新的条件来检测敏感信息，以确保策略符合 Contoso 有限公司的合规性需求。

1. 你仍应使用 Joni 的帐户登录 Microsoft Purview 合规门户中的“通信合规性”。

1. 从顶部导航窗格中选择“策略”。

1. 选中“检测财务机密”策略旁边的复选框。

1. 从顶部导航窗格中选择“编辑”。

1. 在“命名并描述策略”页上，选择“下一步” 。

1. 在“选择用户和审阅者”页上，选择“下一步” 。

1. 在“选择要检测通信的位置”页上，选择“下一步” 。

1. 在“**选择条件和查看百分比**”页面上，选择“**+ 添加条件**”，然后选择“**内容包含以下任一敏感信息类型**”。

1. 在“内容包含以下任一敏感信息类型”下，选择“添加”，然后选择“敏感信息类型”  。

1. 在“敏感信息类型”窗格中搜索“信用卡号”，然后选中此敏感信息类型旁边的复选框 。

1. 选择“添加”将此敏感信息类型添加到此条件，然后选择“下一步” 。

1. 在“查看并完成”页上，选择“保存” 。

1. 在“策略已更新”页上，选择“完成” 。

你已成功修改通信合规性策略，使其包含用于检测敏感信息类型的新条件。
