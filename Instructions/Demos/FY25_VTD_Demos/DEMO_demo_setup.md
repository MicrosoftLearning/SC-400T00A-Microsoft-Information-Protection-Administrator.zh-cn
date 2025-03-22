---
lab:
  title: 演示设置
  module: FY25 VTD Demo - Setup
---

# 演示实验室 0 - VTD 演示设置

本实验室是为 FY25 VTD 设置演示环境。 这些实验室的主要任务是：

- 在 Microsoft Purview 中为内部风险管理启用审核
- 载入终结点 DLP、内部风险管理、自适应保护和 AI 中心的设备。

请确保在运行 VTD 演示之前提前 48 小时执行这些任务，以确保环境已准备好进行演示。

如果你在使用这些实验室时遇到任何问题，请通过 richelle.swinton@microsoft.com 与我联系以解决这些问题。

## 访问 Skillable 环境

1. 访问 SC-400 实验室配置文件 - [https://gtllabs.learnondemand.net/Lab/68392](https://gtllabs.learnondemand.net/Lab/68392)。

1. 使用适当的凭据登录。

1. 选择“**启动**”按钮，启动实验室。

1. 此时会打开一个新窗口来加载实验室环境。 等待实验室配置文件载入。 此过程需要几分钟。

1. 要轻松显示此实验室以进行演示，最简单的方法是使用“**资源**”选项卡中的凭据，并在 Microsoft Edge 的隐身窗口中运行实验室。

    ![显示“欢迎使用新的 Microsoft Purview 门户屏幕”的屏幕截图。](/Instructions/Media/skillable-credentials.png)

1. 你需要在 Skillable 实验室 VM 中运行实验室设置以载入设备。

## 任务 1 - 设置用户密码演示演练

在此任务中，你将为实验室所需的用户帐户设置密码。

1. 使用 **SC-400-CL1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)。 密码应由实验室托管提供程序提供。

1. 打开 **Microsoft Edge**，导航到 **`https://admin.microsoft.com`** 并以 MOD 管理员“`admin@WWLxZZZZZZ.onmicrosoft.com`”（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）的身份登录到 Microsoft Purview 门户。

1. 在左侧导航窗格中，展开“**用户**”，然后选择“**活动用户**”。

1. 选中 **Joni Sherman** 左侧的复选框。

   此帐户将用于演示演练。

1. 从顶部导航功能区选择“**重置密码**”按钮，重置 Joni 的密码。

   ![显示 Microsoft 365 管理中心中的“重置密码”按钮的屏幕截图。](/Instructions/Media/reset-password-button.png)

1. 在右侧的“**重置密码**”浮出控件页面，确保取消选择所有选项。

   这将确保你可以为用于演示演练的 Joni 选择密码，并且首次登录时无需重置这些密码。

1. 在“**密码**”字段中，输入可记住的密码以重置用户密码，供今后练习使用。

1. 在“**重置密码**”浮出控件页面底部，选择“**重置密码**”按钮。

1. 在“**密码已重置**”页面，应会看到已重置的三个用户帐户。 在此浮出控制页底部，选择“**关闭**”。

已成功重置实验室练习的密码。

## 任务 2 - 在 Microsoft Purview 中启用审核

1. 使用 **SC-400-CL1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)。 密码应由实验室托管提供程序提供。

1. 打开 **Microsoft Edge**，导航到 **`https://purview.microsoft.com`** 并以 MOD 管理员“`admin@WWLxZZZZZZ.onmicrosoft.com`”（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）的身份登录到 Microsoft Purview 门户。

1. 有关新的 Microsoft Purview 门户的消息将显示在屏幕上。 选择同意数据流披露条款和隐私声明的选项，然后选择“**立即试用**”。

    ![显示“欢迎使用新的 Microsoft Purview 门户屏幕”的屏幕截图。](/Instructions/Media/welcome-purview-portal.png)

1. 从左侧边栏中选择“**解决方案**”，然后选择“**审核**”。

1. 在“**搜索**”页面，选择“**开始录制用户和管理活动**”栏以启用审核日志记录。

    ![显示“开始录制用户和管理员活动”按钮的屏幕截图。](/Instructions/Media/enable-audit-button.png)

