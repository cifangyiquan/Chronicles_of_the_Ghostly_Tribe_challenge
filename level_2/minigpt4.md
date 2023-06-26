# MiniGPT4 模型学习与实践

# 简介

2023年4月17日，多模态问答模型MiniGPT-4发布，实现了GPT-4里的宣传效果

《MiniGPT-4: Enhancing Vision-language Understanding with Advanced Large Language Models》

阿卜杜拉国王科技大学的几位博士（看名字都是中国人）开发，他们认为GPT-4 先进的多模态生成能力，主要原因在于利用了更先进的大型语言模型。

为了验证这一想法，团队成员将一个冻结的视觉编码器(Q-Former&ViT)与一个冻结的 文本生成大模型（Vicuna，江湖人称：小羊驼） 进行对齐，造出了 MiniGPT-4。

MiniGPT-4 具有许多类似于 GPT-4 的能力, 图像描述生成、从手写草稿创建网站等
MiniGPT-4 还能根据图像创作故事和诗歌，为图像中显示的问题提供解决方案，教用户如何根据食物照片做饭等。

# 模型

* 投影层（Projection Layer）是神经网络中常见层类型，将输入数据从一个空间映射到另一个空间。
* NLP中，投影层通常用于将高维词向量映射到低维空间，以减少模型参数数量和计算量。
* CV中，投影层可以将高维图像特征向量映射到低维空间，以便于后续处理和分析。

# 环境

```shell

$ git clone https://github.com/Vision-CAIR/MiniGPT-4.git

$ cd MiniGPT-4
$ conda env create -f environment.yml
$ conda activate minigpt4

# 模型下载
$ git lfs install
$ git clone https://huggingface.co/lmsys/vicuna-13b-delta-v1.1  # more powerful, need at least 24G gpu memory
$ # or
$ git clone https://huggingface.co/lmsys/vicuna-7b-delta-v1.1  # smaller, need 12G gpu memory

```

## 执行

```shell
$ python demo.py --cfg-path eval_configs/minigpt4_eval.yaml  --gpu-id 0
```
