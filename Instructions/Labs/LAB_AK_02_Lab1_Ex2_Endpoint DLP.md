---
lab:
  title: 练习 2 - 管理终结点 DLP
  module: Module 2 - Implement Data Loss Prevention
ms.openlocfilehash: 5b217ee6531ed7135de8c12db5d6399beab718ca
ms.sourcegitcommit: 53488624251b6cf8f79f2d1ff561e3f334764821
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2022
ms.locfileid: "147694939"
---
# <a name="lab-2---exercise-2---manage-endpoint-dlp"></a>实验室 2 - 练习 2 - 管理终结点 DLP

你是 Joni Sherman，Contoso Ltd. 新上任的合规性管理员，负责配置公司的 Microsoft 365 租户以防止数据丢失。 Contoso Ltd. 是美国的一家提供驾驶指导服务的公司，你需要确保敏感客户信息不会泄露到组织外部。 所以，你决定不仅要实现 Microsoft 365 DLP 策略，还要将此保护扩展到组织中的设备。

### <a name="task-1--enable-device-onboarding"></a>任务 1 - 启用设备加入

在本任务中，你将为组织启用设备加入。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。 以 JoniS@WWLxZZZZZZ.onmicrosoft.com 身份登录（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）。  Joni 的密码应由实验室托管提供程序提供。

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 https://compliance.microsoft.com。

1. 在 Microsoft Purview 门户的左侧导航窗格中，选择“设置”，然后选择“设备加入”  。

1. 选择“启用设备加入”，为租户启用解决方案。

1. 选择“确定”，接受“启用设备加入”对话框中的内容 。

1. 选择“确定”，接受“正在开启设备监视”对话框中的内容 。

你现在已经启用了设备加入，可以开始加入 Windows 10 设备以使用终结点 DLP 策略对其进行保护。 启用该功能的过程可能需要长达 30 分钟的时间，但你可以继续执行下一个任务，因为该任务不依赖此功能。

### <a name="task-2---onboard-a-device-to-endpoint-dlp"></a>任务 2 - 将设备加入到终结点 DLP

在本任务中，你将使用本地脚本选项加入 Windows 10 设备，使其得到终结点 DLP 策略的保护。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 在 Microsoft Edge 中，导航到 https://compliance.microsoft.com ，并应以 Joni Sherman 的身份登录到 Microsoft 365。  

1. 在 Microsoft Purview 门户的左侧导航窗格中，选择“设置”，然后选择“设备加入”  。

1. 在“设备加入”页面上的导航窗格中，选择“加入” 。

1. 在“部署方法”下拉菜单中，选择“本地脚本(最多可用于 10 台计算机)”，然后选择“下载包”  。

1. 在下载对话框中，选择“保存”，然后选择“打开文件夹” 。

1. 将 Zip 文件解压缩至 LON-CL1 的桌面。 应该会看到名为 DeviceComplianceLocalOnboardingScript.cmd 的脚本。

1. 在桌面上，右键单击刚刚解压缩的 DeviceComplianceLocalOnboardingScript.cmd 文件，然后选择“以管理员身份运行” 。  如果选择“更多信息”并选择“仍然运行”，可能会弹出 Windows SmartScreen 警告框 。  如果弹出“用户帐户控制”窗口，请为所有脚本选择“是”以对电脑进行更改。

1. 在“命令提示符”屏幕中键入 Y 以进行确认，然后按 Enter 键 。

1. 脚本完成后，按任意键以继续。  完成此加入可能需要一分钟时间。

1. 打开开始菜单，查找并选择“访问工作或学校帐户”。

1. 在“访问工作或学校帐户”窗口中，选择“+ 连接” 。

1. 在“设置工作或学校帐户”对话框中，选择“让此设备加入 Azure Active Directory”链接，并以 Joni Sherman 的身份 JoniS@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管服务提供程序提供的唯一租户 ID）登录。    Joni 的密码应由实验室托管提供程序提供。

