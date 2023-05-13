# [1.1]ChatGLM学习实战-闯关笔记

> ChatGLM-6B 是清华与智谱AI开源的LLM模型。官网地址：[https://chatglm.cn/blog](https://chatglm.cn/blog)
> 
> 目前已ChatGLM-6B已开源。github：[https://github.com/THUDM/ChatGLM-6B](https://github.com/THUDM/ChatGLM-6B)。
> 
> ChatGLM-130B正在内测。申请链接：[https://modelnet.ai/chatglm_application](https://modelnet.ai/chatglm_application)

## ChatGLM-6B特点
* 可以finetune：相较于国内其他的LLM模型，ChatGLM是较早开放Finetune的LLM。
* 模型量级较小。本身参数量只用6B，如果使用量化版本(INT4)可以在6G显存的GPU上进行推理。
* 支持中英双语。

## 安装部署
> 环境：云主机的ubuntu 18.04 
>
> GPU: V100 32G
> 
> torch: 1.12

由于之前踩过坑，系统选择16.04会与torch不匹配。torch需要1.10以上。同时不能安装最新的2.0版本，同样会有报错。

其他安装只需要：
```
pip install -r requirements.txt
```

## 初体验

可以直接调用提供的终端client:
```
python cli_demo.py
```

这里有一点需要注意，由于使用的是input()函数进行输入，如果输入错误使用退格键(backspace)时，每按一次只会删除一个byte的字符。但utf8的汉字一般有3bytes，如果没有完整删除，会报错：UnicodeDecoderError。有如下方法可以避免：
```
# 第一种方法
import readline
# 第二种方法
try:
    input("\n用户:")
except Exception as e:
    print("输入有误，请重新输入:", e)
    continue
```

## ptuning
> 官网提供的例子需要单独下载数据集：AdvertiseGen。地址：[https://cloud.tsinghua.edu.cn/f/b3f119a008264b1cabd1/?dl=1](https://cloud.tsinghua.edu.cn/f/b3f119a008264b1cabd1/?dl=1)
>

使用默认参数执行了一下train和evaluate

在V100上需要4个小时ptuning。

其他功能待后续尝试补充。
