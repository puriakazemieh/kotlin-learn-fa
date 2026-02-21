[//]: # (title: Numbers)

## انواع عدد صحیح (Integer types)

کاتلین مجموعه‌ای از نوع‌های داخلی (built-in) را برای نمایش اعداد فراهم می‌کند.  
برای اعداد صحیح، چهار نوع با اندازه‌ها و بازه‌های مقداری متفاوت وجود دارد:

| نوع     | اندازه (بیت) | حداقل مقدار                       | حداکثر مقدار                        |
| ------- | ------------ | --------------------------------- | ----------------------------------- |
| `Byte`  | 8            | -128                              | 127                                 |
| `Short` | 16           | -32768                            | 32767                               |
| `Int`   | 32           | -2,147,483,648 (-2³¹)             | 2,147,483,647 (2³¹ - 1)             |
| `Long`  | 64           | -9,223,372,036,854,775,808 (-2⁶³) | 9,223,372,036,854,775,807 (2⁶³ - 1) |

> علاوه بر نوع‌های صحیح علامت‌دار (signed)، کاتلین نوع‌های صحیح بدون علامت (unsigned) را نیز فراهم می‌کند.  
> از آنجا که اعداد بدون علامت برای موارد استفاده متفاوتی طراحی شده‌اند، به‌صورت جداگانه توضیح داده می‌شوند.  
> به فایل `unsigned-integer-types.md` مراجعه کنید.

وقتی متغیری را بدون مشخص کردن صریح نوع آن مقداردهی اولیه می‌کنید، کامپایلر به‌صورت خودکار کوچک‌ترین نوعی را که بتواند مقدار را نگه دارد (از `Int` شروع می‌کند) تشخیص می‌دهد.

اگر مقدار از بازه `Int` خارج نشود، نوع آن `Int` خواهد بود.  
اگر از این بازه بیشتر باشد، نوع آن `Long` خواهد بود.

برای مشخص کردن صریح مقدار `Long`، پسوند `L` را به عدد اضافه کنید.  
برای استفاده از نوع‌های `Byte` یا `Short` باید آن‌ها را صریحاً در اعلان مشخص کنید.  
مشخص کردن صریح نوع باعث می‌شود کامپایلر بررسی کند که مقدار از بازه آن نوع خارج نشده باشد.

```kotlin
val one = 1 // Int
val threeBillion = 3000000000 // Long
val oneLong = 1L // Long
val oneByte: Byte = 1
```

## انواع اعشاری (Floating-point types)

برای اعداد حقیقی، کاتلین نوع‌های اعشاری `Float` و `Double` را ارائه می‌دهد که مطابق با استاندارد IEEE 754 هستند.

و `Float` مطابق با دقت تکی (single precision)  
و `Double` مطابق با دقت دوگانه (double precision) است.

این نوع‌ها از نظر اندازه و میزان دقت متفاوت هستند:

| نوع      | اندازه (بیت) | بیت‌های معنادار | بیت‌های نما | تعداد رقم اعشاری |
| -------- | ------------ | --------------- | ----------- | ---------------- |
| `Float`  | 32           | 24              | 8           | 6–7              |
| `Double` | 64           | 53              | 11          | 15–16            |

می‌توانید متغیرهای `Double` و `Float` را فقط با اعدادی مقداردهی کنید که بخش اعشاری دارند.  
بخش اعشاری با یک نقطه (`.`) از بخش صحیح جدا می‌شود.

برای متغیرهایی که با عدد اعشاری مقداردهی می‌شوند، کامپایلر نوع `Double` را استنباط می‌کند:

```kotlin
val pi = 3.14          // Double

val one: Double = 1    // Int is inferred
// Initializer type mismatch

val oneDouble = 1.0    // Double
```

برای مشخص کردن صریح نوع `Float`، پسوند `f` یا `F` را اضافه کنید.  
اگر عدد بیش از 7 رقم اعشار داشته باشد، گرد می‌شود:

```kotlin
val e = 2.7182818284          // Double
val eFloat = 2.7182818284f    // Float, actual value is 2.7182817
```

برخلاف برخی زبان‌ها، در کاتلین تبدیل ضمنی (implicit widening) بین انواع عددی وجود ندارد.  
مثلاً تابعی که پارامتر `Double` دارد، فقط با مقدار `Double` قابل فراخوانی است، نه `Float` یا `Int`:

```kotlin
fun main() {
//sampleStart
    fun printDouble(x: Double) { print(x) }

    val x = 1.0
    val xInt = 1    
    val xFloat = 1.0f 

    printDouble(x)
    
    printDouble(xInt)   
    // Argument type mismatch
    
    printDouble(xFloat)
    // Argument type mismatch
//sampleEnd
}
```
برای تبدیل مقادیر عددی به نوع‌های دیگر، از [تبدیل‌های صریح](#explicit-number-conversions) استفاده کنید.

## ثابت‌های لیترال برای اعداد (Literal constants for numbers)

چندین نوع ثابت لیترال برای مقادیر صحیح وجود دارد:

- ده‌دهی‌ها: `123`
- نوع‌های Long، با `L` بزرگ در انتها: `123L`
- شانزده‌شانزدهی‌ها: `0x0F`
- دودویی‌ها: `0b00001011`

> لیترال‌های هشت‌هشتی (Octal) در Kotlin پشتیبانی نمی‌شوند.


در Kotlin همچنین نگارش مرسوم برای اعداد اعشاری را پشتیبانی می‌کند:
- در Doubleها (پیش‌فرض وقتی بخش اعشاری با حرف تمام نشود): `123.5`, `123.5e10`
- در Floatها، با حرف `f` یا `F` در انتها: `123.5f`

می‌توانید برای خواناتر کردن ثابت‌های عددی از آندرلاین استفاده کنید:

```kotlin
val oneMillion = 1_000_000
val creditCardNumber = 1234_5678_9012_3456L
val socialSecurityNumber = 999_99_9999L
val hexBytes = 0xFF_EC_DE_5E
val bytes = 0b11010010_01101001_10010100_10010010
val bigFractional = 1_234_567.7182818284
```

> برای لیترال‌های عدد صحیح بدون علامت نیز پسوندهای ویژه‌ای وجود دارد.  
> درباره [لیترال‌ها برای نوع‌های عدد صحیح بدون علامت](unsigned-integer-types.md) بیشتر بخوانید.


## باکس‌کردن (Boxing) و کش‌کردن اعداد روی ماشین مجازی جاوا

نحوه ذخیره‌سازی اعداد در JVM می‌تواند باعث شود کد شما به شکل غیرمنتظره‌ای رفتار کند، به‌خاطر کشی که به‌صورت پیش‌فرض  
برای اعداد کوچک (در حد اندازهٔ بایت) استفاده می‌شود.

در JVM اعداد را به‌صورت نوع‌های اولیه ذخیره می‌کند: `int`، `double` و غیره.  
وقتی از [نوع‌های جنریک](generics.md) استفاده می‌کنید یا یک ارجاع عددی nullable مثل `Int?` می‌سازید، اعداد در کلاس‌های جاوا  
مثل `Integer` یا `Double` باکس (boxed) می‌شوند.

در JVM یک [تکنیک بهینه‌سازی حافظه](https://docs.oracle.com/javase/specs/jls/se22/html/jls-5.html#jls-5.1.7)  
را روی `Integer` و سایر اشیائی که اعداد بین `−128` و `127` را نمایش می‌دهند اعمال می‌کند.  
تمام ارجاع‌های nullable به چنین اشیائی به همان شیء کش‌شده اشاره می‌کنند.  
برای مثال، اشیاء nullable در کد زیر از نظر [برابری ارجاعی](equality.md#referential-equality) برابر هستند:

```kotlin
fun main() {
//sampleStart
    val a: Int = 100
    val boxedA: Int? = a
    val anotherBoxedA: Int? = a
    
    println(boxedA === anotherBoxedA) // true
//sampleEnd
}
```

برای اعداد خارج از این بازه، اشیاء nullable متفاوت هستند اما از نظر [برابری ساختاری](equality.md#structural-equality) برابرند:

```kotlin
fun main() {
//sampleStart
    val b: Int = 10000
    val boxedB: Int? = b
    val anotherBoxedB: Int? = b
    
    println(boxedB === anotherBoxedB) // false
    println(boxedB == anotherBoxedB) // true
//sampleEnd
}
```

به همین دلیل، Kotlin درباره استفاده از برابری ارجاعی با اعداد و لیترال‌های قابل‌باکس‌شدن هشدار می‌دهد  
با پیام زیر: `"Identity equality for arguments of types ... and ... is prohibited."`  
هنگام مقایسه نوع‌های `Int`، `Short`، `Long` و `Byte` (و همچنین `Char` و `Boolean`)، از  
بررسی‌های برابری ساختاری استفاده کنید تا نتایج سازگاری بگیرید.

## تبدیل‌های صریح اعداد (Explicit number conversions)

به دلیل نمایش‌های متفاوت، نوع‌های عددی _زیرنوع_ یکدیگر نیستند.  
در نتیجه، نوع‌های کوچک‌تر _به‌طور ضمنی_ به نوع‌های بزرگ‌تر تبدیل نمی‌شوند و بالعکس.  
برای مثال، نسبت دادن مقداری از نوع `Byte` به یک متغیر `Int` به یک تبدیل صریح نیاز دارد:

```kotlin
fun main() {
//sampleStart
    val byte: Byte = 1
    // OK, literals are checked statically
    
    val intAssignedByte: Int = byte 
    // Initializer type mismatch
    
    val intConvertedByte: Int = byte.toInt()
    
    println(intConvertedByte)
//sampleEnd
}
```
تمام نوع‌های عددی از تبدیل به نوع‌های دیگر پشتیبانی می‌کنند:

- `toByte(): Byte` (برای [Float](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-float/to-byte.html) و [Double](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-double/to-byte.html) منسوخ شده است)
- `toShort(): Short`
- `toInt(): Int`
- `toLong(): Long`
- `toFloat(): Float`
- `toDouble(): Double`

در بسیاری موارد، نیازی به تبدیل صریح نیست چون نوع از متن (context) استنباط می‌شود،  
و عملگرهای حسابی برای انجام تبدیل‌ها به‌صورت خودکار overload شده‌اند. برای مثال:

```kotlin
fun main() {
//sampleStart
    val l = 1L + 3       // Long + Int => Long
    println(l is Long)   // true
//sampleEnd
}
```
### استدلال علیه تبدیل‌های ضمنی (Reasoning against implicit conversions)

در Kotlin از تبدیل‌های ضمنی پشتیبانی نمی‌کند چون می‌توانند به رفتار غیرمنتظره منجر شوند.

اگر اعدادِ با نوع‌های مختلف به‌طور ضمنی تبدیل می‌شدند، ممکن بود گاهی برابری و هویت (identity) را بی‌سروصدا از دست بدهیم.  
برای مثال، تصور کنید اگر `Int` زیرنوع `Long` بود:

```kotlin
// کد فرضی، در واقع کامپایل نمی‌شود:
val a: Int? = 1    // یک Int باکس‌شده (java.lang.Integer)
val b: Long? = a   // تبدیل ضمنی یک Long باکس‌شده تولید می‌کند (java.lang.Long)
print(b == a)      // "false" چاپ می‌کند چون Long.equals() فقط مقدار را چک نمی‌کند، بلکه بررسی می‌کند عدد دیگر هم Long باشد
```

## عملیات روی اعداد (Operations on numbers)

در Kotlin مجموعه استاندارد عملیات حسابی روی اعداد را پشتیبانی می‌کند: `+`، `-`، `*`، `/`، `%`.  
این‌ها به‌عنوان عضوِ کلاس‌های مناسب اعلان شده‌اند:

```kotlin
fun main() {
//sampleStart
    println(1 + 2)
    println(2_500_000_000L - 1L)
    println(3.14 * 2.71)
    println(10.0 / 3)
//sampleEnd
}
```

می‌توانید این عملگرها را در کلاس‌های عددی سفارشی override کنید.  
برای جزئیات، [Operator overloading](operator-overloading.md) را ببینید.

### تقسیم اعداد صحیح (Division of integers)

تقسیم بین اعداد صحیح همیشه یک عدد صحیح برمی‌گرداند. هر بخش اعشاری حذف می‌شود.

```kotlin
fun main() {
//sampleStart
    val x = 5 / 2
    println(x == 2.5) 
    // Operator '==' cannot be applied to 'Int' and 'Double'
    
    println(x == 2)   
    // true
//sampleEnd
}
```

این موضوع برای تقسیم بین هر دو نوع صحیح نیز درست است:

```kotlin
fun main() {
//sampleStart
    val x = 5L / 2
    println (x == 2)
    // Error, as Long (x) cannot be compared to Int (2)
    
    println(x == 2L)
    // true
//sampleEnd
}
```

برای برگرداندن نتیجه تقسیم همراه با بخش اعشاری، یکی از آرگومان‌ها را به‌صورت صریح به یک نوع اعشاری تبدیل کنید:

```kotlin
fun main() {
//sampleStart
    val x = 5 / 2.toDouble()
    println(x == 2.5)
//sampleEnd
}
```

### عملیات بیتی (Bitwise operations)

در Kotlin مجموعه‌ای از _عملیات بیتی_ روی اعداد صحیح فراهم می‌کند. این عملیات‌ها در سطح دودویی، مستقیم با بیت‌های نمایش عدد کار می‌کنند.  
عملیات بیتی با توابعی نمایش داده می‌شوند که می‌توان آن‌ها را به‌شکل infix فراخوانی کرد. آن‌ها فقط روی `Int` و `Long` قابل اعمال هستند:

```kotlin
fun main() {
//sampleStart
    val x = 1
    val xShiftedLeft = (x shl 2)
    println(xShiftedLeft)  
    // 4
    
    val xAnd = x and 0x000FF000
    println(xAnd)          
    // 0
//sampleEnd
}
```

فهرست کامل عملیات بیتی:

- `shl(bits)` – شیفت چپ علامت‌دار
- `shr(bits)` – شیفت راست علامت‌دار
- `ushr(bits)` – شیفت راست بدون علامت
- `and(bits)` – **AND** بیتی
- `or(bits)` – **OR** بیتی
- `xor(bits)` – **XOR** بیتی
- `inv()` – وارون‌سازی بیتی

### مقایسه اعداد اعشاری (Floating-point numbers comparison)

عملیات روی اعداد اعشاری که در این بخش بحث می‌شوند عبارت‌اند از:

- بررسی‌های برابری: `a == b` و `a != b`
- عملگرهای مقایسه: `a < b`، `a > b`، `a <= b`، `a >= b`
- ساخت بازه و بررسی بازه: `a..b`، `x in a..b`، `x !in a..b` 

وقتی عملوندهای `a` و `b` به‌صورت ایستا (statically) معلوم باشد که `Float` یا `Double` (یا نسخه‌های nullable آن‌ها) هستند  
(نوع اعلان شده یا استنباط شده است یا نتیجهٔ یک [smart cast](typecasts.md#smart-casts) است)، عملیات روی اعداد و بازه‌ای که می‌سازند  
از [استاندارد IEEE 754 برای محاسبات اعشاری](https://en.wikipedia.org/wiki/IEEE_754) پیروی می‌کند.

اما برای پشتیبانی از موارد استفادهٔ جنریک و فراهم کردن ترتیب‌دهی کلی (total ordering)، رفتار برای عملوندهایی که **به‌صورت ایستا**  
به‌عنوان اعداد اعشاری تایپ نشده‌اند متفاوت است. برای مثال نوع‌های `Any`، `Comparable<...>` یا `Collection<T>`. در این حالت،  
عملیات از پیاده‌سازی‌های `equals` و `compareTo` برای `Float` و `Double` استفاده می‌کند. در نتیجه:

- `NaN` برابر با خودش در نظر گرفته می‌شود
- `NaN` بزرگ‌تر از هر عنصر دیگری از جمله `POSITIVE_INFINITY` در نظر گرفته می‌شود
- `-0.0` کوچک‌تر از `0.0` در نظر گرفته می‌شود

در اینجا مثالی هست که تفاوت رفتار بین عملوندهایی که به‌صورت ایستا عدد اعشاری تایپ شده‌اند  
در (`Double.NaN`) و عملوندهایی که **به‌صورت ایستا** عدد اعشاری تایپ نشده‌اند (`listOf(T)`) را نشان می‌دهد.

```kotlin
fun main() {
    //sampleStart
    // Operand statically typed as floating-point number
    println(Double.NaN == Double.NaN)                 // false
    
    // Operand NOT statically typed as floating-point number
    // So NaN is equal to itself
    println(listOf(Double.NaN) == listOf(Double.NaN)) // true

    // Operand statically typed as floating-point number
    println(0.0 == -0.0)                              // true
    
    // Operand NOT statically typed as floating-point number
    // So -0.0 is less than 0.0
    println(listOf(0.0) == listOf(-0.0))              // false

    println(listOf(Double.NaN, Double.POSITIVE_INFINITY, 0.0, -0.0).sorted())
    // [-0.0, 0.0, Infinity, NaN]
    //sampleEnd
}
```


