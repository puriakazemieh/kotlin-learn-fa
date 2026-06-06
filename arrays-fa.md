[//]: # (title: Arrays)

## آرایه‌ها (Arrays)

یک آرایه، یک ساختار داده است که تعداد ثابتی از مقادیر با یک نوع مشخص (یا زیرنوع‌های آن) را در خود نگه‌داری می‌کند.

رایج‌ترین نوع آرایه در کاتلین، آرایه از نوع شیء (Object-type array) است که با کلاس `Array` نمایش داده می‌شود.

> **نکته:** اگر از نوع‌های اولیه (Primitives) در یک آرایه از نوع شیء استفاده کنید، این کار به دلیل تبدیل نوع‌های اولیه به اشیاء (Boxing)، بر روی کارایی (Performance) برنامه تأثیر منفی می‌گذارد. برای جلوگیری از این هزینه بار اضافی (Boxing overhead)، به جای آن از آرایه‌های نوع اولیه (Primitive-type arrays) استفاده کنید.

### چه زمانی از آرایه‌ها استفاده کنیم؟

زمانی در کاتلین از آرایه‌ها استفاده کنید که نیازمندی‌های خاص و سطح پایینی (Low-level) برای برآورده کردن داشته باشید. به عنوان مثال، اگر نیازمند کارایی بسیار بالایی فراتر از نیاز برنامه‌های معمولی هستید، یا می‌خواهید ساختارهای داده سفارشی بسازید. در غیر این صورت، از مجموعه‌ها (Collections) استفاده کنید.

مجموعه‌ها در مقایسه با آرایه‌ها مزایای زیر را دارند:

- مجموعه‌ها می‌توانند فقط‌خواندنی (Read-only) باشند، که کنترل بیشتری به شما می‌دهد و اجازه می‌دهد کدهایی پایدار با هدفی واضح بنویسید.
- افزودن یا حذف عناصر از مجموعه‌ها آسان است. در مقایسه، آرایه‌ها اندازه ثابتی دارند. تنها راه برای افزودن یا حذف یک عنصر از آرایه این است که هر بار یک آرایه جدید ایجاد کنید که این کار بسیار ناکارآمد است:


  ```kotlin
fun main() {
//sampleStart
    var riversArray = arrayOf("Nile", "Amazon", "Yangtze")

    // با استفاده از عملگر تخصیص =+ یک آرایه جدید ایجاد می‌شود،
    // عناصر اصلی کپی شده و مقدار "Mississippi" به آن اضافه می‌گردد.
    riversArray += "Mississippi"
    println(riversArray.joinToString())
    // Nile, Amazon, Yangtze, Mississippi
//sampleEnd
}
  ```


- شما می‌توانید از عملگر مساوی (`==`) برای بررسی برابری ساختاری (Structural equality) مجموعه‌ها استفاده کنید. اما نمی‌توانید از این عملگر برای آرایه‌ها استفاده کنید. در عوض، باید از یک تابع خاص استفاده کنید که در بخش «مقایسه آرایه‌ها» درباره آن بیشتر می‌خوانید.

برای اطلاعات بیشتر درباره مجموعه‌ها، بخش Collections overview را ببینید.

### ساخت آرایه‌ها (Create arrays)

برای ساخت آرایه‌ها در کاتلین، می‌توانید از روش‌های زیر استفاده کنید:

- توابعی مانند `arrayOf()`، `arrayOfNulls()` یا `emptyArray()`.
- سازنده کلاس `Array` (همان Array constructor).

در مثال زیر از تابع `arrayOf()` استفاده شده و مقادیر عناصر به آن پاس داده شده است:

```kotlin
fun main() {
//sampleStart
    // Creates an array with values [1, 2, 3]
    val simpleArray = arrayOf(1, 2, 3)
    println(simpleArray.joinToString())
    // 1, 2, 3
//sampleEnd
}
```

در مثال زیر از تابع `arrayOfNulls()` برای ایجاد آرایه‌ای با اندازه مشخص که با عناصر `null` پر شده، استفاده شده است:

```kotlin
fun main() {
//sampleStart
    // Creates an array with values [null, null, null]
    val nullArray: Array<Int?> = arrayOfNulls(3)
    println(nullArray.joinToString())
    // null, null, null
//sampleEnd
}
```

در مثال زیر از تابع `emptyArray()` برای ایجاد یک آرایه خالی استفاده شده است:

```kotlin
    var exampleArray = emptyArray<String>()
```

به دلیل ویژگی استنتاج نوع (Type inference) در کاتلین، می‌توانید نوع آرایه خالی را در سمت چپ یا سمت راست انتساب مشخص کنید:

```kotlin
var exampleArray = emptyArray<String>()

var exampleArray: Array<String> = emptyArray()
```

سازنده `Array` اندازه آرایه و تابعی را دریافت می‌کند که این تابع با توجه به ایندکس هر عنصر، مقدار آن عنصر را برمی‌گرداند:

```kotlin
fun main() {
//sampleStart
    // یک Array<Int> ایجاد می‌کند که با صفرهای [0, 0, 0] مقداردهی اولیه شده است
    val initArray = Array<Int>(3) { 0 }
    println(initArray.joinToString())
    // 0, 0, 0

    // ایجاد می‌کند ["0", "1", "4", "9", "16"] با مقادیر Array<String> یک
    val asc = Array(5) { i -> (i * i).toString() }
    asc.forEach { print(it) }
    // 014916
//sampleEnd
}
```


> **نکته:** مانند بیشتر زبان‌های برنامه‌نویسی، ایندکس‌ها در کاتلین نیز از 0 شروع می‌شوند.
#### آرایه‌های تودرتو (Nested arrays)

آرایه‌ها می‌توانند درون یکدیگر قرار بگیرند تا آرایه‌های چندبعدی ایجاد شوند:

```kotlin
fun main() {
//sampleStart
    // Creates a two-dimensional array
    val twoDArray = Array(2) { Array<Int>(2) { 0 } }
    println(twoDArray.contentDeepToString())
    // [[0, 0], [0, 0]]

    // Creates a three-dimensional array
    val threeDArray = Array(3) { Array(3) { Array<Int>(3) { 0 } } }
    println(threeDArray.contentDeepToString())
    // [[[0, 0, 0], [0, 0, 0], [0, 0, 0]], [[0, 0, 0], [0, 0, 0], [0, 0, 0]], [[0, 0, 0], [0, 0, 0], [0, 0, 0]]]
//sampleEnd
}
```

> **نکته:** آرایه‌های تودرتو نیازی ندارند که حتماً از یک نوع یا هم‌اندازه باشند.

### دسترسی و اصلاح عناصر (Access and modify elements)

آرایه‌ها همیشه تغییرپذیر (Mutable) هستند. برای دسترسی و اصلاح عناصر یک آرایه، از عملگر دسترسی ایندکس‌شده `[]` استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val simpleArray = arrayOf(1, 2, 3)
    val twoDArray = Array(2) { Array<Int>(2) { 0 } }

    // Accesses the element and modifies it
    simpleArray[0] = 10
    twoDArray[0][0] = 2

    // Prints the modified element
    println(simpleArray[0].toString()) // 10
    println(twoDArray[0][0].toString()) // 2
//sampleEnd
}
```

آرایه‌ها در کاتلین ناوردا (Invariant) هستند. این بدان معناست که کاتلین به شما اجازه نمی‌دهد یک `Array<String>` را به یک `Array<Any>` نسبت دهید تا از خطای احتمالی در زمان اجرا (Runtime failure) جلوگیری کند. به جای آن، می‌توانید از `Array<out Any>` استفاده کنید. برای اطلاعات بیشتر، بخش Type Projections را ببینید.

### کار با آرایه‌ها (Work with arrays)

در کاتلین، می‌توانید با آرایه‌ها کار کنید؛ به این صورت که آن‌ها را برای پاس دادن تعداد متغیری از آرگومان‌ها به یک تابع بفرستید یا عملیاتی را روی خود آرایه‌ها انجام دهید؛ مانند مقایسه آرایه‌ها، تغییر دادن محتوای آن‌ها یا تبدیل آن‌ها به مجموعه‌ها.

#### پاس دادن تعداد متغیر آرگومان‌ها به یک تابع

در کاتلین، می‌توانید تعداد متغیری از آرگومان‌ها را از طریق پارامتر `vararg` به یک تابع پاس دهید. این ویژگی زمانی مفید است که تعداد آرگومان‌ها را از قبل نمی‌دانید، مانند زمان قالب‌بندی یک پیام یا ایجاد یک کوئری SQL.

برای پاس دادن آرایه‌ای حاوی تعداد متغیری از آرگومان‌ها به یک تابع، از **عملگر پخش‌کننده (Spread operator)** یعنی `*` استفاده کنید. عملگر پخش‌کننده هر عنصر از آرایه را به عنوان آرگومان‌های مجزا به تابع مورد نظر شما پاس می‌دهد:

```kotlin
fun main() {
    val lettersArray = arrayOf("c", "d")
    printAllStrings("a", "b", *lettersArray)
    // abcd
}

