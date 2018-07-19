# 版本

<p align="center">
	<a href="https://gitmoji.carloscuesta.me">
		<img src="https://img.shields.io/badge/gitmoji-%20😜%20😍-FFDD67.svg?style=flat-square"
			 alt="Gitmoji">
	</a>
</p>
> 关于版本控制提交的一些总结

## 版本提交

|序号|名称|说明|
|---------|:---------|:---------|
|1|feat|新功能（feature）|
|2|chore|构建过程或辅助工具的变动|
|3|fix|修补bug|
|4|docs|文档（documentation）|
|5|refactor|重构（即不是新增功能，也不是修改bug的代码变动）|
|6|test|增加测试|
|7|style|格式（不影响代码运行的变动）|
|8|perf(**不建议再使用**)|提升性能的代码改动|
|9|revert(**不建议再使用**)|撤销以前的commit|
|10|ci(**不建议再使用**)|持续集成|
|11|build(**不建议再使用**)|构建程序|
|12|continue(**不建议再使用**)|继续开发某个功能|

## 格式

+ 每次提交，Commit message 都包括三个部分：header，body 和 footer。

+ Header部分只有一行，包括三个字段：type（必需）、scope（可选）和subject（必需）。

+ Body 部分是对本次 commit 的详细描述，可以分成多行。

+ Footer 部分只用于不兼容变动和关闭 Issue
  + 不兼容变动
    + 如果当前代码与上一个版本不兼容，则 Footer 部分以 BREAKING CHANGE开头，后面是对变动的描述、以及变动理由和迁移方法。
  + 关闭 Issue
    + 如果当前 commit 针对某个 issue，那么可以在 Footer 部分关闭这个 issue 。

```shell
<type>[必须](<scope>)[可选]: <subject>[可选]
<BLANK LINE>[有 body 须添加]
<body>[可选]
<BLANK LINE>[有 footer 须添加]
<footer>[可选]
```

## 示例

```shell
# Bug修复
fix(Promise function): fix Promise's function
# 空行
[Bug #2873942]

# 撤销
revert: feat: add new func...
# 空行
Description......

# 新功能
feat(userManagement): develop user management

# 更新文档
docs(userManagement): update userManagement's doc

# Revert
还有一种特殊情况，如果当前 commit 用于撤销以前的 commit，则必须以revert:开头，后面跟着被撤销 Commit 的 Header。
revert: feat(pencil): add 'graphiteWidth' option
This reverts commit 667ecc1654a317a13331b17617d973392f415f02.
Body部分的格式是固定的，必须写成This reverts commit &lt;hash>.，其中的hash是被撤销 commit 的 SHA 标识符。

# 关闭 Issue
如果当前 commit 针对某个issue，那么可以在 Footer 部分关闭这个 issue 。
Closes #234

```

### git commit emoji 指南

emoji                                   | emoji 代码                   | commit 说明
:--------                               | :--------                    | :--------
:art: (调色板)                          | `:art:`                      | 改进代码结构/代码格式
:zap: (闪电)<br>:racehorse: (赛马)                            | `:zap:`<br>`:racehorse:`                      | 提升性能
:fire: (火焰)                           | `:fire:`                     | 移除代码或文件
:bug: (bug)                             | `:bug:`                      | 修复 bug
:ambulance: (急救车)                    | `:ambulance:`                | 重要补丁
:sparkles: (火花)                       | `:sparkles:`                 | 引入新功能
:memo: (备忘录)                         | `:memo:`                     | 撰写文档
:rocket: (火箭)                         | `:rocket:`                   | 部署功能
:lipstick: (口红)                       | `:lipstick:`                 | 更新 UI 和样式文件
:tada: (庆祝)                           | `:tada:`                     | 初次提交
:white_check_mark: (白色复选框)         | `:white_check_mark:`         | 增加测试
:lock: (锁)                             | `:lock:`                     | 修复安全问题
:apple: (苹果)                          | `:apple:`                    | 修复 macOS 下的问题
:penguin: (企鹅)                        | `:penguin:`                  | 修复 Linux 下的问题
:checkered_flag: (旗帜)                 | `:checked_flag:`             | 修复 Windows 下的问题
:bookmark: (书签)                       | `:bookmark:`                 | 发行/版本标签
:rotating_light: (警车灯)               | `:rotating_light:`           | 移除 linter 警告
:construction: (施工)                   | `:construction:`               | 工作进行中
:green_heart: (绿心)                    | `:green_heart:`              | 修复 CI 构建问题
:arrow_down: (下降箭头)                 | `:arrow_down:`               | 降级依赖
:arrow_up: (上升箭头)                   | `:arrow_up:`                 | 升级依赖
:construction_worker: (工人)            | `:construction_worker:`      | 添加 CI 构建系统
:chart_with_upwards_trend: (上升趋势图) | `:chart_with_upwards_trend:` | 添加分析或跟踪代码
:hammer: (锤子)                         | `:hammer:`                   | 重大重构
:heavy_minus_sign: (减号)               | `:heavy_minus_sign:`         | 减少一个依赖
:whale: (鲸鱼)                          | `:whale:`                    | Docker 相关工作
:heavy_plus_sign: (加号)                | `:heavy_plus_sign:`          | 增加一个依赖
:wrench: (扳手)                         | `:wrench:`                   | 修改配置文件
:globe_with_meridians: (地球)           | `:globe_with_meridians:`     | 国际化与本地化
:pencil2: (铅笔)                        | `:pencil2:`                  | 修复 typo

## git commit emoji 使用

```sh
git commit -m ":tada: Initialize Repo"
```

## 语义化版本

对于一个给定的版本号 *MAJOR.MINOR.PATCH (主、次、补丁)*，其变化的规律是：

MAJOR version (主版本) 会在 API 发生不可向下兼容的改变时增大。

MINOR version (次版本) 会在有向下兼容的新功能加入时增大。

PATCH version (补丁版本) 会在bug以向下兼容的方式被修复时增大。

我们还可以根据预发布、构建元数据 (build metadata) 的实际需求，在 MAJOR.MINOR.PATCH 格式之上扩展出额外的标记。

## 示例

```shell
V1.0.1
V0.1.1-alpha1
```
