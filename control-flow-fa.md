[//]: # (title: شرط‌ها و حلقه‌ها (Conditions and loops))

کاتلین ابزارهای انعطاف‌پذیری را برای کنترل جریان برنامه (Control Flow) در اختیار شما قرار می‌دهد. از `if` ،`when` و حلقه‌ها برای تعریف منطقی شفاف و گویا برای شرایط خود استفاده کنید.

## عبارت If

برای استفاده از `if` در کاتلین، شرط مورد نظر را داخل پرانتز `()` و عملیاتی که در صورت درست بودن (true) باید انجام شود را داخل آکولاد `{}` قرار دهید. می‌توانید از `else` و `else if` برای شاخه‌ها و بررسی‌های اضافی استفاده کنید.

همچنین می‌توانید `if` را به صورت یک **عبارت (expression)** بنویسید که به شما اجازه می‌دهد مقدار بازگشتی آن را مستقیماً به یک متغیر نسبت دهید. در این حالت، وجود شاخه `else` الزامی است. عبارت `if` همان هدفی را دنبال می‌کند که عملگر سه‌تایی (ternary operator یا `condition ? then : else`) در زبان‌های دیگر دارد.

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

    // استفاده از if به عنوان یک عبارت
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

هر شاخه در یک عبارت `if` می‌تواند یک بلوک کد باشد که در آن مقدار آخرین عبارت، به عنوان نتیجه در نظر گرفته می‌شود:

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

## عبارات و دستورات When

ساختار `when` یک عبارت شرطی است که کد را بر اساس مقادیر یا شرایط مختلف اجرا می‌کند. این ساختار مشابه دستور `switch` در جاوا، C و زبان‌های دیگر است. `when` آرگومان خود را ارزیابی کرده و نتیجه را به ترتیب با هر شاخه مقایسه می‌کند تا زمانی که شرط یک شاخه برقرار شود. مثال:

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

می‌توانید از `when` هم به عنوان یک **عبارت (expression)** و هم به عنوان یک **دستور (statement)** استفاده کنید. به عنوان یک عبارت، `when` مقداری را برمی‌گرداند که می‌توانید بعداً در کد خود از آن استفاده کنید. به عنوان یک دستور، `when` عملی را انجام می‌دهد بدون اینکه نتیجه‌ای برگرداند:

| عبارت (Expression) | دستور (Statement) |
|---|---|
| ```kotlin val text = when (x) { 1 -> "x == 1" 2 -> "x == 2" else -> "x is neither 1 nor 2" } ``` | ```kotlin when (x) { 1 -> print("x == 1") 2 -> print("x == 2") else -> print("x is neither 1 nor 2") } ``` |

ثانیاً، می‌توانید از `when` با یا بدون یک موضوع (subject) استفاده کنید. رفتار در هر دو حالت یکسان است. استفاده از موضوع معمولاً کد شما را خواناتر و قابل نگهداری‌تر می‌کند زیرا به وضوح نشان می‌دهد چه چیزی را بررسی می‌کنید.

| با موضوع (subject) `x` | بدون موضوع |
|---|---|
| `when(x) { ... }` | `when { ... }` |

نحوه استفاده شما از `when` تعیین می‌کند که آیا لازم است تمام حالت‌های ممکن را در شاخه‌های خود پوشش دهید یا خیر. پوشش دادن تمام حالت‌های ممکن، **جامع بودن (exhaustive)** نامیده می‌شود.

### دستورات (Statements)

اگر از `when` به عنوان یک دستور استفاده کنید، نیازی به پوشش دادن تمام حالت‌های ممکن ندارید. در مثال زیر، برخی از حالت‌ها پوشش داده نشده‌اند، بنابراین هیچ شاخه‌ای اجرا نمی‌شود، اما خطایی هم رخ نمی‌دهد:

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

درست مانند `if` ، هر شاخه می‌تواند یک بلوک کد باشد و مقدار آن برابر با مقدار آخرین عبارت در آن بلوک است.

### عبارات (Expressions)

اگر از `when` به عنوان یک عبارت استفاده کنید، **باید** تمام حالت‌های ممکن را پوشش دهید. مقدار اولین شاخه منطبق، به عنوان مقدار کل عبارت در نظر گرفته می‌شود. اگر تمام حالت‌ها را پوشش ندهید، کامپایلر خطا می‌دهد.

اگر عبارت `when` شما دارای موضوع باشد، می‌توانید از شاخه `else` استفاده کنید تا مطمئن شوید تمام حالت‌های ممکن پوشش داده شده‌اند، اما این کار اجباری نیست. برای مثال، اگر موضوع شما یک `Boolean` ، [کلاس `enum`](https://kotlinlang.org/docs/enum-classes.html) ، [کلاس `sealed`](https://kotlinlang.org/docs/sealed-classes.html) یا یکی از معادل‌های قابل تهی (nullable) آن‌ها باشد، می‌توانید بدون شاخه `else` تمام حالت‌ها را پوشش دهید:

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
        // نیازی به شاخه else نیست چون تمام حالت‌ها پوشش داده شده‌اند
        Bit.ZERO -> 0
        Bit.ONE -> 1
    }

    println("Random bit as number: $numericValue")
    // Random bit as number: 0
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-when-expression-subject"}

> برای ساده‌سازی عبارات `when` و کاهش تکرار، قابلیت **context-sensitive resolution** را امتحان کنید (در حال حاضر در مرحله پیش‌نمایش). این ویژگی به شما اجازه می‌دهد هنگام استفاده از ورودی‌های enum یا اعضای کلاس‌های sealed در عبارات `when` ، اگر نوع مورد انتظار مشخص باشد، نام نوع را حذف کنید.
>
> برای اطلاعات بیشتر، [Preview of context-sensitive resolution](https://kotlinlang.org/docs/whatsnew22.html#preview-of-context-sensitive-resolution) یا [KEEP proposal](https://github.com/Kotlin/KEEP/blob/improved-resolution-expected-type/proposals/context-sensitive-resolution.md) را ببینید.
>
{style="tip"}

اگر عبارت `when` شما موضوع **نداشته باشد**، حتماً **باید** شاخه `else` داشته باشید، در غیر این صورت کامپایلر خطا می‌دهد. شاخه `else` زمانی ارزیابی می‌شود که هیچ‌کدام از شرایط شاخه‌های دیگر برقرار نباشد:

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

### روش‌های دیگر استفاده از when

عبارات و دستورات `when` روش‌های مختلفی را برای ساده‌سازی کد، مدیریت شرایط چندگانه و انجام بررسی‌های نوع داده پیشنهاد می‌دهند.

چندین شرط را با استفاده از کاما در یک شاخه گروه‌بندی کنید:

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

از عباراتی که نتیجه آن‌ها `true` یا `false` است به عنوان شرایط شاخه استفاده کنید:

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

نوع داده یک مقدار را با استفاده از کلمات کلیدی `is` یا `!is` بررسی کنید. به دلیل قابلیت [کست هوشمند (smart casts)](https://kotlinlang.org/docs/typecasts.html#smart-casts)، می‌توانید مستقیماً به توابع و ویژگی‌های (properties) آن نوع دسترسی داشته باشید:

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

می‌توانید از `when` به جای زنجیره‌ای از `if`-`else` `if` های سنتی استفاده کنید. بدون موضوع، شرایط شاخه‌ها صرفاً عبارات بولین (boolean) هستند. اولین شاخه‌ای که شرط آن `true` باشد اجرا می‌شود:

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

در نهایت، می‌توانید موضوع را با استفاده از نحو (syntax) زیر در یک متغیر ذخیره کنید:

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

محدوده (scope) متغیری که به عنوان موضوع تعریف شده است، به بدنه همان عبارت یا دستور `when` محدود می‌شود.

### شرایط محافظ (Guard conditions) {id="guard-conditions-in-when-expressions"}

شرایط محافظ به شما اجازه می‌دهند بیش از یک شرط را در شاخه‌های یک عبارت یا دستور `when` بگنجانید و جریان‌های کنترلی پیچیده را صریح‌تر و کوتاه‌تر کنید. تا زمانی که `when` دارای موضوع باشد، می‌توانید از شرایط محافظ استفاده کنید.

شرط محافظ را بعد از شرط اصلی در همان شاخه قرار دهید و آن‌ها را با `if` از هم جدا کنید:

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
        // شاخه‌ای فقط با شرط اصلی
        // زمانی که animal از نوع Dog باشد feedDog() فراخوانی می‌شود
        is Animal.Dog -> feedDog()
        // شاخه‌ای با هر دو شرط اصلی و محافظ
        // زمانی که animal از نوع Cat باشد و mouseHunter نباشد feedCat() فراخوانی می‌شود
        is Animal.Cat if !animal.mouseHunter -> feedCat()
        // اگر هیچ‌کدام از شرایط بالا برقرار نباشد "Unknown animal" چاپ می‌شود
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

شما نمی‌توانید زمانی که چندین شرط با کاما از هم جدا شده‌اند، از شرایط محافظ استفاده کنید. به عنوان مثال:

```kotlin
0, 1 -> print("x == 0 or x == 1")
```

در یک عبارت یا دستور `when` واحد، می‌توانید شاخه‌های دارای شرط محافظ و بدون آن را با هم ترکیب کنید. کد یک شاخه با شرط محافظ تنها زمانی اجرا می‌شود که هر دو شرط اصلی و شرط محافظ `true` باشند. اگر شرط اصلی مطابقت نداشته باشد، شرط محافظ ارزیابی نمی‌شود.

از آنجایی که دستورات `when` نیازی به پوشش تمام حالت‌ها ندارند، استفاده از شرایط محافظ در دستورات `when` بدون شاخه `else` به این معنی است که اگر هیچ شرطی مطابقت نداشته باشد، هیچ کدی اجرا نمی‌شود.

برخلاف دستورات، عبارات `when` باید تمام حالت‌ها را پوشش دهند. اگر از شرایط محافظ در عبارات `when` بدون شاخه `else` استفاده کنید، کامپایلر از شما می‌خواهد که هر حالت ممکن را مدیریت کنید تا از خطاهای زمان اجرا جلوگیری شود.

چندین شرط محافظ را در یک شاخه با استفاده از عملگرهای بولین `&&` (AND) یا `||` (OR) ترکیب کنید. برای [جلوگیری از سردرگمی](https://kotlinlang.org/docs/coding-conventions-fa.html#guard-conditions-in-when-expression)، از پرانتز در اطراف عبارات بولین استفاده کنید:

```kotlin
when (animal) {
    is Animal.Cat if (!animal.mouseHunter && animal.hungry) -> feedCat()
}
```

شرایط محافظ همچنین از `else if` پشتیبانی می‌کنند:

```kotlin
when (animal) {
    // بررسی می‌کند که آیا animal از نوع Dog است
    is Animal.Dog -> feedDog()
    // شرط محافظی که بررسی می‌کند آیا animal از نوع Cat است و mouseHunter نیست
    is Animal.Cat if !animal.mouseHunter -> feedCat()
    // اگر هیچ‌کدام از شرایط بالا برقرار نباشد و animal.eatsPlants برابر true باشد giveLettuce() فراخوانی می‌شود
    else if animal.eatsPlants -> giveLettuce()
    // اگر هیچ‌کدام از شرایط بالا برقرار نباشد "Unknown animal" چاپ می‌شود
    else -> println("Unknown animal")
}
```

## حلقه‌های For

از حلقه `for` برای پیمایش در یک [مجموعه (collection)](https://kotlinlang.org/docs/collections-overview.html) ، [آرایه (array)](arrays-fa.md) یا [بازه (range)](https://kotlinlang.org/docs/ranges.html) استفاده کنید:

```kotlin
for (item in collection) print(item)
```

بدنه یک حلقه `for` می‌تواند یک بلوک کد با آکولاد `{}` باشد.

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

برای پیمایش روی بازه‌ای از اعداد، از یک [عبارت بازه (range expression)](https://kotlinlang.org/docs/ranges.html) با عملگرهای `..` و `..<` استفاده کنید:

```kotlin
fun main() {
//sampleStart
    println("Closed-ended range:")
    for (i in 1..6) {
        print(i)
    }
    // Closed-ended range:
    // 123456
  
    println("\nOpen-ended range:")
    for (i in 1..<6) {
        print(i)
    }
    // Open-ended range:
    // 12345
  
    println("\nReverse order in steps of 2:")
    for (i in 6 downTo 0 step 2) {
        print(i)
    }
    // Reverse order in steps of 2:
    // 6420
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-for-loop-range"}

### آرایه‌ها (Arrays)

اگر می‌خواهید یک آرایه یا لیست را همراه با ایندکس (index) پیمایش کنید، می‌توانید از ویژگی `indices` استفاده کنید:

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

به عنوان جایگزین، می‌توانید از تابع [`.withIndex()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/with-index.html) از کتابخانه استاندارد استفاده کنید:

```kotlin
fun main() {
    val routineSteps = arrayOf("Wake up", "Brush teeth", "Make coffee")
    //sampleStart
    for ((index, value) in routineSteps.withIndex()) {
        println("The step at $index is \"$value\"")
    }
    // The step at 0 is "Wake up"
    // The step at 1 is "Brush teeth"
    // The step at 2 is "Make coffee"
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-for-loop-array-index"}

### تکرارکننده‌ها (Iterators)

حلقه `for` هر چیزی را که یک [تکرارکننده (iterator)](https://kotlinlang.org/docs/iterators.html) فراهم کند، پیمایش می‌کند. مجموعه‌ها به صورت پیش‌فرض تکرارکننده دارند، در حالی که بازه‌ها و آرایه‌ها به حلقه‌های مبتنی بر ایندکس کامپایل می‌شوند.

شما می‌توانید با ارائه یک تابع عضو یا یک تابع الحاقی (extension function) به نام `iterator()` که یک `Iterator<>` برمی‌گرداند، تکرارکننده خود را بسازید. تابع `iterator()` باید دارای تابع `next()` و تابع `hasNext()` باشد که یک `Boolean` برمی‌گرداند.

ساده‌ترین راه برای ایجاد تکرارکننده برای یک کلاس، ارث‌بری از رابط (interface) [`Iterable<T>`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/-iterable/) و بازنویسی (override) توابع `iterator()` ، `next()` و `hasNext()` است که از قبل در آنجا وجود دارند. برای مثال:

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
    // Reading page 1
    // Reading page 2
    // Reading page 3
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-for-loop-inherit-iterator"}

> درباره [رابط‌ها (interfaces)](https://kotlinlang.org/docs/interfaces.html) و [ارث‌بری (inheritance)](https://kotlinlang.org/docs/inheritance.html) بیشتر بیاموزید.
>
{style="tip"}

به عنوان جایگزین، می‌توانید توابع را از ابتدا بسازید. در این صورت، کلمه کلیدی `operator` را به توابع اضافه کنید:

```kotlin
//sampleStart
class Booklet(val totalPages: Int) {
    operator fun iterator(): Iterator<Int> {
        return object {
            var current = 1

            operator fun hasNext() = current <= totalPages
            operator fun next() = current++
        }.let {
            object : Iterator<Int> {
                override fun hasNext() = it.hasNext()
                override fun next() = it.next()
            }
        }
    }
}
//sampleEnd

fun main() {
    val booklet = Booklet(3)
    for (page in booklet) {
        println("Reading page $page")
    }
    // Reading page 1
    // Reading page 2
    // Reading page 3
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-for-loop-iterator-from-scratch"}

## حلقه‌های While

حلقه‌های `while` و `do-while` کد موجود در بدنه خود را تا زمانی که شرط برقرار باشد، به طور مداوم اجرا می‌کنند. تفاوت بین آن‌ها در زمان بررسی شرط است:

* `while` ابتدا شرط را بررسی می‌کند و اگر برقرار بود، کد بدنه را اجرا کرده و سپس دوباره به مرحله بررسی شرط بازمی‌گردد.
* `do-while` ابتدا کد بدنه را اجرا کرده و سپس شرط را بررسی می‌کند. اگر برقرار بود، حلقه تکرار می‌شود. بنابراین، بدنه `do-while` حداقل یک بار، صرف‌نظر از شرط، اجرا می‌شود.

برای حلقه `while` ، شرط مورد نظر را در پرانتز `()` و بدنه را در آکولاد `{}` قرار دهید:

```kotlin
fun main() {
    var carsInGarage = 0
    val maxCapacity = 3
//sampleStart
    while (carsInGarage < maxCapacity) {
        println("Car entered. Cars now in garage: ${++carsInGarage}")
    }
    // Car entered. Cars now in garage: 1
    // Car entered. Cars now in garage: 2
    // Car entered. Cars now in garage: 3

    println("Garage is full!")
    // Garage is full!
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-while-loop"}

برای حلقه `do-while` ، ابتدا بدنه را در آکولاد `{}` و سپس شرط را در پرانتز `()` بنویسید:

```kotlin
import kotlin.random.Random

fun main() {
    var roll: Int
//sampleStart
    do {
        roll = Random.nextInt(1, 7)
        println("Rolled a $roll")
    } while (roll != 6)
    // Rolled a 2
    // Rolled a 6
    
    println("Got a 6! Game over.")
    // Got a 6! Game over.
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="kotlin-do-while-loop"}

## Break و continue در حلقه‌ها

کاتلین از عملگرهای سنتی `break` و `continue` در حلقه‌ها پشتیبانی می‌کند. به بخش [بازگشت‌ها و پرش‌ها (Returns and jumps)](https://kotlinlang.org/docs/returns.html) مراجعه کنید.
