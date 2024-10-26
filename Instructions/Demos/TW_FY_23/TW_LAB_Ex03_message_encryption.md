---
lab:
  title: 练习 2 - 管理 Microsoft Purview 邮件加密
  module: Module 1 - Implement Information Protection
---

<!--
# Lab 1 - Exercise 2 - Manage Microsoft Purview Message Encryption
-->

# 练习 3 - 管理 Microsoft Purview 邮件加密

Joni Sherman 需要与其试点团队配置和测试的第一个设置是 Microsoft Purview 邮件加密。 为此，她将修改默认模板并创建一个新的品牌模板，该模板将分配给其中一位试点用户。 然后，试点用户将使用其帐户测试邮件加密功能。

## 任务 1 - 验证 Azure RMS 功能

在此任务中，你将安装 Exchange Online PowerShell 模块并在 Joni Sherman 的上下文中验证租户的正确 Azure RMS 功能，Joni Sherman 在上一练习中被指定为合规性管理员。

<!--
1. You should still be signed in to Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. Open an elevated PowerShell window by selecting the Windows button with the right mouse button and then select **Windows PowerShell (Admin)**.

1. Confirm the **User Account Control** window with **Yes**.
-->

1. 从任务栏中打开提升的 PowerShell 窗口。

1. 输入以下 cmdlet，安装最新版 Exchange Online PowerShell 模块：

    ```powershell
    Install-Module ExchangeOnlineManagement
    ```

1. 输入表示“是”的 Y 并按 Enter 键，以确认“不受信任的存储库安全”对话框 。  此过程可能需要一段时间才能完成。

1. 输入以下 cmdlet 以更改执行策略，然后按 Enter 键

    ```powershell
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
    ```

1. 单击表示“是”的 Y 并按 Enter 键，以确认“执行策略更改” 。

<!--
1. Close the PowerShell window.

1. Open a regular PowerShell window, without elevation, by selecting the Windows button with the right mouse button and select **Windows PowerShell**.
-->

1. 输入以下 cmdlet 以使用 Exchange Online PowerShell 模块并连接到租户：

    ```powershell
    Connect-ExchangeOnline
    ```

1. 显示“登录”窗口时，以 JoniS@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录。 你将使用上一个实验室中 Joni 密码重置后的密码。

1. 使用以下 cmdlet 并按 Enter 键，以验证是否在租户中激活了 Azure RMS 和 IRM：

    ```powershell
    Get-IRMConfiguration | fl AzureRMSLicensingEnabled
    ```

1. 当“AzureRMSLicensingEnabled”结果为“True”时，将为租户激活 Azure RMS 。 继续下一个步骤。 

1. 使用以下 cmdlet 并按 Enter 键，以针对另一个试点用户 Megan Bowen 测试用于 Office 365 邮件加密的 Azure RMS 模板 ：

    ```powershell
    Test-IRMConfiguration -Sender MeganB@contoso.com -Recipient MeganB@contoso.com
    ```

    ![IRM 验证脚本结果。 ](../Media/IRMvalidationl.png)

1. 验证是否所有测试均显示为“**通过**”，并且未显示任何错误。

1. 使 PowerShell 窗口保持打开状态。

你已成功安装 Exchange Online PowerShell 模块，将其连接到租户，并验证了 Azure RMS 的正确功能。

## 任务 2 – 修改默认品牌模板

组织中要求限制对外部标识提供者（例如 Google 或 Facebook）的信任。 默认情况下，这些用于访问受邮件加密保护的邮件的社交 ID 处于激活状态，因此需要在组织中停用所有用户的社交 ID。

<!--
1. You should still be signed in to your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account and there should still be an open PowerShell window with Exchange Online connected.
-->

1. 运行以下 cmdlet 以查看默认配置：

    ```powershell
    Get-OMEConfiguration -Identity "OME Configuration" | fl
    ```

1. 查看设置，并确认 **SocialIdSignIn** 参数设置为 **True**。

1. 运行以下 cmdlet，以限制使用社交 ID 从受 OME 保护的租户访问邮件：

    ```powershell
    Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn:$false
    ```