1. 选择此选项后，蓝色栏应从此页面消失。

已在 Microsoft 365 中成功启用审核。

## 任务 3 - 为终结点 DLP 载入设备

在本任务中，你将为组织启用设备加入。

1. 你仍应使用 **SC-400-CL1\admin** 登录到客户端 1 VM (SC-400-CL1)。

    你仍应以“MOD 管理员”身份登录 Microsoft Purview。

1. 在 Microsoft Purview 门户的左侧边栏中，选择“**设置**”。 展开“**设备加入**”，然后选择“**设备**”。

1. 在“**设备**”页上，选择“**启用设备加入**”，为租户启用解决方案。

1. 选择“确定”，接受“启用设备加入”对话框中的内容 。

1. 选择“确定”，接受“正在开启设备监视”对话框中的内容 。

你现在已经启用了设备加入功能，可以开始加入设备以使用终结点 DLP 策略对其进行保护。 启用该功能的过程可能需要长达 30 分钟。

## 任务 4 - 将设备加入到终结点 DLP

在本任务中，你将使用本地脚本选项加入 Windows 11 设备，使其得到终结点 DLP 策略的保护。

1. 你仍然应该会使用 **SC-400-CL1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)。

   你仍应以“MOD 管理员”身份登录 Microsoft Purview。

   你仍应位于终结点 DLP 的“**设备**”页上。

1. 在 Microsoft Purview 门户中的 **“设备”** 页中，确保 **“设备加入** ”已展开，然后选择“ **加入**”。

1. 在“设备加入”页面上的导航窗格中，选择“加入” 。

1. 在“部署方法”下拉菜单中，选择“本地脚本(最多可用于 10 台计算机)”，然后选择“下载包”。************

1. 在“**下载**”对话框中，将鼠标悬停在下载上方，然后选择文件夹图标以“**在文件夹中显示**”。

1. 将 Zip 文件解压缩至 SC-400-CL1 的**桌面**。 应该会看到名为 DeviceComplianceLocalOnboardingScript.cmd 的脚本。

1. 在桌面上，右键单击刚刚解压的 **DeviceComplianceLocalOnboardingScript.cmd** 文件，然后选择“**显示更多选项**”，再选择“**属性**”。

1. 在属性窗口的“**常规**”选项卡底部，选择“**安全**”部分中的“**取消阻止**”，然后选择“**确定**”以保存此设置。

1. 返回桌面，右键单击 **DeviceComplianceLocalOnboardingScript.cmd** 文件，然后选择“**以管理员身份运行**”。 在“**用户帐户控制**”对话框中，选择“**是**”。

1. 在“命令提示符”屏幕中键入 Y 以进行确认，然后按 Enter 键 。

1. 脚本完成后，将收到成功消息和“**按任意键继续**”提示。 按任意键关闭命令窗口。 完成此加入可能需要一分钟时间。

1. 打开“开始”菜单并搜索 `Access work or school`。 在“**最佳匹配**”下选择“**访问工作或学校**”。

1. 在“**添加工作或学校帐户**”的“**访问工作或学校**”窗口中，选择“**连接**”。

1. 在“**设置工作或学校帐户**”对话框中，选择“**让此设备加入 Microsoft Entra ID**”链接，并以 **MOD 管理员**`admin@WWLxZZZZZZ.onmicrosoft.com`（其中 ZZZZZZ 是实验室托管服务提供商提供的唯一租户 ID）的身份登录。

1. 在“请确认这是你的组织”对话框中查看租户 URL 并选择“加入”。********  

1. 设备连接后，在“**你已完成所有设置!**”屏幕上选择“**完成**” 。

1. 重启客户端 1 VM (SC-400-CL1)。

1. 客户端 1 VM 可用后，请重新登录到客户端 1 VM (SC-400-CL1)。

1. 打开 Microsoft Edge，导航回 **`https://purview.microsoft.com`** 并以“MOD 管理员”`admin@WWLxZZZZZZ.onmicrosoft.com`（其中 ZZZZZZ 是实验室托管提供商提供的唯一租户 ID）的身份登录到 Microsoft Purview 门户。

