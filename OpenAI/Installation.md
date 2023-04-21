## 直接运行 (Windows, Linux or MacOS)

- 下载项目
```
git clone https://github.com/binary-husky/chatgpt_academic.git
cd chatgpt_academic
```

- 复制config文件
我们建议将`config.py`复制为`config_private.py`并将后者用作个性化配置文件以避免`config.py`中的变更影响你的使用或不小心将包含你的OpenAI API KEY的`config.py`提交至本项目。
```
cp config.py config_private.py
```

- 填写必要参数
在`config_private.py`中，配置 海外Proxy 和 OpenAI API KEY
```
1. 如果你在国内，需要设置海外代理才能够使用 OpenAI API，你可以通过 config.py 文件来进行设置。
2. 配置 OpenAI API KEY。你需要在 OpenAI 官网上注册并获取 API KEY。一旦你拿到了 API KEY，在 config.py 文件里配置好即可。
```

- 安装依赖
```
python -m pip install -r requirements.txt
```

或者，如果你希望使用`conda`
```
conda create -n gptac 'gradio>=3.23' requests
conda activate gptac
python3 -m pip install mdtex2html
```

- 运行
```
python main.py
```

- 测试实验性功能
```
- 测试C++项目头文件分析
    input区域 输入 `./crazy_functions/test_project/cpp/libJPG` ， 然后点击 "[实验] 解析整个C++项目（input输入项目根路径）"
- 测试给Latex项目写摘要
    input区域 输入 `./crazy_functions/test_project/latex/attention` ， 然后点击 "[实验] 读tex论文写摘要（input输入项目根路径）"
- 测试Python项目分析
    input区域 输入 `./crazy_functions/test_project/python/dqn` ， 然后点击 "[实验] 解析整个py项目（input输入项目根路径）"
- 测试自我代码解读
    点击 "[实验] 请解析并解构此项目本身"
- 测试实验功能模板函数（要求gpt回答历史上的今天发生了什么），您可以根据此函数为模板，实现更复杂的功能
    点击 "[实验] 实验功能函数模板"
```

与代理网络有关的issue（网络超时、代理不起作用）汇总到 [#1](https://github.com/binary-husky/chatgpt_academic/issues/1)

```
# 改为True应用代理
USE_PROXY = False
if USE_PROXY:

    # 填写格式是 [协议]://  [地址] :[端口] ，
    # 例如    "socks5h://localhost:11284"
    # [协议] 常见协议无非socks5h/http，例如 v2***[v2ray] 和 s**[ssr] 的默认本地协议是socks5h，cl**h[clash] 的默认本地协议是http
    # [地址] 懂的都懂，不懂就填localhost或者127.0.0.1肯定错不了（localhost意思是代理软件安装在本机上）
    # [端口] 在代理软件的设置里，不同的代理软件界面不一样，但端口号都应该在最显眼的位置上

    # 代理网络的地址，打开你的科学上网软件查看代理的协议(socks5/http)、地址(localhost)和端口(11284)
    proxies = { "http": "socks5h://localhost:11284", "https": "socks5h://localhost:11284", }
    print('网络代理状态：运行。')
else:
    proxies = None
    print('网络代理状态：未配置。无代理状态下很可能无法访问。')
```

以上是master中，有关代理部分的注释。

>目前实测：
>- Macbook Pro with Surge可用
>- 