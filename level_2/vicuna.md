# Vicuna模型学习与实践

## Vicuna简介
UC伯克利学者联手CMU、斯坦福等，再次推出一个全新模型70亿/130亿参数的Vicuna，俗称「小羊驼」（骆马）。小羊驼号称能达到GPT-4的90%性能

## Vicuna模型安装
Vicuna依托与fastchat项目。需要下载或安装FastChat使用。

> 注意：FastChat需要python 3.8以上版本

两种安装方式

```
# 1. with pip
pip3 install fschat

# 2. from source
git clone https://github.com/lm-sys/FastChat.git
cd FastChat
pip3 install --upgrade pip  # enable PEP 660 support
pip3 install -e .
```

## 使用方法
| Size | Chat Command | Hugging Face Repo |
| ---  | --- | --- |
| 7B   | `python3 -m fastchat.serve.cli --model-path lmsys/vicuna-7b-v1.3`  | [lmsys/vicuna-7b-v1.3](https://huggingface.co/lmsys/vicuna-7b-v1.3)   |
| 13B  | `python3 -m fastchat.serve.cli --model-path lmsys/vicuna-13b-v1.3` | [lmsys/vicuna-13b-v1.3](https://huggingface.co/lmsys/vicuna-13b-v1.3) |

## 使用效果
"""
Loading checkpoint shards: 100%|██████████████████████████████████████████████████████████████████████████████████████████| 2/2 [00:59<00:00, 29.63s/it]Human: 你好Assistant: 你好！有什么我可以帮助你的吗？Human: 你是谁Assistant: 我是 Assistant，一个人工智能助手。我可以回答你关于各种话题的问题，并根据你的需要提供建议和解决方案。你需要什么帮助吗？Human:
"""

> 如果huggingface连接不上，可以尝试用modelscope下载模型
