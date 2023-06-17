---
lab:
  title: 练习 3 - 管理 DLP 报告
  module: Module 2 - Implement Data Loss Prevention
---

# 实验室 2 - 练习 3 - 管理 DLP 报告

你是 Joni Sherman，Contoso Ltd. 的合规性管理员，负责配置公司的 Microsoft 365 租户以防止数据丢失。 Contoso Ltd. 是美国的一家提供驾驶指导服务的公司，你需要确保敏感客户信息不会泄露到组织外部。 你已获悉新的合规官将帮助你查看 DLP 报告。

## 任务 1 - 授予对 DLP 报告的访问权限

在本练习中，你将授予新的合规官 Megan Bowen 对 DLP 报告的访问权限。 作为非技术用户，该合规部主管将只读取报告，而不会更改 DLP 配置。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在 Microsoft Edge 中，导航到 https://compliance.microsoft.com 并以 MOD 管理员的身份 admin@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户  。  管理员的密码应由实验室托管提供程序提供。

1. 在左侧导航窗格中，选择“权限”，然后在“Microsoft Purview 解决方案”下，选择“角色”  。   选择“信息保护分析师”角色的字段。

1. 在“信息保护分析师”窗格的“成员”区域中选择“编辑” 。

1. 选择“选择成员”，然后选择“+ 添加” 。

1. 搜索 Megan Bowen 并选中其姓名前面的复选框，然后选择“添加” 。

1. 查看对成员列表所做的更改，然后选择“完成”。

1. 选择“保存”  。 关闭“信息保护分析师”角色窗格。

你现在已为新的合规部主管授予了对 Microsoft 365 合规门户中的 DLP 报告的访问权限。

## 任务 2 - 测试对 DLP 报告的访问权限

在此任务中，你将测试是否正确应用了在任务 1 中授予的对 DLP 报告的访问权限。

1. 使用 lon-cl2\admin 帐户登录到客户端 2 VM (LON-CL2)。

1. 在 Microsoft Edge 中，导航到 https://compliance.microsoft.com 并以 Megan Bowen 的身份 MeganB@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft Purview 门户  。  Megan 的密码应由实验室托管提供程序提供。

1. 在左侧导航窗格中，选择“数据丢失防护”下拉菜单，然后选择“活动资源管理器” 。

1. 在“活动资源管理器”页上，选择“内置筛选器”下拉菜单 。 

1. 浏览“检测到活动的 DLP 策略”筛选器和“检测到活动的 DLP 策略规则”筛选器 。

1. 使客户端保持打开状态，用于完成最后一个练习。

你现在验证了已配置访问权限，新的合规官可以在 Purview 门户中查看报告。
