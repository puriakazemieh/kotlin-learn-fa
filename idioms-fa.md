[//]: # (title: Idioms)

مجموعه‌ای از اصطلاحات تصادفی و پرکاربرد در کاتلین. اگر اصطلاح موردعلاقه‌ای دارید، با ارسال یک pull request آن را اضافه کنید.

## ایجاد DTOها (POJOها / POCOها)

```kotlin
data class Customer(val name: String, val email: String)
```

این کد یک کلاس `Customer` با قابلیت‌های زیر فراهم می‌کند:

- getter (و در صورت استفاده از `var`، setter) برای تمام ویژگی‌ها
- `equals()`
- `hashCode()`
- `toString()`
- `copy()`
- `component1()`, `component2()` و ... برای تمام ویژگی‌ها (به [Data classes](data-classes.md) مراجعه کنید)


## مقادیر پیش‌فرض برای پارامترهای تابع

```kotlin
fun foo(a: Int = 0, b: String = "") { ... }
```

## فیلتر کردن یک لیست

```kotlin
val positives = list.filter { x -> x > 0 }
```

یا به شکل کوتاه‌تر:

```kotlin
val positives = list.filter { it > 0 }
```

تفاوت [فیلتر کردن در جاوا و کاتلین](java-to-kotlin-collections-guide.md#filter-elements) را یاد بگیرید.

## بررسی وجود یک عنصر در یک کالکشن

```kotlin
if ("john@example.com" in emailsList) { ... }

if ("jane@example.com" !in emailsList) { ... }
```

## درون‌یابی رشته (String interpolation)

```kotlin
println("Name $name")
```

تفاوت [چسباندن رشته‌ها در جاوا و کاتلین](java-to-kotlin-idioms-strings.md#concatenate-strings) را یاد بگیرید.

## خواندن امن ورودی استاندارد

```kotlin
// یک رشته می‌خواند و اگر ورودی قابل تبدیل به عدد صحیح نباشد، null برمی‌گرداند. مثال: Hi there!
val wrongInt = readln().toIntOrNull()
println(wrongInt)
// null

// یک رشته می‌خواند که قابل تبدیل به عدد صحیح است و یک عدد صحیح برمی‌گرداند. مثال: 13
val correctInt = readln().toIntOrNull()
println(correctInt)
// 13
```

برای اطلاعات بیشتر، به [خواندن ورودی استاندارد](read-standard-input.md) مراجعه کنید.

## بررسی نوع (Instance checks)

```kotlin
when (x) {
    is Foo -> ...
    is Bar -> ...
    else   -> ...
}
```

## لیست فقط‌خواندنی (Read-only)

```kotlin
val list = listOf("a", "b", "c")
```
## مپ فقط‌خواندنی (Read-only)

```kotlin
val map = mapOf("a" to 1, "b" to 2, "c" to 3)
```

## دسترسی به یک ورودی در مپ

```kotlin
println(map["key"])
map["key"] = value
```

## پیمایش یک مپ یا لیستی از زوج‌ها

```kotlin
for ((k, v) in map) {
    println("$k -> $v")
}
```

در `k` و `v` می‌توانند هر نام دلخواهی مانند `name` و `age` باشند.

## پیمایش یک بازه (Range)

```kotlin
for (i in 1..100) { ... }  // بازه بسته: شامل 100 می‌شود
for (i in 1..<100) { ... } // بازه باز: شامل 100 نمی‌شود
for (x in 2..10 step 2) { ... }
for (x in 10 downTo 1) { ... }
(1..10).forEach { ... }
```

## ویژگی تنبل (Lazy property)

```kotlin
val p: String by lazy { // مقدار فقط در اولین دسترسی محاسبه می‌شود
    // محاسبه رشته
}
```

## توابع توسعه‌ای (Extension functions)

```kotlin
fun String.spaceToCamelCase() { ... }

"Convert this to camelcase".spaceToCamelCase()
```

## ایجاد یک Singleton

```kotlin
object Resource {
    val name = "Name"
}
```

## استفاده از کلاس‌های مقدار درون‌خطی برای مقادیر type-safe

```kotlin
@JvmInline
value class EmployeeId(private val id: String)

@JvmInline
value class CustomerId(private val id: String)
```

اگر به‌اشتباه `EmployeeId` و `CustomerId` را با هم جابه‌جا کنید، خطای کامپایل رخ می‌دهد.

> انوتیشن `@JvmInline` فقط برای بک‌اند JVM لازم است.

## نمونه‌سازی از یک کلاس abstract

```kotlin
abstract class MyAbstractClass {
    abstract fun doSomething()
    abstract fun sleep()
}

fun main() {
    val myObject = object : MyAbstractClass() {
        override fun doSomething() {
            // ...
        }

        override fun sleep() { // ...
        }
    }
    myObject.doSomething()
}
```

## شکل کوتاه if-not-null

```kotlin
val files = File("Test").listFiles()

println(files?.size) // size is printed if files is not null
```

## شکل کوتاه if-not-null-else

```kotlin
val files = File("Test").listFiles()

// For simple fallback values:
println(files?.size ?: "empty") // if files is null, this prints "empty"

// To calculate a more complicated fallback value in a code block, use `run`
val filesSize = files?.size ?: run { 
    val someSize = getSomeSize()
    someSize * 2
}
println(filesSize)
```

## اجرای یک عبارت در صورت نال بودن

```kotlin
val values = ...
val email = values["email"] ?: throw IllegalStateException("Email is missing!")
```

## گرفتن اولین عنصر از یک کالکشن که ممکن است خالی باشد
```kotlin
val emails = ... // might be empty
val mainEmail = emails.firstOrNull() ?: ""
```

تفاوت [گرفتن اولین آیتم در جاوا و کاتلین](java-to-kotlin-collections-guide.md#get-the-first-and-the-last-items-of-a-possibly-empty-collection) را یاد بگیرید.

## اجرا در صورت نال نبودن

```kotlin
val value = ...

value?.let {
    ... // execute this block if not null
}
```

## نگاشت مقدار nullable در صورت نال نبودن

```kotlin
val value = ...

val mapped = value?.let { transformValue(it) } ?: defaultValue 
// defaultValue is returned if the value or the transform result is null.
```

## استفاده از return در عبارت when

```kotlin
fun transform(color: String): Int {
    return when (color) {
        "Red" -> 0
        "Green" -> 1
        "Blue" -> 2
        else -> throw IllegalArgumentException("Invalid color param value")
    }
}
```

## عبارت try-catch

```kotlin
fun test() {
    val result = try {
        count()
    } catch (e: ArithmeticException) {
        throw IllegalStateException(e)
    }

    // Working with result
}
```

## عبارت if

```kotlin
val y = if (x == 1) {
    "one"
} else if (x == 2) {
    "two"
} else {
    "other"
}
```

## استفاده builder-style از متدهایی که Unit برمی‌گردانند

```kotlin
fun arrayOfMinusOnes(size: Int): IntArray {
    return IntArray(size).apply { fill(-1) }
}
```

## توابع تک‌عبارتی (Single-expression functions)

```kotlin
fun theAnswer() = 42
```

معادل است با:

```kotlin
fun theAnswer(): Int {
    return 42
}
```

می‌توان این روش را با سایر اصطلاحات ترکیب کرد تا کد کوتاه‌تر شود. برای مثال با عبارت `when`:

```kotlin
fun transform(color: String): Int = when (color) {
    "Red" -> 0
    "Green" -> 1
    "Blue" -> 2
    else -> throw IllegalArgumentException("Invalid color param value")
}
```

## فراخوانی چند متد روی یک نمونه شیء (with)

```kotlin
class Turtle {
    fun penDown()
    fun penUp()
    fun turn(degrees: Double)
    fun forward(pixels: Double)
}

val myTurtle = Turtle()
with(myTurtle) { //draw a 100 pix square
    penDown()
    for (i in 1..4) {
        forward(100.0)
        turn(90.0)
    }
    penUp()
}
```

## پیکربندی ویژگی‌های یک شیء (apply)

```kotlin
val myRectangle = Rectangle().apply {
    length = 4
    breadth = 5
    color = 0xFAFAFA
}
```

این روش برای پیکربندی ویژگی‌هایی که در سازنده شیء وجود ندارند مفید است.

## معادل try-with-resources در جاوا 7

```kotlin
val stream = Files.newInputStream(Paths.get("/some/file.txt"))
stream.buffered().reader().use { reader ->
    println(reader.readText())
}
```

## تابع جنریک که به اطلاعات نوع جنریک نیاز دارد

```kotlin
//  public final class Gson {
//     ...
//     public <T> T fromJson(JsonElement json, Class<T> classOfT) throws JsonSyntaxException {
//     ...

inline fun <reified T: Any> Gson.fromJson(json: JsonElement): T = this.fromJson(json, T::class.java)
```

## جابه‌جایی دو متغیر

```kotlin
var a = 1
var b = 2
a = b.also { b = a }
```

## علامت‌گذاری کد ناتمام (TODO)

کتابخانه استاندارد کاتلین یک تابع `TODO()` دارد که همیشه یک `NotImplementedError` پرتاب می‌کند.  
نوع بازگشتی آن `Nothing` است، بنابراین می‌توان از آن صرف‌نظر از نوع مورد انتظار استفاده کرد.  
یک نسخه overload هم دارد که یک پارامتر دلیل (reason) می‌پذیرد:

```kotlin
fun calcTaxes(): BigDecimal = TODO("Waiting for feedback from accounting")
```

پلاگین کاتلین در IntelliJ IDEA معنای `TODO()` را درک می‌کند و به‌صورت خودکار یک اشاره‌گر کد در پنجره TODO اضافه می‌کند.

## قدم بعدی چیست؟

- حل کردن [مسائل Advent of Code](advent-of-code.md) با سبک ایدیوماتیک کاتلین.
- یادگیری نحوه انجام [کارهای متداول با رشته‌ها در جاوا و کاتلین](java-to-kotlin-idioms-strings.md).
- یادگیری نحوه انجام [کارهای متداول با کالکشن‌ها در جاوا و کاتلین](java-to-kotlin-collections-guide.md).
- یادگیری نحوه [مدیریت nullability در جاوا و کاتلین](java-to-kotlin-nullability-guide.md).
