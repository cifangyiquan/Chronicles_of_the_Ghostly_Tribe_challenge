# [1.2]ChatGLM学习实战-闯关笔记
# ChatGLM-6B微调实战

> 1.2 根据ChatGLM-6B官方的微调教程进行实战。官方文档：[https://github.com/THUDM/ChatGLM-6B/tree/main/ptuning](https://github.com/THUDM/ChatGLM-6B/tree/main/ptuning)
>
> 对于ChatGLM-6B模型基于P-Tuning v2的微调。P-Tuning v2 将需要微调的参数量减少到原理的0.1%，再通过模型量化、Gradient Checkpoint等方法，最低只需要7GB显存即可运行。
>
> 之前只1.1中其实已经运行过了P-Tuning任务。本文详细叙述一下过程。

## 环境搭建

继续使用之前搭建的chatglm-6B的环境。主要依赖有torch 1.12, transformers 4.27.1以上。

新增的依赖有: rouge_chinese, nltk, jieba, datasets

## 训练数据

官网提供的例子需要单独下载数据集：AdvertiseGen。

地址：[https://cloud.tsinghua.edu.cn/f/b3f119a008264b1cabd1/?dl=1](https://cloud.tsinghua.edu.cn/f/b3f119a008264b1cabd1/?dl=1)

> 任务描述：根据商品内容的tag生成一段广告词。
> 
> 数据为json格式，content是产品标签。summary为label。

举个例子：
```json
{"content": "类型#上衣*材质#牛仔布*颜色#白色*风格#简约*图案#刺绣*衣样式#外套*衣款式#破洞", "summary": "简约而不简单的牛仔外套，白色的衣身十分百搭。衣身多处有做旧破洞设计，打破单调乏味，增加一丝造型看点。衣身后背处有趣味刺绣装饰，丰富层次感，彰显别样时尚。"}
{"content": "类型#裙*材质#针织*颜色#纯色*风格#复古*风格#文艺*风格#简约*图案#格子*图案#纯色*图案#复古*裙型#背带裙*裙长#连衣裙*裙领型#半高领", "summary": "这款BRAND针织两件套连衣裙，简约的纯色半高领针织上衣，修饰着颈部线，尽显优雅气质。同时搭配叠穿起一条背带式的复古格纹裙，整体散发着一股怀旧的时髦魅力，很是文艺范。"}
{"content": "类型#上衣*风格#嘻哈*图案#卡通*图案#印花*图案#撞色*衣样式#卫衣*衣款式#连帽", "summary": "嘻哈玩转童年，随时<UNK>，没错，出街还是要靠卫衣来装酷哦！时尚个性的连帽设计，率性有范还防风保暖。还有胸前撞色的卡通印花设计，靓丽抢眼更富有趣味性，加上前幅大容量又时尚美观的袋鼠兜，简直就是孩子耍帅装酷必备的利器。"}
```

## 模型训练
执行脚本train.sh
```shell
sh -x train.sh
```

我在V100上需要4个小时ptuning。

## 模型推理
执行脚本evaluate.sh
```shell
sh -x evaluate.sh
```
