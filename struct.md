# struct

其实学了前面的内容后，我们已经可以实现绝大部分想要的功能了。

下面我带大家理一下如何用上面的那些功能去写一个程序：

1. 首先弄明白自己要实现的是个什么东西，大概可以分为哪几个模块。模块之前的逻辑（判断、循环）的什么样的。
2. 每个模块具体如何实现？有哪些代码可以封装成函数以复用？
3. 遇到不会的地方，可能有两种情况：
   1. 对语法不熟，补一下就好了，几乎没有人能一下子学会哪门编程语言的所有语法的。
   2. 某块功能不知道怎么实现。第一，可以尝试去搜一下你想要的功能描述，大概率能得到现成的解决方案，去学一下别人怎么写的就好。第二，很多特定的软件，比如你想发个短信，这种看起来复杂的对你而言无法想象的功能，大多数时候都有现成的库（库你可以理解为函数的集合），去搜一搜，对照着文档用就好

小册子开头我提到还要教你如何去学一门编程语言，其实在我看来主要也是两点，就像你回忆一下我是如何在小册子中引导你那样：

1. 首先是任务驱动，你有特定的想做的事情，然后去想着它如何实现，再去自己写也好，边搜现成的方案边学也好。写得越多你就能发现要学的东西越多，久而久之就什么都会写了，或者说看到一个需求马上就会有思路，以及遇到一个新的东西能很快上手。
2. 然后是，先去最快速地去建立对一个东西的核心的认识。比如我这个小册子到目前为止只介绍了编程中非常少的一部分内容，但却是在核心的，有了这个你能更快地去理解其他的内容，去实现更多的复杂的功能。先建立自己的核心理解，再通过不断学习扩大自己的知识范围。

## 为什么有 struct

前面的章节基本已经能让你开始实现各种功能了，但正如前文某篇文章所说的，**「编程是对现实世界的模拟」**。

遗憾的是我们前面学到的并不能很好的去对这个世界进行建模。就拿数据类型来说，我们只学了基本的数字啊字符串的基本类型。

如果我们去描述一个学生的信息的话，我们可能会定义这样几个变量：

```go
var name string
var ID string	// 学号
var class string
var birthYear int
var gender string
// ... 还有很多其他字段就不一一举例
```

诚然，我们可以用各种基本的数据类型来定义学生的各个属性。但是，有没有觉得这些属性是「散」的。

换句话说，如果上面这些变量模拟了张三这个学生，那么再来个李四怎么办呢？再定义一套 `name2`, `ID2` ...?

再来一个呢？疯狂新定义不同名字的变量？

有没有什么办法，能把这些变量真正地组合到一起，甚至说新定义个专门用来描述学生的类型呢？

上代码：

```go
type Student struct {
  name string
  ID string	// 学号
  class string
  birthYear int
  gender string
}
```

我们直接对着英文猜测含义吧：用 `type` 定义了一个新的数据类型 `Student`，同时这是个 `struct`（结构体）。

（如前文所述，这个结构体里的 `name`, `class`, `birthYear`, `gender` 开头是小写，非导出，外部的包是无法访问到具体的字段的值的）

下面我们可以直接声明 `Student` 类型的变量了：

```go
// 一下内容请复制到某个函数内，比如 main 函数
var zhangsan Student		// 可以这么定义变量
zhangsan.name = "张三"	// 赋值的时候可以对结构体内的字段用 "变量名.字段名=值" 来赋值。你可以把 "A.B" 理解成"A的B"。
zhangsan.birthYear = 2006
zhangsan.ID = "22051620"
// ...

fmt.Printf("张三的学号是%s\n", zhangsan.ID)	// 引用结构体字段的时候也是 "变量名.字段名" 就行。

lisi := Student{	// 也可以用 := 语法快捷定义
  name: "李四",
  ID: "22051620",
  birthYear: 2002,
  gender: "男",
  class: "22050516",
}

fmt.Printf("李四的学号是%s\n", lisi.ID)
fmt.Println(lisi)	// 也可以直接输出整个结构体类型，Go对struct设置了默认的输出格式
```

有了 `struct` （结构体）的话，我们就可以定义更符合现实世界的新类型了。



`struct` 还有很多玩法，比如像 `struct` 里可以嵌套基本的数据类型那样，它里面也可以嵌套 `struct`。

```go
type Car struct {
  Wheel1 Wheel	// 车有四个轮子，每个轮子又是一个 struct
  Wheel2 Wheel
  Wheel3 Wheel
  Wheel4 Wheel
  Kind string	// 车的类型
  Engine Engine	// 引擎。前面那个 Engine 是字段名，后面那个 Engine 是类型名。Go 是允许这两个名字重复的。
}

type Wheel struct {
  Radius float64	// 轮子的半径
}
type Engine struct {
  Info string
}

func main() {
  var car Car
  car.Wheel1 = Wheel{Radius: 123}
  car.Wheel2 = Wheel{Radius: 123}
  car.Wheel3 = Wheel{Radius: 123}
  car.Wheel4 = Wheel{Radius: 123}
  car.Engine = Engine{Info: "引擎信息"}
  car.Kind = "小轿车"
  
  bigCar := Car{
    Wheel1: Wheel{Radius: 321},
    Wheel2: Wheel{Radius: 321},
    Wheel3: Wheel{Radius: 321},
    Wheel4: Wheel{Radius: 321},
    Engine: Engine{
      Info: "超大引擎",
    },
    Kind: "大轿车",
  }
}

```

 （这里 Car 的里面的字段开头都是大写，对其他包可见）



`struct` 还有什么诸如匿名嵌套一类的慢慢学就好~