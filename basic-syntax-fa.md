[//]: # (title: Basic syntax overview)

این مجموعه‌ای از عناصر پایهٔ سینتکس به همراه مثال‌ها است. در انتهای هر بخش، لینکی به  
توضیح مفصل‌تر دربارهٔ موضوع مرتبط پیدا خواهید کرد.

همچنین می‌توانید تمام مباحث ضروری Kotlin را با دورهٔ رایگان  
[Kotlin Core track](https://hyperskill.org/tracks?category=4&utm_source=jbkotlin_hs&utm_medium=referral&utm_campaign=kotlinlang-docs&utm_content=button_1&utm_term=22.03.23)  
از JetBrains Academy یاد بگیرید.

## تعریف پکیج و ایمپورت‌ها

مشخص‌کردن پکیج باید در بالای فایل سورس قرار بگیرد:

```kotlin
package my.demo

import kotlin.text.*

// ...
```

لازم نیست مسیر دایرکتوری‌ها با نام پکیج‌ها یکی باشد؛ فایل‌های سورس می‌توانند به‌صورت دلخواه در سیستم فایل قرار بگیرند.

ببینید: [Packages](kotlin-learn-fa/packages-fa.md).

## نقطهٔ شروع برنامه

نقطهٔ شروع یک برنامهٔ Kotlin تابع `main` است:

```kotlin
fun main() {
    println("Hello world!")
}
```
شکل دیگری از `main` وجود دارد که تعداد متغیری از آرگومان‌های `String` را می‌پذیرد:

```kotlin
fun main(args: Array<String>) {
    println(args.contentToString())
}
```
## چاپ در خروجی استاندارد

تابع `print` آرگومان خود را در خروجی استاندارد چاپ می‌کند:

```kotlin
fun main() {
//sampleStart
    print("Hello ")
    print("world!")
//sampleEnd
}
```
تابع `println` آرگومان‌های خود را چاپ می‌کند و یک خط جدید اضافه می‌کند، به‌طوری که خروجی بعدی در خط بعدی نمایش داده می‌شود:

```kotlin
fun main() {
//sampleStart
    println("Hello world!")
    println(42)
//sampleEnd
}
```
## خواندن از ورودی استاندارد

تابع `readln()` از ورودی استاندارد می‌خواند. این تابع کل خطی را که کاربر وارد می‌کند به‌صورت یک رشته برمی‌گرداند.

می‌توانید از توابع `println()`، `readln()` و `print()` به‌صورت ترکیبی برای نمایش پیام درخواست ورودی  
و نمایش ورودی کاربر استفاده کنید:

```kotlin
// Prints a message to request input
println("Enter any word: ")

// Reads and stores the user input. For example: Happiness
val yourWord = readln()

// Prints a message with the input
print("You entered the word: ")
print(yourWord)
// You entered the word: Happiness
```

برای اطلاعات بیشتر ببینید: [Read standard input](read-standard-input-fa.md).

## توابع

تابعی با دو پارامتر `Int` و نوع بازگشتی `Int`:

```kotlin
//sampleStart
fun sum(a: Int, b: Int): Int {
    return a + b
}
//sampleEnd

fun main() {
    print("sum of 3 and 5 is ")
    println(sum(3, 5))
}
```
بدنهٔ یک تابع می‌تواند یک expression باشد. در این حالت نوع بازگشتی به‌صورت خودکار تشخیص داده می‌شود:

```kotlin
//sampleStart
fun sum(a: Int, b: Int) = a + b
//sampleEnd

fun main() {
    println("sum of 19 and 23 is ${sum(19, 23)}")
}
```
تابعی که مقدار معناداری برنمی‌گرداند:

```kotlin
//sampleStart
fun printSum(a: Int, b: Int): Unit {
    println("sum of $a and $b is ${a + b}")
}
//sampleEnd

fun main() {
    printSum(-1, 8)
}
```
می‌توان نوع بازگشتی `Unit` را حذف کرد:

```kotlin
//sampleStart
fun printSum(a: Int, b: Int) {
    println("sum of $a and $b is ${a + b}")
}
//sampleEnd

fun main() {
    printSum(-1, 8)
}
```
ببینید: [Functions](functions.md).

## متغیرها

در Kotlin، متغیر با یکی از کلمات کلیدی `val` یا `var` و سپس نام متغیر تعریف می‌شود.

از کلمهٔ کلیدی `val` برای تعریف متغیرهایی استفاده می‌شود که فقط یک‌بار مقداردهی می‌شوند. این متغیرها تغییرناپذیر هستند و بعد از مقداردهی اولیه نمی‌توان مقدار جدیدی به آن‌ها اختصاص داد:

```kotlin
fun main() {
//sampleStart
    // Declares the variable x and initializes it with the value of 5
    val x: Int = 5
    // 5
//sampleEnd
    println(x)
}
```
از کلمهٔ کلیدی `var` برای تعریف متغیرهایی استفاده می‌شود که می‌توان مقدارشان را تغییر داد. این متغیرها قابل تغییر هستند و بعد از مقداردهی اولیه می‌توان مقدار آن‌ها را عوض کرد:

```kotlin
fun main() {
//sampleStart
    // Declares the variable x and initializes it with the value of 5
    var x: Int = 5
    // Reassigns a new value of 6 to the variable x
    x += 1
    // 6
//sampleEnd
    println(x)
}
```
Kotlin از استنتاج نوع پشتیبانی می‌کند و نوع دادهٔ متغیر را به‌صورت خودکار تشخیص می‌دهد. هنگام تعریف متغیر می‌توانید نوع را حذف کنید:

```kotlin
fun main() {
//sampleStart
    // Declares the variable x with the value of 5;`Int` type is inferred
    val x = 5
    // 5
//sampleEnd
    println(x)
}
```
می‌توانید متغیرها را فقط بعد از مقداردهی اولیه استفاده کنید. یا باید در زمان تعریف مقداردهی شوند، یا ابتدا تعریف و بعداً مقداردهی شوند.  
در حالت دوم، باید نوع داده مشخص شود:

```kotlin
fun main() {
//sampleStart
    // Initializes the variable x at the moment of declaration; type is not required
    val x = 5
    // Declares the variable c without initialization; type is required
    val c: Int
    // Initializes the variable c after declaration 
    c = 3
    // 5 
    // 3
//sampleEnd
    println(x)
    println(c)
}
```
می‌توانید متغیرها را در سطح بالا (top-level) تعریف کنید:

```kotlin
//sampleStart
val PI = 3.14
var x = 0

fun incrementX() {
    x += 1
}
// x = 0; PI = 3.14
// incrementX()
// x = 1; PI = 3.14
//sampleEnd

fun main() {
    println("x = $x; PI = $PI")
    incrementX()
    println("incrementX()")
    println("x = $x; PI = $PI")
}
```
برای اطلاعات بیشتر دربارهٔ تعریف property‌ها ببینید: [Properties](properties.md).

## ساخت کلاس‌ها و نمونه‌ها

برای تعریف یک کلاس از کلمهٔ کلیدی `class` استفاده می‌شود:
```kotlin
class Shape
```

ویژگی‌های یک کلاس می‌توانند در اعلان کلاس یا در بدنهٔ آن تعریف شوند:

```kotlin
class Rectangle(val height: Double, val length: Double) {
    val perimeter = (height + length) * 2 
}
```

سازندهٔ پیش‌فرض با پارامترهایی که در اعلان کلاس آمده‌اند به‌صورت خودکار در دسترس است:

```kotlin
class Rectangle(val height: Double, val length: Double) {
    val perimeter = (height + length) * 2 
}
fun main() {
    val rectangle = Rectangle(5.0, 2.0)
    println("The perimeter is ${rectangle.perimeter}")
}
```
ارث‌بری بین کلاس‌ها با علامت دونقطه (`:`) مشخص می‌شود. کلاس‌ها به‌صورت پیش‌فرض `final` هستند؛ برای قابل‌ارث‌بری کردن یک کلاس باید آن را `open` علامت‌گذاری کرد:

```kotlin
open class Shape

class Rectangle(val height: Double, val length: Double): Shape() {
    val perimeter = (height + length) * 2 
}
```

برای اطلاعات بیشتر دربارهٔ سازنده‌ها و ارث‌بری ببینید: [Classes](classes.md) و [Objects and instances](object-declarations.md).

## کامنت‌ها

مانند اکثر زبان‌های مدرن، Kotlin از کامنت‌های تک‌خطی (یا انتهای خط) و چندخطی (بلاک) پشتیبانی می‌کند:

```kotlin
// This is an end-of-line comment

/* This is a block comment
   on multiple lines. */
```

کامنت‌های بلاکی در Kotlin می‌توانند تو‌در‌تو باشند:

```kotlin
/* The comment starts here
/* contains a nested comment *​/  
and ends here. */
```

برای اطلاعات بیشتر دربارهٔ سینتکس کامنت‌های مستندات ببینید: [Documenting Kotlin Code](kotlin-doc.md).

## قالب‌های رشته‌ای (String templates)

```kotlin
fun main() {
//sampleStart
    var a = 1
    // simple name in template:
    val s1 = "a is $a" 
    
    a = 2
    // arbitrary expression in template:
    val s2 = "${s1.replace("is", "was")}, but now is $a"
//sampleEnd
    println(s2)
}
```
برای جزئیات بیشتر ببینید: [String templates](strings.md#string-templates).

## عبارات شرطی

```kotlin
//sampleStart
fun maxOf(a: Int, b: Int): Int {
    if (a > b) {
        return a
    } else {
        return b
    }
}
//sampleEnd

fun main() {
    println("max of 0 and 42 is ${maxOf(0, 42)}")
}
```
در Kotlin، `if` می‌تواند به‌عنوان یک expression نیز استفاده شود:

```kotlin
//sampleStart
fun maxOf(a: Int, b: Int) = if (a > b) a else b
//sampleEnd

fun main() {
    println("max of 0 and 42 is ${maxOf(0, 42)}")
}
```
ببینید: [`if`-expressions](control-flow.md#if-expression).

## حلقهٔ for

```kotlin
fun main() {
//sampleStart
    val items = listOf("apple", "banana", "kiwifruit")
    for (item in items) {
        println(item)
    }
//sampleEnd
}
```
یا:

```kotlin
fun main() {
//sampleStart
    val items = listOf("apple", "banana", "kiwifruit")
    for (index in items.indices) {
        println("item at $index is ${items[index]}")
    }
//sampleEnd
}
```
ببینید: [for loop](control-flow.md#for-loops).

## حلقهٔ while

```kotlin
fun main() {
//sampleStart
    val items = listOf("apple", "banana", "kiwifruit")
    var index = 0
    while (index < items.size) {
        println("item at $index is ${items[index]}")
        index++
    }
//sampleEnd
}
```
ببینید: [while loop](control-flow.md#while-loops).

## عبارت when

```kotlin
//sampleStart
fun describe(obj: Any): String =
    when (obj) {
        1          -> "One"
        "Hello"    -> "Greeting"
        is Long    -> "Long"
        !is String -> "Not a string"
        else       -> "Unknown"
    }
//sampleEnd

fun main() {
    println(describe(1))
    println(describe("Hello"))
    println(describe(1000L))
    println(describe(2))
    println(describe("other"))
}
```
ببینید: [when expressions and statements](control-flow.md#when-expressions-and-statements).

## بازه‌ها (Ranges)

بررسی اینکه یک عدد داخل یک بازه است با استفاده از عملگر `in`:

```kotlin
fun main() {
//sampleStart
    val x = 10
    val y = 9
    if (x in 1..y+1) {
        println("fits in range")
    }
//sampleEnd
}
```
بررسی اینکه یک عدد خارج از بازه است:

```kotlin
fun main() {
//sampleStart
    val list = listOf("a", "b", "c")
    
    if (-1 !in 0..list.lastIndex) {
        println("-1 is out of range")
    }
    if (list.size !in list.indices) {
        println("list size is out of valid list indices range, too")
    }
//sampleEnd
}
```
پیمایش یک بازه:

```kotlin
fun main() {
//sampleStart
    for (x in 1..5) {
        print(x)
    }
//sampleEnd
}
```
یا یک progression:

```kotlin
fun main() {
//sampleStart
    for (x in 1..10 step 2) {
        print(x)
    }
    println()
    for (x in 9 downTo 0 step 3) {
        print(x)
    }
//sampleEnd
}
```
ببینید: [Ranges and progressions](ranges.md).

## کالکشن‌ها

پیمایش یک کالکشن:

```kotlin
fun main() {
    val items = listOf("apple", "banana", "kiwifruit")
//sampleStart
    for (item in items) {
        println(item)
    }
//sampleEnd
}
```
بررسی اینکه آیا یک کالکشن شامل یک شیء هست با استفاده از عملگر `in`:

```kotlin
fun main() {
    val items = setOf("apple", "banana", "kiwifruit")
//sampleStart
    when {
        "orange" in items -> println("juicy")
        "apple" in items -> println("apple is fine too")
    }
//sampleEnd
}
```
استفاده از [lambda expressions](lambdas.md) برای فیلتر و map کردن کالکشن‌ها:

```kotlin
fun main() {
//sampleStart
    val fruits = listOf("banana", "avocado", "apple", "kiwifruit")
    fruits
      .filter { it.startsWith("a") }
      .sortedBy { it }
      .map { it.uppercase() }
      .forEach { println(it) }
//sampleEnd
}
```
ببینید: [Collections overview](collections-overview.md).

## مقادیر nullable و بررسی null

وقتی امکان `null` بودن وجود دارد، باید مرجع به‌صورت صریح nullable علامت‌گذاری شود. نوع‌های nullable در انتها علامت `?` دارند.

اگر `str` شامل یک عدد صحیح نباشد، `null` برگردانده می‌شود:

```kotlin
fun parseInt(str: String): Int? {
    // ...
}
```

استفاده از تابعی که مقدار nullable برمی‌گرداند:

```kotlin
fun parseInt(str: String): Int? {
    return str.toIntOrNull()
}

//sampleStart
fun printProduct(arg1: String, arg2: String) {
    val x = parseInt(arg1)
    val y = parseInt(arg2)

    // Using `x * y` yields error because they may hold nulls.
    if (x != null && y != null) {
        // x and y are automatically cast to non-nullable after null check
        println(x * y)
    }
    else {
        println("'$arg1' or '$arg2' is not a number")
    }    
}
//sampleEnd

fun main() {
    printProduct("6", "7")
    printProduct("a", "7")
    printProduct("a", "b")
}
```
یا:

```kotlin
fun parseInt(str: String): Int? {
    return str.toIntOrNull()
}

fun printProduct(arg1: String, arg2: String) {
    val x = parseInt(arg1)
    val y = parseInt(arg2)
    
//sampleStart
    // ...
    if (x == null) {
        println("Wrong number format in arg1: '$arg1'")
        return
    }
    if (y == null) {
        println("Wrong number format in arg2: '$arg2'")
        return
    }

    // x and y are automatically cast to non-nullable after null check
    println(x * y)
//sampleEnd
}

fun main() {
    printProduct("6", "7")
    printProduct("a", "7")
    printProduct("99", "b")
}
```
ببینید: [Null-safety](null-safety.md).

## بررسی نوع و تبدیل خودکار

عملگر `is` بررسی می‌کند که آیا یک expression نمونه‌ای از یک نوع مشخص است یا نه.  
اگر یک متغیر محلی immutable یا یک property برای یک نوع خاص بررسی شود، نیازی به cast صریح نیست.


```kotlin
//sampleStart
fun getStringLength(obj: Any): Int? {
    if (obj is String) {
        // `obj` is automatically cast to `String` in this branch
        return obj.length
    }

    // `obj` is still of type `Any` outside of the type-checked branch
    return null
}
//sampleEnd

fun main() {
    fun printLength(obj: Any) {
        println("Getting the length of '$obj'. Result: ${getStringLength(obj) ?: "Error: The object is not a string"} ")
    }
    printLength("Incomprehensibilities")
    printLength(1000)
    printLength(listOf(Any()))
}
```
یا:

```kotlin
//sampleStart
fun getStringLength(obj: Any): Int? {
    if (obj !is String) return null

    // `obj` is automatically cast to `String` in this branch
    return obj.length
}
//sampleEnd

fun main() {
    fun printLength(obj: Any) {
        println("Getting the length of '$obj'. Result: ${getStringLength(obj) ?: "Error: The object is not a string"} ")
    }
    printLength("Incomprehensibilities")
    printLength(1000)
    printLength(listOf(Any()))
}
```
یا:

```kotlin
//sampleStart
fun getStringLength(obj: Any): Int? {
    // `obj` is automatically cast to `String` on the right-hand side of `&&`
    if (obj is String && obj.length >= 0) {
        return obj.length
    }

    return null
}
//sampleEnd

fun main() {
    fun printLength(obj: Any) {
        println("Getting the length of '$obj'. Result: ${getStringLength(obj) ?: "Error: The object is not a string"} ")
    }
    printLength("Incomprehensibilities")
    printLength("")
    printLength(1000)
}
```

ببینید: [Classes](classes.md) و [Type casts](typecasts.md).