1. 输入表示“是”的 Y 并按 Enter 键，以确认有关自定义默认模板的警告消息 。

1. 再次检查默认配置，并验证 SocialIdSignIn 参数现在是否已设置为 False。

    ```powershell
    Get-OMEConfiguration -Identity "OME Configuration" | fl
    ```

1. 注意结果应显示为 **SocialIDSignIn** 设置为 **False**。 使 PowerShell 窗口和客户端保持打开状态。

你已成功停用 Office 365 邮件加密中的外部标识提供者（例如 Google 和 Facebook）。

## 任务 3 – 测试默认品牌模板

必须确认在从租户的用户收到受 Office 365 消息加密保护的消息时不会为外部收件人显示任何社交 ID 对话框，并且他们需要在访问加密内容时使用 OTP。

1. 以 **lon-cl2\admin** 账户身份登录另一个VM，即客户端 2 VM (LON-CL2)。

<!--
1. Make sure all available Windows Updates are installed and the client does not require a restart to finish update installation.

[//]: <> (Installing the latest OS updates will also update the Edge browser to the new chromium version required to do this labs.)

1. Open **Microsoft Edge** from the taskbar and when a **Welcome to Microsoft Edge** windows is displayed, select **Start without your data**, select **Continue without this data** again and select **Confirm and start browsing**.

1. If the welcome message is missing, navigate to https://microsoft.com/edge, select **DOWNLOAD for Windows** and **Windows 10**. Select **Accept and download** and **Run** to install the latest version of the Edge browser. Once this is complete perform the previous step.
-->

1. 打开 **Microsoft Edge** 并转到 https://outlook.office.com。

1. 以 LynneR@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）的身份登录 Outlook 网页版。 

    >在课程开始时重置 Lynne 的密码，以及 Joni Sherman 的密码。

1. 在“保持登录?”对话框上，选中“不再显示此内容”复选框，然后选择“否”  。

1. 在“保存密码”对话框中选择“保存”，将试点用户密码保存在浏览器中 。

1. 如果显示“从其中翻译页面…”窗口，请选择向下箭头，然后选择“从不从其中翻译…” 。

1. 从 Outlook 左上角选择“**新建邮件**”。

1. 在“**收件人**”字段中，输入不在租户域中的个人或其他第三方电子邮件地址。 

1. 在“**添加主题**”字段中，输入“**机密消息**”。

1. 在正文中，输入“**我的超级机密消息**”。

1. 在顶部栏中，选择“**选项**”选项卡，然后选择“**加密**”（锁定图标），再从下拉列表中“**加密**”。 

    >在“**发送**”上方的邮件窗格顶部，应会看到一条通知，显示“此邮件已加密。 收件人无法移除加密”。

    ![“加密”设置的屏幕截图](../Media/OptionsEncrypt.png)

1. 选择“发送”发送该消息。

1. 登录到个人电子邮件帐户，然后打开来自 Lynne Robbins 的邮件。 

1. 如果将此电子邮件发送到 Microsoft 帐户（如 @outlook.com），则系统会自动处理加密，并显示该邮件，无需其他步骤。

    >**备注：** 如果看到“**我的超级机密消息**”。 此任务已经完成。 否则，继续执行以下步骤。

1. 如果将电子邮件发送到其他电子邮件服务（如 @gmail.com），则可能必须执行以下步骤才能处理加密和阅读邮件。

    >注意：你可能需要在垃圾邮件文件夹中查找来自 Lynne Robbins 的消息。

1. 选择“阅读邮件”。

1. 如果未激活社交 ID，则没有用于对 Google 帐户进行身份验证的按钮。

1. 选择“使用一次性密码登录”以接收限时密码。

1. 转到个人电子邮件门户并打开主题为“用于查看邮件的一次性密码”的邮件。

1. 复制密码，将其粘贴到 OME 门户中，然后选择“继续”****。

1. 查看已加密的邮件。

<!--
1. Leave Client 1 VM (LON-CL1) open as it is.
-->

你已成功使用已停用的社交 ID 测试了修改后的默认 OME 模板。

## 任务 4 - 创建自定义品牌模板

组织财务部门发送的受保护邮件需要特殊的品牌信息，包括自定义的简介和正文文本，以及页脚中的“免责声明”链接。 财务邮件也应在 7 天后过期。 在此任务中，你将创建新的自定义 OME 配置以及传输规则，以将 OME 配置应用于财务部门发送的所有邮件。

1. 使用 **lon-cl1\admin** 帐户登录到客户端 1 VM (LON-CL1)，并且仍应有一个处于打开状态且已连接 Exchange Online 的 PowerShell 窗口。

1. 运行以下 cmdlet 以创建新的配置：

    ```powershell
    New-OMEConfiguration -Identity "Finance Department" -ExternalMailExpiryInDays 7
    ```

1. 输入表示“是”的 Y 并按 Enter 键，以确认有关自定义模板的警告消息 。 

1. 使用以下 cmdlet 更改说明文本消息：

    ```powershell
    Set-OMEConfiguration -Identity "Finance Department" -IntroductionText " from Contoso Ltd. finance department has sent you a secure message."
    ```

1. 输入表示“是”的 Y 并按 Enter 键，以确认有关自定义模板的警告消息 。

1. 使用以下 cmdlet 更改邮件的正文电子邮件文本：

    ```powershell
    Set-OMEConfiguration -Identity "Finance Department" -EmailText "Encrypted message sent from Contoso Ltd. finance department. Handle the content responsibly."
    ```

1. 输入表示“是”的 Y 并按 Enter 键，以确认有关自定义模板的警告消息 。

1. 将免责声明 URL 更改为指向 Contoso 的隐私声明站点：

    ```powershell
    Set-OMEConfiguration -Identity "Finance Department" -PrivacyStatementURL "https://contoso.com/privacystatement.html"
    ```

1. 输入表示“是”的 Y 并按 Enter 键，以确认有关自定义模板的警告消息 。

1. 使用以下 cmdlet 创建邮件流规则，该规则将自定义 OME 模板应用于财务团队发送的所有邮件。  完成此进程可能需要几秒钟时间。

    ```powershell
    New-TransportRule -Name "Encrypt all mails from Finance team" -FromScope InOrganization -FromMemberOf "Finance Team" -ApplyRightsProtectionCustomizationTemplate "Finance Department" -ApplyRightsProtectionTemplate Encrypt
    ```

1. 键入以下 cmdlet 以验证更改。

    ```powershell
    Get-OMEConfiguration -Identity "Finance Department" | Format-List
    ```

1. 使 PowerShell 窗口保持打开状态。

你已经成功创建了新的传输规则，当财务部门的成员向外部收件人发送邮件时，该规则将自动应用自定义品牌模板。

## 任务 5 - 测试自定义品牌模板

要验证新的自定义配置，需要再次使用财务团队成员 Lynne Robbins 的帐户。

1. 以 **lon-cl2\admin** 帐户的身份登录到客户端 2 VM (LON-CL2)。

1. Outlook 网页版选项卡仍应处于打开状态，并以 **Lynne Robbins** 的身份登录。

1. 从 Outlook 左上角选择“**新建邮件**”。

1. 在“**收件人**”字段中，输入不在租户域中的个人或其他第三方电子邮件地址。 

1. 在“**添加主题**”字段中，输入“**财务报表**”。

1. 在正文中，输入“**机密财务信息**”。

1. 选择**Send**。

1. 登录到个人电子邮件帐户，然后打开来自 **Lynne Robbins** 的邮件。 看起来与下图类似。 选择“阅读邮件”。

    ![来自 Lynne Robbins 的加密电子邮件示例。 ](../Media/EncryptedEmail.png)

1. 由于这两个选项均可用，因此自定义配置已激活社交 ID。 选择“使用一次性密码登录”以接收限时密码。

1. 返回个人电子邮件并打开主题为“**用于查看邮件的一次性密码**”的邮件。

1. 复制密码，将其粘贴到门户中，然后选择“继续”****。

1. 查看包含自定义品牌信息的加密邮件。

你已经成功测试了新的自定义模板。
