---
lab:
  title: 练习 3 - 管理可训练的分类器
  module: Module 1 - Implement Information Protection
---

# 实验室 1 - 练习 3 - 管理可训练的分类器

Contoso Ltd. 租户包含一个名为“销售和营销”的 SharePoint 网站集，将在未来用于存储一些与财务相关的文档和报表。 由于这些文档的性质，你需要创建一个可训练的分类器来识别和标记这些文件。 为此，你将激活自定义可训练的分类器并新建一个可训练的分类器。

**重要事项**：在租户中激活可训练的分类器后，需 7 到 14 天才能创建任意自定义可训练分类器。 完成整个激活过程后，“新建可训练的分类器”按钮才可用。  因此，你现在只能执行任务 1。 如果想要完成任务 2 和 3，则需要等待可训练分类器设置处理完毕。  这些实验室说明可通过 GitHub.com 获得。 用于执行任务 1 的 Microsoft 365 租户应仍处于活动状态。

## 任务 1 - 激活可训练的分类器

创建自定义的可训练分类器之前，需在租户中激活该功能。 若要激活所需的全局管理员权限，需先注销 Joni Sherman 帐户，并使用 MOD 管理员激活该功能。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。

1. 选择右上角的图片，然后选择“注销”，以注销 Joni Sherman 帐户。

1. 关闭浏览器窗口，并打开新的浏览器窗口。

1. 在“Microsoft Edge”中，导航到 `https://compliance.microsoft.com`。

1. 显示“选择帐户”页面时，选择“使用其他帐户”并以“MOD 管理员”身份 admin@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）登录  。  管理员的密码应由实验室托管提供程序提供。

1. 从左侧导航窗格导航到“**数据分类**”并将其展开，然后选择“**分类器**”。

1. 默认情况下，将从顶部窗格中选择“**可训练的分类器**”。

1. 在“**开始使用可训练的分类器**”对话框中，选择“**开始扫描过程**”。

1. 刷新浏览器窗口。

1. 阅读窗口顶部的信息横幅消息“为使你能够创建可训练的分类器，我们目前正在扫描你的内容位置以生成分析，该分析可帮助我们了解你的组织中有哪些内容类型。此过程需要 7 到 14 天才能完成”。

1. 使客户端保持打开状态。

你在租户中成功激活了可训练的分类器。 现在需等待 7 到 14 天，直到“创建可训练的分类器”按钮可用。  如果你在教室，没有 7 到 14 天的时间来等待可训练分类器完成处理，你可以登录在可训练的分类器处理完成后提供的租户来执行本练习中的其他任务。  租户应仍处于活动状态。

## 任务 2 - 创建可训练的分类器（可选实验室任务）

成功激活可训练的分类器后，“创建可训练的分类器”按钮将变为可用，并且可以新建自定义分类器。 在本任务中，Joni 将新建可训练的分类器，并选择其他 SharePoint 网站来标识 Contoso Ltd 创建和存储的典型数据。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 MOD 管理员身份登录到 Microsoft 365 。

1. 选择右上角的 MA，然后选择“注销”，以注销 MOD 管理员帐户。

1. 关闭浏览器窗口，并打开新的浏览器窗口。

1. 在“Microsoft Edge”中，导航到 `https://compliance.microsoft.com`。

1. 显示“选择帐户”页面时，请选择“使用其他帐户”并以 Joni Sherman 身份登录  。 JoniS@WWLxZZZZZZ.onmicrosoft.com（其中 ZZZZZZ 是实验室托管提供程序提供的唯一租户 ID）。  Joni 的密码应由实验室托管提供程序提供。

1. 从左侧导航窗格导航到“数据分类”。

1. 从顶部窗格中选择“可训练的分类器”。

1. 选择“+ 创建可训练的分类器”以新建分类器。

1. 在“命名和描述可训练的分类器”页面中输入以下信息：

    - **名称**：Contoso 公司数据
    - **说明**：可训练的分类器，适用于 Contoso Ltd 生成和存储的公司数据。

1. 选择“**下一步**”。

1. 选择“选择网站”，打开右侧窗格。

