---
lab:
  title: 设置演示：为管理准备环境
  module: Module 0 - Lab Setup
---

## WWL 租户 - 使用条款

如果在讲师引导式培训过程中向你提供租户，请注意，提供租户旨在支持讲师引导式培训中的动手实验室。

租户不应共享或用于动手实验室以外的用途。 本课程使用的租户为试用租户，课程结束后无法使用或访问，不符合扩展条件。

租户不得转换为付费订阅。 在本课程中获得的租户仍然是 Microsoft Corporation 的财产，我们保留随时获取访问权限和收回的权利。

# 实验室设置：为管理准备环境

在本实验室中，你将为管理任务配置和准备环境。 按照提供的步骤，你将确保提前启用基本功能和设置，从而在即将进行的实验室活动中获得更轻松的学习体验。 此准备工作将包括激活必要的功能、设置管理权限，以及确保正确配置关键元素。

## 任务 - 在 Microsoft Purview 门户中启用审核

在此任务中，你将在 Microsoft Purview 合规门户中启用“审核”。 此跟踪功能通过监视门户活动来确保可见性和实施问责。

1. 你仍应使用 **lon-cl1\admin** 帐户登录到客户端 1 VM (LON-CL1)，并使用 MOD 管理员帐户登录到 Microsoft 365。

1. 在“Microsoft Edge”中，导航到 https://compliance.microsoft.com。

1. 在左侧导航窗格中选择“**审核**”。

1. 在“审核”页上。 选择“开始记录用户和管理员活动”以激活审核日志记录。

## 任务 - 启用对敏感度标签的支持

在本任务中，你将安装 MSOnline 模块和 SharePoint Online PowerShell 模块，并在租户上启用对敏感度标签的支持。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 右键选择开始菜单，然后选择 Windows PowerShell 并以管理员身份运行，以打开权限提升的 PowerShell 窗口。

1. 输入表示“是”的 Y 并按 Enter，以确认“用户帐户控制”窗口 。

1. 输入以下 cmdlet，以安装最新版 MS Online PowerShell 模块：

   ```powershell
   Install-Module -Name MSOnline
   ```

1. 输入表示“是”的 Y 并按 Enter 键以确认“NuGet 安全性”对话框以及“不受信任的存储库安全”对话框。  这可能需要一段时间才能处理完成。

1. 输入以下 cmdlet，以安装最新版 SharePoint Online PowerShell 模块：

    ```powershell
    Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

1. 输入表示“是”的 Y 并按 Enter 键，以确认“不受信任的存储库安全”对话框。

1. 输入以下 cmdlet，以连接到 MS Online 服务：

    ```powershell
    Connect-MsolService
    ```

1. 在“**登录到帐户**”窗体中，以 **MOD 管理员**admin@WWLxZZZZZZ.onmicrosoft.com的身份（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录。  Joni 的密码应由实验室托管提供程序提供。

1. 登录后，选择 PowerShell 窗口。

1. 输入以下 cmdlet，以获取域：

    ```powershell
    $domain = get-msoldomain
    ```

1. 输入以下 cmdlet，以创建 SharePoint 管理员 URL：

    ```powershell
    $adminurl = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"
    ```

1. 输入以下 cmdlet，以登录到 SharePoint Online 管理中心：

    ```powershell
    Connect-SPOService -url $adminurl
    ```

1. 在“登录到帐户”窗体中，以 MOD 管理员身份登录。 admin@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）。  管理员的密码应由实验室托管提供程序提供。

1. 登录后，选择 PowerShell 窗口。

1. 输入以下 cmdlet，以启用对敏感度标签的支持：

    ```powershell
    Set-SPOTenant -EnableAIPIntegration $true
    ```

1. 输入表示“是”的 Y 并按 Enter 键，以确认更改。

1. 关闭 PowerShell 窗口。

你通过 Teams 和 SharePoint 网站成功启用了对敏感度标签的支持。