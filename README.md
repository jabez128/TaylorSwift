#TaylorSwift  ( *・ω・)✄╰ひ╯

![](./assets/taylor.jpg)

I'm a TaylorSwift fan and This repo is used to learn Swift.    

>Is this sort of a punchline?

I'm learning ios programming now!

##[第一个例子Hello World](./hellotaylor.swift)

最初级的Hello World例子，so easy！

#Swift世界巡回（又名：Swift语言指南）

程序员的传统教导我们在学习一门新语言时编写的第一个程序应该是在屏幕上打印“Hello, world”，在swift中，我们可以使用一行代码轻松的办到：  


    println("Hello, world")

如果你之前使用过C或者Objective-C写过代码，那么上面的语法对你而言应该很熟悉 -- 在Swift中，这行代码是一个完整的程序。你不需要引入一个单独的库来进行一些输入/输出或者字符串处理的功能。全局作用域中的代码被用作程序的切入点，因此你不需要一个`main`函数。你也不需要在每行语句的后面添加分号。  

这篇指南将会向你展示足够的信息来开始使用Swift编写程序，其中会向你展示如何完成不同的编程任务。如果你没有理解其中的某些部分也不要担心 -- 在这篇指南中提到的所有细节在本书（指的是The Swift Programming Language，在itunes上免费下载，网页版地址https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/GuidedTour.html#//apple_ref/doc/uid/TP40014097-CH2-XID_1）的后面部分由详细说明。  

#简单值

在Swift中，使用`let`指定一个常量，使用`var`指定一个变量。常量的值在编译的时候不需要被了解，但是你必须一次性给它赋予一个值。这意味着你只定义一次常量，然后在多个地方使用它。  

    var myVariable = 42
    myVariable = 50
    let myConstant = 42

一个常量或者变量必须拥有和你赋予给它的值一样的类型。但是，你不需要每次都显式的指明类型。当你在创建一个常量或变量时，编译器会去推测它的类型。在上面的例子中，编译器会推测`myVariable`是一个整形值，因为它的初始值是一个整数。   

如果初始值没有提供足够的信息（或者没有初始值），你需要在变量的后面指明类型，用一个冒号隔开。   

    let implicitInteger = 70
    let implicitDouble = 70.0
    let explicitDouble: Double = 70  

值不会被隐式的转换到别的类型。如果你需要将一个值转换为其他类型，你需要显示的创建一个期望类型的实例。  

    let label = "The width is "
    let width = 94
    let widthLabel = label + String(width)   

有一种更加简单的方式在字符串中包含值：将值写在括号中，然后在括号前面加上反斜杠(\)。例如：  

    let apples = 3
    let oranges = 5
    let appleSummary = "I have \(apples) apples."
    let fruitSummary = "I have \(apples + oranges) pieces of fruit."

使用方括号([])来创建数组和字典，并且通过方括号中的索引数字或者键值来获取相关元素。  
    
    var shoppingList = ["catfish", "water", "tulips", "blue paint"]
    shoppingList[1] = "bottle of water"
     
    var occupations = [
    "Malcolm": "Captain",
    "Kaylee": "Mechanic",
    ]
    occupations["Jayne"] = "Public Relations"

为了创建一个空数组或者字典，使用初始化表达式语法。  

    let emptyArray = String[]()
    let emptyDictionary = Dictionary<String, Float>()  

如果类型信息可以被推测，你可以将一个空数组写为[]，将一个空字典写为[:] -- 例如，当你为一个变量设定了一个新的值或者为一个函数传递一个参数时。  


shoppingList = []   // 你去购物然后买所有种类的东西 

#控制流   

使用`if`和`switch`来控制条件，使用`for-in`,`fo`,`while`,以及`do-while`来进行循环。条件或者循环变量周围的括号是可选的。代码块周围的大括号是必须的。   

    let individualScores = [75, 43, 103, 87, 12]
    var teamScore = 0
    for score in individualScores {
    if score > 50 {
    teamScore += 3
    } else {
    teamScore += 1
    }
    }
    teamScore

在一个`if`语句中，条件必须是一个布尔值表达式 -- 这意味着例如`if score { ... } `这样的代码是错误的，它并不代表一个和0的隐式比较。  

你可以将`if`和`let`一起和可能缺失的值一起使用。这些值代表可选值。一个可选的值要么包含一个值要么包含`nil`来说明这个值是缺失的。在一个值的类型后面添加一个问号(?)可以标明这个值是可选的。 

    var optionalString: String? = "Hello"
    optionalString == nil
     
    var optionalName: String? = "John Appleseed"
    var greeting = "Hello!"
    if let name = optionalName {
    greeting = "Hello, \(name)"
    }

如果一个可选值是`nil`,那么对应的条件语句将会是`false`，大括号里面的代码将会被跳过。否则，可选值将会被展开并在`let`之后被赋予一个常量，这使得展开的值可以再代码块的内部使用。  

Switch支持任何类型的数据以及各种各样的表达式 -- 它们不限于整数或者用于测试等价。   
    
    let vegetable = "red pepper"
    switch vegetable {
    case "celery":
    let vegetableComment = "Add some raisins and make ants on a log."
    case "cucumber", "watercress":
    let vegetableComment = "That would make a good tea sandwich."
    case let x where x.hasSuffix("pepper"):
    let vegetableComment = "Is it a spicy \(x)?"
    default:
    let vegetableComment = "Everything tastes good in soup."
    }
    
在执行完匹配到的case中的代码之后，程序会从Swift语句中跳出。程序并不会继续执行下一个case，因此没有必要在每一个case的最后显式的break out。  

你可以通过将每个键-值对中的名字，使用`for-in`语句来对一个字典中的项目进行迭代。  
    
    let interestingNumbers = [
    "Prime": [2, 3, 5, 7, 11, 13],
    "Fibonacci": [1, 1, 2, 3, 5, 8],
    "Square": [1, 4, 9, 16, 25],
    ]
    var largest = 0
    for (kind, numbers) in interestingNumbers {
    for number in numbers {
    if number > largest {
    largest = number
    }
    }
    }
    largest

使用`while`来重复一个代码块知道一个条件发生变化。循环的条件可以再代码的最后，这可以确保代码至少执行一次。  
    
    var n = 2
    while n < 100 {
    n = n * 2
    }
    n
     
    var m = 2
    do {
    m = m * 2
    } while m < 100
    m

你可以在循环中使用一个索引 -- 或者使用 .. 来制造一个索引的范围或者编写一个显式的初始化，条件，以及递增。下面的两段循环代码作用一样：  

    var firstForLoop = 0
    for i in 0..3 {
    firstForLoop += i
    }
    firstForLoop
     
    var secondForLoop = 0
    for var i = 0; i < 3; ++i {
    secondForLoop += 1
    }
    secondForLoop  


使用 .. 产生的范围将会忽略最大值，使用 ... 产生的范围将会包括最大值和最小值。 

>To be contuniue... 


