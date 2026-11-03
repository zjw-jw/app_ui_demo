# app_ui_demo

#### 介绍

appium app自动化测试框架

#### 软件架构

python + pytest + appium + parametrize + json + log + allure POM模式三层分离app自动化测试框架

#### 目录结构

    |--app自动化测试框架 # 主目录
       ├─ base # 封装等待元素，页面元素的基本操作方法
       ├─ common # 常用工具
         └─ render_template.py  # 渲染配置文件
         └─ template.conf  # 模板文件
         └─ env.json  # 使用的环境数据
         └─ read_json.py  # 封装测试case数据读取
         └─ utils  # 获取/退出 driver 工具
       ├─ config # 配置文件封装与读取
         └─ config.ini  # 配置文件
         └─ confRead.py   # 封装读取配置文件，可修改代码中的配置文件名字
       ├─ data # 测试数据相关文件
         └─ xxx.json # 测试数据
         └─ xxx.json # 测试数据
       ├─ log # 运行时日志
         └─ xxx.log # 日志
       ├─ page # 封装元素获取、操作、业务执行
         └─ xxx.py # 模块封装文件
       ├─ report # allure测试报告	
       ├─ scripts # 测试脚本调用
         └─ conftest.py # 运行用例前置、后置配置、配置全局日志、自动生成allure测试报告
         └─ test_xxx.py # 运行的用例
       ├─ tmp # allure运行时数据、截图等
         └─ xxx.json # 运行的数据
         └─ xxx.png # 运行的截图
         └─ xxx.txt # 运行的数据
       ├─ global_config.py	  # 公用log日志封装
       ├─ pytest.ini  	# pytest配置	  
       └─ README.md

#### 使用说明

根据需要,根据模版生成config配置文件,可直接修改confRead.py 中 config.ini 运行其它测试系统配置

```
cd cd .\common\
python render_template.py template.conf test_env.json ../config/config.ini
```

运行脚本 （快手app软件进入直播间 发送消息demo）

```
pytest -v -m 'smoke'
```

你准备什么：第一步

通过 Appium Inspector 复制你要测的页面元素 XML 结构树。

复制你项目里 base_page.py 的核心方法（让 AI 知道你有什么武器）。

给 AI 的 Prompt（可以喂给你的本地 Qwen 或 GPT）：

“你是一个资深 Python + Appium 自动化测试专家。现在我提供给你一段 App 的页面元素结构树（XML），以及我现有框架的 BasePage 基础操作方法。
请帮我生成一个 POM 模式下的 Page 类代码。要求：

继承我的 BasePage。

提取出‘账号输入框’、‘密码输入框’和‘登录按钮’的定位器（优先用 ID，备用 XPath）。

封装一个 login(username, password) 方法，包含输入和点击操作，并加上适当的显式等待。

【我的 BasePage 代码】：[粘贴你的 base_page.py]
【页面元素结构树】：[粘贴你复制的 XML]”

效果：AI 会直接吐出 login_page.py 的代码。你只需复制粘贴到你的项目里，稍微改改就能用。



第二步：

给 AI 的 Prompt：

“基于上面生成的 login_page.py 代码，请帮我写一个 pytest 测试用例文件，以及配套的 JSON 测试数据文件。
要求：

用例文件放在 scripts/test_login.py，使用 @pytest.mark.parametrize 读取 JSON 数据。

JSON 数据里包含 5 条用例：正常登录、账号为空、密码为空、账号不存在、密码错误。

JSON 格式包含：case_name, username, password, expect_toast。”

效果：AI 会直接给你一份完美的 test_login.py 和 login_data.json，你直接丢进框架运行。


第三步：

给 AI 的 Prompt：

“基于上面生成的 login_page.py 代码，请帮我写一个 pytest 测试用例文件，以及配套的 JSON 测试数据文件。
要求：

用例文件放在 scripts/test_login.py，使用 @pytest.mark.parametrize 读取 JSON 数据。

JSON 数据里包含 5 条用例：正常登录、账号为空、密码为空、账号不存在、密码错误。

JSON 格式包含：case_name, username, password, expect_toast。”

效果：AI 会直接给你一份完美的 test_login.py 和 login_data.json，你直接丢进框架运行。