1. 在 Microsoft Purview 门户中，导航到“**设置**” > “**设备加入**” > “**设备**”并验证设备是否已成功加入。

你已经成功加入了一个设备，并将其加入到 Microsoft Entra ID 中，以受终结点 DLP 策略保护。

## 任务 5 - 启用对敏感度标签的支持

在此任务中，你将安装必要的模块，并在租户上启用对敏感度标签的支持。

1. 你仍然应该会使用 **SC-400-CL1\admin** 帐户登录到客户端 1 VM (SC-400-CL1)。

1. 右键单击任务栏中的“Windows”按钮，然后选择“**终端(管理员)**”，打开提升的 PowerShell 窗口。

1. 输入表示“是”的 Y 并按 Enter，以确认“用户帐户控制”窗口 。

1. 运行 **Install-Module** cmdlet，以安装最新版 MS Online PowerShell 模块：

    ```powershell
    Install-Module -Name MSOnline
    ```

1. 输入表示“是”的 Y 并按 Enter 键以确认“NuGet 安全性”对话框以及“不受信任的存储库安全”对话框。 这可能需要一段时间才能处理完成。

1. 运行 **Install-Module** cmdlet，以安装最新版本的 Sharepoint Online PowerShell 模块：

    ```powershell
    Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

1. 输入表示“是”的 Y 并按 Enter 键，以确认“不受信任的存储库安全”对话框。

1. 运行 **Connect-MsolService** 以连接到 MS Online 服务：

    ```powershell
    Connect-MsolService
    ```

1. 在“**登录到帐户**”窗体中，以“**MOD 管理员**"的身份`admin@WWLxZZZZZZ.onmicrosoft.com`（其中 ZZZZZZ 是实验室托管提供商提供的唯一租户 ID）登录。

1. 登录后，导航回终端窗口。

1. 运行 **Get-Msoldomain** cmdlet 并将域另存为变量：

    ```powershell
    $domain = get-msoldomain
    ```

1. 使用在上一步中创建的 _$domain_ 变量为 _$adminurl_ 创建新变量：

    ```powershell
    $adminurl = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"
    ```

1. 使用在上一步中创建的 _$adminurl_ 变量运行 **Connect-SPOService** cmdlet：

    ```powershell
    Connect-SPOService -url $adminurl
    ```

1. 在“登录到帐户”窗体中，以 MOD 管理员身份登录。 `admin@WWLxZZZZZZ.onmicrosoft.com`（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）。 管理员的密码应由实验室托管提供程序提供。

1. 登录后，导航回终端窗口。

1. 运行 **Set-SPOTenant** cmdlet，以启用对敏感度标签的支持：

    ```powershell
    Set-SPOTenant -EnableAIPIntegration $true
    ```

1. 输入表示“是”的 Y 并按 Enter 键，以确认更改。

1. 关闭 PowerShell 窗口。

你已为 Teams 和 SharePoint 网站成功启用对敏感度标签的支持。

## 任务 6 - 开启处理 Office 联机文件（已应用加密的敏感度标签且存储在 OneDrive 和 SharePoint 中）中的内容的功能。

1. 打开 **Microsoft Edge**，导航到 **`https://purview.microsoft.com`** 并以 MOD 管理员“`admin@WWLxZZZZZZ.onmicrosoft.com`”（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）的身份登录到 Microsoft Purview 门户。

1. 选择左侧边栏的“**解决方案**”，然后选择“**信息保护**” > “**敏感度标签**”。

1. 在黄色对话框中选择“**立即开启**”，此对话框指示：**你的组织尚未开启处理 Office 联机文件（已应用加密的敏感度标签且存储在 OneDrive 和 SharePoint 中）中的内容的功能。可以在此处启用该功能，但请注意，多地理位置环境需要其他配置。**

1. 你现在应该会看到一条消息：**现在可以使用 Teams、SharePoint 站点和 Microsoft 365 组的隐私和访问控制设置创建敏感度标签。**
