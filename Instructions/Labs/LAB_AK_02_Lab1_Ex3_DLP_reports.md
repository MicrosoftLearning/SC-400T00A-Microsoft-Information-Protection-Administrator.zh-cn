---
ms.openlocfilehash: d8cf9d01fd8f69396de10007c3da442a391c2f36
ms.sourcegitcommit: 8194831011a18168bab9873a95798c96a13cc448
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2022
ms.locfileid: "145025189"
---
# <a name="lab-2---exercise-3---manage-dlp-reports"></a>实验室 2 - 练习 3 - 管理 DLP 报告

你是 Joni Sherman，Contoso Ltd. 的合规性管理员，负责配置公司的 Microsoft 365 租户以防止数据丢失。 Contoso Ltd. 是美国的一家提供驾驶指导服务的公司，你需要确保敏感客户信息不会泄露到组织外部。 你已获悉新的合规官将帮助你查看 DLP 报告。

### <a name="task-1---grant-access-to-dlp-reports"></a>任务 1 - 授予对 DLP 报告的访问权限

在本练习中，你将授予新的合规部主管对 DLP 报告的访问权限。 作为非技术用户，该合规部主管将只读取报告，而不会更改 DLP 配置。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

2. 在 Microsoft Edge 中，导航到 https://compliance.microsoft.com 并以 MOD 管理员身份 admin@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft 365 合规门户  。  管理员的密码应由实验室托管提供程序提供。

3. 在左侧导航窗格中，选择“权限”，然后在“Microsoft Purview 解决方案”下，选择“角色”  。  标记“安全读取者”角色旁边的复选框。

4. 在“安全读取者”窗格中，在“成员”领域，选择“编辑”。

5. 选择“选择成员”，然后选择“+ 添加” 。

6. 搜索 Megan Bowen 并选中其姓名前面的复选框，然后选择“添加” 。

7. 查看对成员列表所做的更改，然后选择“完成”。

8. 选择“保存”  。 关闭“安全读取者”角色窗格。

你现在已为新的合规部主管授予了对 Microsoft 365 合规门户中的 DLP 报告的访问权限。

### <a name="task-2---test-access-to-dlp-reports"></a>任务 2 - 测试对 DLP 报告的访问权限

在此任务中，你将测试是否正确应用了在任务 1 中授予的对 DLP 报告的访问权限。

1. 使用 lon-cl2\admin 帐户登录到客户端 2 VM (LON-CL2)。

2. 在 Microsoft Edge 中，导航到 https://compliance.microsoft.com 并以 Megan Bowen 的身份 MeganB@WWLxZZZZZZ.onmicrosoft.com （其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录到 Microsoft 365 合规门户  。  Megan 的密码应由实验室托管提供程序提供。

3. 在左侧导航窗格中，选择“报告”并查看对“报告仪表板”的访问权限。

你现在已验证访问权限已配置，新的合规部主管可以在合规中心查看报告。

## <a name="you-have-completed-the-lab-2-proceed-to-lab-3---exercise-1"></a>你已完成本实验室 2。 继续进行实验室 3 - 练习 1。
