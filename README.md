# 游子产品团队 PHP 程序编码规范

本 PHP 程序编写规范从[FIG 小组推荐规范](https://github.com/php-fig/fig-standards)和[其汉化版本](https://github.com/hfcorriez/fig-standards)衍生而来，用于规范和约束团队在针对 PHP 5.3.x 以上应用框架中的协作开发。

## 几点约定

* 凡以 Laravel 和 ZendFramework 为主应用框架的核心项目，请严格遵守本规范。
* 凡以 CodeIgniter 为主应用框架的核心项目，请暂时遵守[游子 CodeIgniter 应用开发规范](https://github.com/yoozi/styleguide)。
* 请尽量选用遵守 PSR 规范的第三方开源组件/类库。
* 由于 Laravel 3 未能完全遵守 PSR 规范，故团队暂不对指定项目的编码风格进行强制性检测。
* 本规范亦可作为其他将产品核心应用框架从 CodeIgniter 迁移至 Laravel 的团队参考。

## 规范列表

* [PSR-0 自动加载器](https://github.com/yoozi/fig-standards/blob/zh_CN/接受/PSR-0.md)
* [PSR-1 基本代码规范](https://github.com/yoozi/fig-standards/blob/zh_CN/接受/PSR-1-basic-coding-standard.md)
* [PSR-2 代码样式规范](https://github.com/yoozi/fig-standards/blob/zh_CN/接受/PSR-2-coding-style-guide.md) 
* 暂不对 PSR-3 做强制性要求。

## 代码编辑器

请不要使用 Windows 自带的记事本（Notepad）编辑项目文件。团队推荐如下编辑器：

* 使用 Sublime Text 2 作为日常开发编辑器。我们为开发人员准备了 ST2 的正版序列号，请邮件至 support@yoozi.cn 索要序列号。
* 使用 Vim 作为 Linux 环境下的文本编辑器。对 Vim 不熟悉或欠熟悉的同学，请前往 OpenVim 网站进行学习。

鉴于团队的所有全职开发人员、部分高级技术顾问将会采用 Mac OS X 作为日常开发环境，我们还推荐其使用 Panic Coda 作为 Mac 下备选 IDE。

## 联系我们

support@yoozi.cn