fun printAllStrings(vararg strings: String) {
    for (string in strings) {
        print(string)
    }
}
```


برای اطلاعات بیشتر، بخش (Variable number of arguments (varargs را ببینید.

#### مقایسه آرایه‌ها (Compare arrays)

برای مقایسه اینکه آیا دو آرایه دارای عناصر یکسان و با ترتیب یکسانی هستند، از توابع `.contentEquals()` و `.contentDeepEquals()` استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val simpleArray = arrayOf(1, 2, 3)
    val anotherArray = arrayOf(1, 2, 3)

    // Compares contents of arrays
    println(simpleArray.contentEquals(anotherArray))
    // true

    // Using infix notation, compares contents of arrays after an element 
    // is changed
    simpleArray[0] = 10
    println(simpleArray contentEquals anotherArray)
    // false
//sampleEnd
}
```

> **هشدار:** از عملگرهای مساوی (`==`) و نامساوی (`!=`) برای مقایسه محتوای آرایه‌ها استفاده نکنید. این عملگرها بررسی می‌کنند که آیا متغیرهای تخصیص‌داده‌شده به یک شیء واحد اشاره می‌کنند یا خیر (بررسی برابری مرجع). برای کسب اطلاعات بیشتر درباره اینکه چرا آرایه‌ها در کاتلین اینگونه رفتار می‌کنند، پست وبلاگ ما را بخوانید.

