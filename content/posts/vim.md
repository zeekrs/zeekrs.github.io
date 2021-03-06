+++
title="Vim学习笔记"
date=2022-02-20

[taxonomies]
categories = ["editor"]
tags = ["vim"]
[extra]
toc = true
comments = false
+++

> 本笔记记录一些 vim 的学习过程 主要用于熟练掌握 vim
> 基础章节来自慕课网的视频教程 [《玩转 Vim 从放弃到爱不释手》](https://www.imooc.com/learn/1129)

## 初识 Vim 想说爱你不容易 {#basic}

#### 1. vim 的基础操作

普通模式进入插入模式的基本操作

| 操作符 | 助记符      | 作用                   |
| ------ | ----------- | ---------------------- |
| i      | insert      | 从光标前插入           |
| I      | insert      | 从行前插入             |
| a      | append      | 从光标后插入           |
| A      | append      | 从行后出入             |
| o      | open a line | 从光标下方插入新的一行 |
| O      | open a line | 从光标上方插入新的一行 |

从插入模式回到普通模式 Esc

普通模式下 按 `:` 进入命令模式

命令模式下的基本操作

| 操作符 | 助记符        | 作用       |
| ------ | ------------- | ---------- |
| w      | write         | 保存       |
| q      | quit          | 退出       |
| wq     | save and quit | 保存并退出 |

---

#### 2. Vim,为什么你有这么多模式

- 普通模式

  - 普通模式下可以进行各种移动呵命令操作
  - 大部分情况下是制作浏览而不是在编辑

- 插入模式

  - 插入模式和大部分文编编辑器一致 主要用于编辑文本

- 命令模式
  - 命令模式下 可以执行 vim 命令
  - 比如 :sp(split) 竖分屏 :vs(vertical split) 横分屏
  - 使用:% s/foo/bar/g 进行全局替换
- 可视化模式
  - 普通模式下使用 v 进入 visual 选择
  - 使用 V 选择行
  - 使用 ctrl + v 进行块选择

---

#### 3. Vim,插入模式小技巧

- ctrl + h 删除上一个字符
- ctrl + w 删除上一个单词
- ctrl + u 删除当前行
- ctrl + c 代替 Esc 回到普通模式
- gi 从普通模式到上一次插入的位置

---

#### 4. Vim,快速移动大法

| 操作符   | 助记符    | 作用                                                  |
| -------- | --------- | ----------------------------------------------------- |
| h        | -         | 左移                                                  |
| j        | -         | 下移                                                  |
| k        | -         | 上移                                                  |
| l        | -         | 右移                                                  |
| w        | word      | 移动到下一个单词开头                                  |
| W        | word      | 移动到下一个单词开头(已空白符分隔)                    |
| e        | end word  | 移动到下一个单词的结尾                                |
| E        | end word  | 移动到下一个单词的结尾(已空包符分隔)                  |
| b        | back word | 移动到上一个单词的开头                                |
| B        | back word | 移动到上一个单词的开头(已空白符分隔)                  |
| f{char}  | find      | 移动到{char}字符 (;搜索下一个 ,搜索上一个)            |
| F{char}  | find      | 反向搜索,同上                                         |
| t{char}  | until     | 移动到{char}字符的前一个字符(;搜索下一个 ,搜索上一个) |
| T{char}  | until     | 方向搜索,同上                                         |
| 0        | -         | 移动到行首                                            |
| ^        | -         | 移动到行首(不包含空白字符)                            |
| $        | -         | 移动到行尾                                            |
| g\_      | -         | 移动到行尾(不包含空白字符)                            |
| {}       | -         | 在段落间进行移动                                      |
| gg       | -         | 移动到文件开头                                        |
| G        | -         | 移动到文件结尾                                        |
| ctrl + o | old       | 移动到上一次光标的位置                                |
| ctrl + u | upward    | 向上翻页                                              |
| ctrl + f | forward   | 向下翻页                                              |
| zz       | -         | 把当前光标放到屏幕中间                                |

---

#### 5. Vim,快速增删改查

| 操作符 | 助记符     | 作用                                                        |
| ------ | ---------- | ----------------------------------------------------------- |
| x      | cut        | 删除一个字符                                                |
| d      | delete     | 删除(`dw` `diw` `dd` `dt{char}` `d$` `d0`)                  |
| r      | replace    | 替换当前光标下的字符                                        |
| R      | replace    | 替换当前光标下的字符,直到退出输入模式                       |
| s      | substitute | 删除当前字符并进入插入模式                                  |
| S      | substitute | 删除一整行并进入插入模式                                    |
| c      | change     | 类似 d 的使用方式,删除后进入插入模式                        |
| /      | -          | 搜索输入的字符(`n`移动到搜索的上一个,`N`移动到搜索的下一个) |
| #      | -          | 匹配光标上的单词,移动到上一个                               |
| \*     | -          | 匹配光标上的单词,移动到下一个                               |

---

#### 6. Vim,如何搜索替换

` :[range] s[substitute]/{pattern}/{string}/[flags]`

`range` 表示范围 比如:10,20 表示 10-20 行 %表示全部  
`pattern` 表示要替换的模式 正则表达式  
`string` 表示替换后的文本  
`flags`表示执行的方式 `g`表示全局范围内执行 `c`表示确认 可以确认或者这拒绝 `n`报告匹配的次数而不进行替换

---

#### 7. Vim,多文件操作

- Buffer  
  打开的文件在内存中的缓冲区
- Window  
  Buffer 可视化的分割区域
- Tab  
  可以组织窗口为一个工作区

> Buffer 的操作

| 操作符           | 助记符    | 作用                   |
| ---------------- | --------- | ---------------------- |
| :ls              | list show | 列出当前缓冲区列表     |
| :b{n}            | -         | 跳转到第 n 个缓冲区    |
| :bpre            | previous  | 跳转到上一个缓冲区     |
| :bnext           | next      | 跳转到下一个缓冲区     |
| :bfirst          | first     | 跳转到第一个缓冲区     |
| :blast           | last      | 跳转到最后一个缓冲区   |
| :b {buffer_name} | -         | 跳转到指定名称的缓冲区 |

> Window 的操作

| 操作符        | 助记符                | 作用             |
| ------------- | --------------------- | ---------------- |
| <Ctrl+w>s :sp | window split          | 水平分割         |
| <Ctrl+w>v :vs | window vertical split | 垂直分割         |
| <Ctrl+w>w     | window                | 在窗口间循环切换 |
| <Ctrl+w>h     | window                | 切换到左边的窗口 |
| <Ctrl+w>j     | window                | 切换到下边的窗口 |
| <Ctrl+w>k     | window                | 切换到上边的窗口 |
| <Ctrl+w>l     | window                | 切换到右边的窗口 |
| <Ctrl+w>H     | window                | 将窗口移动到左边 |
| <Ctrl+w>J     | window                | 将窗口移动到下边 |
| <Ctrl+w>K     | window                | 将窗口移动到上边 |
| <Ctrl+w>L     | window                | 将窗口移动到右边 |

> Tab 的操作(不常用)

| 操作符                | 作用                                |
| --------------------- | ----------------------------------- |
| :tabe[dit] {filename} | 在新标签页中打开 {filename}         |
| <C-w>T                | 把当前窗口移动到一个新的标签页      |
| :tabcc[lose]          | 关闭当前标签页及其中的所有窗口      |
| :tabo[nly]            | 只保留活动标签页,关闭所有其他标签页 |
| :tabn[ext] gt         | 切换到上一个标签                    |
| :tabp[revious] gT     | 切换到下一个标签                    |

---

#### 8. 什么是 Vim 的 text object

- Vim 里文本也有对象的概念, 比如一个单词、一短句子、一个段落.
- 通过操作文本对象来修改要比只操作单个子字符高效很多.

`[number]<command>[text object]`  
`number` 表示次数  
`command` 表示命令 `d`(elet) `c`(hange) `y`(ank)  
`text object` 表示要操作的文本对象 比如 `w`(ord) `s`(entence) `p`(aragraph)

example: `diw` `daw` `ciw` `caw` `viw` `vaw` `yiw` `yaw`  
`i` 表示 inner  
`a` 表示 around

---

#### 9. Vim 复制粘贴于寄存器的使用

- 复制粘贴的使用

  - Normal 模式
    - 普通模式下复制粘贴分别使用 y(ank) 呵 p(ut) , 剪切 d(elet)
    - 配合 v(isual)命令选中所要复制的文本
    - 配合文本对象使用 如 yiw 复制一个单词 yy 复制一行
  - Insert 模式
    - 和其他为本编辑器差不多 使用 cmd+v 进行粘贴

- 什么是 Vim 的寄存器
  - Vim 里操作的是寄存器而不是系统剪切板
  - 默认使用 dd 删除或 y 复制的内容都放到了`无名寄存器`
  - 通过`"{register}`前缀可以指定寄存器,不指定默认使用无名寄存器
  - `a-z` 都可以作为寄存器使用 `"ayaw` 表示将复制的单词存入寄存器`a`
  - 可使用 `:reg {register}` 查看寄存器内容
  - 可使用 `"ap` 粘贴存在寄存器`a`中的内容
  - 复制专用寄存暖气 `"0` 系统剪切板 `"+`

---

#### 10. 强大的 Vim 宏(macro)

- 什么是 Vim 宏

  - 宏可以看成是一系列命令的集合
  - 我们可以用宏**录制**一系列操作,然后用于**回放**
  - 宏可以把一系列命令用在多行文本上

- 如何使用宏
  - 使用`q`来录制,同时也是 q 结束录制
  - 使用`q{register}`选择要保存的寄存器,把录制的命令保存在其中
  - 使用`@{register}`回放寄存器中保存的一系列命令

---

#### 11. Vim 补全大法

- 常见的三种补全类型
  - 使用 ctrl + n 和 ctrl + p 补全单词
  - 使用 ctrl + x 和 ctrl + f 补全文件名
  - 使用 ctrl + x 和 ctrl + o 补全代码 需要开启文件类型检查 安装插件

---

#### 12. 给 Vim 换个配色

- 使用 `:colorscheme` 显示当前的主题配色
- 用 `:colorscheme <C+d>` 可以显示所有的配色
- 用 `:colorscheme {scheme_name}` 更换主题

---

---

## 编写 Vim 配置,我的 Vim 我做主 {#config}

vim 配置文件 `~/.vimrc`

- 常用设置 如 `:set nu` `colorscheme onedark`
- 常用的 vim 映射 如 `noremap <leader> w :w<cr>`
- 自定义的 vimscript 函数 和 插件配置

Vim 中的映射比较复杂 源于 vim 有多种模式

- 设置一下`leader`键 `let mapleader = "<Space>"`
-
- `nnoremap` 普通模式下的键位映射
- `inoremap` insert 模式下的映射
- `com!` 命令模式下执行的操作

使用`:h option-list` 查找所有的 vim 常用设置选项

#### Vim 映射迷人眼

- 基本映射
  基本映射指的是 normal 模式下的映射  
  使用`map`就可以实现映射 比如 `:map <C-d> dd`  
  使用`unmap`取消映射比如 `:unmap <C-d>`  
  `nmap/vmap/imap`定义映射只在 `normal/visual/insert` 模式下有效
- `*map`系列命令有递归的风险
- Vim 提供了非递归映射,这些命令不会的递归解释  
  使用 `*map`的对应版本 `nnoremap/vnoremap/inoremap`
- 任何情况下 都应该使用非递归映射

#### 学习和使用配置

- 了解常见常见的配置选项
- 学习和使用 Vim 映射

#### 从零配置自己的 NeoVim

- 个人[Dotfiles](https://github.com/zeekrs/dotfiles)已上传至 Github
- 使用[chezmoi](https://www.chezmoi.io)管理

## 常 Vim 安装插件,竟如此简单 {#plugin}

参考

- [《笨方法学 VimScript》](https://www.kancloud.cn/kancloud/learn-vimscript-the-hard-way/49321)
- [Vim 从入门到精通](https://github.com/wsdjeg/vim-galore-zh_cn)
- [Vim 帮助文档(中文)](https://yianwillis.github.io/vimcdoc/doc/quickref.html)
- awesome-neovim [awesome-neovim](https://github.com/rockerBOO/awesome-neovim)

插件推荐

- 插件管理
  - [packer](https://github.com/wbthomason/packer.nvim)
- 主题
  - [tokynight](https://github.com/folke/tokyonight.nvim)
  - [nightfox](https://github.com/EdenEast/nightfox.nvim)
- 自动补全 代码高亮格式化代码与诊断
  - [lsp-config](https://github.com/neovim/nvim-lspconfig)
  - [tree-sitter](https://github.com/nvim-treesitter/nvim-treesitter)
  - [cmp](https://github.com/hrsh7th/nvim-cmp)
  - [autopairs](https://github.com/windwp/nvim-autopairs)
  - [aototag](https://github.com/windwp/nvim-ts-autotag)
  - [rainbow](https://github.com/p00f/nvim-ts-rainbow)
  - [null-ls](https://github.com/jose-elias-alvarez/null-ls.nvim)
  - [comment](https://github.com/numToStr/Comment.nvim)
  - [comment-string](https://github.com/JoosepAlviste/nvim-ts-context-commentstring)
  - [trouble](https://github.com/folke/trouble.nvim)
- Git
  - [gitsigns](https://github.com/lewis6991/gitsigns.nvim)
- 文件管理
  - [tree](https://github.com/kyazdani42/nvim-tree.lua)
  - [project](https://github.com/ahmedkhalf/project.nvim)
- 文件查找
  - [telescope](https://github.com/nvim-telescope/telescope.nvim)
- UI
  - [bufferline](https://github.com/akinsho/bufferline.nvim)
  - [indentline](https://github.com/lukas-reineke/indent-blankline.nvim)
  - [alpha](https://github.com/goolord/alpha-nvim)
- 键位操作
  - [whichkey](https://github.com/folke/which-key.nvim)
- Markdown
  - [markdown-preview](https://github.com/iamcco/markdown-preview.nvim)
