# LearningPython
Python开发环境搭建
{
Windows下：官网下载安装；环境变量配置
Linux下：ipython的安装
$ sudo apt install ipython

Python的文件类型
字节码文件：.pyc，.pyo

Eclipse+PyDev的安装
}

Python中的数据类型：
整数/浮点数/字符串/布尔值/空值（None）

注释：#
raw字符串与多行字符串

Python中Unicode字符串

如果中文字符串在Python环境下遇到 UnicodeDecodeError，这是因为.py文件保存的格式有问题。可以在第一行添加注释
# -*- coding: utf-8 -*-

Python把0、空字符串''和None看成 False，其他数值和非空字符串都看成 True