#### تبدیل و تحول آرایه‌ها (Transform arrays)

کاتلین توابع مفید بسیاری برای تبدیل آرایه‌ها دارد. این سند به چند مورد اشاره می‌کند اما این یک لیست کامل نیست. برای مشاهده لیست کامل توابع، مرجع API ما را ببینید.

##### مجموع (Sum)

برای بازگرداندن مجموع تمام عناصر یک آرایه، از تابع `.sum()` استفاده کنید:

```Kotlin
fun main() {
//sampleStart
    val sumArray = arrayOf(1, 2, 3)

    // Sums array elements
    println(sumArray.sum())
    // 6
//sampleEnd
}
```

> **نکته:** تابع `.sum()` فقط برای آرایه‌هایی با انواع داده‌های عددی مانند `Int` قابل استفاده است.

##### برهم‌زدن ترتیب / شافل (Shuffle)

برای برهم‌زدن تصادفی ترتیب عناصر در یک آرایه، از تابع `.shuffle()` استفاده کنید:

```Kotlin
fun main() {
//sampleStart
    val simpleArray = arrayOf(1, 2, 3)

    // Shuffles elements [3, 2, 1]
    simpleArray.shuffle()
    println(simpleArray.joinToString())

    // Shuffles elements again [2, 3, 1]
    simpleArray.shuffle()
    println(simpleArray.joinToString())
//sampleEnd
}
```

#### تبدیل آرایه‌ها به مجموعه‌ها (Convert arrays to collections)

اگر با APIهای مختلفی کار می‌کنید که برخی از آن‌ها از آرایه‌ها و برخی از مجموعه‌ها استفاده می‌کنند، می‌توانید آرایه‌های خود را به مجموعه‌ها و بالعکس تبدیل کنید.

