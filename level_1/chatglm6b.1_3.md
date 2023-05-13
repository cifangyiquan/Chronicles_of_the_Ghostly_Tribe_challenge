# [1.3]ChatGLM学习实战-闯关笔记
# ChatGLM-6B特定任务的微调实战

> 1.3 根据chatglm-maths项目，微调chatglm的数学运算。项目地址：[https://github.com/yongzhuo/chatglm-maths](https://github.com/yongzhuo/chatglm-maths)
>
> 本次优化的方式是lora进行finetune。

## 什么是lora？

最近lora是随着stable diffusion而大火起来。但实际上lora的发明，是为了llm的finetune。

> LoRA，英文全称Low-Rank Adaptation of Large Language Models，直译为大语言模型的低阶适应，这是微软的研究人员为了解决大语言模型微调而开发的一项技术。
>
> 比如，GPT-3有1750亿参数，为了让它能干特定领域的活儿，需要做微调，但是如果直接对GPT-3做微调，成本太高太麻烦了。
> 
> LoRA的做法是，冻结预训练好的模型权重参数，然后在每个Transformer（Transforme就是GPT的那个T）块里注入可训练的层，由于不需要对模型的权重参数重新计算梯度，所以，大大减少了需要训练的计算量。
>
> form: [https://zhuanlan.zhihu.com/p/610031713](https://zhuanlan.zhihu.com/p/610031713)

## 训练数据

使用的是[BelleGroup/school_math_0.25M](https://huggingface.co/datasets/BelleGroup/school_math_0.25M)。最近国内连huggingface有些不稳定。可能需要调整下载方式。

> 任务描述： instruction为中文的小学数学应用题的。input为空。output为题目的解题步骤和答案。这些题目由chatgpt生成，可能包含错误。
>
> 数据格式为json格式，132M数据

举个例子：
```json
{
  "instruction": "题目：小华手里有一个装满糖果的袋子，共有12个，小明想知道里面有多少颗糖果，于是他问小华：“你手里的糖果袋子里有偶数个糖果吗？”小华回答：“有，而且多于10颗。”请问小华手里的糖果袋子里最少有几颗糖果？",
  "input": "",
  "output": "\n由题目可知：小华手里的糖果袋子里有偶数个糖果；\n又知道小华手里的糖果袋子里有多于10颗糖果。\n因为糖果数为偶数，多于10颗，所以糖果数最小必须是12。\n所以小华手里的糖果袋子里最少有12颗糖果。"
}
```

## 模型训练:
执行命令
```shell
python c00_toy_lora_train_6b.py
```

## 模型推理：
执行命令
```shell
python p00_toy_lora_predict_6b.py
```