1. 在“请确认这是你的组织”对话框中查看租户 URL 并选择“加入” 。  如果你的设备加入失败，可能需要排查 Azure AD 配置加入设置的问题。 请执行以下操作，确保可以加入设备：

        1. Open a new browser tab and go to the Azure Portal https://portal.azure.com
        2. Sign in as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com
        3. Select **Manage Azure Active Directory**.
        4. Select **Devices**
        5. Select **Device settings**
        6. Scroll-down until you see **Maximum number of devices per user** change the value to **20 (Recommended)**
        7. Once you have updated the setting re-try to connect your device.

1. 连接设备后，选择“完成”。

1. 重启客户端 1 VM (LON-CL1)。

你已经成功加入了一个设备，并将其加入到 Azure AD 中以受终结点 DLP 策略保护。

### <a name="task-3---create-and-endpoint-dlp-policy"></a>任务 3 - 创建终结点 DLP 策略

在本任务中，你将在 Microsoft Purview 门户中创建数据丢失防护策略，以保护组织中驻留在 Windows 10 设备上的敏感数据。 如果用户想从包含信用卡信息的文档中复制内容，你创建的 DLP 策略将阻止该操作。

1. 使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)。

1. 从任务栏打开 Microsoft Edge，通过 https://compliance.microsoft.com 导航到 Microsoft Purview 门户，并在显示“登录”窗口时，以 JoniS@WWLxZZZZZZ.onmicrosoft.com 的身份（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录。 Joni 的密码应由实验室托管提供程序提供。 提示：密码可能与 MOD 管理员之前使用的密码相同。 

1. 在 Microsoft Purview 门户的左侧导航窗格中，选择“数据丢失防护”，然后从顶部窗格中选择“策略”  。

1. 选择“+ 创建策略”以启动用于创建新数据丢失防护策略的向导。

1. 在“从模板开始或创建自定义策略”页面上，依次选择“自定义”、“自定义策略”以及“下一步”   。

1. 在“为 DLP 策略命名”页面中，输入以下信息：

    - 名称：员工疾病终结点 DLP 策略
    - 说明：防止员工 ID 号和疾病被共享在终结点上。

1. 选择“**下一步**”。

1. 在“选择应用策略的位置”页面上，仅选择“设备”选项，然后选择“下一步”  。

1. 在“定义策略设置”页面上，需要选择“创建或自定义高级 DLP 规则”选项，该选项默认处于选中状态 。 选择“**下一步**”。

1. 在“自定义高级 DLP 规则”页面上选择“+ 创建规则” 。

1. 在“创建规则”页面上，输入以下内容：

    - 名称：EmployeeID 和疾病规则
    - 说明：检测员工 ID 和疾病是否在附近范围共享。

1. 选择“+ 添加条件”，然后从下拉菜单中选择“内容包含” 。

1. 在新打开的“内容包含”区域中，选择“添加”，然后从下拉菜单中选择“敏感信息类型”  。

1. 在右侧窗格“敏感信息类型”中，选择“Contoso 员工 ID”和“Contoso 疾病列表”，然后选择“添加”   。

1. 将“这其中的任何项”下拉列表更改为“这其中的所有项”，使策略能够检测两个邻近的信息 。

1. 向下滚动到“操作”，选择“+ 添加操作”下拉列表，然后选择“审核或限制 Windows 设备上的活动”  。

1. 保留启用的所有复选框，并将右侧的下拉列表选项从“仅审核”更改为“阻止” 。

1. 在“用户通知”部分中，通过启用“使用通知来通知用户并帮助引导他们正确使用敏感信息”来启用通知 。 切换到“开”。

1. 在“终结点设备”下，选中“当限制活动时向用户显示策略提示通知”复选框。 当你在 Windows 中为活动选择“阻止”时会打开此功能。 若要关闭 Windows 设备上的通知，请禁用限制。

1. 向下滚动到“用户替代”部分，在“允许从终结点设备替代”下选择“从剪贴板复制”  。

1. 选择“保存”，然后选择“下一步” 。

1. 在“测试或启用策略”页面上，选择“立即启用策略” 。