##### تبدیل به List یا Set

برای تبدیل یک آرایه به یک `List` یا `Set`، از توابع `.toList()` و `.toSet()` استفاده کنید.

```kotlin
fun main() {
//sampleStart
    val simpleArray = arrayOf("a", "b", "c", "c")

    // Converts to a Set
    println(simpleArray.toSet())
    // [a, b, c]

    // Converts to a List
    println(simpleArray.toList())
    // [a, b, c, c]
//sampleEnd
}
```

##### تبدیل به Map

برای تبدیل یک آرایه به یک `Map`، از تابع `.toMap()` استفاده کنید.

تنها آرایه‌ای از نوع `Pair<K,V>` می‌تواند به یک `Map` تبدیل شود. مقدار اول از یک نمونه `Pair` تبدیل به کلید (Key) و مقدار دوم تبدیل به مقدار (Value) می‌شود. این مثال از نشانه‌گذاری اینفیکس برای فراخوانی تابع `to` جهت ایجاد تاپل‌های `Pair` استفاده می‌کند:

```kotlin
fun main() {
//sampleStart
    val pairArray = arrayOf("apple" to 120, "banana" to 150, "cherry" to 90, "apple" to 140)

    // Map تبدیل به یک
    // کلیدها میوه‌ها هستند و مقادیر تعداد کالری آن‌ها است
    // توجه داشته باشید که کلیدها باید منحصربه‌فرد باشند، بنابراین آخرین مقدار "apple"
    // جایگزین مقدار اول می‌شود
    println(pairArray.toMap())
    // {apple=140, banana=150, cherry=90}

//sampleEnd
}
```

### آرایه‌های نوع اولیه (Primitive-type arrays)

اگر از کلاس `Array` همراه با مقادیر اولیه استفاده کنید، این مقادیر درون اشیاء باکس (Box) می‌شوند. به عنوان یک جایگزین، می‌توانید از آرایه‌های نوع اولیه استفاده کنید که به شما امکان می‌دهند نوع‌های اولیه را بدون عوارض جانبی هزینه بار اضافی باکسینگ (Boxing overhead) در آرایه ذخیره کنید:

| Primitive-type array | Equivalent in Java |
|---|----------------|
| [`BooleanArray`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean-array/) | `boolean[]`|
| [`ByteArray`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-byte-array/) | `byte[]`|
| [`CharArray`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-char-array/) | `char[]`|
| [`DoubleArray`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-double-array/) | `double[]`|
| [`FloatArray`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-float-array/) | `float[]`|
| [`IntArray`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-int-array/) | `int[]`|
| [`LongArray`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-long-array/) | `long[]`|
| [`ShortArray`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-short-array/) | `short[]`|

این کلاس‌ها هیچ رابطه ارث‌بری با کلاس `Array` ندارند، اما مجموعه توابع و ویژگی‌های یکسانی دارند.

مثال زیر نمونه‌ای از کلاس `IntArray` ایجاد می‌کند:

```kotlin
fun main() {
//sampleStart
    // Creates an array of Int of size 5 with the values initialized to zero
    val exampleArray = IntArray(5)
    println(exampleArray.joinToString())
    // 0, 0, 0, 0, 0
//sampleEnd
}
```

> **نکته:** برای تبدیل آرایه‌های نوع اولیه به آرایه‌های نوع شیء، از تابع `.toTypedArray()` استفاده کنید. برای تبدیل آرایه‌های نوع شیء به آرایه‌های نوع اولیه، از توابع `.toBooleanArray()`، `.toByteArray()`، `.toCharArray()` و غیره استفاده کنید.

### قدم بعدی چیست؟

- برای اینکه بیشتر بدانید چرا توصیه می‌کنیم برای اکثر موارد از مجموعه‌ها استفاده کنید، بخش Collections overview را بخوانید.
- درباره سایر انواع پایه (Basic types) یاد بگیرید.
- اگر توسعه‌دهنده جاوا هستید، راهنمای مهاجرت از جاوا به کاتلین برای مجموعه‌ها (Java to Kotlin migration guide for Collections) را مطالعه کنید.
