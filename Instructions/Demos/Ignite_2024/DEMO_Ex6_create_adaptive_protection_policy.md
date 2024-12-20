# 练习 6 - 创建自适应保护策略

Contoso 已实现 DLP 策略，以防止将数据复制到生成式 AI 平台。 但是，该公司已确定需要进行更多的动态控制，确保对参与风险行为的用户采取更严格的措施。 为了解决此问题，Contoso 将使用 Microsoft Purviews 自适应保护根据用户的内部风险级别自动调整对 DLP 策略的执行，确保风险较高的用户面临更多限制，同时对其他人保持灵活性。

**任务**：

1. 在内部风险管理中启用自适应保护

## 任务 1 - 在内部风险管理中启用自适应保护

在此任务中，将通过设置内部风险级别并在内部风险管理中启用自适应保护来配置自适应保护。 这可确保 DLP 策略根据用户行为和风险级别进行动态调整。

1. 在 Microsoft Purview 门户中，选择“**解决方案**” > “**内部风险管理**”。

1. 在“**内部风险管理**”页上，从左侧边栏选择“**自适应保护**”。

1. 在“**自适应保护**”页上，选择左侧的“**内部风险级别**”选项卡。

1. 在“**内部风险级别**”页的“**内部风险策略**”下，选择在上一任务中创建的“**敏感数据保护**”策略。

1. 对“**内部风险级别的条件**”使用内置条件，然后在页面底部选择“**保存**”。

1. 选择“**自适应保护设置**”选项卡，并将“**自适应保护**”开关切换为“**打开**”，然后在页面底部选择“**保存**”。

你已成功启用内部风险管理中的自适应保护功能。
