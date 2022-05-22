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
| 名词                 | 解释                                                                                                       |
|:---------------------|:-----------------------------------------------------------------------------------------------------------|
| ruby                 | : 一种编程语言，红宝石                                                                                     |
| gem, RubyGems        | : ruby 的包管理器                                                                                          |
| ruby on rails, rails | : 用 ruby 编写的 web 应用框架 (A web-app framework)                                                        |
| framework            | : 架构，框架，脚手架。比较抽象宽泛的概念，笔者暂时无法给出精确定义                                         |
| bundle, bundler      | : 打包, 打包器, `bundle install`, `bundle exec`, [为 Ruby 项目提供一致的运行环境](https://www.bundler.cn/) |
