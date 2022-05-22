# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# *Ruby on Rails Tutorial* 笔记 (rails 6)

## 第一章

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
| views      | template of html (生成发送给浏览器到 HTML 代码)                                             |
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
控制器文件名 (命名规则：下划线命名/underline_case/蛇形命名法/snake_case)
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
| lib/         | : 模块？                                                                           |
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
|                          |                                                                                                            |

