---
lab:
  title: 练习 3 - 管理可训练的分类器
  module: Module 1 - Implement Information Protection
---

# 实验室 1 - 练习 3 - 管理可训练的分类器

Contoso Ltd. 需要确保存储在“销售和营销”SharePoint 网站中的财务文档和报表已正确分类。 若要实现此目的，需要创建可训练的分类器来识别和标记这些文件。

## 任务 1 – 创建可训练的分类器

在此任务中，你将激活租户中可训练的分类器，以创建自定义分类器。

1. 仍应使用 LON-CL1\admin 帐户登录到客户端 1 VM (LON-CL1)，并且应该以 Joni Sherman 帐户登录到 Microsoft 365。********

1. 在“Microsoft Edge”中，导航到 `https://compliance.microsoft.com`。

1. 在左侧导航窗格中，展开“数据分类”，然后选择“分类器”。********

1. 在“分类器”页上，应已选择“可训练分类器”的选项卡。********

2. 选择“+ 创建可训练的分类器”以新建分类器。

1. 在“命名和描述可训练的分类器”**** 页中输入：

    - **名称**：`Contoso Company Data`
    - **说明**：`Trainable classifier for company data produced and stored by Contoso Ltd.`

1. 选择**下一步**。

1. 在“正面示例内容来源”**** 上，选择“+选择网站”****。

1. 在右侧的“添加 SharePoint 网站”弹出页面中，选择以下 SharePoint 网站：****

    - Mark8ProjectTeam

1. 选择弹出页面底部的“添加”。****

1. 返回“正面示例内容来源”页，选择“下一步”。********

1. 在“负面示例内容来源”页上，选择以下 SharePoint 网站：****

    - HR

1. 选择弹出页面底部的“添加”。****

1. 返回“负面示例内容来源”页，选择“下一步”。********

1. 在**查看和创建分类器以开始处理示例内容**上，选择**创建可训练的分类器**

1. 在“正在训练分类器”页上，选择“完成”。********

现在，正在分析所选 SharePoint 网站中的文档和文件，可能需要长达 24 个小时。

<!---
## Task 3 – Publish a trainable classifier (optional lab task)

After the new trainable classifier was created and the initial analysis of the documents and files is done, the manual training process needs to be performed. In this task, Joni will start the calibration of the classifier to achieve the required accuracy for publishing.

1. You should still be logged into your Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In your browser window, you are in the Microsoft Purview portal at **Data classification** in the **Trainable classifiers** tab.

1. Select the trainable classifier with the name **Contoso Company Data** of the type **Custom** to open the detailed settings.

1. Review the **Details** tab on the right side, including the source site for the classifier, the number of processed items and the **Status**, which is in **Need test items**.

1. To add items for training the classifier, select **Add items to test** to open the right side selection pane.

1. In the **Choose sites with items to test** pane, select **+ Choose sites**.

1. Select the following SharePoint sites:

    - **Communication site**
    - **News @ Contoso**
    - **Contoso Web 1**
    - **Brand**
    - **Digital Initiative Public Relations**
    - **Work @ Contoso**
    - **Sales and Marketing**
    - **Contoso Landings**
    - **Mark 8 Project Team**
    - **HR**
    - **Operations**
    - **Retail**
    - **PointPublishing Hub Site**
    - **Team Site**
    - **Leadership Team**
    - **Community**
    - **Give @ Contoso**
    - **Benefits @ Contoso**
    - **Learn @ Contoso**
    - **Campaigns - Events**

1. Select **Add**.

1. Wait until the sites are shown in the list and select **Add**.

1. When the **Overview** section is updated, a new tab is shown in the top of the window.

1. Select **Tested items to review** from the top pane.

1. It will take between 15 to 30 minutes until first results are ready for review. Refresh the browser window if no files are shown in the list, until data is available.

1. Select the name of the first file from the list to open the preview window.

1. When the **Prediction** row is equal to **Match**, the file was identified as a match for the classifier. Below the preview window, a message **We predict this item "matched" this classifier.** is shown. Select **Match** to approve the automatic classification.

1. When the **Prediction** row is equal to **Not a match**, the file was identified not as a match for the classifier. Below the preview window, a message **We predict this item "does not match" this classifier.** is shown. Select **Not a match** to approve the automatic classification.

1. Proceed with all items in the list and approve the automatic classification. After all items have been reviewed, select **Overview** from the top pane and **Tested items to review** again, to load the next set of items for review.

1. For each 30 reviewed items an **Auto-retrain performed** window is shown. Select **OK** and proceed with the previous steps, until no items for review are left.

1. After sufficient items are reviewed, the **Publish** button in the upper right gets available. Select it as soon it is available.

1. In the **Publish classifier** window, select **Yes** to publish the classifier.

1. When the right side pane with **Your trainable classifier has been published** is displayed, the trainable classifier was successfully published.

1. Close the right side pane with the **X** in the upper right.

1. Back at the main site, the custom classifier was moved to **Published** and the **Status** has been changed to **Ready to use**.

1. Leave the browser window open.

You have successfully created, trained, and published a custom trainable classifier that matches the files stored on the existing SharePoint sites of Contoso Ltd.
