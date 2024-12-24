# 《Zig语言入门》（Introduction to Zig）

正在翻译中

---

<a href=""><img src="Cover/cover-artv3.png" width="250" height="366" class="cover" align="right"/></a>

嘿！这是Pedro Duarte Faria写的《Zig语言入门：一本基于项目的书》的官方仓库（的非官方中文翻译）。
想知道更多关于这本书的事儿吗？往下看看[关于本书](#about-this-book)这部分就行。
你可以在浏览器里直接阅读本书的最新版：<https://pedropark99.github.io/zig-book/>。

本书用的是[Quarto](https://quarto.org)出版系统，还加了一点R代码（`zig_engine.R`），负责调用Zig编译器来编译和运行那些Zig代码例子。

## 支持这个项目！

如果你觉得这个项目不错，想支持一波，可以去Amazon上买电子书或者实体书：

<https://www.amazon.com/dp/B0DJYMDRLP>

### 直接给作者打钱

你还可以通过以下方式直接向作者捐点小费：

- 通过PayPal捐赠。
- 通过Revolut转账。

这些捐款能帮作者继续创作类似的内容，还能让他有精力为社区编写更多有用的工具和材料。

### PayPal

[![PayPal](https://img.shields.io/badge/PayPal-003087?logo=paypal&logoColor=fff)](https://www.paypal.com/donate/?business=D58J5LFEERC3N&no_recurring=0&item_name=These+donations+make+it+possible+for+me+to+continue+writing+new+and+useful+content+for+our+community%F0%9F%98%89+Thank+you%21%E2%9D%A4%EF%B8%8F%F0%9F%A5%B3&currency_code=USD)

### Revolut

如果你想用Swift支付，可以用以下银行和Swift信息：

```
收款人：Pedro Duarte Faria
BIC/SWIFT代码：REVOSGS2
账户号码：6124512226
银行名称和地址：Revolut Technologies Singapore Pte. Ltd, 6 Battery Road, Floor 6-01, 049909, Singapore, Singapore
对应BIC：CHASGB2L
```

要是你有Revolut账户，扫下面的二维码就行：

## 关于本书

这是一本开放（即开源）、技术性和入门性的书籍，面向[Zig编程语言](https://ziglang.org/)。Zig是一种新的通用低级编程语言，专为打造最优且健壮的软件而生。

本书的官方仓库：<https://github.com/pedropark99/zig-book>。

无论你是初学者还是有经验的老手，这本书都适合你。它通过小项目（类似于Eric Matthes的《Python Crash Course》）带你走进Zig的精彩世界。这些项目包括：Base64编码器/解码器、HTTP服务器和图像滤镜。

通过这本书，你会学到：

- Zig的语法，以及它与C、C++和Rust的区别。
- 数据结构、内存分配器、文件系统和I/O操作。
- Optionals——一种处理空值的新范式。
- 如何测试和调试Zig应用程序。
- 把错误当作值来处理的方法。
- 使用嵌入在语言中的构建系统来编译C和Zig代码。
- Zig与C的互操作。
- 利用多线程和SIMD实现并行计算。
- 还有很多其他内容。

## 如何构建本书

本书依赖三款主要软件：

1. [Zig编译器](https://ziglang.org/download/)，用来编译书中大部分代码示例。
2. [R编程语言](https://cran.r-project.org/)，提供一些有用的工具来收集代码示例，并将它们发送给Zig编译器进行编译和执行，同时收集结果以包含在书中。
3. [Quarto出版系统](https://quarto.org/docs/get-started/)，用于编译本书，创建内部链接、引用、章节结构和HTML内容等。

所以，首先你需要在你的机器上安装这三款软件。

你可以通过点击上面的超链接找到如何安装这些软件的说明。

### 安装R包

在你搞定上面列出的三个软件后，下一步就是跑一下`dependencies.R`这个R脚本，来装上本书要用到的各种R包。只需要在你的终端里敲下下面这行命令就好，一切应该会顺利搞定。

注意：如果你用的是Linux或MacOS，这个过程可能会有点耗时，因为每个依赖项都得从源码构建。而在Windows上，这通常很快，因为一般有预构建的二进制文件可用。

```bash
Rscript dependencies.R
```

### 渲染书籍

要是你在电脑上已经正确安好了Quarto，那接下来构建这本书就很简单了。只要在终端里执行下面这行命令就好。

```bash
quarto render
```

### 脚本如何找到Zig编译器的路径

有些R代码（`zig_engine.R`）用来收集书中各个地方的Zig代码示例，并把它们送给Zig编译器去编译和执行。

但这之前，这段R代码得先找到你机器上装着的Zig编译器。这个搜索分两步走。首先，它会用[`Sys.which()`函数](https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/Sys.which)来找Zig编译器的路径，这其实就是`which`命令行工具的一个R接口。

这是个快速又简单的方法，但不是所有情况下都管用，特别是当你的Zig编译器没装在标准位置的时候。所以，就有了第二招：搜PATH环境变量。

它会获取你的PATH环境变量的值，然后挨个检查里面列出的目录，试着在里面找Zig编译器。虽然这种方法慢很多，但成功率高。

## License

Copyright © 2024 Pedro Duarte Faria。本书采用CC-BY 4.0 Creative Commons Attribution 4.0 International Public License许可。

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a>