1. 选择以下 SharePoint 网站：

    - 通信网站
    - News @ Contoso
    - Contoso Web 1
    - **品牌**
    - 数字倡议组织公共关系
    - Work @ Contoso
    - **销售和营销**
    - Contoso Landings
    - **Mark 8 项目团队**
    - HR
    - **操作**
    - **零售**
    - PointPublishing Hub 网站
    - **团队网站**
    - 领导团队
    - **社区**
    - Give @ Contoso
    - Benefits @ Contoso
    - Learn @ Contoso
    - 活动 - 事件

1. 等待列表中显示所选网站，然后选择“下一步”。

1. 检查设置，然后选择“创建可训练的分类器”。

1. 显示消息“已创建可训练的分类器”时，选择“完成” 。

1. 现在，需等待 1 到 24 个小时才能继续操作。 使浏览器保持打开状态。

现在，正在分析所选 SharePoint 网站中的文档和文件，最多可能需要 24 个小时。

## 任务 3 - 发布可训练的分类器（可选实验室任务）
新建可训练的分类器并完成文档和文件的初始分析后，需执行手动训练过程。 在本任务中，Joni 将开始对分类器进行校准，以达到发布所需的准确度。

1. 你仍应使用 lon-cl1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 的身份登录到 Microsoft 365 。

1. 浏览器窗口此时显示 Microsoft Purview 门户中“可训练的分类器”选项卡中的“数据分类” 。

1. 选择名称为“Contoso 公司数据”、类型为“自定义”的可训练分类器，打开详细设置 。

1. 查看右侧的“详细信息”选项卡，包括分类器的源网站、已处理的项数以及“需对项进行测试”的“状态”  。

1. 若要添加用于训练分类器的项，请选择“添加要测试的项”，以打开右侧的选择窗格。

1. 在“选择具有要测试的项的网站”窗格中，选择“+ 选择网站” 。

1. 选择以下 SharePoint 网站：

    - 通信网站
    - News @ Contoso
    - Contoso Web 1
    - **品牌**
    - 数字倡议组织公共关系
    - Work @ Contoso
    - **销售和营销**
    - Contoso Landings
    - **Mark 8 项目团队**
    - HR
    - **操作**
    - **零售**
    - PointPublishing Hub 网站
    - **团队网站**
    - 领导团队
    - **社区**
    - Give @ Contoso
    - Benefits @ Contoso
    - Learn @ Contoso
    - 活动 - 事件

1. 选择 **添加** 。

1. 等待列表中显示网站，然后选择“添加”。

1. 更新“概述”部分后，窗口顶部将显示新选项卡。

1. 从顶部窗格中选择“要查看的已测试项”。

1. 可能需要 15 到 30 分钟才能查看第一批结果。 如果列表中未显示任何文件，请刷新浏览器窗口，直到有可用数据。

1. 从列表中选择第一个文件的名称，打开预览窗口。

1. “预测”行为“匹配”时，该文件会标识为分类器的匹配项 。 预览窗口下方会显示消息：“我们预测此项与该分类器‘匹配’” 。 选择“匹配”，以批准自动分类。

1. “预测”行为“不匹配”时，该文件不会标识为分类器的匹配项 。 预览窗口下方会显示消息：“我们预测此项与该分类器‘不匹配’” 。 选择“不匹配”，以批准自动分类。

1. 继续对列表中的所有项执行上述操作并批准自动分类。 查看所有项后，从顶部窗格中选择“概述”，然后再次选择“要查看的已测试项”，以加载下一组要查看的项 。

1. 对于每 30 个已查看项，系统会显示“自动执行再训练”窗口。 选择“确定”，并继续执行上述步骤，直到查看完所有项。

1. 查看足够多的项后，右上角的“发布”按钮将变为可用。 可用时即将其选中。

1. 在“发布分类器”窗口中，选择“是”以发布分类器 。

1. 右侧窗格显示消息“已发布可训练的分类器”时，表示已成功发布了可训练的分类器。

1. 单击右上角的 X，关闭右侧窗格。

1. 返回主网站，自定义分类器已移至“已发布”，“状态”已更改为“可以使用”  。

1. 使浏览器窗口保持打开状态。

你成功创建、训练和发布了自定义的可训练分类器，该分类器与 Contoso Ltd 的现有 SharePoint 网站中存储的文件匹配。
