# 《365天深入理解Go语言》

本书籍是记录自己在学习Go语言的过程中遇到的思考与感悟。写作过程中，大量参考借鉴甚至是复制了其他类似的项目。感谢每一个项目，致敬每一位Gopher！尽可能的熟练使用Go语言，尽可能的深入理解Go语言。努力成为Go语言特长型程序员。学习Go语言，面向信仰编程！作者：[0e0w](https://github.com/0e0w/LearnGolang)。Less is More or Less is Less.

本项目创建于2020年9月1日，最近的一次更新时间为2021年11月21日。本项目会持续更新，直到海枯石烂。

项目暂计划共七章。项目未完成，持续更新整理中！感谢关注！今天你学习Go语言了吗？

- [0x01-Go语言基础](https://github.com/0e0w/365GoLang#0x01-go%E8%AF%AD%E8%A8%80%E5%9F%BA%E7%A1%80)
- [0x02-Go语言进阶](https://github.com/0e0w/365GoLang#0x02-go%E8%AF%AD%E8%A8%80%E8%BF%9B%E9%98%B6)
- [0x03-Go语言库包](https://github.com/0e0w/365GoLang#0x03-go%E8%AF%AD%E8%A8%80%E5%BA%93%E5%8C%85)
- [0x04-Go语言算法](https://github.com/0e0w/365GoLang#0x04-go%E8%AF%AD%E8%A8%80%E7%AE%97%E6%B3%95)
- [0x05-Go安全开发](https://github.com/0e0w/365GoLang#0x05-go%E5%AE%89%E5%85%A8%E5%BC%80%E5%8F%91)
- [0x06-Go语言源码](https://github.com/0e0w/365GoLang#0x06-go%E8%AF%AD%E8%A8%80%E6%BA%90%E7%A0%81)
- [0x07-Go逆向工程](https://github.com/0e0w/365GoLang#0x07-go%E9%80%86%E5%90%91%E5%B7%A5%E7%A8%8B)

## 0x01-Go语言基础

<details>
<summary>Day001: 基础-Go语言入门</summary>

- [x] 本节说明：本节介绍Go语言的历史与发展。

- [x] Go语言介绍：

  - Go语言是一门编译型的开源的程序设计语言。通过Go语言可以容易的构造出简单、可靠且高效的软件。 因为开源，所以编译器、库和工具的源代码可以免费获得。
  - Go语言是由[Robert Griesemer](https://github.com/griesemer)、[Rob Pike](https://github.com/robpike)、[Ken Thompson](https://baike.baidu.com/item/Ken%20Thompson/3441433)在2007年末主持开发，后来加入了[Ian Lance Taylor](https://github.com/ianlancetaylor/)、[Russ Cox](https://github.com/rsc)等。在2009年11月开源发布，并在2012年发布了Go1稳定版本。
  - Go语言没有构造或析构函数、没有运算符重载、没有形参默认值、没有异常、没有宏、没有函数注解、没有线程局部存储。暂时没有泛型。
  - Go 语言不是面向对象编程语言：没有类继承，甚至没有类。
  - Go语言以一种不同寻常的方式来诠释面向对象程序设计。
  - Go语言有垃圾回收、有包系统、有一等公民函数、有词法作用域、有系统调用接口等。
- [x] Go语言特点：Go语言和其他语言相比的优势是什么？

  - 快速编译，高效执行，易于开发。
  - 对于网络通信、并发和并行编程有很好的支持，可以更好地利用大量的分布式和多核的计算机。
  - Go语言通过 goroutine 这种轻量级线程的概念来实现这个目标，然后通过 channel 来实现各个 goroutine 之间的通信。它们实现了分段栈增长和 goroutine 在线程基础上多路复用技术的自动化。
  - Go语言从本质上（程序和结构方面）来实现并发编程。
  - Go语言作为强类型语言，隐式的类型转换是不被允许的。一条原则：让所有的东西都是显式的。
  - Go语言本身是由C语言开发的，而不是Go语言（Go1.5开始自举）。
  - Go语言的二进制文件体积是最大的（每个可执行文件都包含 runtime）。
  - Go语言做为一门静态语言，但却和很多动态脚本语言一样得灵活。

- [x] Go语言资源：有大量的教程和代码想项目案例。

  - https://github.com/golang
  - https://github.com/0e0w/LearnGolang


- [x] Go语言安装：

  - [官网下载](https://golang.org/dl/)后，直接按照安装说明安装即可。在Ubuntu虚拟机里面开发使用Go语言：

    ```
    wget https://golang.google.cn/dl/go1.16.4.linux-amd64.tar.gz
    tar -C /usr/local -xzf go1.16.4.linux-amd64.tar.gz
    vi ~/.bashrc
    export PATH=/usr/local/go/bin:$PATH
    source .bashrc
    ```

- [x] Go环境变量：

  - 设置GOPATH：

    ```
    mkdir ~/go
    echo "GOPATH=$HOME/go" >> ~/.bashrc
    echo "export GOPATH" >> ~/.bashrc
    echo "PATH=\$PATH:\$GOPATH/bin # Add GOPATH/bin to PATH for scripting" >> ~/.bashrc
    source ~/.bashrc
    ```

  - 设置Go env

    ```
    go env -w GO111MODULE=off
    ```

- [x] Go语言编辑器：

  - [Goland](https://www.jetbrains.com/go)：JetBrains 公司的 Go 开发工具。
  - [LiteIDE](http://liteide.org)：一款开源跨平台轻量级的Go语言IDE。
  
- [x] Go语言命令：

  - 运行go程序：

    ```
    go run main.go
    ```

  - 打包成可执行程序：
    
    ```
    // 直接编译
    go build main.go
    //去掉符号表去掉调试信息
    go build -ldflags "-w -s" main.go
    go build -ldflags="-s -w" main.go
    //实现无窗口运行
    go build -ldflags "-w -s -H windowsgui" main.go
    ```
    
  - 生成不同平台下的可执行程序：需配置GOPATH。
    
    ```
    // Linux下编译Mac, Windows平台的64位可执行程序：
    CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build main.go
    CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build main.go
    
    // Linux下编译Mac, Windows平台的32位可执行程序：
    CGO_ENABLED=0 GOOS=windows GOARCH=386 go build main.go
    CGO_ENABLED=0 GOOS=darwin GOARCH=386 go build main.go
    ```
    
    ```
    // Windows下编译Mac, Linux平台的64位可执行程序：
    CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build main.go
    CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build main.go
    ```
    
    ```
    // Mac下编译Linux, Windows平台的64位可执行程序：
    CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build main.go
    CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build main.go
    ```
    
  - 安装依赖：
    
    ```
    go mod download
    go get -u github.com/0e0w/365GoLang
    ```
    
  - 格式化Go代码：
    
    ```
    gofmt
    ```
    
  - 查看Go环境配置：
    
    ```
    go env
    ```
    
  - 第三方包进行部署：

    ```
    go install
    ```

  - 其他的go命令：

    ```
    bug         start a bug report
    build       compile packages and dependencies
    clean       remove object files and cached files
    doc         show documentation for package or symbol
    env         print Go environment information
    fix         update packages to use new APIs
    fmt         gofmt (reformat) package sources
    generate    generate Go files by processing source
    get         add dependencies to current module and install them
    install     compile and install packages and dependencies
    list        list packages or modules
    mod         module maintenance
    run         compile and run Go program
    test        test packages
    tool        run specified go tool
    version     print Go version
    vet         report likely mistakes in packages
    ```
    
  - 从GOPATH/src目录开始引入包，需关闭go mod模式：

    ```
    export GO111MODULE=off
    ```

- [x] Go语言代理：

  - Go语言大量项目托管于Github，导致国内进行构建程序时会很慢。可使用下列的代理加快构建。

    ```
    https://mirrors.aliyun.com/goproxy/
    https://goproxy.io/zh/
    ```
    
    ```
    go env -w GO111MODULE=on
    go env -w GOPROXY=https://goproxy.cn,direct
    ```

- [x] Go语言未来：

  - Go语言拥有大量的优秀社区框架。
  - Go语言的未来发展前景是光明的。

- [x] 一个例子：Hello World！

  ```go
  package main
  
  import (
  	"fmt"
  )
  
  func main() {
  	fmt.Println("Hello World!")
  }
  ```
  
  
  - 包声明：package main表示一个可独立执行的程序，每个 Go 应用程序都包含一个名为 main 的包。
    - 在完成包的 import 之后，开始对常量、变量和类型的定义或声明。
    - 引入包：使用import圆括号进行引入包。
  
      - 引入标准包
      - 引入第三方包
    - 函数：使用func定义
    - 变量：
    - 常量：
    - 语句：
    - 语法：
  
- [x] Go语言名称：

  - 程序一般由关键字、常量、变量、运算符、类型和函数组成。 程序中可能会使用到这些分隔符：括号 ()，中括号 [] 和大括号 {}。 程序中可能会使用到这些标点符号：.、,、;、: 和 …。
  - 在变量与运算符间加入空格，程序看起来更加美观。
  - 标识符：用来命名变量、类型等程序实体。一个标识符就是一个或是多个字母( A ~ Z 和 a ~ z)数字(0~9)、下划线_组成的序列，但是第一个字符必须是字母或下划线而不能是数字。

- [x] 关键字：关键字是一些特殊的用来帮助编译器理解和解析源代码的单词。Go语言中有25个关键字或保留字。只能用在语法允许的地方，不能作为名称使用。

    - 声明代码元素：const、func、import、package、type、var
    - 组合类型表示：chan、interface、map、struct
    - 流程控制语句：break、case、continue、default、else、fallthrough、for、goto、if、switch、select、range、return
    - 特殊的关键字：defer、go。也可以看作是流程控制关键字， 但它们有一些特殊的作用。

- [x] 预定义标识符：三十几个内置的预申明的常量、类型和函数。所有的类型名、变量名、常量名、跳转标签、包名和包的引入名都必须是标识符。

     - 常量：true、flase、iota、nil
     - 类型：int、int8、int16、int32、int64、uint、uint8、uint16、uint32、uint64、uintptr、float32、float64、complex128、complex64、bool、byte、rune、string、error
     - 函数：make、len、cap、new、append、copy、close、delete、complex、real、imag、panic、recover

- [x] 声明：

   - 声明是给一个程序实体命名，并设定其部分或全部属性。
   - 有4个主要的声明：
     - 变量（var）
     - 常量（const）
     - 类型（type）
     - 函数（func）

   - 函数的声明包含一个名字、一个参数列表、一个可选的返回值列表以及函数体。

- [x] 一个例子：

   ```go
   package main
   
   import (
   	"fmt"
   )
   
   func main() {
   	fmt.Println("Hello World!")
   }
   ```

- [x] Go编码规范：https://golang.org/ref/spec

- [x] 可见性规则：

  - 在Go语言中，标识符必须以一个大写字母开头，这样才可以被外部包的代码所使用，这被称为导出。标识符如果以小写字母开头，则对包外是不可见的，但是他们在整个包的内部是可见并且可用的。但是包名不管在什么情况下都必须小写。
  - 在设计Go语言时，设计者们也希望确保它不是过于以ASCII为中心，这意味着需要从7位ASCII的范围来扩展标识符的空间。 所以Go语言标识符规定必须是Unicode定义的字母或数字，标识符是一个或多个Unicode字母和数字的序列， 标识符中的第一个字符必须是Unicode字母。
  - 总而言之，为了确保我们的标识符能正常导出，我们建议在开发中还是尽量使用ASCII 码来作为标识符，虽然设计者们在避免以ASCII 码为中心，但出于习惯我们还是服从于这个现实。

- [x] 命名规范：

  - 当某个函数需要被外部包调用的时候需要使用大写字母开头，并遵循 Pascal 命名法（“大驼峰式命名法”）；否则就遵循“小驼峰式命名法”，即第一个单词的首字母小写，其余单词的首字母大写。
  - 单词之间不以空格断开或连接号（-）、底线（_）连结，第一个单词首字母采用大写字母；后续单词的首字母亦用大写字母，例如：FirstName、LastName。每一个单词的首字母都采用大写字母的命名格式，被称为“Pascal命名法”，源自于Pascal语言的命名惯例，也有人称之为“大驼峰式命名法”（Upper Camel Case），为驼峰式大小写的子集。
  - Go 语言追求简洁的代码风格，并通过 gofmt 强制实现风格统一。
  
- [x] 语法惯例：

  - Go 语言也使用分号作为语句的结束，但一般会省略分号。像在标识符后面；整数、浮点、复数、Rune或字符串等字面量后面；关键字break、continue、fallthrough、或者return后面；操作符或标点符号++、--、)、]或}之后等等都可以使用分号，但是往往会省略掉，像LiteIDE编辑器会在保存.go文件时自动过滤掉这些分号，所以在Go语言开发中一般不用过多关注分号的使用。
  - 左大括号 { 不能单独一行，这是编译器的强制规定，否则你在使用 gofmt 时就会出现错误提示“ expected declaration, found '{' ”。右大括号 } 需要单独一行。
  - 在定义接口名时也有惯例，接口的名字由方法名加 [e]r 后缀组成，例如 Printer、Reader、Writer、Logger、Converter 等等。还有一些不常用的方式（当后缀 er 不合适时），比如 Recoverable，此时接口名以 able 结尾，或者以 I 开头（像 .NET 或 Java 中那样）。

- [x] 注释：

  - 尽管高级编程语言代码比底层机器指令友好和易懂，我们还是需要一些注释来帮助自己和其他程序员理解我们所写的代码。
  - 行注释：使用双斜线//开始，一般后面紧跟一个空格。行注释是Go语言中最常见的注释形式，在标准包中，一般都采用行注释，建议采用这种方式。
  - 块注释：使用 /* */，块注释不能嵌套。块注释一般用于包描述或注释成块的代码片段。
  
  </details>
<details>
<summary>Day002: 数据-Go语言变量</summary>

- [x] 本节说明：本节介绍Go语言变量的相关内容。

- [x] Go变量基本描述：

  - 变量是程序在运行时存储在内存中并且可以被更改的有名字的值。
  - 所有的变量值都是类型确定值。每个局部声明的变量至少要被有效使用一次。
  - Go语言变量标识符由字母、数字、下划线组成，首字母不能是数字，区分大小写。
  - Go语言规范中，下划线“_”也被认为是字母。
  - Go语言声明变量时将变量的类型放在变量的名称后面。
  - Go语言变量有2种声明方式，var标准变量申明和短变量声明。

- [x] 标准变量声明：

  - 使用var声明，声明之后需要进行初始化。未初始化时是对应数据的零值。
  - Go语言变量的命名规则遵循骆驼命名法。
  - 下列的因式分解关键字的写法一般用于声明全局变量。

    ```go
    var (
        a int
        b bool
        str string
        浮点 float32    // 中文可以作为变量标识符
    )
    ```

    ```go
    // 变量a，b都是指针类型
    var a, b *int
    ```

  - 声明变量之后，变量会自动初始化。初始值对应类型的零值。当一个变量被var声明之后，系统自动赋予它该类型的零值。所有的内存在 Go 中都是经过初始化的。数字类型对应的是0、布尔类型对应的是flase、字符串类型对应的是""、接口和引用类型对应的是nil。

    ```go
    var name type = expression
    var i, j, k int
    var b, f, s, = true, 2.3, "four" 
    ```

- [x] 短变量声明：

  - 在函数内部声明变量可以使用短变量声明方式。

  - 变量初始化时省略变量的类型会由系统自动推断。短变量声明时会同时进行初始化。

  - 短变量声明是变量声明的首选形式，但是只能用在函数体内，不可以用于全局变量的声明与赋值。

  - 使用操作符 := 可以高效地创建一个新的变量，称之为初始化声明。

  - 简式声明一般用在func内，要注意的是：全局变量和简式声明的变量尽量不要同名，否则很容易产生偶然的变量隐藏Accidental Variable Shadowing。

  - name := expression

    ```go
    a, b, c := 5, 7, "abc"  // 注意等号前的冒号
    ```

- [x] 变量赋值：

  - 多变量可以在同一行进行赋值，也称为并行或同时或平行赋值。

    ```go
    a, b, c = 5, 7, "abc"
    ```

  - 并行赋值也被用于当一个函数返回多个返回值时，比如这里的 val 和错误 err 是通过调用 Func1 函数同时得到：

    ```go
    val, err = Func1(var1)
    ```

- [x] 空白标识符 _ ：

  - 空白标识符 _ 也被用于抛弃值，如值 5 在：_, b = 5, 7 中被抛弃。
  - _ 实际上是一个只写变量，你不能得到它的值。这样做是因为 Go 语言中你必须使用所有被声明的变量，但有时你并不需要使用从一个函数得到的所有返回值。
  - 空白标识符是一个特殊的标识符.它可以像其他标识符那样用于变量的声明或赋值（任何类型都可以赋值给它），但任何赋给这个标识符的值都将被抛弃，因此这些值不能在后续的代码中使用，也不可以使用这个标识符作为变量对其它变量进行赋值或运算。
  - 由于Go语言有个强制规定，在函数内一定要使用声明的变量，但未使用的全局变量是没问题的。为了避免有未使用的变量，代码将编译失败，我们可以将该未使用的变量改为 _。
  - 另外，在Go语言中，如果引入的包未使用，也不能通过编译。有时我们需要引入的包，比如需要init()，或者调试代码时我们可能去掉了某些包的功能使用，你可以添加一个下划线标记符，_，来作为这个包的名字，从而避免编译失败。下滑线标记符用于引入，但不使用。

- [x] 零值nil：

  - nil 标志符用于表示interface、函数、maps、slices、channels、error、指针等的“零值”。如果你不指定变量的类型，编译器将无法编译你的代码，因为它猜不出具体的类型。

- [ ] 本节案例：

  </details>
<details>
<summary>Day003: 数据-Go语言常量</summary>

- [x] 本节说明：本节介绍Go语言常量的内容。
- [x] 常量说明：
  - 常量使用关键字 const 定义，用来存储不会改变的数据。
  - 常量不能被重新赋予任何值。常量名建议使用大写字母。
  - 存储在常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型。
  - 常量声明中的等号=表示“绑定”而非“赋值”。每个常量描述将一个或多个字面量绑定到各自对应的有名常量上。每个有名常量其实代表着一个字面常量。
  - 常量可以直接声明在包中（全局常量），也可以声明在函数体中（局部常量）。

- [x] 常量定义：

  - 常量的定义格式：const identifier [type] = value，例如：

    ```go
    const Pi = 3.14159
    ```
    
  - Go语言常量定义可以指定常量类型，但不是必需的。如果定义常量时没有指定类型，那么它与字面常量一样，是无类型（untyped）的常量。
    
  - 一个未指定类型的常量被使用时，会根据其使用环境而推断出它所需要具备的类型。
    
    ```go
    显式类型定义：const b string = "abc"
    隐式类型定义：const b = "abc"
    ```
  - 常量也可以在单行进行多重赋值：
  
    ```go
    const a, b, c = 1, false, "str" //多重赋值
    ```
  
- [x] iota： 特殊常量

  - iota 在 const关键字出现时将被重置为 0，const 中每新增一行常量声明将使 iota 计数一次。
  - iota 可理解为 const 语句块中的行索引。
  - iota 可以被用作枚举值。第一个 iota 等于 0，每当 iota 在新的一行被使用时，它的值都会自动加 1。

     ```go
     const (
         a = iota
         b = iota
         c = iota
     )
     ```

     第一个 iota 等于 0，每当 iota 在新的一行被使用时，它的值都会自动加 1；所以 a=0, b=1, c=2 可以简写为如下形式：

     ```go
     const (
         a = iota
         b
         c
      )
     ```

     如果对b重新赋值之后，a, b, c分别为0, 8, 8，新的常量b声明后，iota 不再向下赋值，后面常量如果没有赋值，则继承上一个常量值。

     ```go
     const (
         a = iota
         b = 8
         c
      )
     ```

     使用位左移与 iota 计数配合可优雅地实现存储单位的常量枚举：

     ```go
     type ByteSize float64
     const (
         _ = iota // 通过赋值给空白标识符来忽略值
         KB ByteSize = 1<<(10*iota)
         MB
         GB
         TB
     )
     ```

  </details>
<details>
<summary>Day004: 数据-Go基本数据</summary>

- [x] 本节说明：本节介绍Go语言的基本数据类型。

- [x] 基本数据类型：

  - 在Go语言中，数据类型用于声明函数和变量。
  - 数据类型的出现是为了把数据分成所需内存大小不同的数据，编程的时候需要用大数据的时候才需要申请大内存，就可以充分利用内存。
  - 在大多数高级编程语言中，数据通常被抽象为各种类型（type）和值（value）。 
  - 一个类型可以看作是值的模板。一个值可以看作是某个类型的实例。
  - 大多数编程语言支持自定 义类型和若干预定义类型（即内置类型）。 
  - 一门语言的类型系统是这门语言的灵魂。Go语言拥有独特的灵魂。
  
  **一、布尔类型：**
  
  
    - 布尔型的值只可以是常量 true 或者 false。布尔类型的初值是false。
    - 两个类型相同的值可以使用相等 == 或者不等 != 运算符来进行比较并获得一个布尔型的值。
    - 非运算符：
  
  ```go
  !T -> false
  !F -> true
  ```
  
    - 和运算符：
  
  ```go
  T && T -> true
  T && F -> false
  F && T -> false
  F && F -> false
  ```
  
  
    - 或运算符：
  
  ```go
  T || T -> true
  T || F -> true
  F || T -> true
  F || F -> false
  ```
  
  **二、数值类型：**
  
  - Go语言支持整型和浮点型数字，并且支持复数，其中位的运算采用补码。整型 int 和浮点型 float32、float64。
  - Go语言中没有 float 类型。Go语言中只有 float32 和 float64。没有double类型。
  - 整型的零值为 0，浮点型的零值为 0.0。
  - 整数：rune是int32的内置别名。 
  
    ```
    int8（-128 -> 127）
    int16（-32768 -> 32767）
    int32（-2,147,483,648 -> 2,147,483,647）
    int64（-9,223,372,036,854,775,808 -> 9,223,372,036,854,775,807）
    ```
  
  - 无符号整数：byte是uint8的内置别名。
  
    ```
    uint8（0 -> 255）
    uint16（0 -> 65,535）
    uint32（0 -> 4,294,967,295）
    uint64（0 -> 18,446,744,073,709,551,615）
    ```
  
  - 浮点型（IEEE-754 标准）：
  
    ```
    float32（+- 1e-45 -> +- 3.4 * 1e38）
    float64（+- 5 * 1e-324 -> 107 * 1e308）
    ```
  
  - 字节型：byte 型，也就是uint8类型。代表了ASCII码的一个字符。
  
    ```go
    vat bt byte
    bt = 'a'
    fmt.Println(bt)
    //打印97
    ```
  
  **三、字符串类型：**
  
  - 从逻辑上说，一个字符串值表示一段文本。 在内存中，一个字符串存储为一个字节 （byte）序列。
  - Go语言中可以使用反引号或者双引号来定义字符串。反引号表示原生的字符串，不进行转义。
  - Go语言中的string类型是一种值类型，存储的字符串是不可变的，如果要修改string内容需要将string转换为[]byte或[]rune，并且修改后的string内容是重新分配的。
  - Go语言中的string类型是一种值类型，存储的字符串是不可变的，如果要修改string内容需要将string转换为[]byte或[]rune，并且修改后的string内容是重新分配的。
  - 字符串是字节的定长数组。字符串的零值是为长度为零的字符串，即空字符串 ""。
  - 一般的比较运算符（==、!=、<、<=、>=、>）通过在内存中按字节比较来实现字符串的对比。可以通过函数 len() 来获取字符串所占的字节长度，例如：len(str)。
  - 在Go中，字符串值是UTF-8编码的， 甚至所有的Go源代码都必须是UTF-8编码的。
  - 字符串的内容（纯字节）可以通过标准索引法来获取，在中括号 [] 内写入索引，索引从 0 开始计数。
  - 解释字符串：该类字符串使用双引号括起来，其中的相关的转义字符将被替换，这些转义字符包括：
  
    ```
    \n：换行符
    \r：回车符
    \t：tab 键
    \u 或 \U：Unicode 字符
    \\：反斜杠自身
    ```
  
  - 非解释字符串：
    
    ```
    `This is a raw string \n` 中的 `\n\` 会被原样输出。
    ```
    
  - 字符串拼接：
    
    - 直接使用运算符+
    - fmt.Sprintf()
    - strings.Join()
    - bytes.Buffer
    
  - strings.Builder
    
  - 标准库中有四个包对字符串处理尤为重要：bytes、strings、strconv和unicode包。
  
  - [字符串参考1](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/04.7.md)
  
  - 格式化输出：fmt.Printf()
  
    ```
    %d  //整型格式
    %c  //字符型
    %s  //字符串格式
    %v  //自动匹配类型
    %T  //数据类型
    ```
  
  - 数据类型转换：int(a)
  
- [x] 组合类型分类：

  - 指针类型 - 类C指针。
  - 结构体类型 - 类C结构体。
  - 函数类型 - 函数类型在Go中是一种一等公民类别。
  - 容器类型，包括:
    - 数组类型 - 定长容器类型。
    - 切片类型 - 动态长度和容量容器类型。
    - 映射类型（map）- 也常称为字典类型。在标准编译器中映射是使用哈希表实现的。
  - 通道类型 - 通道用来同步并发的协程。
  - 接口类型 - 接口在反射和多态中发挥着重要角色。

  ```go
  // 假设T为任意一个类型，Tkey为一个支持比较的类型。
  
  *T         // 一个指针类型
  [5]T       // 一个元素类型为T、元素个数为5的数组类型
  []T        // 一个元素类型为T的切片类型
  map[Tkey]T // 一个键值类型为Tkey、元素类型为T的映射类型
  
  // 一个结构体类型
  struct {
  	name string
  	age  int
  }
  
  // 一个函数类型
  func(int) (bool, string)
  
  // 一个接口类型
  interface {
  	Method0(string) int
  	Method1() (int, bool)
  }
  
  // 几个通道类型
  chan T
  chan<- T
  <-chan T
  ```

- [ ] 类型的种类：

  - 每种上面提到的基本类型和组合类型都对应着一个类型种类（kind）。除了这些种类，今后将要介绍的非类型安全指针类型属于另外一个新的类型种类。

  - 所以，目前（Go 1.15），Go有26个类型种类。

- [ ] 语法-类型定义：

  - 在Go语言中，我们可以用type关键字来定义新的类型。
  - 一些类型定义的例子：

    ```go
    // 下面这些新定义的类型和它们的源类型都是基本类型。
    type (
    	MyInt int
    	Age   int
    	Text  string
    )
    
    // 下面这些新定义的类型和它们的源类型都是组合类型。
    type IntPtr *int
    type Book struct{author, title string; pages int}
    type Convert func(in0 int, in1 bool)(out0 int, out1 string)
    type StringArray [5]string
    type StringSlice []string
    
    func f() {
    	// 这三个新定义的类型名称只能在此函数内使用。
    	type PersonAge map[string]int
    	type MessageQueue chan string
    	type Reader interface{Read([]byte) int}
    }
    ```

- [ ] 类型别名声明：

  - 给一个类型另取一个别名：

    ```go
    type bigint int64
    var a bigint
    ```

    ```go
    type (
    	Name = string
    	Age  = int
    )
    
    type table = map[string]int
    type Table = map[Name]Age
    ```

- [ ] 定义类型和非定义类型：

- [ ] 有名类型和无名类型：

- [ ] 底层类型：
  - 在Go语言中，每个类型都有一个底层类型。
  - 一个内置类型的底层类型为它自己。
  - unsafe标准库包中定义的Pointer类型的底层类型是它自己。
  - 一个非定义类型（必为一个组合类型）的底层类型为它自己。
  - 在一个类型声明中，新声明的类型和源类型共享底层类型。
  - 一个例子：

    ```go
    // 这四个类型的底层类型均为内置类型int。
    type (
    	MyInt int
    	Age   MyInt
    )
    
    // 下面这三个新声明的类型的底层类型各不相同。
    type (
    	IntSlice   []int   // 底层类型为[]int
    	MyIntSlice []MyInt // 底层类型为[]MyInt
    	AgeSlice   []Age   // 底层类型为[]Age
    )
    
    // 类型[]Age、Ages和AgeSlice的底层类型均为[]Age。
    type Ages AgeSlice
    ```

- [ ] 值、值部、值尺寸

  - 一个类型的一个实例称为此类型的一个值。一个类型可以有很多不同的值，其中一个为它的零值。 同一类型的不同值共享很多相同的属性。
  - 每个类型有一个零值。一个类型的零值可以看作是此类型的默认值。 预声明的标识符nil可以看作是切片、映射、函数、通道、指针（包括非类型安全指针）和接口类型的零值的字面量表示。 我们以后可以在Go中的nil一文中了解到关于nil的各种事实。

- [x] 本节案例：


  </details>

<details>
<summary>Day005: 数据-Go语言指针</summary>

- [x] 本节说明：本节介绍Go语言指针(pointer)的相关内容。

- [ ] 指针基础概述：

  指针就是内存地址。内存地址是一种用于软件及硬件等不同层级中的数据概念，用来访问电脑主存中的数据。指针是存储另一个变量的内存地址的变量。一个指针中存储的内存地址是另外一个值的地址。 

- [x] Go语言指针概述：

  - 虽然Go语言吸收融合了很多其语言中的各种特性，但是Go语言主要被归入C语言家族。其中一个重要的原因是Go语言和C语言一样，也支持指针。但Go语言中的指针相比C语言指针有很多限制。Go语言不支持指针运算。
  - 指针是Go语言中的一种类型分类（kind）。一个指针是某个指针类型的一个值。一个指针可以存储一个内存地址。  
  - 一个指针值存储着另一个值的地址，除非此指针值是一个nil空指针。我们可以说此指针引用着另外一个值，或者说另外一个值正被此指针所引用。
  - 将一个含有（直接或者间接）指针字段的结构体类型称为一个指针包裹类型，将一个含有（直接或者间接）指针的类型称为指针持有者类型。

- [ ] Go语言为什么需要指针？
  
- [ ] Go语言指针操作：
  
  一、获取指针值：  
  - 可以用内置函数new来为任何类型的值开辟一块内存并将此内存块的起始地址做为此值的地址返回。 假设T是任一类型，则函数调用new(T)返回一个类型为*T的指针值。 存储在返回指针值所表示的地址处的值（可被看作是一个匿名变量）为T的零值。
  - 可以用前置取地址操作符&来获取一个可寻址的值的地址。 对于一个类型为T的可寻址的值t，我们可以用&t来取得它的地址。&t的类型为*T。  
  
  二、指针引用：  
  
  - 一个指针中存储着另一个值的地址，则此指针值引用着另一个值。同时另一个值当前至少有一个引用。 
  - 一个指针引用着另外一个值，也就是此指针指向另外一个值。  
  
- [x] 内存地址介绍：
  
  - 一个内存地址表示操作系统管理的整个内存中的一个偏移量（相对于从整个内存的起始，以字节计数）。
  - 一个内存地址用一个操作系统原生字（native word）来存储。
  - 一个原生字在32位操作系统上占4个字节，在64位操作系统上占8个字节。
  - 内存地址的字面形式常用整数的十六进制字面量来表示，比如0x1234CDEF。  
  
- [ ] 指针类型和值：  
  - 在Go语言中，一个非定义指针类型的字面形式为\*T，其中T为一个任意类型。  
  
  - 类型T称为指针类型\*T的基类型（base type）。 如果一个指针类型的基类型为T，则我们可以称此指针类型为一个T指针类型。  
  - 虽然我们可以声明定义指针类型，但是一般不推荐这么做。非定义指针类型的可读性更高。  
  - 如果一个指针类型的底层类型是\*T，则它的基类型为T。  
  - 如果两个非定义指针类型的基类型为同一类型，则这两个非定义指针类型亦为同一类型。  
  - 如果一个指针类型的基类型为T，则此指针类型的值只能存储类型为T的值的地址。
  - 一个值的地址是指此值的直接部分占据的内存的起始地址。  
  - 一些指针类型的例子：  
    ```go
    *int  // 一个基类型为int的非定义指针类型。
    **int // 一个多级非定义指针类型，它的基类型为*int。
    
    type Ptr *int // Ptr是一个定义的指针类型，它的基类型为int。
    type PP *Ptr  // PP是一个定义的多级指针类型，它的基类型为Ptr。
    ```
    
  - 指针类型的零值的字面量使用预声明的nil来表示。一个nil指针（常称为空指针）中不存储任何地址。  
  
- [ ] 指针解引用：  
  - 解引用一个nil指针将产生一个恐慌。  
  - 取地址和解引用例子：  
    ```go
    package main
    
    import "fmt"
    
    func main() {
    	p0 := new(int)   // p0指向一个int类型的零值
    	fmt.Println(p0)  // （打印出一个十六进制形式的地址）
    	fmt.Println(*p0) // 0
    
    	x := *p0              // x是p0所引用的值的一个复制。
    	p1, p2 := &x, &x      // p1和p2中都存储着x的地址。
    	                      // x、*p1和*p2表示着同一个int值。
    	fmt.Println(p1 == p2) // true
    	fmt.Println(p0 == p1) // false
    	p3 := &*p0            // <=> p3 := &(*p0)
    	                      // <=> p3 := p0
    	                      // p3和p0中存储的地址是一样的。
    	fmt.Println(p0 == p3) // true
    	*p0, *p1 = 123, 789
    	fmt.Println(*p2, x, *p3) // 789 789 123
    
    	fmt.Printf("%T, %T \n", *p0, x) // int, int
    	fmt.Printf("%T, %T \n", p0, p1) // *int, *int
    }
    ```
  
- [ ] Go指针的一些限制：  
  - Go语言指针一般不支持算术运算。
  - 一个指针类型的值不能被随意转换为另一个指针类型。
  - 一个指针值不能和其它任一指针类型的值进行比较。
  - 一个指针值不能被赋值给其它任意类型的指针值。
  - 上述Go语言指针的限制是可以被打破的。unsafe标准库包中提供的非类型安全指针（unsafe.Pointer）机制可以被用来打破上述Go语言指针的安全限制。
  
- [ ] 指针参考：[指针参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_24_pointer.md)、[指针参考2](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/04.9.md)、[指针参考3](https://gfw.go101.org/article/pointer.html)
  
  </details>
<details>
<summary>Day006: 数据-Go语言数组</summary>

- [x] 本节说明：本节介绍Go语言数组(array)的相关内容。

- [x] 数组Array介绍：

  - 数组是具有相同类型的一组已知编号且长度固定的数据项序列。一个数组可以由零个或多个元素组成。
  - 数组类型可以是任意的原始类型例如整型、字符串或者自定义类型。
  - 数组长度必须是一个常量表达式，并且必须是一个非负整数。
  - 以 [] 符号标识的数组类型几乎在所有的编程语言中都是一个基本主力。因为数组的长度是固定的，所以在Go语言中很少直接使用数组。
  - 数组长度也是数组类型的一部分，所以[5]int和[10]int是属于不同类型的。
  
- [x] 声明数组：

  - Go 语言数组声明需要指定元素类型及元素个数，语法格式如下：

    ```go
    var 数组变量名 [元素数量]Type
    var a [3]int             // 定义三个整数的数组
    ```
  
  - Go 语言中的数组是一种值类型，所以可以通过 new() 来创建：
  
    ```go
    var arr1 = new([5]int)
    ```
  
- [x] 初始化数组：

  - 初始化数组中 {} 中的元素个数不能大于 [] 中的数字。

- [x] 访问数组元素：

  - 数组元素可以通过索引（位置）来读取。格式为数组名后加中括号，中括号中为索引的值。

    ```go
    var team [3]string
    team[0] = "hammer"
    team[1] = "soldier"
    team[2] = "mum"
    for k, v := range team {
        fmt.Println(k, v)
    }
    ```

- [x] 多维数组：

  - 数数组通常是一维的，但是可以用来组装成多维数组例如：

    ```
    [3][5]int
    [2][2][2]float64
    ```

- [x] 将数组传递给函数：

  - 把一个大数组传递给函数会消耗很多内存。有两种方法可以避免这种现象：
    - 传递数组的指针
    - 使用数组的切片

- [x] 本节案例：

  </details>

<details>
<summary>Day007: 数据-Go语言切片</summary>

- [x] 本节说明：本节介绍Go语言切片(slice)的相关内容。

- [x] 切片Slice介绍：

  - Go语言切片是对数组的抽象。
  - 切片是对底层数组一个连续片段的引用，所以切片是一个引用类型。
  - 切片提供对该数组中编号的元素序列的访问。未初始化切片的值为nil。
  - Go语言数组的长度不可改变，但切片好比动态数组，可以追加元素，在追加时可能使切片的容量增大。
  - 因为切片是引用，不需要使用额外的内存且比使用数组更有效率，所以在Go代码中切片比数组更常用。
  
- [x] 定义切片：

  - 切片有俩种定义方式

    ```go
    var 切片变量名 []type // 声明一个未指定大小的数组来定义切片
    var silice = []int{2,4,6}
    var silice = []string{"aaa","bbb","ccc"}
    ```

    ```go
    var slice1 []type = make([]type, len,cap)// 使用make()函数来创建切片
    ```

  - 使用make生成切片：

    ```go
    package main
    import "fmt"
    
    func main() {
    	var slice1 []int = make([]int, 10)
    	// load the array/slice:
    	for i := 0; i < len(slice1); i++ {
    		slice1[i] = 5 * i
    	}
    
    	// print the slice:
    	for i := 0; i < len(slice1); i++ {
    		fmt.Printf("Slice at %d is %d\n", i, slice1[i])
    	}
    	fmt.Printf("\nThe length of slice1 is %d\n", len(slice1))
    	fmt.Printf("The capacity of slice1 is %d\n", cap(slice1))
    }
    ```

- [x] 将切片传递给函数：

  ```go
  func sum(a []int) int {
  	s := 0
  	for i := 0; i < len(a); i++ {
  		s += a[i]
  	}
  	return s
  }
  
  func main() {
  	var arr = [5]int{0, 1, 2, 3, 4}
  	sum(arr[:])
  }
  ```

- [x] 切片重组

  - 通过改变切片长度得到新切片的过程称之为切片重组 reslicing。
  - 在一个切片基础上重新划分一个切片时，新的切片会继续引用原有切片的数组。
  - 为了避免这个陷阱，我们需要从临时的切片中使用内置函数copy()，拷贝数据到新切片。

- [ ] 切片初始化：

- [ ] 空(nil)切片：

- [ ] 切片参考：[参考1：Go Slice全面指南](https://mp.weixin.qq.com/s/rYY6TnZcb0FIWjouD2cznQ)、[切片参考2](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/07.2.md)

- [ ] 本节案例：

  </details>
<details>
<summary>Day008: 数据-Go语言映射</summary>

- [x] 本节说明：本节介绍集合Go语言映射(Map)的相关内容。

- [x] 映射Map介绍：

  - Go语言中的Map类型也称之为映射、字典、集合。
  - Map 是一种元素对（pair）的无序集合，pair 的一个元素是 key，对应的另一个元素是 value，Map结构也称为关联数组或字典。
  - Map 最重要的一点是通过 key 来快速检索数据，key 类似于索引，指向数据的值。
  - Map 是一种集合，所以我们可以像迭代数组和切片那样迭代它。不过，Map 是无序的，我们无法决定它的返回顺序，这是因为 Map 是使用 hash 表来实现的。
  - 在声明的时候不需要知道 Map 的长度，Map 是可以动态增长的。
  - 不要使用 new，永远用 make 来构造 map。
  
- [x] 申明定义Map：

  - map 是引用类型，可以使用如下声明：

    ```go
    var map1 map[keytype]valuetype
    var map1 map[string]int
    map1 = map[string]int{"one": 1, "two": 2}
    ```
    
  - 可以使用内建函数 make 也可以使用 map 关键字来定义 Map。

    ```go
    // 声明变量，默认 map 是 nil
    var map_variable map[key_data_type]value_data_type
    
    // 使用 make 函数
    map_variable := make(map[key_data_type]value_data_type)
    
    var m map[string]int
    
    // 声明但未初始化map，此时是map的零值状态
    map1 := make(map[string]string, 5)
    
    map2 := make(map[string]string)
    
    // 创建了初始化了一个空的的map，这个时候没有任何元素
    map3 := map[string]string{}
    
    // map中有三个值
    map4 := map[string]string{"a": "1", "b": "2", "c": "3"}
    ```

  - 一个示例：

    ```go
    package main
    import "fmt"
    
    func main() {
    	var mapLit map[string]int
    	//var mapCreated map[string]float32
    	var mapAssigned map[string]int
    
    	mapLit = map[string]int{"one": 1, "two": 2}
    	mapCreated := make(map[string]float32)
    	mapAssigned = mapLit
    
    	mapCreated["key1"] = 4.5
    	mapCreated["key2"] = 3.14159
    	mapAssigned["two"] = 3
    
    	fmt.Printf("Map literal at \"one\" is: %d\n", mapLit["one"])
    	fmt.Printf("Map created at \"key2\" is: %f\n", mapCreated["key2"])
    	fmt.Printf("Map assigned at \"two\" is: %d\n", mapLit["two"])
    	fmt.Printf("Map literal at \"ten\" is: %d\n", mapLit["ten"])
    }
    ```

  - for-range与map

    ```go
    // 使用 for 循环构造 map
    for key, value := range map1 {
    	...
    }
    ```

    ```go
    // 只获取值
    for _, value := range map1 {
    	...
    }
    ```

    ```go
    // 只获取 key
    for key := range map1 {
    	fmt.Printf("key is: %d\n", key)
    }
    ```

- [x] Go语言容器：
  
  - Go语言中有三种一等公民容器类型：数组、切片和映射。
  - 有时候，字符串类型和通道类型也属于容器类型。
  - 每个容器（值）用来表示和存储一个元素（element）序列或集合。一个容器中的所有元素的类型是相同的。此相同的类型称为此容器的类型的元素类型（或简称此容器的元素类型）。
  - 存储在一个容器中的每个元素值都关联着一个键值（key）。每个元素可以通过它的键值而被访问到。
  - 每个容器值有一个长度属性，用来表明此容器中当前存储了多少个元素。
  - 每个数组值仅由一个直接部分组成，而一个切片或者映射值是由一个直接部分和一个可能的被此直接部分引用着的间接部分组成。
  - 容器字面量是不可寻址的但可以被取地址。
  
- [x] 非定义容器类型的字面表示：
  
  - 数组类型：[N]T
  
  - 切片类型：[]T
  
  - 映射类型：map[K]T
  
  - 说明：T可为任意类型，表示一个容器类型的元素类型。N必须为非负整数常量。K必须为一个可比较类型，K指定了映射类型的键值类型。
  
  - 一些例子：
  
    ```go
    const Size = 32
    
    type Person struct {
    	name string
    	age  int
    }
    
    // 数组类型
    [5]string
    [Size]int
    [16][]byte  // 元素类型为一个切片类型：[]byte
    [100]Person // 元素类型为一个结构体类型：Person
    
    // 切片类型
    []bool
    []int64
    []map[int]bool // 元素类型为一个映射类型：map[int]bool
    []*int         // 元素类型为一个指针类型：*int
    
    // 映射类型
    map[string]int
    map[int]bool
    map[int16][6]string     // 元素类型为一个数组类型：[6]string
    map[bool][]string       // 元素类型为一个切片类型：[]string
    map[struct{x int}]*int8 // 元素类型为一个指针类型：*int8；
                            // 键值类型为一个结构体类型。
    ```
  
- [ ] 查看容器值的长度和容量：

  - 长度：len()
  - 容量：cap()
  - 说明：数组值的长度和容量永不改变。切片值的长度和容量可在运行时改变。

- [ ] 读取和修改容器元素：

  - 一个容器值v中存储的对应着键值k的元素用语法形式v[k]来表示。 v[k]为一个元素索引表达式。

- [ ] 添加和删除容器元素：

- [ ] 使用内置make函数来创建切片和映射：

- [ ] 使用内置new函数来创建容器值：

- [ ] 从数组或者切片派生切片（取子切片）：

- [ ] 使用内置copy函数来复制切片元素：

- [ ] 遍历容器元素：

  - 一个例子：

    ```go
    for key, element = range aContainer {
    	// 使用key和element ...
    }
    ```
  
- [ ] 把数组指针当做数组来使用：

- [ ] 单独修改一个切片的长度或者容量：

- [ ] 容器参考：[容器参考链接1](https://gfw.go101.org/article/container.html)  
  
  </details>
<details>
<summary>Day009: 数据-Go语言结构</summary>

- [x] 本节说明：本节介绍Go语言结构体(struct)的相关内容。
- [x] 结构体struct介绍：
  - Go语言通过类型别名（alias types）和结构体的形式支持用户自定义类型，或者叫定制类型。
  - 一个带属性的结构体试图表示一个现实世界中的实体。
  - 结构体是由一系列具有相同类型或不同类型的数据构成的数据集合。结构体中可以定义不同类型的数据。
  - 结构体是复合类型（composite types），它由一系列属性组成，每个属性都有自己的类型和值的，结构体通过属性把数据聚集在一起。结构体也是值类型，因此可以通过new函数来创建。
  - 组成结构体类型的那些数据称为 字段（fields）。每个字段都有一个类型和一个名字；在一个结构体中，字段名字必须是唯一的。
  - Go语言结构体不支持字段联合（union）。
  - 方法（Method）可以访问这些数据，就好像它们是这个独立实体的一部分。
- [x] 定义结构体：
  - 结构体定义需要使用 type 和 struct 语句。结构体中有一个或多个成员。type 语句设定了结构体的名称。结构体的格式如下：

    ```go
    struct {
        title, author string
        pages         int
        X, Y   		  bool
    }
    ```
    
  - `type T struct {a, b int}` 也是合法的语法，它更适用于简单的结构体。
  - 一个空结构体：struct {}
  - 一旦定义了结构体类型，它就能用于变量的声明。
  - 结构体的字段可以是任何类型，甚至是结构体本身，也可以是函数或者接口。可以声明结构体类型的一个变量，然后像下面这样给它的字段赋值：

    ```go
    var s T
    s.a = 5
    s.b = 8
    ```

  - 一些结构体例子：
    ```go
    package main
    import "fmt"
    
    type struct1 struct {
        i1  int
        f1  float32
        str string
    }
    
    func main() {
        ms := new(struct1)
        ms.i1 = 10
        ms.f1 = 15.5
        ms.str= "Chris"
    
        fmt.Printf("The int is: %d\n", ms.i1)
        fmt.Printf("The float is: %f\n", ms.f1)
        fmt.Printf("The string is: %s\n", ms.str)
        fmt.Println(ms)
    }
    ```
    
    ```go
    package main
    
    import (
    	"fmt"
    )
    
    type Book struct {
    	title, author string
    	pages         int
    }
    
    func main() {
    	book := Book{"Go语言笔记", "0e0w", 365}
    	fmt.Println(book)
    
    	// 使用带字段名的组合字面量来表示结构体值。
    	book = Book{author: "0e0w", pages: 365, title: "Go语言笔记"}
    	book = Book{}
    	book = Book{author: "0e0w"}
    
    	// 使用选择器来访问和修改字段值。
    	var book2 Book // <=> book2 := Book{}
    	book2.author = "Tapir"
    	book2.pages = 300
    	fmt.Println(book.pages) // 300
    }
    
    func f() {
    	book1 := Book{pages: 300}
    	book2 := Book{"Go语言笔记", "0e0w", 365}
    
    	book2 = book1
    	// 上面这行和下面这三行是等价的。
    	book2.title = book1.title
    	book2.author = book1.author
    	book2.pages = book1.pages
    }
    ```

- [x] 访问结构体成员：
  - 如果要访问结构体成员，需要使用点号 . 操作符，格式为：
    ```go
    结构体.成员名
    ```
- [x] 结构体特性：
  - 结构体的内存布局：Go 语言中，结构体和它所包含的数据在内存中是以连续块的形式存在的，即使结构体中嵌套有其他的结构体，这在性能上带来了很大的优势。
  - 递归结构体：递归结构体类型可以通过引用自身指针来定义。这在定义链表或二叉树的节点时特别有用，此时节点包含指向临近节点的链接。
  - 可见性：通过参考应用可见性规则，如果结构体名不能导出，可使用 new 函数使用工厂方法的方法达到同样的目的。
  - 带标签的结构体：结构体中的字段除了有名字和类型外，还可以有一个可选的标签（tag）。它是一个附属于字段的字符串，可以是文档或其他的重要标记。标签的内容不可以在一般的编程中使用，只有 reflect 包能获取它。

- [ ] 结构体参考：[结构体参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_18_struct.md)、[结构体参考2](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/10.1.md)、[结构体参考3](https://gfw.go101.org/article/struct.html)
  
- [x] 本节案例：
  
  ```go
  package main
  
  import (
  	"fmt"
  )
  
  type Human struct {
  	name   string // 姓名
  	Gender string // 性别
  	Age    int    // 年龄
  	string        // 匿名字段
  }
  
  type Student struct {
  	Human     // 匿名字段
  	Room  int // 教室
  	int       // 匿名字段
  }
  
  func main() {
  	//使用new方式
  	stu := new(Student)
  	stu.Room = 102
  	stu.Human.name = "Titan"
  	stu.Gender = "男"
  	stu.Human.Age = 14
  	stu.Human.string = "Student"
  
  	fmt.Println("stu is:", stu)
  	fmt.Printf("Student.Room is: %d\n", stu.Room)
  	fmt.Printf("Student.int is: %d\n", stu.int) // 初始化时已自动给予零值：0
  	fmt.Printf("Student.Human.name is: %s\n", stu.name) //  (*stu).name
  	fmt.Printf("Student.Human.Gender is: %s\n", stu.Gender)
  	fmt.Printf("Student.Human.Age is: %d\n", stu.Age)
  	fmt.Printf("Student.Human.string is: %s\n", stu.string)
  
  	// 使用结构体字面量赋值
  	stud := Student{Room: 102, Human: Human{"Hawking", "男", 14, "Monitor"}}
  
  	fmt.Println("stud is:", stud)
  	fmt.Printf("Student.Room is: %d\n", stud.Room)
  	fmt.Printf("Student.int is: %d\n", stud.int) // 初始化时已自动给予零值：0
  	fmt.Printf("Student.Human.name is: %s\n", stud.Human.name)
  	fmt.Printf("Student.Human.Gender is: %s\n", stud.Human.Gender)
  	fmt.Printf("Student.Human.Age is: %d\n", stud.Human.Age)
  	fmt.Printf("Student.Human.string is: %s\n", stud.Human.string)
  }
  ```
  
  </details> 
<details>
<summary>Day010: 语法-Go基本语法</summary>

- [x] 本节说明：本节介绍表达式、语句和简单语句的相关内容。

- [x] Go语言语法介绍：

  - 一个表达式表示一个值，而一条语句表示一个操作。 
  - 和很多其它流行语言一样，Go也支持break、continue和goto等跳转语句。 另外，Go 还支持一个特有的fallthrough跳转语句。
  
- [x] 简单语句类型：

  - 变量短声明语句。
  - 纯赋值语句，包括x op= y这种运算形式。
  - 有返回结果的函数或方法调用，以及通道的接收数据操作。 
  - 通道的发送数据操作。
  - 空语句。
  - 自增（x++）和自减（x--）语句。
  
- [ ] 非简单语句类型：
  
  - 标准变量声明语句。
  - 常量声明语句。
  - 类型声明语句。
  - 包引入语句。
  - 显式代码块。
  - 函数声明。 
  - 流程控制跳转语句。
  - 函数返回（return）语句。
  - 延迟函数调用和协程创建语句。
  
- [ ] 三种基本的流程控制：
  
  - if-else条件分支代码块。
  - switch-case多条件分支代码块
  - for循环代码块。
  
- [ ] 特定类型相关的流程控制代码块：
  
  - 容器类型相关的for-range循环代码块。
  - 接口类型相关的type-switch多条件分支代码块。
  - 通道类型相关的select-case多分支代码块。
  
- [ ] 本节案例
  
  </details>
<details>
<summary>Day011: 语句-Go运算符号</summary>

- [x] 本节说明：本节介绍Go运算符相关内容。

- [x] Go运算符：

  - Go语言不需要在语句或声明后面是有分号结尾。
  
- [x] 算术运算符：

  | 算术运算符 | 描述 | 实例               |
  | :--------- | :--- | :----------------- |
  | +          | 相加 | A + B 输出结果 30  |
  | -          | 相减 | A - B 输出结果 -10 |
  | *          | 相乘 | A * B 输出结果 200 |
  | /          | 相除 | B / A 输出结果 2   |
  | %          | 求余 | B % A 输出结果 0   |
  | ++         | 自增 | A++ 输出结果 11    |
  | --         | 自减 | A--   输出结果 9   |

- [x] 比较运算符：

  | 运算符 |                             描述                             | 实例              |
  | :----- | :----------------------------------------------------------: | :---------------- |
  | ==    |    检查两个值是否相等，如果相等返回 True 否则返回 False。    | (A == B) 为 False |
  | !=     |  检查两个值是否不相等，如果不相等返回 True 否则返回 False。  | (A != B) 为 True  |
  | >      |  检查左边值是否大于右边值，如果是返回 True 否则返回 False。  | (A > B) 为 False  |
  | <      |  检查左边值是否小于右边值，如果是返回 True 否则返回 False。  | (A < B) 为 True   |
  | >=    | 检查左边值是否大于等于右边值，如果是返回 True 否则返回 False。 | (A >= B) 为 False |
  | <=     | 检查左边值是否小于等于右边值，如果是返回 True 否则返回 False。 | (A <= B) 为 True |
  
- [x] 逻辑运算符：

  - Go支持两种布尔二元运算符和一种布尔一元运算符。
  
  | 运算符 |  描述  |        实例        |
  | :----: | :----: | :----------------: |
  |   &&   | 逻辑与 | (A && B) 为 False  |
  |  \|\|  | 逻辑或 | (A \|\| B) 为 True |
  |   !    | 逻辑非 | !(A && B) 为 True  |
  
- [x] 位运算符：

  位运算符对整数在内存中的二进制位进行操作。 下表列出了位运算符 &，|，和 ^ 的计算：
  
  | p    | q    | p & q | p \| q | p ^ q |
  | :---  | :--- | :---- | :----- | :---: |
  | 0    | 0    | 0     | 0      |   0   |
  | 0    | 1    | 0     | 1      |   1   |
  | 1    | 1    | 1     | 1      |   0   |
  | 1    | 0    | 0     | 1      |   1   |
  
  | 运算符 |                    描述                    |                  实例                  |
  | :----: | :----------------------------------------: | :------------------------------------: |
  |   &    | 其功能是参与运算的两数各对应的二进位相与。 | (A & B) 结果为 12, 二进制为 0000 1100  |
  |   \|   |  其功能是参与运算的两数各对应的二进位相或  | (A \| B) 结果为 61, 二进制为 0011 1101 |
  |   ^    | 二进位相异或，两对应的二进位相异时结果为1  | (A ^ B) 结果为 49, 二进制为 0011 0001  |
  |   <<   |                                            | A << 2 结果为 240 ，二进制为 1111 0000 |
  |   >>   |                                            |       A >> 2 结果为 15 ，二进制        |
  
- [x] 赋值运算符：

  | 运算符 |       描述       |                 实例                  |
  | :----: | :--------------: | :-----------------------------------: |
  |   =    | 简单的赋值运算符 | C = A + B 将 A + B 表达式结果赋值给 C |
  |   +=   |   相加后再赋值   |         C += A 等于 C = C + A         |
  |   -=   |   相减后再赋值   |         C -= A 等于 C = C - A         |
  |   *=   |   相乘后再赋值   |         C *= A 等于 C = C * A         |
  |   /=   |   相除后再赋值   |         C /= A 等于 C = C / A         |
  |   %=   |   求余后再赋值   |         C %= A 等于 C = C % A         |
  |  <<=   |    左移后赋值    |        C <<= 2 等于 C = C << 2        |
  |  >>=   |    右移后赋值    |        C >>= 2 等于 C = C >> 2        |
  |   &=   |   按位与后赋值   |         C &= 2 等于 C = C & 2         |
  |   ^=   |  按位异或后赋值  |         C ^= 2 等于 C = C ^ 2         |
  |  \|=   |   按位或后赋值   |        C \|= 2 等于 C = C \| 2        |
  
- [x] 其他运算符：

  | 运算符 | 描述             |            实例            |
  | :----- | :--------------- | :------------------------: |
  | &      | 返回变量存储地址 | &a; 将给出变量的实际地址。 |
  | *      | 指针变量。       |     *a; 是一个指针变量     |
  
- [x] 运算符优先级：
  
  | 优先级 |      运算符      |
  | :----: | :--------------: |
  |   5    | * / % << >> & &^ |
  |   4    |     + - \| ^     |
  |   3    | == != < <= > >=  |
  |   2    |        &&        |
  |   1    |       \|\|       |
  
- [ ] 几个特殊运算符：

  - 位清除 &^：将指定位置上的值设置为 0。将运算符左边数据相异的位保留，相同位清零 ：

- [ ] 本节案例：

  
  </details>
<details>
<summary>Day012: 语句-Go条件判断</summary>

- [x] 本节说明：本节介绍Go语言条件判断语句的相关内容。

- [x] 条件判断语句介绍：

  - 条件语句需要指定一个或多个条件，通过测试条件是否为 true 来决定是否执行指定语句，当条件为 false 的情况在执行另外的语句。
  
- [x] if语句：

  - if 语句用于测试某个条件（布尔型或逻辑型）的语句。由一个布尔表达式或关系运算符后紧跟一个或多个语句组成。

    ```go
    if 布尔表达式 {
       /* 在布尔表达式为 true 时执行 */
    }
    ```

- [x] if...else 语句：

  - if 语句后可以使用可选的else语句, else语句中的表达式在布尔表达式为 false 时执行。

    ```go
    if 布尔表达式 {
       /* 在布尔表达式为 true 时执行 */
    } else {
      /* 在布尔表达式为 false 时执行 */
    }
    ```

- [x] if 嵌套语句：

  - 你可以在 if 或 else if 语句中嵌入一个或多个 if 或 else if 语句。

    ```go
    if 布尔表达式 1 {
       /* 在布尔表达式 1 为 true 时执行 */
       if 布尔表达式 2 {
          /* 在布尔表达式 2 为 true 时执行 */
       }
    }
    ```

  - 三层嵌套。

    ```go
    if condition1 {
    	// do something	
    } else if condition2 {
    	// do something else	
    } else {
    	// catch-all or default
    }
    ```

- [x] if条件判断语句案例：

  - 案例1：

    ```go
    if a := 10; a == 10 {
    	fmt.Println("=10")
    } else if a > 10 {
    	fmt.Println(">10")
    } else if a < 10 {
    	fmt.Println("<10")
    } else {
        fmt.Println("这是不可能的!")
    }
    ```

  - 案例2

    ```go
    if a := 10; a == 10 {
    	fmt.Println("10")
    } else {
    	fmt.Println("not 10")
    }
    ```

  - 案例3

    ```go
    a := 10 // 初始化赋值语句
    if a == 10 {
    	fmt.Println("10")
    } else {
    	fmt.Println("not 10")
    }
    ```

- [x] switch 语句：

  - switch语句是存在多个条件判断的情况下，分别执行其对应的语句。

  - switch语句默认情况下 case 最后自带 break 语句，匹配成功后就不会执行其他 case。

  - 如果我们需要执行后面的 case，可以使用 fallthrough 。

  - switch后面可以写变量本身。和case后面的变量进行比较之后进行执行对应语句。

    ```go
    switch var1 { 
        case val1:
            ...
        case val2:
            ...
        default:
            ...
    }
    ```

  - 任何支持进行相等判断的类型都可以作为测试表达式的条件，包括 int、string、指针等。

    ```go
    package main
    
    import "fmt"
    
    func main() {
    	var num1 int = 7
    
    	switch { //无条件执行
    	    case num1 < 0:
    		    fmt.Println("Number is negative")
    	    case num1 > 0 && num1 < 10:
    		    fmt.Println("Number is between 0 and 10")
    	    default:
    		    fmt.Println("Number is 10 or greater")
    	}
    }
    ```

- [ ] [switch 参考1](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/05.3.md)

- [x] select 语句：

  - select 结构，用于 channel 的选择。
  - select 是 Go 中的一个控制结构，类似于 switch 语句。每个 case 必须是一个通信操作，要么是发送要么是接收。
  - select 随机执行一个可运行的 case。如果没有 case 可运行，它将阻塞，直到有 case 可运行。一个默认的子句应该总是可运行的。
  - select没有条件表达式，一直在等待分支进入可运行状态。

    ```go
    select {
        case communication clause  :
           statement(s);      
        case communication clause  :
           statement(s);
        /* 你可以定义任意数量的 case */
        default : /* 可选 */
           statement(s);
    }
    ```

  注意：Go 没有三目运算符，所以不支持 ?: 形式的条件判断。

- [ ] [select参考1](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/05.1.md)
  
- [ ] 本节案例：
  
  
  </details>
<details>
<summary>Day013: 语句-Go循环语句</summary>

- [x] 本节说明：本节介绍Go语言循环语句的相关内容。
- [x] Go循环语句：

  - 在Go语言中只有for循环一种循环结构。
  - 在实际问题中有大量的具有规律性的重复操作，在程序开发中便需要重复执行某些语句。

- [x] for循环：重复执行语句

  - Go语言中只有 for 结构可以重复执行某些语句。
  - for循环是一个循环控制结构，可以执行指定次数的循环。
  - Go语言的for循环有 3 种形式，只有其中的一种使用分号。

  - **基于计数器的迭代**：

    ```go
    for  初始化条件; 判断条件; 条件变化 {}
    for init; condition; post { }
    // init： 一般为赋值表达式，给控制变量赋初值；
    // condition： 关系表达式或逻辑表达式，循环控制条件；
    // post： 一般为赋值表达式，给控制变量增量或减量。
    // 在循环中同时使用多个计数器：
    for i, j := 0, N; i < j; i, j = i+1, j-1 {}
    ```

    ```go
    package main
    
    import "fmt"
    
    func main() {
    	for i := 0; i < 5; i++ {
    		fmt.Printf("This is the %d iteration\n", i)
    	}
    }
    ```

  - **基于条件判断的迭代**：

    ```go
    package main
    
    import "fmt"
    
    func main() {
    	var i int = 5
    
    	for i >= 0 {
    		i = i - 1
    		fmt.Printf("The variable i is now: %d\n", i)
    	}
    }
    ```

  - **无限循环：**

    条件语句是可以被省略的，如 i:=0; ; i++ 或 for { } 或 for ;; { }（;; 会在使用 gofmt 时被移除）：这些循环的本质就是无限循环。最后一个形式可以被改写为 for true { }，但一般情况下都会直接写

    ```go
    for { }
    ```

    ```go
    for t, err = p.Token(); err == nil; t, err = p.Token() {
    	...
    }
    ```

    ```go
    package main
    
    import "fmt"
    
    func main() {
            sum := 0
            for {
                sum++ // 无限循环下去
            }
            fmt.Println(sum) // 无法输出
    }
    ```

  - **for-range 结构：**

    for 循环的 range 格式可以对 slice、map、数组、字符串等进行迭代循环。

    在循环中可以同时使用多个计数器：

    ```go
    for key, value := range oldMap {
        newMap[key] = value
    }
    ```

    ```go
    package main
    import "fmt"
    
    func main() {
            strings := []string{"google", "runoob"}
            for i, s := range strings {
                    fmt.Println(i, s)
            }
            numbers := [6]int{1, 2, 3, 5}
            for i,x:= range numbers {
                    fmt.Printf("第 %d 位 x 的值 = %d\n", i,x)
            }  
    }
    ```

- [x] 循环嵌套：在循环内使用循环。

  - 使用方法：

    ```go
    for [condition |  ( init; condition; increment ) | Range]
    {
       for [condition |  ( init; condition; increment ) | Range]
       {
          statement(s);
       }
       statement(s);
    }
    ```

  - 使用循环嵌套来输出 2 到 100 间的素数：

    ```go
    package main
    import "fmt"
    func main() {
       /* 定义局部变量 */
       var i, j int
       for i=2; i < 100; i++ {
          for j=2; j <= (i/j); j++ {
             if(i%j==0) {
                break; // 如果发现因子，则不是素数
             }
          }
          if(j > (i/j)) {
             fmt.Printf("%d  是素数\n", i);
          }
       }  
    }
    ```

- [x] 循环控制语句：

  - break 语句：

    break可用于for、switch、select语句中。

    用于循环语句中跳出循环，并开始执行循环之后的语句。

    break 在 switch（开关语句）中在执行一条 case 后跳出语句的作用。

    在多重循环中，可以用标号 label 标出想 break 的循环。

    ```go
    break
    ```

    ```go
    for {
    	i = i - 1
    	fmt.Printf("The variable i is now: %d\n", i)
    	if i < 0 {
    		break
    	}
    }
    ```

    ```go
    i := 0
    for { // for循环条件永真，会一直循环
    	if i >= 10 { // if条件判断i是否大于10
    	break // if大于10的话就break跳出for循环
    	}
    	i++ // i+1
    	g.Println(i) // 打印i
    }
    ```

  - continue语句：

    continue只能用于for循环。跳过当前循环执行下一次循环语句。

    for 循环中，执行 continue 语句会触发 for 增量语句的执行。

    在多重循环中，可以用标号 label 标出想 continue 的循环。

    ```go
    continue
    ```

    ```go
    package main
    
    func main() {
    	for i := 0; i < 10; i++ {
    		if i == 5 { // 判断i等于5时跳出for循环
    			continue
    		}
    		print(i)
    		print(" ")
    	}
    }
    ```

  - goto 语句：

    Go语言的 goto 语句可以无条件地转移到过程中指定的行。

    goto语句可以用在任何地方，但是不能跨函数使用。

    goto 语句通常与条件语句配合使用。可用来实现条件转移， 构成循环，跳出循环体等功能。

    但是，在结构化程序设计中一般不主张使用 goto 语句， 以免造成程序流程的混乱，使理解和调试程序都产生困难。
    
    ```go
    goto End  //goto是关键字，End是用户起的名字，叫做标签
    .......
    End:
  	fmt.Print("aaa")
    ```
    
    ```go
    package main
    
    func main() {
    	i:=0
    	HERE:
    		print(i)
    		i++
    		if i==5 {
    			return // 跳出函数
    		}
    		goto HERE
    }
    ```

  - return语句：

    如果 return 语句使用在普通的 函数 中，则表示跳出该函数，不再执行函数中 return 后面的代码，可以理解成终止函数。

    如果 return 语句使用在 main 函数中，表示终止 main 函数，也就是终止程序的运行。

- [ ] 本节案例： 
  
  
  </details> 
<details>
<summary>Day014: 函数-Go语言函数</summary>

- [x] 本节说明：本节介绍Go语言函数的相关内容。

- [x] Go语言函数介绍：

  - 在Go语言中，函数是一等公民类型。换句话说，可以把函数当作值来使用。
  - 函数是基本的代码块，用于执行一个任务。Go语言最少需要有 main函数。
  - main函数是在启动后第一个执行的函数（如果有 init函数则会先执行该函数）。main函数没有参数，没有返回类型。
  - Go语言是编译型语言，函数编写的顺序是无关紧要的。但鉴于可读性的需求，最好把main函数写在文件的前面，其他函数按照一定逻辑顺序进行编写（例如函数被调用的顺序）。
  - Go语言标准库提供了多种内置函数。不需要导入包，可直接使用。
  - 目前Go语言没有泛型（generic）的概念，也就是不支持支持多种类型的函数。

- [x] Go语言有三种类型的函数：

  - 普通的带有名字的函数。
  - 匿名函数或者lambda函数。
  
  - 方法（Methods）。
  
- [x] 函数声明定义：
  - 函数声明告诉了编译器，函数的名称，返回类型和参数。

  - Go语言函数不支持输入参数默认值。每个返回结果的默认值是它的类型的零值。

  - 任何一个函数都不能被声明在另一个函数体内。 虽然匿名函数可以定义在函数体内，但匿名函数定义不属于函数声明。

  - Go语言函数基本组成：关键字func、函数名、参数列表、返回值、函数体和返回语句。语法如下：
    ```GO
    func 函数名(参数) 返回类型{
      函数体
    }
    ```
    
  - 无参数无返回的函数：
  
    ```go
    func MyFunc(){
    }
    ```
    
  - 有参数无返回的函数：
  
    ```go
      func main() {
      	Myfunc("url", "t")
      }
      
      func Myfunc(aa, bb string) {
      	fmt.Println(aa)
      	fmt.Println(bb)
      }
    ```
  
  - 不定参数类型：不定参数只能是形参中的最后一个参数。
  
    ```go
      func Myfunc(args ...int) {
      	fmt.Println(aa)
      	fmt.Println(bb)
      }
    ```
  
  - 无参数有返回的函数：有返回值的函数需要通过return返回。
  
      ```go
        func MyFunc() int {
        }
      ```
  
  - 有参数有返回的函数：
  
      ```go
      func main() {
      	max, min := MaxAndMin(10, 20)
      	fmt.Println(max, min)
      }
      
      func MaxAndMin(a, b int) (max, min int) {
      	if a > b {
      		max = a
      		min = b
      	} else {
      		max = b
      		min = a
      	}
      	return
      }
      ```
  
- [x] 函数调用：

  - 已经声明的函数可以通过它的名称和一个实参列表来调用。

  - 函数的声明可以出现在它的调用之前，也可以出现在它的调用之后。

  - 函数调用可以被延迟执行或者在另一个协程（goroutine）中执行。

  - 当创建函数时，定义了函数需要做什么，通过调用该函数来执行指定任务。

  - 函数调用流程：先调用的函数后返回。先进后出。

  - 调用函数，向函数传递参数，并返回值。

    ```go
    pack1.Function(arg1, arg2, …, argn)
    ```
    
    上面的代码中Function 是 pack1 包里面的一个函数，括号里的是被调用函数的实参（argument）：这些值被传递给被调用函数的形参。
    
    ```go
    package main
    
    func main() {
        greeting()
    }
    
    func greeting() {
        println("aa")
    }
    ```
    
  - 一个函数也可以作为其他函数的参数。只要这个被调用函数的返回值个数、返回值类型和返回值的顺序与调用函数所需求的实参是一致的。

  - 函数也可以以申明的方式被使用，作为一个函数类型，就像：

      ```go
      type binOp func(int, int) int
      ```

      这里不需要函数体 {}。


  - 函数是一等值（first-class value）：它们可以赋值给变量，就像 add := binOp 一样。

- [x] 函数参数：
  - 函数定义时，它的形参一般是有名字的，不过我们也可以定义没有形参名的函数，只有相应的形参类型，就像这样：func f(int, int, float64)。
  - 函数如果使用参数，该变量可称为函数的形参。形参就像定义在函数体内的局部变量。
  - 没有参数的函数通常被称为niladic函数（niladic function），就像main.main()。
  - 调用函数，可以通过两种方式来传递参数：

    1、按值传递(call by value)：值传递是指在调用函数时将实际参数复制一份传递到函数中，这样在函数中如果对参数进行修改，将不会影响到实际参数。

    2、按引用传递(call by reference)：引用传递是指在调用函数时将实际参数的地址传递到函数中，那么在函数中对参数所进行的修改，将影响到实际参数。

    ```go
    package main
    
    import "fmt"
    
    func main() {
        fmt.Printf("Multiply 2 * 5 * 6 = %d\n", MultiPly3Nums(2, 5, 6))
        // var i1 int = MultiPly3Nums(2, 5, 6)
        // fmt.Printf("MultiPly 2 * 5 * 6 = %d\n", i1)
    }
    
    func MultiPly3Nums(a int, b int, c int) int {
        // var product int = a * b * c
        // return product
        return a * b * c
    }
    ```

- [x] 函数返回值：

  - Go语言的函数通常情况下会有多个返回值。

  - 尽量使用命名返回值：这样会使代码更清晰、更简短，更加容易读懂。

  - 一个例子：

    ```go
    package main
    import "fmt"
    func swap(x, y string) (string, string) {
       return y, x
    }
    func main() {
       a, b := swap("Google", "Runoob")
     fmt.Println(a, b)
    }
    ```

- [ ] 延迟函数调用：

  - 在Go语言中，一个函数调用可以跟在一个defer关键字后面，形成一个延迟函数调用。 

  - 和协程调用类似，被延迟的函数调用的所有返回值必须全部被舍弃。
    
  - 当一个函数调用被延迟后，它不会立即被执行。它将被推入由当前协程维护的一个延迟调用堆栈。  
  - 延迟调用例子：

    ```go
    defer fmt.Println("3")
    defer fmt.Println("2")
    fmt.Println("1")
    // 打印 1 2 3
    ```

- [x] 回调函数：

  - 一个函数可以作为其它函数的参数进行传递，然后在其它函数内调用执行，一般称之为回调。

    ```go
    package main
    
    import (
    	"fmt"
    )
    
    func main() {
    	callback(1, Add)
    }
    
    func Add(a, b int) {
    	fmt.Printf("The sum of %d and %d is: %d\n", a, b, a+b)
    }
    
    func callback(y int, f func(int, int)) {
    	f(y, 2) // this becomes Add(1, 2)
    }
    ```

- [ ] 递归函数：

  - 函数自己调用自己。

- [x] 匿名函数：
  - 当我们不希望给函数起名字的时候，可以使用匿名函数，例如：func(x, y int) int { return x + y }。
  - 关键字 defer经常配合匿名函数使用，它可以用于改变函数的命名返回值。
  - 匿名函数同样被称之为闭包（函数式语言的术语）：它们被允许调用定义在其它环境下的变量。
  - 包可使得某个函数捕捉到一些外部状态，例如：函数被创建时的状态。
  - Go语言中的所有的自定义函数（包括声明的函数和匿名函数）都可以被视为闭包。一个闭包继承了函数所声明时的作用域。这种状态（作用域内的变量）都被共享到闭包的环境中，因此这些变量可以在闭包中被操作，直到被销毁。
  - 一个匿名函数在定义后可以被立即调用。
  - 闭包经常被用作包装函数：它们会预先定义好 1 个或多个参数以用于包装。

    ```go
    func() {
    	sum := 0
    	for i := 1; i <= 1e6; i++ {
    		sum += i
    	}
    }()
    ```

- [x] 函数用法：
  - 函数作为另外一个函数的实参：函数定义后可作为另外一个函数的实参数传入。
  - 闭包：闭包是匿名函数，可在动态编程中使用。
  - 方法：方法就是一个包含了接受者的函数。

- [ ] 本节案例：

  

  </details>

<details>
<summary>Day015: 函数-Go语言方法</summary>

- [x] 本节说明：本节介绍Go语言方法相关内容。
- [x] Go语言方法介绍：
  - 方法是包含了接收者的函数。接受者可以是命名类型或者结构体类型的一个值或者是一个指针。
  - 在Go语言中，结构体就像是类的一种简化形式，Go 方法是作用在接收者（receiver）上的一个函数，接收者是某种类型的变量。因此方法是一种特殊类型的函数。
  - 接收者类型可以是（几乎）任何类型，不仅仅是结构体类型。任何类型都可以有方法，甚至可以是函数类型，可以是 int、bool、string 或数组的别名类型。但是接收者不能是一个接口类型，因为接口是一个抽象定义，但是方法却是具体实现。
  - 接收者不能是一个指针类型，但是它可以是任何其他允许类型的指针。
  - 一个类型加上它的方法等价于面向对象中的一个类。
  - Go语言支持一些面向对象编程特性，方法是这些所支持的一个特性。

- [ ] Go语言方法声明：

  - Go语言方法的申明和普通函数声明类似，在函数名前放一个变量，即是一个方法。这个附加的参数会将该函数附加到这种类型上，即相当于为这种类型定义了一个独占的方法。这个参数是接受者。
  - 在Go语言中，可以为类型T和*T显式地声明一个方法，其中类型T必须满足四个条件：`T`必须是一个定义类型；`T`必须和此方法声明定义在同一个代码包中；`T`不能是一个指针类型；`T`不能是一个接口类型。

- [ ] Go语言方法接受者：

  - 值接收者
  - 指针接收者

- [ ] Go语言方法案例：

  - 示例一：函数和方法的使用对比

    ```go
    package main
    
    import (
    	"fmt"
    	"math"
    )
    
    type Point struct{ X, Y float64 }
    
    // traditional function
    func Distance(p, q Point) float64 {
    	return math.Hypot(q.X-p.X, q.Y-p.Y)
    }
    
    // same thing, but as a method of the Point type
    func (p Point) Distance(q Point) float64 {
    	return math.Hypot(q.X-p.X, q.Y-p.Y)
    }
    
    func main() {
    	p := Point{1, 2}
    	q := Point{4, 6}
    	fmt.Println(Distance(p, q)) // "5", function call
    	fmt.Println(p.Distance(q))  // "5", method call
    }
    
    ```

  - 示例二：

    ```go
    package main
    
    import (
    	"fmt"
    )
    
    /* 定义结构体 */
    type Circle struct {
    	radius float64
    }
    
    func main() {
    	var c1 Circle
    	c1.radius = 10.00
    	fmt.Println("圆的面积 = ", c1.getArea())
    }
    
    //该 method 属于 Circle 类型对象中的方法
    func (c Circle) getArea() float64 {
    	//c.radius 即为 Circle 类型对象中的属性
    	return 3.14 * c.radius * c.radius
    }
    ```

- [ ] 参考链接：[方法参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_20_method.md)、[方法参考2](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/10.6.md)、[方法参考3](https://gfw.go101.org/article/method.html)
  
  </details>
<details>
<summary>Day016: 数据-Go语言接口</summary>

- [x] 本节说明：本节介绍Go语言接口(interface)的相关内容。
- [x] Go语言接口介绍：
  - Go语言接口类型是对其他类型行为的概括与抽象。
  
  - Go语言的接口非常灵活，通过接口可以实现很多面向对象的特性。
  
  - Go语言接口定义了一组方法，这些方法不包含具体实现代码。它们是抽象的。接口里也不能包含变量。  
  
  - Go语言中的所有类型包括自定义类型都实现了interface{}接口，所有的类型如string、 int、 int64甚至是自定义的结构体类型都拥有interface{}空接口，这一点interface{}和Java中的Object类比较相似。  
  
  - 一个接口可以包含一个或多个其他的接口，但是在接口内不能嵌入结构体，也不能嵌入接口自身。
  
  - 空接口interface{}可以被当做任意类型的数值。  
  
  - 接口的定义是非常棒的，而且也是实现Go语言中多态性的唯一途径。
  
  - Go语言中的接口都很简短，通常它们会包含0个或最多3个方法。  
  
  - 使用接口可以使代码更具有普适性。  
  
  - 接口类型的未初始化变量的值为nil。
  
    ```go
    var i interface{} = 99 // i可以是任何类型
    i = 44.09
    i = "All"  // i 可接受任意类型的赋值
    ```
  
- [x] Go语言接口定义：
  - 接口是一组抽象方法的集合，它必须由其他非接口类型实现，不能自我实现。Go 语言通过它可以实现很多面向对象的特性。通过如下格式定义接口：
  
    ```go
    type Namer interface {
        Method1(param_list) return_type
        Method2(param_list) return_type
        ...
    }
    ```
  
- [x] Go语言接口案例：

  - 示例1：

    ```go
    package main
    
    import "fmt"
    
    type Shaper interface {
    	Area() float32
    }
    
    type Square struct {
    	side float32
    }
    
    func (sq *Square) Area() float32 {
    	return sq.side * sq.side
    }
    
    func main() {
    	sq1 := new(Square)
    	sq1.side = 2
    
    	var areaIntf Shaper
    	areaIntf = sq1
    	fmt.Printf("The square has area: %f\n", areaIntf.Area())
    }
    
    ```
    
  - 示例2：接口嵌套接口。接口File包含了ReadWrite和Lock的所有方法，它还额外有一个Close()方法。
  
    ```go
    type ReadWrite interface {
        Read(b Buffer) bool
        Write(b Buffer) bool
    }
      
    type Lock interface {
          Lock()
          Unlock()
      }
      
      type File interface {
          ReadWrite
          Lock
          Close()
      }
    ```
  
- [ ] 接口排序：
  
  - 使用 Sorter 接口排序
  
- [ ] 参考链接：[接口参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_19_interface.md)、[接口参考2](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/11.1.md)、[接口参考3](https://gfw.go101.org/article/interface.html)
  
  </details>
<details>
<summary>Day017: 错误-Go错误处理</summary>

- [x] 本节说明：本节介绍Go语言中的错误处理。

- [x] 错误处理介绍：

  - Go语言中没有像 Java等语言的 try/catch异常机制，不能执行抛异常操作。但是有defer-panic-and-recover 机制。这种机制就是错误处理。
  - Go语言的设计者觉得try/catch 机制的使用太泛滥了，而且从底层向更高的层级抛异常太耗费资源。他们给Go语言设计的机制也可以 “捕捉” 异常，但是更轻量，并且只应该作为（处理错误的）最后的手段。
  - Go语言是怎么处理普通错误的呢？通过在函数和方法中返回错误对象作为它们的唯一或最后一个返回值——如果返回 nil，则没有错误发生——并且主调（calling）函数总是应该检查收到的错误。
  - Go语言检查和报告错误条件的惯有方式：
    - 产生错误的函数会返回两个变量，一个值和一个错误码；如果后者是 nil 就是成功，非 nil 就是发生了错误。
    - 为了防止发生错误时正在执行的函数（如果有必要的话甚至会是整个程序）被中止，在调用函数后必须检查错误。
  
- [x] 错误处理：

  - Go 有一个预先定义的 error 接口类型：
  
    ```go
    type error interface {
    	Error() string
    }
    ```
  
- [ ] 定义错误：

- [ ] [错误参考1](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/13.1.md)

- [ ] 本节案例：

  </details>
<details>
<summary>Day018: 并发-Go语言并发</summary>

- [x] 本节说明：本节介绍Go语言并发协程(goroutine)相关内容。

- [x] 协程goroutine介绍：

  - Go语言原生支持应用之间的通信（网络，客户端和服务端，分布式计算）和程序的并发。
    - 不要通过共享内存来通信，而通过通信来共享内存。 
    - Go语言协程比其他语言协程更强大，也很容易从协程的逻辑复用到Go协程。
    - 在Go语言中，协程是创建计算的唯一途径。
    - Go语言不支持创建系统线程，协程是一个Go程序内部唯一的并发实现方式。
  
- [ ] 协程goroutine用法：

  - 使用go关键字。
  - 启动一个新的协程时，协程的调用会立即返回。与函数不同，程序控制不会去等待 Go 协程执行完毕。在调用 Go 协程之后，程序控制会立即返回到代码的下一行，忽略该协程的任何返回值。
  - 如果希望运行其他 Go 协程，Go 主协程必须继续运行着。如果 Go 主协程终止，则程序终止，于是其他 Go 协程也不会继续运行。

- [x] 协程goroutine案例：

  - 案例一：使用延时来返回协程的返回值

    ```go
    func main() {	
    	start := time.Now()
    	go tester()
    	time.Sleep(1 * time.Millisecond)
    	end := time.Now()
    	delta := end.Sub(start)
    	g.Println(delta)
    }
    
    func tester() {
    	i := 0
    HERE:
    	g.Println(i)
    	i++
    	if i == 10 {
    		return
    	}
    	goto HERE
    }
    ```

- [ ] 恐慌：一些致命性错误不属于恐慌。对于官方标准编译器来说，很多致命性错误（比如堆栈溢出和内存不足）不能被恢复。它们一旦产生，程序将崩溃。

  - 产生一个恐慌
  - 消除一个恐慌

- [ ] 恢复：

- [x] 参考链接：[协程参考1](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/14.1.md)、[协程参考2](https://gfw.go101.org/article/control-flows-more.html)

- [ ] 本节案例：
  
  </details>
<details>
<summary>Day019: 并发-Go语言通道</summary>

- [x] 本节说明：本节介绍Go语言通道(channel)的相关内容。

- [x] 通道channel介绍：
  - Go语言设计团队的首任负责人Rob Pike对并发编程的一个建议是：**不要让计算通过共享内存来通讯，而应该通过通讯来共享内存**。 通道就是这种哲学的一个设计结果。在Go语言中，可以认为一个计算就是一个协程。channel是协程之间互相通信的通道，协程之间可以通过它发送消息和接收消息。
  - 通过共享内存来通讯和通过通讯来共享内存是并发编程中的两种编程风格。
  - 一个通道可以看作是在一个程序内部的一个先进先出（FIFO：first in first out）数据队列。 一些协程可以向此通道发送数据，另外一些协程可以从此通道接收数据。
  - 通道是Go语言中的一等公民类型，是Go语言的招牌特性之一。 和协程一起使用，这两个招牌特性使得使用Go进行并发编程变得方便和有趣，降低了并发编程的难度。通道的主要作用是用来实现并发同步。
  - 通道是进程内的通信方式，因此通过通道传递对象的行为与函数调用时参数传递行为比较一致，比如也可以传递指针等。
  - 通道可以想像成Go语言协程之间通信的管道。如同管道中的水会从一端流到另一端，通过使用信道，数据也可以从一端发送，在另一端接收。  
  - 通道的一个问题是通道的编程体验常常很有趣以至于程序员们经常在并非是通道的最佳应用场景中仍坚持使用通道。
  
- [ ] 通道类型和值：
  - 和数组、切片以及映射类型一样，每个通道类型也有一个元素类型。 一个通道只能传送它的（通道类型的）元素类型的值。
  - 通道可以是双向的，也可以是单向的。
    1、字面形式`chan T`表示一个元素类型为`T`的双向通道类型。 编译器允许从此类型的值中接收和向此类型的值中发送数据。 
    2、字面形式`chan<- T`表示一个元素类型为`T`的单向发送通道类型。 编译器不允许从此类型的值中接收数据。
    3、字面形式`<-chan T`表示一个元素类型为`T`的单向接收通道类型。 编译器不允许向此类型的值中发送数据。
  - 一个非零通道值必须通过内置的make函数来创建。 比如make(chan int, 10)将创建一个元素类型为int的通道值。 第二个参数指定了欲创建的通道的容量。此第二个实参是可选的，它的默认值为0。

- [ ] 通道值的比较：  
  
  - 所有通道类型均为可比较类型。比较这两个通道的结果为布尔值。  
  
- [ ] 通道操作：
  - 同一个操作符 <- 既用于发送也用于接收，但Go会根据操作对象弄明白该干什么。  
  - Go语言中有五种通道相关的操作。假设一个通道为ch，下面列出了这五种操作的语法或者函数调用：
    1、调用内置函数close来关闭一个通道：

    ```go
    close(ch)
    ```
    2、向通道ch发送一个值v。ch不能为单向接收通道。<-称为数据发送操作符。
    ```go
    ch <- v
    ```
    3、从通道ch接收一个值。
    ```go
    <-ch
    ```
    4、查询一个通道的容量。
    ```go
    cap(ch)
    ```
    5、查询一个通道的长度。
    ```go
    len(ch)
    ```
  - 通道可以分为三类：
    1、零值（nil）通道。
    2、非零值但已关闭的通道。
    3、非零值并且尚未关闭的通道。

  |   操作   | 一个零值nil通道 | 一个非零值但已关闭的通道 | 一个非零值且尚未关闭的通道 |
  | :------: | :-------------: | :----------------------: | :------------------------: |
  |   关闭   |    产生恐慌     |         产生恐慌         |        成功关闭(C)         |
  | 发送数据 |    永久阻塞     |         产生恐慌         |    阻塞或者成功发送(B)     |
  | 接收数据 |    永久阻塞     |       永不阻塞(D)        |    阻塞或者成功接收(A)     |

- [ ] 死锁：

- [ ] 恐慌绝望：

- [ ] 通道案例：
  - 通道案例一：

    ```go
    package main
     
    import (  
        "fmt"
    )
     
    func hello(done chan bool) {  
        fmt.Println("Hello world goroutine")
        done <- true
    }
    func main() {  
        done := make(chan bool)
        go hello(done)
        <-done
        fmt.Println("main function")
    }
    ```

  - 通道案例二：
  
    ```go
    package main
    
    import (
    	"fmt"
    	"time"
    )
    
    func main() {
    	c := make(chan int) // 一个非缓冲通道
    	go func(ch chan<- int, x int) {
    		time.Sleep(time.Second)
    		// <-ch    // 此操作编译不通过
    		ch <- x*x  // 阻塞在此，直到发送的值被接收
    	}(c, 3)
    	done := make(chan struct{})
    	go func(ch <-chan int) {
    		n := <-ch      // 阻塞在此，直到有值发送到c
    		fmt.Println(n) // 9
    		// ch <- 123   // 此操作编译不通过
    		time.Sleep(time.Second)
    		done <- struct{}{}
    	}(c)
    	<-done // 阻塞在此，直到有值发送到done
    	fmt.Println("bye")
    }
    ```
  
  - 通道案例三：
  
    ```go
    package main
    
    import "fmt"
    
    func main() {
    	c := make(chan int, 2) // 一个容量为2的缓冲通道
    	c <- 3
    	c <- 5
    	close(c)
    	fmt.Println(len(c), cap(c)) // 2 2
    	x, ok := <-c
    	fmt.Println(x, ok) // 3 true
    	fmt.Println(len(c), cap(c)) // 1 2
    	x, ok = <-c
    	fmt.Println(x, ok) // 5 true
    	fmt.Println(len(c), cap(c)) // 0 2
    	x, ok = <-c
    	fmt.Println(x, ok) // 0 false
    	x, ok = <-c
    	fmt.Println(x, ok) // 0 false
    	fmt.Println(len(c), cap(c)) // 0 2
    	close(c) // 此行将产生一个恐慌
    	c <- 7   // 如果上一行不存在，此行也将产生一个恐慌。
    }
    ```
  
  - 通道案例四：
  
    ```go
    package main
    
    import (
    	"fmt"
    	"time"
    )
    
    func main() {
    	var ball = make(chan string)
    	kickBall := func(playerName string) {
    		for {
    			fmt.Print(<-ball, "传球", "\n")
    			time.Sleep(time.Second)
    			ball <- playerName
    		}
    	}
    	go kickBall("张三")
    	go kickBall("李四")
    	go kickBall("王二麻子")
    	go kickBall("刘大")
    	ball <- "裁判"   // 开球
    	var c chan bool // 一个零值nil通道
    	<-c             // 永久阻塞在此
    }
    ```
  
  - 通道案例五：
  
    ```go
    // chanmain
    package main
    
    import (
    	"fmt"
    )
    
    func main() {
    	done := make(chan bool)
    	data := make(chan int)
    	go xfz(data, done)
    	go scz(data)
    	<-done
    
    }
    
    func xfz(data chan int, done chan bool) {
    	for x := range data {
    		fmt.Println("recv:", x)
    	}
    	done <- true
    }
    
    func scz(data chan int) {
    	for i := 0; i < 100; i++ {
    		data <- i
    	}
    	close(data)
    }
    ```
  
- [ ] 本节参考：[通道参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_22_channel.md)、[通道参考2](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/14.2.md)、[通道参考3](https://blog.csdn.net/ytd7777/article/details/85004371)、[通道参考4](https://gfw.go101.org/article/channel.html)

- [ ] 本节案例：


  </details>

## 0x02-Go语言进阶

<details>
<summary>Day023: 测试-Go语言测试</summary>

- [ ] 本节说明：本节介绍Go语言测试的相关内容。

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  </details>
<details>
<summary>Day024: 进阶-Go同步与锁</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  </details>
<details>
<summary>Day024: 对象-Go面向对象</summary>

- [x] 本节说明：本节介绍Go语言面向对象的相关内容。

- [ ] Go面向对象：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [ ] [面向对象参考1](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/11.13.md)

- [ ] 本节案例：

  
  </details>
<details>
<summary>Day025: 数据-Go语言反射</summary>

- [x] 本节说明：本节介绍Go语言反射(reflect)相关内容。

- [ ] 反射概念介绍：
  
  - 在计算机科学中，反射是指计算机程序在运行时（Run time）可以访问、检测和修改它本身状态或行为的一种能力。用比喻来说，反射就是程序在运行的时候能够“观察”并且修改自己的行为。
  
- [ ] Go语言反射介绍：
  
  - 反射是程序执行时检查其所拥有的结构。尤其是类型的一种能力。是元编程的一种形式。  
  
- [ ] [反射参考1](http://c.biancheng.net/golang/reflect/)、[反射参考2](https://www.cnblogs.com/qcrao-2018/p/10822655.html)、

- [ ] 本节案例：

  </details>
<details>
<summary>Day026: 泛型-Go语言泛型</summary>

- [ ] 本节说明：本节介绍Go语言中泛型的相关内容。

- [x] 泛型介绍：

  - 泛型程序设计（generic programming）是程序设计语言的一种风格或范式。泛型允许程序员在强类型程序设计语言中编写代码时使用一些以后才指定的类型，在实例化时作为参数指明这些类型。各种程序设计语言和其编译器、运行环境对泛型的支持均不一样。Ada、Delphi、Eiffel、Java、C#、F#、Swift和Visual Basic .NET称之为泛型（generics）；ML、Scala和Haskell称之为参数多态（parametric polymorphism）；C++和D称之为模板。具有广泛影响的1994年版的《Design Patterns》一书称之为参数化类型（parameterized type）。
  - 泛型就是把类型当成参数。
  
- [x] Go语言中的泛型：

  - Go目前不支持自定义泛型。
  - 泛型指日可待！
  
- [ ] 泛型的优点？为什么需要泛型？

- [ ] 本节案例：

  </details>
<details>
<summary>Day027: 进阶-Go反序列化</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  
  </details>
<details>
<summary>Day028: 进阶-Go垃圾回收</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] [垃圾回收参考1](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/10.8.md)

- [ ] 本节案例：

  </details>
<details>
<summary>Day029: 函数-Go内置函数</summary>

- [x] 本节说明：本节介绍Go语言内置函数的相关内容。

- [x] Go内置函数介绍：

  - 不引入任何库包而调用一个内置函数。
  - 不需要进行导入操作就可以使用的内置函数。它们有时可以针对不同的类型进行操作，例如：len、cap 和 append，或必须用于系统级的操作，例如：panic。因此，它们需要直接获得编译器的支持。
  - 内置函数和自定义函数有很多差别。其中一个差别是很多内置函数支持泛型参数，但自定义函数不支持。
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 进阶-Go内存结构</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  </details>
<details>
<summary>Day000: 进阶-Go语言进阶</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  </details>

## 0x03-Go语言库包

​		本章节用来记录Go语言官方标准库的相关内容。包括很多具体的使用例子，初学者拿来即可使用，甚至不需要任何的修改。也包括优秀的第三方库，利用这些第三方库可以构建更完善的项目代码。

<details>
<summary>Day301: 库包-Go包的管理</summary>

- [x] 本节说明：本节介绍Go语言库包的相关内容。
- [x] Go语言标准库概述：
  - Go语言标准库就是Go包。需要import导入之后使用某些功能。
  - 像 fmt、os 等这样具有常用功能的内置包在Go语言中有 150 个以上，它们被称为标准库，大部分(一些底层的除外)内置于Go本身。
- [ ] 包发布：
- [ ] 本节案例：

  </details>
<details>
<summary>Day302: 库包-Go命令控制</summary>

- [x] 本节说明：本节介绍命令控制的相关内容。主要是flag标准库的使用。
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。   
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  </details>
<details>
<summary>Day303: 库包-Go请求响应</summary>

- [x] 本节说明：本节介绍Go语言中请求响应的内容。
- [x] HTTP请求响应：
  - 在漏洞利用或是在漏洞验证过程中， 经常使用到的一个方法就是对一个URL发送一个请求，然后从响应中获取相关数据来判断漏洞是否存在。
  - 本小节内容是漏洞验证中较为重要的部分。
- [ ] 请求响应包：

  - net/http 
- [x] 请求响应案例：
  - 访问并读取页面：
  
    ```go
    package main
    
    import (
    	"fmt"
    	"net/http"
    )
    
    var urls = []string{
    	"http://www.google.com",
    	"http://golang.org",
    	"http://blog.golang.org",
    }
    
    func main() {
    	for _, url := range urls {
    		resp, err := http.Head(url)
    		if err != nil {
    			fmt.Println("Error:", url, err)
    		}
    		fmt.Println(url, ": ", resp.Status)
    	}
    }
    ```
    
  - 发送get参数请求：
  - 发送post参数请求：
  - 发送cookie参数请求：  
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day304: 库包-Go配置文件</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。  
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go  
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day305: 库包-Go文本文件</summary>

- [x] 本节说明：本节介绍Go语言处理文本格式的相关内容。

- [x] Go文本处理：也就是处理TXT格式的文件。
  
  - 文本处理在Go开发中用到的比较多，在安全开发中经常会将文本文件的内容作为参数传递给函数，根据响应进行漏洞扫描与漏洞验证。  
  
- [x] 按行读取文本文件：

  - io/ioutil

  - 案例一：按行读取之按行打印内容

    ```go
    package main
    
    import (
        "fmt"
        "os"
    )
    
    func main() {
        userFile := "asatxie.txt"
        fl, err := os.Open(userFile)        
        if err != nil {
            fmt.Println(userFile, err)
            return
        }
        defer fl.Close()
        buf := make([]byte, 1024)
        for {
            n, _ := fl.Read(buf)
            if 0 == n {
                break
            }
            os.Stdout.Write(buf[:n])
        }
    }
    ```

  - 案例二：按行读取之按行打印内容

    ```go
    package main
    
    import (
    	"bufio"
    	"fmt"
    	"io"
    	"os"
    	"strings"
    )
    
    func main() {
    	fileName := "ip.txt"
    	file, err := os.OpenFile(fileName, os.O_RDWR, 0666)
    	if err != nil {
    		fmt.Println("Open file error!", err)
    		return
    	}
    	defer file.Close()
    
    	stat, err := file.Stat()
    	if err != nil {
    		panic(err)
    	}
    
    	var size = stat.Size()
    	fmt.Println("file size=", size)
    
    	buf := bufio.NewReader(file)
    	for {
    		line, err := buf.ReadString('\n')
    		line = strings.TrimSpace(line)
            // 实际编程中处理line即可
    		fmt.Println(line)
    		if err != nil {
    			if err == io.EOF {
    				fmt.Println("File read ok!")
    				break
    			} else {
    				fmt.Println("Read file error!", err)
    				return
    			}
    		}
    	}
    }
    
    ```

- [ ] 把文本文件作为参数：

- [ ] 把结果写入到文本文件中：

  - 案例一：

    ```go
    package main
    
    import (
    	"fmt"
    	"os"
    )
    
    func main() {
    	userFile := "astaxie.txt"
    	fout, err := os.Create(userFile)
    	if err != nil {
    		fmt.Println(userFile, err)
    		return
    	}
    	defer fout.Close()
    	for i := 0; i < 10; i++ {
    		fout.WriteString("Just a test!\r\n")
    		fout.Write([]byte("Just a test!\r\n"))
    	}
    }
    
    ```

  - 案例二：将值传递给domain即可

    ```go
    fileName := "is.txt"
    fd, _ := os.OpenFile(fileName, os.O_RDWR|os.O_CREATE|os.O_APPEND, 0644)
    s := strings.Join([]string{domain, "\t", "\n"}, "")
    buf := []byte(s)
    fd.Write(buf)
    fd.Close()
    ```

- [x] [读写数据参考1](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/12.0.md)、[文本处理参考1](http://c.biancheng.net/golang/102/)、[golang 逐行读取文件](https://www.cnblogs.com/rojas/p/4395866.html)、[Go语言文件读取的一些总结](https://segmentfault.com/a/1190000023691973)

- [ ] 本节案例：

  </details>

<details>
<summary>Day306: 库包-Go电子表格</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。  
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go 
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day307: 库包-Go数据入库</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。  
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go  
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day308: 库包-Go日志记录</summary>

- [x] 本节说明：本节是用来介绍Go日志的相关内容，包括日志记录等。

- [x] log标准库：

  ```go
  package main
  
  import (
  	"io"
  	"log"
  	"os"
  	"time"
  )
  
  func main() {
  	// 日志保存到文件中-开始
  	filename := time.Now().Format("app-20060102150405") + ".log"
  	f, err := os.OpenFile(filename, os.O_WRONLY|os.O_CREATE|os.O_APPEND, 0666)
  	if err != nil {
  		log.Fatal(err)
  	}
  	defer f.Close()
  	writers := []io.Writer{
  		f,
  		os.Stdout}
  	fileAndStdoutWriter := io.MultiWriter(writers...)
  	logger := log.New(fileAndStdoutWriter, "", log.Ldate|log.Ltime)
  	// 日志保存到文件中-结束
  
  	logger.Println("Hello World!")
  
  }
  ```

- [ ] 本节案例：
  
  </details>
<details>
<summary>Day309: 库包-Go错误处理</summary>

- [ ] 本节说明：
- [x] Go语言介绍： 
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day309: 库包-Go单元测试</summary>

- [ ] 本节说明：
- [x] Go语言介绍： 
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day310: 库包-Go协程任务</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day311: 库包-Go电子邮件</summary>

- [ ] 本节说明：本节介绍Go语言中电子邮件的发送内容。

- [x] net/smtp标准库：

  ```go
  package main
  
  import (
  	"bufio"
  	"encoding/base64"
  	"flag"
  	"fmt"
  	"io"
  	"log"
  	"net/smtp"
  	"os"
  	"strings"
  	"time"
  )
  
  //发送邮件的逻辑函数。这个例子大部分是66所写，感谢66。
  func SendMail(user, password, host, to, subject, body, mailtype string) error {
  	hp := strings.Split(host, ":")
  	auth := smtp.PlainAuth("", user, password, hp[0])
  	var content_type string
  	if mailtype == "html" {
  		content_type = "Content-Type: text/" + mailtype + "; charset=UTF-8"
  	} else {
  		content_type = "Content-Type: text/plain" + "; charset=UTF-8"
  	}
  
  	// msg := []byte("To: " + to + "\r\nFrom: " + user + "<" + user + ">\r\nSubject: " + subject + "\r\n" + content_type + "\r\n\r\n" + body)
  	msg := []byte("To: " + to + "\r\nFrom: " + "fajianren" + "<" + user + ">\r\nSubject: " + subject + "\r\n" + content_type + "\r\n\r\n" + body)
  
  	send_to := strings.Split(to, ";")
  	err := smtp.SendMail(host, auth, user, send_to, msg)
  	return err
  }
  
  func main() {
  	// 日志保存到文件中-开始
  	filename := time.Now().Format("20060102150405") + ".log"
  	f, err := os.OpenFile(filename, os.O_WRONLY|os.O_CREATE|os.O_APPEND, 0666)
  	if err != nil {
  		log.Fatal(err)
  	}
  	defer f.Close()
  	writers := []io.Writer{
  		f,
  		os.Stdout}
  	fileAndStdoutWriter := io.MultiWriter(writers...)
  	logger := log.New(fileAndStdoutWriter, "", log.Ldate|log.Ltime)
  	// 日志保存到文件中-结束
  
  	url := "http://127.0.0.1"
  
  	host := "smtp.163.com:25"
  	username := "username@163.com"
  	password := "password"
  
  	logger.Println("程序启动，准备发送邮件！")
  
  	var toFileList string
  
  	flag.StringVar(&toFileList, "f", "", "指定发送的文件，换行结束。")
  	flag.Parse()
  
  	if toFileList == "" {
  		fmt.Print("请通过参数 -f 指定接收的邮箱列表！")
  		return
  	}
  	if !strings.HasSuffix(url, "/") {
  		url += "/"
  	}
  	if toFileList != "" {
  		f, _ := os.Open(toFileList)
  		defer f.Close()
  		r := bufio.NewReader(f)
  		for {
  			if line, _, err := r.ReadLine(); err == nil {
  				email := string(line)
  				diaoyuurl := url + email[0:strings.Index(email, "@")]
  
  				subject := "=?UTF-8?B?" + base64.StdEncoding.EncodeToString([]byte("紧急通知：体检报名")) + "?="
  				body := "<p>全体同事：</p> <p>为了解和掌握员工健康状况、确保员工合理安排健康检查和职业病危害因素检测活动。</p> <p>本年度体检计划将进行调整，从8月开始将分批次安排员工进行上岗前职业健康检查以及在岗期间职业健康检查。</p> <p>请打开如下链接选择合适的时间进行体检报名。每个批次人数报满即止，报名时间截止9月3日。</p> <p>请尽快点击下面链接按照步骤进行报名！</p><a href=\"" + diaoyuurl + "\">第一步：点击填写报名信息</a></p></p><a href=\"http://127.0.0.1\">第二步：点击查看是否报名成功</a></p>"
  				logger.Println("准备 " + email + " 发送邮件！")
  				if err := SendMail(username, password, host, email, subject, body, "html"); err != nil {
  					logger.Println("邮件 "+email+" 发送失败！\n", err.Error())
  				} else {
  					logger.Println("邮件 " + email + " 发送成功！")
  					time.Sleep(time.Duration(3) * time.Second)
  					logger.Println("休眠 3 秒继续发送！请耐心等待！")
  				}
  			} else {
  				break
  			}
  		}
  	}
  	logger.Println("邮件已经全部发送完毕！")
  
  }
  ```

- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 库包-Go时间日期</summary>

- [ ] 本节说明：本节介绍Go语言中时间和日期的相关内容。
- [ ] Go语言时间操作：
- [ ] Go语言日期操作：
- [x] 一些具体使用的例子。
  - 计算函数执行时间：
  
    ```go
    start := time.Now()
    end := time.Now()
    delta := end.Sub(start)
    fmt.Printf("all time: %s\n", delta)
    ```
    
  - 计算日期差值：
  
- [ ] [时间日期参考1](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/04.8.md)、[时间日期参考2](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/06.11.md)

- [ ] 本节案例：

  </details>
<details>
<summary>Day000: 库包-Go输入输出</summary>

- [x] 本节说明：本节介绍Go语言中输入输出的相关内容。
- [x] Go语言输入输出： 
  
  - Go语言标准库就是Go包。需要import导入之后使用某些功能。  
- [ ] 输入案例参考：
  - 案例1：
  
    ```
    package main
    
    import (
    	"fmt"
    )
    
    func main() {
    	var a int
    	fmt.Printf("请输入a:")
    	fmt.Scanf("%d", &a)
    	//fmt.Scan(&a)
    	fmt.Println("a =", a)
    
    }
    ```
  
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 库包-Go正则匹配</summary>
- [x] 本节说明：本节介绍Go语言中正则匹配的相关内容。
- [x] Go语言正则匹配：
  - 在请求响应中经常会根据响应的内容作出判断及操作。也经常需要对响应的内容进行信息提取之后进行下一步的操作，操作的过程中会经常使用正则匹配的方法进行。  
- [x] Go语言命令：
  - go run hello.go //编译运行hello.go  
- [ ] 本节案例：

  </details>
<details>
<summary>Day000: 库包-Go精密计算</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。   
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go  
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 库包-Go读写数据</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。   
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  </details>
<details>
<summary>Day000: 库包-Go保存数据</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。   
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go  
- [ ] 本节案例：

  </details>
<details>
<summary>Day000: 库包-Go语言库包</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。   
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go  
- [ ] 本节案例：

  </details>
<details>
<summary>Day000: 库包-Go语言库包</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。   
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go  
- [ ] 本节案例：

  </details>
<details>
<summary>Day000: 库包-Go语言库包</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。   
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go  
- [ ] 本节案例：

  </details>
  
## 0x04-Go语言算法

<details>
<summary>Day000: 算法-Go排序算法</summary>

- [ ] 本节说明：
- [x] 排序算法介绍：
  
  - 递归函数、递归算法、
- [ ] Go排序算法：
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 算法-Go递归算法</summary>
- [ ] 本节说明：
- [x] 递归算法介绍：
  - 递归函数、递归算法、  
- [ ] Go递归算法： 
- [ ] 本节案例：

  </details>
<details>
<summary>Day000: 算法-Go分治算法</summary>

- [ ] 本节说明：
- [x] 分治算法介绍：
  
  - 递归函数、递归算法、  
- [ ] Go分治算法：  
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 算法-Go动态规划</summary>

- [ ] 本节说明：
- [x] 动态规划算法介绍：
  
  - 递归函数、递归算法  
- [ ] Go动态规划算法：  
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 算法-Go贪心算法</summary>

- [ ] 本节说明：
- [x] 贪心算法介绍：
  
  - 递归函数、递归算法  
- [ ] Go贪心算法：  
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 算法-Go二叉算法</summary>

- [ ] 本节说明：本节介绍二叉树算法的相关内容。
- [x] 二叉树算法介绍：
  
  - 递归函数、递归算法  
- [ ] Go贪心算法： 
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 算法-Go回溯算法</summary>

- [ ] 本节说明：
- [ ] 回溯算法介绍：
- [x] Go回溯算法：
  
  - 递归函数、递归算法、  
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 算法-Go搜索算法</summary>

- [ ] 本节说明：
- [ ] 搜索算法介绍：
- [x] Go搜索算法：
  
  - 递归函数、递归算法、 
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 算法-Go随机算法</summary>

- [ ] 本节说明：
- [ ] 随机算法：
- [x] Go随机算法：
  
  - 递归函数、递归算法、
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 算法-Go图论算法</summary>
- [ ] 本节说明：
- [ ] 图论算法介绍：
- [x] Go图论算法：
  - 递归函数、递归算法、 
- [ ] 本节案例：

  </details>
<details>
<summary>Day000: 算法-Go数论算法</summary>

- [ ] 本节说明：
- [ ] 数论算法介绍：
- [x] Go数论算法：
  
  - 递归函数、递归算法、 
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 算法-Go完全算法</summary>

- [ ] 本节说明：
- [ ] 完全算法介绍：
- [x] Go完全算法：
  
  - 递归函数、递归算法、
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 算法-Go漏桶算法</summary>

- [ ] 本节说明：本节介绍漏桶算法的相关内容。
- [ ] 漏桶算法介绍：
- [x] Go漏桶算法：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。  
- [ ] [漏桶算法参考1](https://github.com/unknwon/the-way-to-go_ZH_CN/blob/master/eBook/14.15.md)
- [ ] 本节案例：

  
  </details>

## 0x05-Go安全开发

​		本章节是在深入学习Go语言的基础上开发安全项目的实例。包括域名扫描、漏洞扫描、密码爆破、病毒免杀等项目。方便在红队攻防领域或是渗透测试领域有自己开发的完善的武器库。

<details>
<summary>Day000: 安全-Go域名扫描</summary>

- [x] 本节说明：本节介绍通过Go语言进行子域名发现的相关内容。
- [x] 子域名发现方法：二级三级域名的发现无外乎下面的这几种方法。
  - 搜索引擎搜索：通过搜索引擎搜索子域名是一种比较好的域名收集方法。
  - 子域名爆破法：通过子域名爆破收集子域名也是很好的方法。
- [ ] 子域名爆破原理：  
- [ ] 子域名字典整理：
- [ ] 项目成品：
  - [SubDomainG](https://github.com/0e0w/SubDomainG)：未开源
  
  </details>
<details>
<summary>Day000: 安全-Go目录扫描</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。  
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go 
- [ ] 本节案例：
  
  
  </details>
<details>
<summary>Day000: 安全-Go端口扫描</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
- [ ] 本节案例：
  
  
  </details>
<details>
<summary>Day000: 安全-Go密码爆破</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。  
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go 
- [ ] 本节案例：
  
  
  </details>
<details>
<summary>Day000: 安全-Go漏洞扫描</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 安全-Go隧道代理</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 安全-Go病毒免杀</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go 
- [ ] 本节案例：
  
  
  </details>
<details>
<summary>Day000: 安全-Go代码审计</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
- [ ] 本节案例：
  
  </details>
## 0x06-Go语言源码

​		本章节是深入理解Go语言必须要学习的内容。包括Go语言底层的功能实现方式，通过深入阅读Go语言源码达到真正深入理解Go语言的境界。

<details>
<summary>Day000: 源码-Go漏洞扫描</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
- [ ] 本节案例：
  
  
  </details>
<details>
<summary>Day000: 源码-Go域名扫描</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
- [ ] 本节案例：
  
  
  </details>

## 0x07-Go逆向工程

​		本章节是关于逆向工程的内容，包括Go语言开发项目的逆向工程等。

<details>
<summary>Day000: 逆向-Go逆向工程</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] [逆向工程参考1](https://www.anquanke.com/member/122079)
- [ ] 本节案例：
  
  </details>
<details>
<summary>Day000: 逆向-Go逆向工程</summary>

- [ ] 本节说明：
- [x] Go语言介绍：
  
  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
- [x] Go语言命令：
  
  - go run hello.go //编译运行hello.go
- [ ] 本节案例：
  
  </details>

## 0x08-Go参考资源

特别感谢：[柴树杉](https://github.com/golang-china/gopl-zh)、[无闻](https://github.com/Unknwon/the-way-to-go_ZH_CN)、[李骁](https://github.com/ffhelicopter/Go42)、[老貘](https://gfw.go101.org/article/101.html)、[王炳明](https://github.com/iswbm)、[韩茹](https://github.com/rubyhan1314)

- https://github.com/0e0w/LearnGolang
- https://www.runoob.com/go/go-tutorial.html
- https://github.com/ffhelicopter/Go42
- https://github.com/unknwon/the-way-to-go_ZH_CN
- https://github.com/golang101/golang101
- https://github.com/iswbm/GolangCodingTime
- https://space.bilibili.com/353694001