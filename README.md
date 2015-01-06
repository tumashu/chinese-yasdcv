# chinese-yasdcv - Yet another sdcv emacs frontend (sdcv: Console version of StarDict program)

*Author:* Feng Shu <tumashu@gmail.com><br>
*Version:* 0.0.1<br>

# 简介 #
Chinese-yasdcv 是 sdcv 的一个emacs前端，其工作原理是：

1. 调用 sdcv 程序，将翻译得到的结果定向到 *Stardict Output* buffer。
2. 调用对应的elisp函数，清理上述 buffer 中的内容，并将其转化为 org-mode 格式。
3. 弹出一个窗口显示上述buffer内容。

注：sdcv 是 StarDict 的 Console 版本，yasdcv 表示：Yet Another Sdcv。

# 安装 #
将这个文件放到任意一个emacs搜索目录之下，然后在~/.emacs中添加：

```lisp
(require 'chinese-yasdcv)
```

另外, 也可以使用 `package-install` 安装，首先添加 melpa 源：

```lisp
(add-to-list 'package-archives
             '("melpa" . "http://melpa.org/packages/") t)
```

然后运行命令：

M-x package-install RET chinese-yasdcv RET

最后在 emacs 配置文件中添加如下代码。

```lisp
(require 'chinese-yasdcv)
```
# 配置 #

1. 设置 `yasdcv-sdcv-command` (具体细节见变量说明)
2. 设置 `yasdcv-sdcv-dicts`   (具体细节见变量说明)

# 使用 #

将光标移动到需要查询的单词上（点词翻译），然后运行命令 `yasdcv-translate-at-point`，
或者选择某一个单词（划词翻译），然后运行上述命令。

查询中文时，划词翻译可以正常使用，但由于 emacs 本身的限制，点词翻译往往不能正常工作。
这时，就需要用户通过变量 `yasdcv-chinese-wordsplit-command` 来设置外部的分词程序。
Chinese-yasdcv 会提取一个范围较大的字符串，通过分词程序将其分成多个词语，然后再查询
光标处字符对应的词语。


---
Converted from `chinese-yasdcv.el` by [*el2markdown*](https://github.com/Lindydancer/el2markdown).
