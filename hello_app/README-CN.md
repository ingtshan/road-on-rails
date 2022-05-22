# *Ruby on Rails Tutorial* 笔记 (rails 6)

## 第一章
- 跳过 1.1 Cloud9 Web IDE
- 跳过 1.3 Git 版本控制 和 Github
- 跳过 1.4 部署, heroku, postgresql, sqlit3
- 跳过 1.6 

rails 环境 (安装了 ruby 2.7.5 的情况下)
```shell
gem install rails -v 6.0.2.1 

rails -v
```
获得一个 hello_app web 应用
```shell
cd ~/road-on-rails
rails _6.0.2.1_ new hello_app
```
包含
- rails 标准的目录结构和文件

Gemfile 保持和 [rails_tutorial_6th_edition_gemfiles](https://github.com/learnenough/rails_tutorial_6th_edition_gemfiles) 一致
```shell
cd hello_app
bundle update
bundle install
```
运行 web 应用
```shell
bundle exec bin/rails server
```

MVC 结构模式 运用在 rails 上
| MVC        | Rails                                                                                       |
|:-----------|:--------------------------------------------------------------------------------------------|
| models     | Ruby object  (数据模型的实现，同时负责数据库的操作) 如 rails ActiveRecord 类                |
| views      | template of html (生成发送给浏览器的 HTML 代码)                                             |
| controller | Ruby object (控制器，负责处理服务器接收到请求，如 决定后台做什么业务处理，返回什么样的页面) |

简单的网站运行过程(rails app 层面)

浏览器==(请求)==>服务器->控制器->视图

浏览器<==(响应)==服务器<-(html)-视图

浏览器==(请求)==>服务器->控制器->模型->数据库->模型->控制器->视图

浏览器<==(响应)==服务器<-(html)-视图

Hello, world! 的过程

browser visit http://localhost:3000 -> Server -(by router)-> ApplicationController -> #hello action/method -> run your ruby code

浏览器访问 http://localhost:3000 -> 服务器 -(路由)-> 对应的控制器 -> #hello 动作/方法 -> 运行ruby代码片段 

```ruby
# 控制器文件名 (命名规则：下划线命名/underline_case/蛇形命名法/snake_case)
# in app/controller/application_controller.rb

# 控制器类名 (命名规则: 帕斯卡命名/PascalCase/大驼峰命名/BigCamelCase)
class ApplicationController < ActionController::Base
  def hello
    render html: 'Hello, world!'
  end
end

# in config/router.rb
Rails.application.routes.draw do
  root 'application#hello' # rails 结构 控制器名称#动作名 name_of_controller#name_of_action
end
```


### rails app 目录一览
hello_app/.

| 路径         | 描述                                                                               |
|:-------------|:-----------------------------------------------------------------------------------|
| app/         | : web 应用核心代码 (models, views, controller, helpers)                            |
| app/assets   | : web 应用的资源文件 (CSS, image)                                                  |
| bin/         | : 二进制可执行文件                                                                 |
| config/      | : web 应用的配置文件                                                               |
| db/          | : 数据库文件                                                                       |
| doc/         | : web 应用的描述文档                                                               |
| lib/         | : 其他模块，第三方代码                                                                    |
| log/         | : web 应用运行日志                                                                 |
| public/      | : web 应用对浏览器(无条件)公开的数据，如 错误页面                                  |
| bin/rails    | : rails 程序，generate(代码生成器)，console(控制台), server(本地运行该web应用服务) |
| test/        | : 测试                                                                             |
| tmp/         | : 临时文件                                                                         |
| Gemfile      | : web 应用依赖关系描述                                                             |
| Gemfile.lock | : 依赖的版本信息                                                                   |

### 名词解释
| 名词                     | 解释                                                                                                       |
|:-------------------------|:-----------------------------------------------------------------------------------------------------------|
| ruby                     | : 一种编程语言，红宝石                                                                                     |
| gem, RubyGems            | : ruby 的包管理器                                                                                          |
| ruby on rails, rails     | : 用 ruby 编写的 web 应用框架 (A web-app framework)                                                        |
| framework                | : 架构，框架，脚手架。比较抽象宽泛的概念，笔者暂时无法给出精确定义                                         |
| bundle, bundler          | : 打包, 打包器, `bundle install`, `bundle exec`, [为 Ruby 项目提供一致的运行环境](https://www.bundler.cn/) |
| puma                     | : https://github.com/puma/puma                                                                             |
| MVC architecture pattern |                                                                                                            |
| models                   |                                                                                                            |
| views                    |                                                                                                            |
| controllers              |                                                                                                            |
| actions                  |                                                                                                            |
| dynamic sites            | : 动态网站                                                                                                 |
| request                  | : 请求                                                                                                     |
| respone                  | : 响应                                                                                                     |
| browser                  | : 浏览器                                                                                                   |
| render                   | : 渲染，输入-(规则)->输出，的实际运算过程，而渲染过程输出的一般是“视觉”的材料                              |
|                          | : 如 生成 HTML 的过程 (因为浏览器可以直接由 HTML 绘制出页面了)                                             |
| router                   | : 路由, "路径"信息->路由表->找到资源 的过程                                                                |
| command-line command     | : 命令行指令                                                                                               |

### 总结

ruby on rails 是一个用 ruby 编写的 web 应用框架，我们可以用它快速搭建一个可以运行和部署的 web 应用，并且在它的规范下进行业务逻辑的实现，从而一步步打造自己的 web 产品。

ruby on rails 自带有 命令行工具 bin/rails 帮助我们生成 rails 的“对象” 和 运行 web 应用。

ruby on rails 提供了一个简洁明了的 web 项目结构，我们从 MVC 模式下“看到了” web 应用在比较靠近业务逻辑层面的运行过程，并自己编写了一个 控制器动作，配置在路由表上，从而使得浏览器可以访问并得到我们预期的页面(Hello, world!)

自此我们从 0 实现了一个 hello_app，学会了以下一些命令和作用

```shell
gem install rails -v x.x.x.x
rails -v
rails _x.x.x.x_ new hello_app
bundle update
bundle install
bundle exec 
rains server
```

体会到 rails 利用命名规范猜测我们的意图自动化处理了某些事情

比如 router.rb 里 `application#hello` (只写核心信息) 可以找到 `application_controller.rb` 里 `ApplicationController` 的 `hello` 方法

命名的策略有
- ruby 文件名：下划线小写命名，underline_case
- ruby 类名：单词首字母大写紧凑，BigCamelCase
- ruby 方法名, 变量名：下划线小写命名, snake_case

(前端常见的命名还剩下一个 驼峰 camalCase 没见到)
