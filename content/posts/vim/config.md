
+++
title="编写Vim配置,我的配置我做主"
date=2022-02-27

[taxonomies]
categories = ["editor"]
tags = ["vim"]
[extra]
toc = true
comments = false
+++


#### 编写Vim配置,我的Vim我做主  

vim配置文件 `~/.vimrc`  

- 常用设置  如 `:set nu`  `colorscheme onedark`
- 常用的vim映射  如 `noremap <leader> w :w<cr>`
- 自定义的 vimscript 函数 和 插件配置   


Vim中的映射比较复杂 源于vim有多种模式  

- 设置一下`leader`键 `let mapleader =  "<Space>"`
- 
- `nnoremap`  普通模式下的键位映射
- `inoremap` insert模式下的映射
- `com!`   命令模式下执行的操作

使用`:h option-list` 查找所有的vim常用设置选项  


#### Vim映射迷人眼  

- 基本映射 
  基本映射指的是normal模式下的映射  
  使用`map`就可以实现映射 比如 `:map <C-d> dd`     
  使用`unmap`取消映射比如 `:unmap <C-d>`  
  `nmap/vmap/imap`定义映射只在 `normal/visual/insert` 模式下有效   
  
- `*map`系列命令有递归的风险
- Vim提供了非递归映射,这些命令不会的递归解释  
  使用 `*map`的对应版本 `nnoremap/vnoremap/inoremap`
- 任何情况下 都应该使用非递归映射  


#### 学习和使用配置

- 了解常见常见的配置选项
- 学习和使用Vim映射
- [《笨方法学VimScript》](https://www.kancloud.cn/kancloud/learn-vimscript-the-hard-way/49321)


#### 从零配置自己的NeoVim

- nvim 配置入口文件  `~/.config/nvim/init.lua`
- vim options 配置 `lua/user/options` 
- vim keymaps 配置 `lua/user/keymaps` 
- vim plugins配置  `lua/user/plugins`


