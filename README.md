#TaylorSwift  ( *・ω・)✄╰ひ╯

![](./assets/taylor.jpg)

I'm a TaylorSwift fan and This repo is used to learn Swift.    

>Is this sort of a punchline?

I'm learning ios programming now!

##Swift资源汇总  

- [Swift编程语言中文版](http://numbbbbb.github.io/the-swift-programming-language-in-chinese/) 


##[第一个例子Hello World](./hellotaylor.swift)

最初级的Hello World例子，so easy！

#Swift世界巡回（又名：Swift语言指南）

程序员的传统教导我们在学习一门新语言时编写的第一个程序应该是在屏幕上打印“Hello, world”，在swift中，我们可以使用一行代码轻松的办到：  


    println("Hello, world")

如果你之前使用过C或者Objective-C写过代码，那么上面的语法对你而言应该很熟悉 -- 在Swift中，这行代码是一个完整的程序。你不需要引入一个单独的库来进行一些输入/输出或者字符串处理的功能。全局作用域中的代码被用作程序的切入点，因此你不需要一个`main`函数。你也不需要在每行语句的后面添加分号。  

这篇指南将会向你展示足够的信息来开始使用Swift编写程序，其中会向你展示如何完成不同的编程任务。如果你没有理解其中的某些部分也不要担心 -- 在这篇指南中提到的所有细节在本书（指的是The Swift Programming Language，在itunes上免费下载，[网页版地址](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/GuidedTour.html#//apple_ref/doc/uid/TP40014097-CH2-XID_1) ）的后面部分由详细说明。  

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

#函数和闭包  

使用`func`可以定义一个函数。在函数名称后面的括号中加上一列参数可以调用函数。使用`->`可以将参数名称和函数的返回类型分隔开。  

    func greet(name: String, day: String) -> String {
       return "Hello \(name), today is \(day)."
    }
    greet("Bob", "Tuesday")

使用一个元组可以从一个函数中返回多个值。  

    func getGasPrices() -> (Double, Double, Double) {
       return (3.59, 3.69, 3.79)
    }
    getGasPrices()

函数也可以接受多个参数，并将它们集合成一个数组。  

    func sumOf(numbers: Int...) -> Int {
         var sum = 0
         for number in numbers {
          sum += number
        }
        return sum
    }
    sumOf()
    sumOf(42, 597, 12)

函数可以嵌套。嵌套函数可以访问在外层函数中声明的变量。你可以使用嵌套函数来组织函数中那些又长又复杂的代码。  

    func returnFifteen() -> Int {
      var y = 10
     func add() {
          y += 5
     }
     add()
     return y
    }
    returnFifteen()

函数是一等类型。这意味着一个函数可以返回另一个函数。 

    func makeIncrementer() -> (Int -> Int) {
        func addOne(number: Int) -> Int {
        return 1 + number
    }
         return addOne
    }
    var increment = makeIncrementer()
    increment(7) 

一个函数可以接收另一个函数作为它的参数。  

    func hasAnyMatches(list: Int[], condition: Int -> Bool) -> Bool {
    for item in list {
        if condition(item) {
            return true
        }
    }
    return false
    }
    func lessThanTen(number: Int) -> Bool {
    return number < 10
    }
    var numbers = [20, 19, 7, 12]
    hasAnyMatches(numbers, lessThanTen)

函数实际上是闭包的一个特例。你可以通过将代码包含在`({})`中间而不需要一个名字来编写一个闭包。你需要使用`in`来分隔参数并从代码体中返回类型。  

    numbers.map({
        (number: Int) -> Int in
         let result = 3 * number
        return result
    })

你有几种选择来更加简洁的编写闭包。当一个闭包的类型还不确定时，例如对于代理的回调，你可以忽略它的参数类型，它的返回值的类型，或者两者都忽略。单行语句的闭包隐式的说明它将返回它的唯一语句的值。

    numbers.map({ number in 3 * number })

你可以通过数字而不是名字来引用参数 -- 这种方法在非常短的闭包中很有用。一个作为一个函数的最后一个参数的闭包可以很快的出现在括号后面。  

    sort([1, 5, 3, 12, 2]) { $0 > $1 }

#对象和类  

使用`class`后面加上类名来创建一个类。在类中声明一个属性的方式和声明一个常量或者变量相同，唯一的不同点在于类的上下文不同。同样的，方法和函数的声明方式也和一般的函数声明方式相同。  

    class Shape {
        var numberOfSides = 0
        func simpleDescription() -> String {
            return "A shape with \(numberOfSides) sides."
        }
    }

通过在类的后面加上括号来创建一个类的实例。使用点语法来获取这个实例中的属性和方法。  

    var shape = Shape()
    shape.numberOfSides = 7
    var shapeDescription = shape.simpleDescription()

这个版本的`Shape`类缺少了一些重要的部分：一个在实例初始化时用来设定类的初始化函数。使用`init`来创建一个初始化函数。  

    class NamedShape {
        var numberOfSides: Int = 0
        var name: String
    
        init(name: String) {
            self.name = name
        }
    
        func simpleDescription() -> String {
            return "A shape with \(numberOfSides) sides."
        }
    }


注意`self`被用来区分`name`属性和来自初始化函数中的`name`。在创建一个实例时，初始化函数中的变量使用方式和一般函数中变量使用方式相同。每一个属性都需要被赋予一个值 -- 无论是在它的声明中(作为 `numberOfSlides`)或者在初始化函数中(作为`name`)。  

如果在对象被销毁以前你需要做一些清理工作，你可以使用`deinit`来创建一个去初始化函数。  

子类会在它们的类名后面加上超类的名字，二者之间用一个冒号隔开。任何的类都不需要是是一个标准根类的子类，因此你可以根据实际需求包含或者忽略一个超类。  

子类中重载超类中具体实现需要标明`override` -- 如果没有`override`的话，重载方法就会被编译器视为一个错误。编译器也能探测到那些标明了`override`但是实际上没有重载任何超类中方法的方法。  

    class Square: NamedShape {
        var sideLength: Double
    
        init(sideLength: Double, name: String) {
            self.sideLength = sideLength
            super.init(name: name)
            numberOfSides = 4
        }
    
        func area() ->  Double {
            return sideLength * sideLength
        }
    
        override func simpleDescription() -> String {
            return "A square with sides of length \(sideLength)."
        }
    }
    let test = Square(sideLength: 5.2, name: "my test square")
    test.area()
    test.simpleDescription()

属性除了可以简单地存储值之外，属性还可以作为一个获取器或者设置器。  

    class EquilateralTriangle: NamedShape {
        var sideLength: Double = 0.0
    
        init(sideLength: Double, name: String) {
            self.sideLength = sideLength
            super.init(name: name)
            numberOfSides = 3
        }
    
        var perimeter: Double {
        get {
            return 3.0 * sideLength
        }   
        set {
            sideLength = newValue / 3.0
        }
        }
    
        override func simpleDescription() -> String {
            return "An equilateral triagle with sides of length \(sideLength)."
        }
    }
    var triangle = EquilateralTriangle(sideLength: 3.1, name: "a triangle")
    triangle.perimeter
    triangle.perimeter = 9.9
    triangle.sideLength

在针对`perimeter`的设置器中，新值有一个隐式的名字`newValue`。你可以在`set`之后的括号中为它提供一个显式的名字。  

注意针对`EquilateralTriangle`类的初始化函数包含三个不同步骤：  

 1. 设置子类声明的属性值
 2. 调用子类的初始化函数
 3. 改变由子类定义的属性值。任何使用方法、获取器、或者设置器的附加设置步骤都将在这一步完成  

如果你在需要那些在设置一个新值之前或者之后才会运行的代码之前不需要计算属性，你可以使用`willSet`和`didSet`。例如，下面的类确保了它的三角形边长总是和正方形的边长相等。 

    class TriangleAndSquare {
        var triangle: EquilateralTriangle {
        willSet {
            square.sideLength = newValue.sideLength
        }
        }
        var square: Square {
        willSet {
            triangle.sideLength = newValue.sideLength
        }
        }
        init(size: Double, name: String) {
            square = Square(sideLength: size, name: name)
            triangle = EquilateralTriangle(sideLength: size, name: name)
        }
    }
    var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
    triangleAndSquare.square.sideLength
    triangleAndSquare.triangle.sideLength
    triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
    triangleAndSquare.triangle.sideLength

类中的方法和一般的函数有一些重要的不同点。函数中的参数名只能在函数中使用，但是方法中的参数名还可以在你调用这个方法时使用（除了第一个参数）。默认情况下，在函数内部使用的参数名称和声明的参数名称一致。但是你可以制定一个别名，在方法内部使用。  

    class Counter {
        var count: Int = 0
        func incrementBy(amount: Int, numberOfTimes times: Int) {
            count += amount * times
        }
    }
    var counter = Counter()
    counter.incrementBy(2, numberOfTimes: 7)

在使用可选值时，你可以在方法、属性、以及子脚本前面写上`?`。如果在`?`之前的值是`nil`，`?`之后的所有东西都会被忽视，同时整个表达式为`nil`。另外，如果可选值是没有被包装的，那么`?`之后的所有东西都会作用域未包装的值上。两种情况中，整个表达式的值将会是一个可选值。  

    let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
    let sideLength = optionalSquare?.sideLength

#枚举和结构体  

使用`enum`来创建一个枚举。和类以及其他命名类型一样，枚举可以拥有相关联的方法。  

    enum Rank: Int {
        case Ace = 1
        case Two, Three, Four, Five, Six, Seven, Eight, Nine, Ten
        case Jack, Queen, King
        func simpleDescription() -> String {
            switch self {
            case .Ace:
                return "ace"
            case .Jack:
                return "jack"
            case .Queen:
                return "queen"
            case .King:
                return "king"
            default:
                return String(self.toRaw())
            }
        }
    }
    let ace = Rank.Ace
    let aceRawValue = ace.toRaw()

在上面的例子中，枚举的原始值类型是`Int`，因此你只需要指明第一个原始值。后面的原始值都会自动按顺序被赋值。你也可以使用字符串或者浮点数作为一个枚举的原始类型。  

你可以使用`toRaw`以及`fromRaw`函将在原始值和枚举值之间来回转换。  

    if let convertedRank = Rank.fromRaw(3) {
        let threeDescription = convertedRank.simpleDescription()
    }

一个枚举的实际成员值是一个实际的值，而不是另一种编写原始值的方式。事实上，除了那些没有包含有意义原始值的情形，你甚至都不需要提供一个原始值。  

    enum Suit {
        case Spades, Hearts, Diamonds, Clubs
            func simpleDescription() -> String {
                switch self {
            case .Spades:
                return "spades"
            case .Hearts:
                return "hearts"
            case .Diamonds:
                return "diamonds"
            case .Clubs:
                return "clubs"
            }
        }
    }
    let hearts = Suit.Hearts
    let heartsDescription = hearts.simpleDescription()

注意上面例子中枚举的`Heart`

> to be continue...