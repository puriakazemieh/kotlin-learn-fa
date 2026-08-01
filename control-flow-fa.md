[//]: # (title: شرط‌ها و حلقه‌ها)

کاتلین ابزارهای انعطاف‌پذیری را برای کنترل جریان برنامه (Control Flow) در اختیار شما قرار می‌دهد. از `if` ،`when` و حلقه‌ها برای تعریف منطقی شفاف و گویا استفاده کنید.

## عبارت If

برای استفاده از `if` در کاتلین، شرط مورد نظر را داخل پرانتز `()` و عملیاتی که در صورت درست بودن (`true`) باید انجام شود را داخل آکولاد `{}` قرار دهید. می‌توانید از `else` و `else if` برای شاخه‌ها و بررسی‌های اضافی استفاده کنید.

همچنین می‌توانید `if` را به صورت یک **عبارت (expression)** بنویسید؛ این کار به شما اجازه می‌دهد مقدار بازگشتی آن را مستقیماً به یک متغیر نسبت دهید. در این حالت، وجود شاخه `else` الزامی است. عبارت `if` در کاتلین همان هدفی را دنبال می‌کند که عملگر سه‌تایی (ternary operator یا `condition ? then : else`) در زبان‌های دیگر دارد.

مثال:

```kotlin
fun main() {
    val heightAlice = 160
    val heightBob = 175

    //sampleStart
    var taller = heightAlice
    if (heightAlice < heightBob) taller = heightBob

    // استفاده از شاخه else
    if (heightAlice > heightBob) {
        taller = heightAlice
    } else {
        taller = heightBob
    }

    // استفاده از if به عنوان یک عبارت (expression)
    taller = if (heightAlice > heightBob) heightAlice else heightBob

    // استفاده از else if به عنوان یک عبارت:
    val heightLimit = 150
    val heightOrLimit = if (heightLimit > heightAlice) heightLimit else if (heightAlice > heightBob) heightAlice else heightBob

    println("Taller height is $taller")
    // Taller height is 175
    println("Height or limit is $heightOrLimit")
    // Height or limit is 175
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="if-else-if-kotlin"}

هر شاخه در یک عبارت `if` می‌تواند یک بلوک کد باشد که در آن، مقدار آخرین عبارت به عنوان نتیجه در نظر گرفته می‌شود:

```kotlin
fun main() {
    //sampleStart
    val heightAlice = 160
    val heightBob = 175

    val taller = if (heightAlice > heightBob) {
        print("Choose Alice\n")
        heightAlice
    } else {
        print("Choose Bob\n")
        heightBob
    }

    println("Taller height is $taller")
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="if-else-blocks-kotlin"}

## عبارت‌ها و دستورهای When

`when` یک عبارت شرطی است که کد را بر اساس چندین مقدار یا شرط احتمالی اجرا می‌کند. این عبارت شبیه به دستور `switch` در زبان‌های Java، C و غیره است. `when` آرگومان خود را ارزیابی کرده و نتیجه را به ترتیب با هر شاخه مقایسه می‌کند تا زمانی که شرط یک شاخه برقرار شود.

مثال:

```kotlin
fun main() {
    //sampleStart
    val userRole = "Editor"
    when (userRole) {
        "Viewer" -> print("User has read-only access")
        "Editor" -> print("User can edit content")
        else -> print("User role is not recognized")
    }
    // User can edit content
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-conditions-when-statement"}

شما می‌توانید از `when` هم به عنوان یک **عبارت (expression)** و هم به عنوان یک **دستور (statement)** استفاده کنید. به عنوان یک عبارت، `when` مقداری را برمی‌گرداند که می‌توانید بعداً در کد استفاده کنید. به عنوان یک دستور، `when` عملیاتی را بدون بازگرداندن نتیجه انجام می‌دهد:

| عبارت (Expression) | دستور (Statement) |
| :--- | :--- |
| ```kotlin val text = when (x) { 1 -> "x == 1" 2 -> "x == 2" else -> "x is neither 1 nor 2" } ``` | ```kotlin when (x) { 1 -> print("x == 1") 2 -> print("x == 2") else -> print("x is neither 1 nor 2") } ``` |

همچنین می‌توانید از `when` با یا بدون موضوع (subject) استفاده کنید. رفتار آن در هر دو حالت یکسان است. استفاده از موضوع معمولاً کد شما را خواناتر و قابل نگهداری‌تر می‌کند زیرا به وضوح نشان می‌دهد چه چیزی را بررسی می‌کنید.

| با موضوع `x` | بدون موضوع |
| :--- | :--- |
| `when(x) { ... }` | `when { ... }` |

نحوه استفاده از `when` تعیین می‌کند که آیا نیاز دارید تمام حالت‌های ممکن را در شاخه‌ها پوشش دهید یا خیر. پوشش دادن تمام حالت‌ها، **جامع بودن (exhaustive)** نامیده می‌شود.

### دستورها (Statements)

اگر از `when` به عنوان یک دستور استفاده کنید، نیازی به پوشش دادن تمام حالت‌های ممکن نیست. در مثال زیر، برخی حالت‌ها پوشش داده نشده‌اند، بنابراین هیچ شاخه‌ای اجرا نمی‌شود، اما خطایی هم رخ نمی‌دهد:

```kotlin
fun main() {
    //sampleStart
    val deliveryStatus = "OutForDelivery"
    when (deliveryStatus) {
        // تمام حالت‌ها پوشش داده نشده‌اند
        "Pending" -> print("Your order is being prepared")
        "Shipped" -> print("Your order is on the way")
    }
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-when-statement"}

همانند `if` هر شاخه می‌تواند یک بلوک باشد و مقدار آن، مقدار آخرین عبارت در آن بلوک است.

### عبارت‌ها (Expressions)

اگر از `when` به عنوان یک عبارت استفاده کنید، **باید** تمام حالت‌های ممکن را پوشش دهید. مقدار اولین شاخه منطبق، به عنوان مقدار کل عبارت در نظر گرفته می‌شود. اگر تمام حالت‌ها را پوشش ندهید، کامپایلر خطا می‌دهد.

اگر عبارت `when` شما دارای موضوع باشد، می‌توانید از یک شاخه `else` استفاده کنید تا مطمئن شوید تمام حالت‌های ممکن پوشش داده شده‌اند، اما این کار الزامی نیست. به عنوان مثال، اگر موضوع شما یک `Boolean` یا یک [`enum` class](https://kotlinlang.org/docs/enum-classes.html) یا یک [`sealed` class](https://kotlinlang.org/docs/sealed-classes.html) باشد، می‌توانید بدون شاخه `else` تمام حالت‌ها را پوشش دهید:

```kotlin
import kotlin.random.Random
//sampleStart
enum class Bit {
    ZERO, ONE
}

fun getRandomBit(): Bit {
    return if (Random.nextBoolean()) Bit.ONE else Bit.ZERO
}

fun main() {
    val numericValue = when (getRandomBit()) {
        // به شاخه else نیازی نیست چون تمام حالت‌ها پوشش داده شده‌اند
        Bit.ZERO -> 0
        Bit.ONE -> 1
    }

    println("Random bit as number: $numericValue")
    // Random bit as number: 0
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-when-expression-subject"}

> برای ساده‌سازی عبارت‌های `when` و کاهش تکرار، ویژگی **حل‌وفصل حساس به متن (context-sensitive resolution)** را امتحان کنید (در حال حاضر در مرحله پیش‌نمایش). این ویژگی به شما اجازه می‌دهد در صورتی که تایپ مورد انتظار مشخص باشد، نام تایپ را هنگام استفاده از ورودی‌های enum یا اعضای sealed class حذف کنید.
>
> برای اطلاعات بیشتر، [پیش‌نمایش context-sensitive resolution](https://kotlinlang.org/docs/whatsnew22.html#preview-of-context-sensitive-resolution) را ببینید.
>
{style="tip"}

اگر عبارت `when` شما موضوع **نداشته باشد**، حتماً باید شاخه `else` داشته باشید، در غیر این صورت کامپایلر خطا می‌دهد. شاخه `else` زمانی اجرا می‌شود که هیچ‌کدام از شرط‌های دیگر برقرار نباشند:

```kotlin
fun main() {
    //sampleStart
    val localFileSize = 1200
    val remoteFileSize = 1200

    val message = when {
        localFileSize > remoteFileSize -> "Local file is larger than remote file"
        localFileSize < remoteFileSize -> "Local file is smaller than remote file"
        else -> "Local and remote files are the same size"
    }

    println(message)
    // Local and remote files are the same size
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-when-no-subject"}

### سایر روش‌های استفاده از When

عبارت‌ها و دستورهای `when` روش‌های مختلفی را برای ساده‌سازی کد، مدیریت چندین شرط و انجام بررسی‌های تایپ (type checks) ارائه می‌دهند.

می‌توانید چندین شرط را با استفاده از کاما در یک شاخه گروه‌بندی کنید:

```kotlin
fun main() {
    val ticketPriority = "High"
    //sampleStart
    when (ticketPriority) {
        "Low", "Medium" -> print("Standard response time")
        else -> print("High-priority handling")
    }
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-when-multiple-cases"}

از عبارت‌هایی که نتیجه آن‌ها `true` یا `false` است به عنوان شرط شاخه‌ها استفاده کنید:

```kotlin
fun main() {
    val storedPin = "1234"
    val enteredPin = 1234
  
    //sampleStart
    when (enteredPin) {
        // Expression
        storedPin.toInt() -> print("PIN is correct")
        else -> print("Incorrect PIN")
    }
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-when-branch-expression"}

با استفاده از کلمات کلیدی `in` یا `!in` بررسی کنید که آیا یک مقدار در یک [بازه (range)](https://kotlinlang.org/docs/ranges.html) یا مجموعه قرار دارد یا خیر:

```kotlin
fun main() {
    val x = 7
    val validNumbers = setOf(15, 16, 17)

    //sampleStart
    when (x) {
        in 1..10 -> print("x is in the range")
        in validNumbers -> print("x is valid")
        !in 10..20 -> print("x is outside the range")
        else -> print("none of the above")
    }
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-when-ranges"}

تایپ یک مقدار را با استفاده از کلمات کلیدی `is` یا `!is` بررسی کنید. به دلیل ویژگی [تبدیل هوشمند (smart casts)](https://kotlinlang.org/docs/typecasts.html#smart-casts)، می‌توانید مستقیماً به توابع و ویژگی‌های آن تایپ دسترسی داشته باشید:

```kotlin
fun hasPrefix(input: Any): Boolean = when (input) {
    is String -> input.startsWith("ID-")
    else -> false
}

fun main() {
    val testInput = "ID-98345"
    println(hasPrefix(testInput))
    // true
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-when-type-checks"}

از `when` به جای زنجیره سنتی `if-else if` استفاده کنید. بدون موضوع، شرط‌های شاخه‌ها صرفاً عبارت‌های بولی هستند و اولین شاخه‌ای که شرط آن `true` باشد اجرا می‌شود:

```kotlin
fun Int.isOdd() = this % 2 != 0
fun Int.isEven() = this % 2 == 0

fun main() {
    //sampleStart
    val x = 5
    val y = 8

    when {
        x.isOdd() -> print("x is odd")
        y.isEven() -> print("y is even")
        else -> print("x+y is odd")
    }
    // x is odd
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-when-replace-if"}

در نهایت، می‌توانید موضوع را با استفاده از نحو (syntax) زیر در یک متغیر کپچر کنید:

```kotlin
fun main() {
    val message = when (val input = "yes") {
        "yes" -> "You said yes"
        "no" -> "You said no"
        else -> "Unrecognized input: $input"
    }

    println(message)
    // You said yes
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-when-capture-subject"}

اسکوپ (scope) متغیری که به عنوان موضوع معرفی شده است، محدود به بدنه عبارت یا دستور `when` است.

### شرط‌های محافظ (Guard conditions) {id="guard-conditions-in-when-expressions"}

شرط‌های محافظ به شما اجازه می‌دهند بیش از یک شرط را در شاخه‌های یک عبارت یا دستور `when` بگنجانید و جریان‌های پیچیده کنترل برنامه را صریح‌تر و فشرده‌تر کنید. شما می‌توانید از شرط‌های محافظ در `when` استفاده کنید به شرطی که دارای موضوع باشد.

یک شرط محافظ را بعد از شرط اصلی در همان شاخه قرار دهید و آن‌ها را با `if` جدا کنید:

```kotlin
sealed interface Animal {
    data class Cat(val mouseHunter: Boolean) : Animal
    data class Dog(val breed: String) : Animal
}

fun feedDog() = println("Feeding a dog")
fun feedCat() = println("Feeding a cat")

//sampleStart
fun feedAnimal(animal: Animal) {
    when (animal) {
        // شاخه با تنها شرط اصلی
        is Animal.Dog -> feedDog()
        // شاخه با هر دو شرط اصلی و محافظ
        // زمانی اجرا می‌شود که حیوان گربه باشد و شکارچی موش نباشد
        is Animal.Cat if !animal.mouseHunter -> feedCat()
        // در صورت عدم انطباق با هیچ‌کدام
        else -> println("Unknown animal")
    }
}

fun main() {
    val animals = listOf(
        Animal.Dog("Beagle"),
        Animal.Cat(mouseHunter = false),
        Animal.Cat(mouseHunter = true)
    )

    animals.forEach { feedAnimal(it) }
    // Feeding a dog
    // Feeding a cat
    // Unknown animal
}
//sampleEnd
```
{kotlin-runnable="true" kotlin-min-compiler-version="2.2" id="kotlin-when-guard-conditions"}

نمی‌توانید از شرط‌های محافظ زمانی که چندین شرط با کاما جدا شده‌اند استفاده کنید. به عنوان مثال: `0, 1 -> print("x == 0 or x == 1")`.

در یک عبارت `when` می‌توانید شاخه‌های دارای شرط محافظ و بدون آن را با هم ترکیب کنید. کد یک شاخه با شرط محافظ تنها زمانی اجرا می‌شود که هم شرط اصلی و هم شرط محافظ برابر با `true` باشند.

برخلاف دستورها، عبارت‌های `when` باید تمام حالت‌ها را پوشش دهند. اگر از شرط‌های محافظ در عبارت‌های `when` بدون شاخه `else` استفاده می‌کنید، کامپایلر از شما می‌خواهد تمام حالت‌های ممکن را مدیریت کنید تا از خطاهای زمان اجرا جلوگیری شود.

می‌توانید چندین شرط محافظ را با استفاده از عملگرهای بولی `&&` (AND) یا `||` (OR) ترکیب کنید. برای [جلوگیری از ابهام](coding-conventions-fa.md#guard-conditions-in-when-expression)، اطراف عبارت‌های بولی از پرانتز استفاده کنید:

```kotlin
when (animal) {
    is Animal.Cat if (!animal.mouseHunter && animal.hungry) -> feedCat()
}
```

شرط‌های محافظ از `else if` نیز پشتیبانی می‌کنند:

```kotlin
when (animal) {
    is Animal.Dog -> feedDog()
    is Animal.Cat if !animal.mouseHunter -> feedCat()
    else if animal.eatsPlants -> giveLettuce()
    else -> println("Unknown animal")
}
```

## حلقه‌های For

از حلقه `for` برای پیمایش در یک [مجموعه (collection)](https://kotlinlang.org/docs/collections-overview.html)، [آرایه](arrays-fa.md) یا [بازه (range)](https://kotlinlang.org/docs/ranges.html) استفاده کنید:

```kotlin
for (item in collection) print(item)
```

بدنه حلقه `for` می‌تواند یک بلوک با آکولاد `{}` باشد.

```kotlin
fun main() {
    val shoppingList = listOf("Milk", "Bananas", "Bread")
    //sampleStart
    println("Things to buy:")
    for (item in shoppingList) {
        println("- $item")
    }
    // Things to buy:
    // - Milk
    // - Bananas
    // - Bread
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-for-loop"}

### بازه‌ها (Ranges)

برای پیمایش روی بازه‌ای از اعداد، از یک [عبارت بازه](https://kotlinlang.org/docs/ranges.html) با عملگرهای `..` و `..<` استفاده کنید:

```kotlin
fun main() {
//sampleStart
    println("Closed-ended range:")
    for (i in 1..6) {
        print(i)
    }
    // 123456
  
    println("\nOpen-ended range:")
    for (i in 1..<6) {
        print(i)
    }
    // 12345
  
    println("\nReverse order in steps of 2:")
    for (i in 6 downTo 0 step 2) {
        print(i)
    }
    // 6420
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-for-loop-range"}

### آرایه‌ها

اگر می‌خواهید در یک آرایه یا لیست با استفاده از ایندکس پیمایش کنید، می‌توانید از ویژگی `indices` استفاده کنید:

```kotlin
fun main() {
    val routineSteps = arrayOf("Wake up", "Brush teeth", "Make coffee")
    //sampleStart
    for (i in routineSteps.indices) {
        println(routineSteps[i])
    }
    // Wake up
    // Brush teeth
    // Make coffee
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-for-loop-array"}

همچنین می‌توانید از تابع `.withIndex()` در کتابخانه استاندارد استفاده کنید:

```kotlin
fun main() {
    val routineSteps = arrayOf("Wake up", "Brush teeth", "Make coffee")
    //sampleStart
    for ((index, value) in routineSteps.withIndex()) {
        println("The step at $index is \"$value\"")
    }
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-for-loop-array-index"}

### ایتریتورها (Iterators)

حلقه `for` روی هر چیزی که یک [ایتریتور (iterator)](https://kotlinlang.org/docs/iterators.html) ارائه دهد پیمایش می‌کند.

شما می‌توانید با ارائه یک تابع عضو یا اکستنشن به نام `iterator()` که یک `Iterator<>` برمی‌گرداند، ایتریتورهای خود را بسازید. تابع `iterator()` باید دارای توابع `next()` و `hasNext()` باشد.

ساده‌ترین راه، ارث‌بری از اینترفیس [`Iterable<T>`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/-iterable/) و پیاده‌سازی توابع آن است.

```kotlin
class Booklet(val totalPages: Int) : Iterable<Int> {
    override fun iterator(): Iterator<Int> {
        return object : Iterator<Int> {
            var current = 1
            override fun hasNext() = current <= totalPages
            override fun next() = current++
        }
    }
}

fun main() {
    val booklet = Booklet(3)
    for (page in booklet) {
        println("Reading page $page")
    }
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-for-loop-inherit-iterator"}

> درباره [اینترفیس‌ها](https://kotlinlang.org/docs/interfaces.html) و [ارث‌بری](https://kotlinlang.org/docs/inheritance.html) بیشتر بخوانید.
>
{style="tip"}

## حلقه‌های While

حلقه‌های `while` و `do-while` تا زمانی که شرط برقرار باشد، کد بدنه خود را اجرا می‌کنند. تفاوت آن‌ها در زمان بررسی شرط است:

*   `while` ابتدا شرط را بررسی می‌کند و در صورت برقرار بودن، بدنه را اجرا می‌کند.
*   `do-while` ابتدا بدنه را اجرا کرده و سپس شرط را بررسی می‌کند. بنابراین بدنه `do-while` **حداقل یک بار** اجرا می‌شود.

```kotlin
fun main() {
    var carsInGarage = 0
    val maxCapacity = 3
//sampleStart
    while (carsInGarage < maxCapacity) {
        println("Car entered. Cars now in garage: ${++carsInGarage}")
    }
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-while-loop"}

مثال `do-while`:

```kotlin
import kotlin.random.Random

fun main() {
    var roll: Int
//sampleStart
    do {
        roll = Random.nextInt(1, 7)
        println("Rolled a $roll")
    } while (roll != 6)
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-do-while-loop"}

## Break و continue در حلقه‌ها

کاتلین از عملگرهای سنتی `break` و `continue` در حلقه‌ها پشتیبانی می‌کند. بخش [بازگشت و پرش](returns-fa.md) را ببینید.
