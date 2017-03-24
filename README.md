# vim-galore 中文翻译

[![掘金翻译计划](https://rawgit.com/aleen42/badges/master/src/juejin_translation.svg)](https://github.com/xitu/gold-miner/)

> Vim from zero to hero - Vim 从入门到精通

- 原文地址：https://github.com/mhinz/vim-galore
- 原文作者：Marco Hinz

## [简介](#简介-1)

- [什么是Vim](#什么是-vim)
- [Vim 哲学](#vim-哲学)
- [起步](#起步)
- [精简的vimrc](#精简的-vimrc)
- [我正在使用的是什么样的vim](#我正在使用什么样的-vim)
- [备忘录](#备忘录)

## [基础](#基础-1)

- [缓冲区, 窗口, 标签?](#缓冲区-窗口-标签)
- [当前缓冲区, 加载缓冲区, 缓冲区列表,命名缓冲区?](#已激活-已载入-已列出-已命名-缓冲区)
- [参数列表](#参数列表)
- [按键映射](#按键映射)
- [Mapleader?](#mapleader)
- [寄存器?](#registers)
- [标注?](#marks)
- [光标移动? 动作和操作符?文本对象?](#motions-operators-text-objects)
- [自动命令?](#autocmds)
- [改变表? 跳转表?](#changelist-jumplist)
- [Quickfix and 位置列表?](#quickfix-and-location-lists)
- [配色方案?](#colorschemes)
- [折叠?](#folding)
- [会话?](#sessions)
- [局部化?](#locality)

## [用法](#usage-1)

- [获取离线帮助](#getting-help-offline)
- [获取离线帮助(可选择的)](#getting-help-offline-alternative)
- [获取在线帮助](#getting-help-online)
- [执行自动命令](#执行自动命令)
  - [用户自定义事件](#用户自定义事件)
  - [内部自带事件](#内部自带事件)
- [剪贴板](#clipboard)
  - [剪贴板使用 (Windows, OSX)](#clipboard-usage-windows-osx)
  - [剪贴板使用 (Linux, BSD, ...)](#clipboard-usage-linux-bsd-)
- [打开文件时恢复光标位置](#restore-cursor-position-when-opening-file)
- [备份文件，交换文件，撤销文件以及viminfo文件的处理](#handling-backup-swap-undo-and-viminfo-files)
- [编辑远程文件](#editing-remote-files)
- [插件管理](#managing-plugins)
- [片段插入](#block-insert)
- [使用外部程序和过滤器](#running-external-programs-and-using-filters)
- [MatchIt](#matchit)

## [技巧](#tips-1)

- [聪明的使用n和N](#saner-behavior-of-n-and-n)
- [聪明的使用命令行历史](#saner-command-line-history)
- [聪明的使用CTRL-L](#saner-ctrl-l) 
- [禁用错误报警声音和图标](#禁用错误报警声音和图标)
- [快速移动当前行](#quickly-move-current-line)
- [快速添加空行](#quickly-add-empty-lines)
- [快速编辑自定义宏](#quickly-edit-your-macros)
- [快速跳转到源(头)文件](#quickly-jump-to-header-or-source-file)
- [在GUI中快速改变字体大小](#quickly-change-font-size-in-gui)
- [根据模式改变光标类型](#change-cursor-style-dependent-on-mode)
- [防止水平滑动的时候失去选择](#dont-lose-selection-when-shifting-sidewards)
- [重新载入保存文件](#reload-a-file-on-saving)
- [智能当前行](#smarter-cursorline)
- [更快的关键字补全](#faster-keyword-completion)

## [命令](#commands-1)

- [:global](#global) - 在所有匹配行执行命令
- [:normal and :execute](#normal-and-execute) - 脚本梦之队
- [:redir](#redir) - 重定向消息

## [调试](#debugging-1)

- [常规建议](#general-tips)
- [启动时刨视](#profiling-startup-time)
- [运行时刨视](#profiling-at-runtime)
- [详细模式](#verbosity)
- [vim脚本调试](#debugging-vim-scripts)
- [语法文件调试](#debugging-syntax-files)

## [杂项](#miscellaneous-1)

- [附加资源](#additional-resources)
- [Vim 发布](#vim-distributions)
- [标准插件](#standard-plugins)
- [将Control映射到CapsLock](#map-capslock-to-control)
- [复活节彩蛋](#easter-eggs)
- [为何使用hjkl](#why-hjkl-for-navigation)

## [奇事](#quirks-1)

- [编辑小文件很慢](#editing-small-files-is-slow)
- [编辑打文件很慢](#editing-huge-files-is-slow)
- [新行用于NUL](#newline-used-for-nul)
- [相同部分粘贴 (要不为什么我总要设置‘粘贴’?)](#bracketed-paste-or-why-do-i-have-to-set-paste-all-the-time)
- [在终端使用Esc延时](#delays-when-using-escape-key-in-terminal)

## [配色主题](#list-of-colorschemes-1)

## [插件列表](content/plugins.md)

## [Neovim](content/neovim.md)

---

# 简介

## 什么是 Vim？
[Vim](http://www.vim.org) 是一个历史悠久的文本编辑器,可以追溯到 [qed](https://en.wikipedia.org/wiki/QED_(text_editor)). [Bram
Moolenaar](https://en.wikipedia.org/wiki/Bram_Moolenaar) 于1991年发布初始版本.

该项目托管在 [vim.org](http://www.vim.org/index.php).

获取Vim: 使用你最喜欢的包管理器安装,或者在vim.org上[下载](http://www.vim.org/download.php) .

讨论使用相关问题最好使用 [vim_use](https://groups.google.com/forum/#!forum/vim_use) 邮件列表或者使用IRC ([Freenode](https://freenode.net)) 的 `#vim` 频道。
欢迎加入我们的中文讨论群：[![QQ](https://img.shields.io/badge/QQ群-121056965-blue.svg)](https://jq.qq.com/?_wv=1027&k=43DB6SG)

项目在 [Github](https://github.com/vim/vim) 上开发, 项目讨论请订阅 [vim_dev](https://groups.google.com/forum/#!forum/vim_dev) 邮件列表.

通过阅读 [Why, oh WHY, do those #?@! nutheads use vi?](http://www.viemu.com/a-why-vi-vim.html) 来对Vim进行大致的了解.


## Vim 哲学

Vim 坚持着模式编辑的理念. 这意味着他提供了多种模式，并根据模式，同一按键有不同含义。你可以在 _普通模式_ 下浏览文件, 在 _插入模式_ 下插入文本, 在 _可视模式_ 下选择行, 在 _命令模式_ 下执行命令.
起初这听起来可能很复杂, 但是这有一个很大的优点: 不需要通过同时按住多个键来完成操作，而是通过连续地单次按键。越常用的操作，所需要的按键数量越少. 

“动作”和“操作符”是一个能在模式编辑中得到良好体现的概念。_操作符_开始一些行为, 例如：修改, 删除, 或者选择文本。之后你要用一个_动作_来指定需要操作的文本区域。比如，要改变括号内的文本, 需要执行`ci(` （读做 _change inner parentheses_）；删除整个段落的内容, 需要执行 `dap` （读做： _delete
around paragraph_）。

如果你能看见 Vim 老司机操作,你会发现他们使用 Vim 脚本语言就如同钢琴师操作自己的乐器一样。复杂的操作只需要几个按键就能完成。他们甚至不用刻意去想，因为这已经成为[肌肉记忆](https://en.wikipedia.org/wiki/Muscle_memory)了. 这减少[认识负荷](https://en.wikipedia.org/wiki/Cognitive_load)并帮助人们专注与实际任务。

## 起步

Vim 自带一个交互式的教程，内含你需要了解的最基础的信息，你可以通过终端运行以下命令打开教程：

```
$ vimtutor
```

不要因为这个看上去很无聊而跳过，按照此教程多练习。你以前用的 IDE 或者其他编辑器很少是有“模式”概念的，因此一开始你会很难适应模式切换。但是你 Vim 使用的越多，[肌肉记忆](https://en.wikipedia.org/wiki/Muscle_memory) 将越容易形成。

Vim 基于一个 [vi](https://en.wikipedia.org/wiki/Vi) 克隆， 叫做 [Stevie](https://en.wikipedia.org/wiki/Stevie_(text_editor))，支持两种运行模式:"compatible" 和 "nocompatible"。在兼容模式下运行 vim 意味着使用 vi 的默认设置，而不是 vim 的默认设置。只要你没有新建一个用户的 vimrc 或者使用 `vim -N` 命令启动 vim，那就是在兼容模式下运行 vim! 请大家不要在兼容模式下运行 vim。
下一步：

1. 创建你自己的 [vimrc](#精简的vimrc)。
2. 在第一周准备[备忘录](#cheatsheets)。
3. 通读[基础](#basics-1) 一节知道做什么是可能的。
4. 按需学习！vim 是学不完的。如果你遇到了任何问题，先去网上去找解决方案。你的问题可能早就被解决了。VIM 拥有大量的参考文档，知道如何去利用这些参考文档是有必要了：[获取离线帮助](#getting-help-offline)。
5. 浏览[附加资源](#additional-resources)。

最后一个建议：使用[插件](#managing-plugins)之前，请先掌握 vim 的基本操作。很多插件都只是对 vim 自带功能的封装。

## 精简的 vimrc

用户的 vimrc 配置文件可以放在 `~/.vimrc`，或者为了更好的分离放在 `~/.vim/vimrc`，后者更便于通过版本控制软件备份和同步整个配置，比方说github。

你可以在网上找到许多精简的 vimrc 配置文件, 我的版本可能并不是最简单的版本, 但是我的版本提供了一套我认为良好的，非常适合入门的设置.

最终你需要阅读完那些设置，然后自行决定需要使用哪些. :-)

精简的 vimrc 地址: [minimal-vimrc](contents/minimal-vimrc.vim)

如果你有兴趣, 这里是我（原作者）的 [vimrc](https://github.com/mhinz/dotfiles/blob/master/vim/vimrc).

**建议**：大多数插件作者都维护不止一个插件并且将他们的 vimrc 放在 Github 上展示(通常放在叫做 "vim-config" 或者 "dotfiles" 的仓库中)，所以当你发现你喜欢的插件时，去插件维护者的 Github 主页看看有没有这样的仓库。

## 我正在使用什么样的 Vim

使用 :version 命令将向你展示当前正在运行的 vim 的所有相关信息，包括它是如何编译的。

第一行告诉你这个二进制文件的编译时间和版本号，比如：7.4。接下来的一行呈现`Included patches: 1-1051`, 这是补丁版本包. 因此你 vim 确切的版本号是 7.4.1051。

另一行显示着一些像 `Tiny version without GUI` 或者 `Huge version with GUI` 的信息。很显然这些信息告诉你当前的 vim 是否支持 GUI，例如：从终端中运行 `gvim` 或者从终端模拟器中的 vim 内运行 `:gui` 命令。另一个重要的信息是 `Tiny` 和 `Huge`。Vim 的特性集区分被叫做 `tiny`，`small`，`normal`，`big` and `huge`，所有的都实现不同的功能子集.

`:version` 主要的输出内容是特性列表.`+clipboard` 意味这剪贴板功能被编译支持了, `-clipboard` 意味着剪贴板特性没有被编译支持.

一些功能特性需要编译支持才能正常工作。例如：为了让 `:prof` 工作, 你需要使用 `huge` 模式编译的 vim, 因为那种模式启用了 `+profile` 特性。

如果你的输出情况并不是那样，并且你是从包管理器安装 vim 的, 确保你安装了 `vim-x`，`vim-x11`，`vim-gtk`，`vim-gnome` 这些包或者相似的, 因为这些包通常都是 `huge` 模式编译的.

你也可以运行下面这段代码来测试 Vim 版本以及功能支持：

```viml
" Do something if running at least Vim 7.4.42 with +profile enabled.
if (v:version > 704 || v:version == 704 && has('patch42')) && has('profile')
  " do stuff
endif
```

相关帮助:

```
:h :version
:h feature-list
:h +feature-list
```

## 备忘录

为了避免版权问题, 我只贴出链接:

- http://people.csail.mit.edu/vgod/vim/vim-cheat-sheet-en.png
- https://cdn.shopify.com/s/files/1/0165/4168/files/preview.png
- http://www.nathael.org/Data/vi-vim-cheat-sheet.svg
- http://michael.peopleofhonoronly.com/vim/vim_cheat_sheet_for_programmers_screen.png
- http://www.rosipov.com/images/posts/vim-movement-commands-cheatsheet.png

或者在 vim 中快速打开备忘录：[vim-cheat40](https://github.com/lifepillar/vim-cheat40)。

# 基础

## 缓冲区，窗口，标签

Vim 是一个文本编辑器。每次文本都是作为**缓冲区**的一部分显示的。每一份文件都是在他们自己独有的缓冲区打开的，插件显示的内容也在它们自己的缓冲区中。

缓冲区有很多属性，比如这个缓冲区的内容是否可以修改，或者这个缓冲区是否和文件相关联，是否需要同步保存到磁盘上。

**窗口** 是缓冲区上一层的视窗. 如果你想同时查看几个文件或者查看同一文件的不同位置，那样你会需要窗口.

请别把他们叫做_分屏_. 你可以把一个窗口分割成两个, 但是这并没有让这两个窗口完全_分离_.

窗口可以水平或者竖直分割并且现有窗口的高度和宽度都是可以被调节设置的，因此，如果你需要多种窗口布局，请考虑使用标签。

**标签页** (标签) 是窗口的集合. 因此使用标签当你想使用多种窗口布局的时候.

简单的说, 如果你启动VIM的时候没有附带任何参数,你会得到一个包含着一个呈现一个缓冲区的窗口的标签.

顺带提一下, 缓冲区列表是全局可见的，你可以在任何标签中访问任何一个缓冲区.

## 已激活，已载入，已列出，已命名 缓冲区

用类似 `vim file1` 的命令启动 vim 。这个文件的内容将会被加载到缓冲区中，你现在有一个**已载入的缓冲区**。如果你在 vim 中保存这个文件，缓冲区内容将会被同步到磁盘上（写回文件中）。

由于这个缓冲区也在一个窗口上显示， 所以他也是一个**已激活的缓冲区**。如果你现在通过 `:e file2` 命令加载另一个文件，`file1` 将会变成一个**隐藏的缓冲区**，并且 `file2` 变成已激活缓冲区。

使用 `:ls` 我们能够列出所有可以列出的缓冲区。插件缓冲区和帮助缓冲区通常被标记为不可以列出的缓冲区，因为那并不是你经常需要在编辑器中编辑的常规文件。通过 `:ls!` 命令可以显示被放入缓冲区列表的和未被放入列表的缓冲区。

**未命名的缓冲区**是一种没有关联特定文件的缓冲区，这种缓冲区经常被插件使用。比如 `:enew` 将会创建一个无名临时缓冲区。添加一些文本然后使用 `:w /tmp/foo` 将他写入到磁盘，这样这个缓冲区就会变成一个**已命名的缓冲区**。

## 参数列表

[全局缓冲区列表](#buffers-windows-tabs)是 vim 的特性。在这之前的 vi 中，仅仅只有参数列表，参数列表在 vim 中依旧可以使用。

每一个通过 shell 命令传递给 vim 的文件名都被记录在一个参数列表中。可以有多个参数列表：默认情况下所有参数都被放在全局参数列表下，但是你可以使用 `:arglocal` 命令去创建一个新的本地窗口的参数列表。

使用 `:args` 命令可以列出当前参数。使用 `:next`，`:previous`，`:first`，`:last` 命令可以在切换在参数列表中的文件。通过使用 `:argadd`，`:argdelete` 或者 `:args` 等命令加上一个文件列表可以改变参数列表。

偏爱缓冲区列表还是参数列表完全是个人选择，我的印象中大多数人都是使用缓冲区列表的。

然而参数列表在有些情况下被大量使用：批处理
使用 `:argdo`！ 一个简单的重构例子：

```vim
:args **/*.[ch]
:argdo %s/foo/bar/ge | update
```

这条命令将替换掉当前目录下以及当前目录的子目录中所有的C源文件和头文件中的"foo"，并用"bar"代替。

相关帮助：`:h argument-list`

## 按键映射

使用 `:map` 命令家族你可以定义属于你自己的快捷键。该家族的每一个命令都限定在特定的模式下。从技术上来说 vim 自带高达12中模式，其中6种可以被映射。另外一些命令作用于多种模式：

| Recursive | Non-recursive | Modes                            |
|-----------|---------------|----------------------------------|
| `:map`    | `:noremap`    | normal, visual, operator-pending |
| `:nmap`   | `:nnoremap`   | normal                           |
| `:xmap`   | `:xnoremap`   | visual                           |
| `:cmap`   | `:cnoremap`   | command-line                     |
| `:omap`   | `:onoremap`   | operator-pending                 |
| `:imap`   | `:inoremap`   | insert                           |

例如：这个自定义的快捷键只在普通模式下工作，

```viml
:nmap <space> :echo "foo"<cr>
```

使用 `:nunmap <space>` 可以取消这个映射。

对于更少数，不常见的模式（或者他们的组合），查看 `:h map-modes`。

到现在为止还好，对新手而言有一个问题会困扰他们：`:nmap` 是**递归执行**的！结果是，右边执行可能的映射。

你自定义了一个简单的映射去输出"Foo"：

```vim
:nmap b :echo "Foo"<cr>
```

但是如果你想要映射 `b` （回退一个单词）的默认功能到一个键上呢？

```vim
:nmap a b
```

如果你敲击<kbd>a</kbd>，我们期望着光标回退到上一个单词，但是实际情况是“Foo”被输出到命令行里！因为在右边，`b` 已经被映射到别的行为上了，换句话说就是 `:echo "Foo"<cr>`。

解决此问题的正确方法是使用一种_非递归_的映射代替：

```vim
:nnoremap a b
```

经验法则: 除非递归是必须的，否则总是使用非递归映射.

通过不给一个右值来检查你的映射. 比如`:nmap` 显示所以普通模式下的映射， `:nmap <leader>` 显示所有以 `<leader>` 键开头的普通模式下的映射。

如果你想禁止用标准映射，把他们映射到特殊字符 `<nop>` 上， 例如：`:noremap <left> <nop>`。

相关帮助：

    :h key-notation
    :h mapping
    :h 05.3

### 加入我们

可以协助我们核对翻译，或者从[章节列表](CONTRIBUTING.md)中认领章节进行翻译。

### 致谢：

- [Linux 中国翻译组](https://github.com/LCTT)
- [掘金翻译计划](https://github.com/xitu/gold-miner)
