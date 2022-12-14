# 基于迁移学习的人工智能框架缺陷修复技术

## 代码结构说明

### Dataset_acquisition

该文件夹下为数据集爬取工具，具体使用方法请参考readme

### Model_implement

该文件夹下为工具的具体实现，如果需要运行，直接使用如下命令即可，参数已经在run.py中写好。

```
cd the/model/path/you/want
python run.py
```

### Data_analysis

该文件夹下为对应的数据分析脚本

## 过程报告

### Basic Models

我们考虑了四种最先进的预训练模型(即CodeT5, CodeBERT, GraphCodeBERT和UniXcoder)作为受试者，并选择最新的技术VRepair作为基线，该技术在缺陷修复任务上显示出了有希望的结果。我们使用完美预测准确率来评估缺陷修复方法的有效性。然后，我们使用两个缺陷数据集比较了预训练模型与VRepair的预测精度。

### Transfer-learning

我们为每个预训练模型设计了三个训练场景。

bug修复场景表示仅用通用bug修复语料库训练的模型的性能。

缺陷修复场景表示仅用我们的缺陷修复语料库训练的模型的性能。

迁移学习场景表示使用迁移学习训练的模型的性能，即采用在bug修复场景中训练的模型，并用我们的缺陷修复语料库对其进行微调。

由于bug修复数据集过大，无法上传至github，如果需要，请访问以下链接

[vulnerability_data](https://smailnjueducn-my.sharepoint.com/personal/201250070_smail_nju_edu_cn/_layouts/15/onedrive.aspx?ga=1&id=%2Fpersonal%2F201250070%5Fsmail%5Fnju%5Fedu%5Fcn%2FDocuments%2Fvulnerability%2FData)

## 实验结果

### Basic Models

基础模型的表现如下：

![image-20221201010146237](pics\image-20221201010146237.png)

比较结果显示， 

(1)预训练模型可以在自动化软件缺陷修复中有着卓越的性能，具有 32.94% ~ 44.96%的预测准确率;

(2)与最先进的技术VRepair相比，预训练模型实质上实现了更好的修复性能，修复性能提升了10.21% ~ 22.23%;(3) CodeT5表现比其他研究的预训练模型更好，提高了4.34% ~ 12.02%的预测精度，这归功于它的编码器-解码器架构和预训练数据集。

### Transfer-learning

迁移学习的表现如下：

![image-20221201010407083](pics\image-20221201010407083.png)

比较结果显示， 

(1)bug修复场景下，模型平均可以修复11.87%的软件缺陷， 展示了现有bug修复技术在缺陷修复技术上的的前景

(2)从bug修复场景下进行迁移学习可以有效提高缺陷修复的表现，创造了修复准确率的新高（对于GraphCodeBert来说高达53.75%）

### 总结

实验结果表明，预训练模型在框架缺陷修复上具有十分优良的表现，同时，使用迁移学习技术能够进一步增强性能。未来，我们可以在这方面进行更多研究。