1. 选择“下一步”并查看策略配置。

1. 选择“提交”以创建策略。

1. 创建策略后，选择“完成”。

你已成功激活该 DLP 策略。 如果策略检测到有人试图从包含信用卡信息的文件中复制内容，它将阻止该尝试并通知用户。

### <a name="task-4---configure-endpoint-dlp-settings"></a>任务 4 - 配置终结点 DLP 设置

在本任务中，你将在 Windows 10 设备上配置一个文件夹的文件路径排除，以确保该文件夹的内容不会被自己创建的终结点 DLP 策略监视。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。 

1. 在 Microsoft Edge 中，Microsoft Purview 门户选项卡应该仍处于打开状态。 如果是这样，请选择该选项卡并继续进行下一步。 如果已关闭，请在新标签页中导航到 https://compliance.microsoft.com。

1. 在 Microsoft Purview 门户的左侧导航窗格中，选择“策略”，然后在“数据”下选择“数据丢失防护”   。

1. 在“数据丢失防护”窗口中选择“终结点 DLP 设置”选项卡 。

1. 在“终结点 DLP 设置”选项卡中，展开“Windows 的文件路径排除”区域，并选择“+ 添加文件路径排除”  。

1. 在“输入要排除的路径”字段中，键入 C:\FilePathExclusionTest，然后选择 +。

1. 选择“添加”  。

1. 展开“敏感数据的浏览器和域限制”，并选择“+ 添加或编辑不允许的浏览器” 。

1. 在右侧的“+ 添加不允许的浏览器”中，选中“Google Chrome”左侧的复选框，然后选择“保存”  。

1. 选择“服务域”左侧的下拉菜单，并将它从“关”更改为“阻止”  。

1. 在“更新云应用模式”中，选择“是”以激活阻止模式 。

1. 选择“+ 添加云服务域”以打开右侧窗格。

1. 在右侧窗格中，在“域”下输入“dropbox.com”，选择“+”符号，然后选择“添加”   。

1. 关闭浏览器窗口。

你现在已为终结点 DLP 策略配置了自定义设置。 你创建的每个策略都将忽略你配置的文件夹中的内容，并且 Google Chrome 浏览器已添加为不允许的浏览器来处理敏感数据。

### <a name="task-5---configure-microsoft-purview-extension"></a>任务 5 - 配置 Microsoft Purview 扩展

作为合规性管理员，你需要评估向多个用户推出 Chrome 浏览器用于处理敏感数据的新业务要求。 对于此测试，你需要将 Google Chrome 浏览器安装到客户端 01，然后从 Google 网上应用店手动为 Google 添加 Purview 合规性扩展。

1. 从任务栏中打开 Edge 浏览器。

1. 通过 https://chrome.google.com 导航到 Google Chrome 下载。

1. 选择“下载 Chrome”，并选择“下载”下方的“打开文件”，然后选择“ChromeSetup.exe”   。

1. 在“用户帐户控制”对话框中选择“是”以安装 Chrome 浏览器 。

1. 安装完成后会打开“欢迎使用 Chrome”页面，通过 https://chrome.google.com/webstore/detail/microsoft-purview-extensi/echcggldkblhodogklpincgchnpgcdco 导航到 Chrome 网上应用店中的 Microsoft Purview 扩展。

1. 验证你是否位于 Microsoft Purview 扩展的扩展页上，然后选择“添加至 Chrome” 。

1. 在添加“Microsoft Purview 扩展”窗口中，选择“添加扩展程序” 。

1. 关闭通知窗口并导航到 chrome://extensions。

1. 验证“Microsoft Purview 扩展”是否可见并是否已激活。

你已成功安装了 Chrome 浏览器，并向客户端添加了 Microsoft Purview 扩展。 现在可以像 Edge 浏览器一样使用 Chrome 浏览器来处理敏感数据，并且以前配置的终结点 DLP 策略在使用 Chrome 浏览器时也适用。

# <a name="proceed-to-lab-2---exercise-3"></a>继续进行实验室 2 - 练习 3 
