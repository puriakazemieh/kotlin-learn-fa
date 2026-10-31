---
cssclasses:
  - persian-rtl
---

# مجموعه‌ها

در برنامه‌نویسی، گروه‌بندی داده‌ها در ساختارهایی برای پردازش بعدی سودمند است. Kotlin دقیقاً برای این منظور مجموعه‌ها را فراهم می‌کند.

Kotlin برای گروه‌بندی آیتم‌ها مجموعه‌های زیر را دارد:

| **نوع مجموعه** | **توضیح** |
|---|---|
| فهرست‌ها (`List`) | مجموعه‌های مرتب از آیتم‌ها |
| مجموعه‌ها (`Set`) | مجموعه‌های نامرتب از آیتم‌های یکتا |
| نگاشت‌ها (`Map`) | مجموعه‌ای از زوج‌های کلید-مقدار که کلیدهای آن یکتا هستند و هر کلید فقط به یک مقدار نگاشت می‌شود |

هر نوع مجموعه می‌تواند تغییرپذیر یا فقط‌خواندنی باشد.

## فهرست

فهرست‌ها آیتم‌ها را به ترتیب افزوده‌شدن نگه می‌دارند و می‌توانند آیتم تکراری داشته باشند.

برای ساخت فهرست فقط‌خواندنی ([`List`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/))، از تابع [`listOf()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/list-of.html) استفاده کنید.

برای ساخت فهرست تغییرپذیر ([`MutableList`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list/))، از تابع [`mutableListOf()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/mutable-list-of.html) استفاده کنید.

هنگام ساخت فهرست، Kotlin می‌تواند نوع آیتم‌های ذخیره‌شده را استنتاج کند. برای اعلان صریح نوع، آن را پس از اعلان فهرست و میان کروشه‌های زاویه‌دار `<>` بنویسید:

```kotlin
fun main() {
//sampleStart
    // Read only list
    val readOnlyShapes = listOf("triangle", "square", "circle")
    println(readOnlyShapes)
    // [triangle, square, circle]

    // Mutable list with explicit type declaration
    val shapes: MutableList<String> = mutableListOf("triangle", "square", "circle")
    println(shapes)
    // [triangle, square, circle]
//sampleEnd
}
```

> [!tip]
> برای جلوگیری از تغییرهای ناخواسته، می‌توانید با انتساب یک فهرست تغییرپذیر به یک `List`، نمایی فقط‌خواندنی از آن بسازید:
>
> ```kotlin
> val shapes: MutableList<String> = mutableListOf("triangle", "square", "circle")
> val shapesLocked: List<String> = shapes
> ```
>
> به این کار **تبدیل نوع (casting)** نیز می‌گویند.

فهرست‌ها مرتب‌اند؛ پس برای دسترسی به یک آیتم از فهرست، از عملگر [دسترسی اندیسی](../operator-overloading.md#indexed-access-operator) `[]` استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val readOnlyShapes = listOf("triangle", "square", "circle")
    println("The first item in the list is: ${readOnlyShapes[0]}")
    // The first item in the list is: triangle
//sampleEnd
}
```

برای گرفتن نخستین یا آخرین آیتم یک فهرست، به‌ترتیب از تابع‌های [`.first()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/first.html) و [`.last()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/last.html) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val readOnlyShapes = listOf("triangle", "square", "circle")
    println("The first item in the list is: ${readOnlyShapes.first()}")
    // The first item in the list is: triangle
//sampleEnd
}
```

> [!note]
> تابع‌های [`.first()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/first.html) و [`.last()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/last.html) نمونه‌هایی از **تابع‌های افزونه (extension functions)** هستند. برای فراخوانی یک تابع افزونه روی شیء، نام تابع را پس از شیء و با یک نقطه `.` بنویسید.
>
> تابع‌های افزونه در [تور سطح متوسط](kotlin-tour-intermediate-extension-functions.md#extension-functions) با جزئیات بررسی می‌شوند. در این مرحله فقط کافی است بدانید چطور آن‌ها را فراخوانی کنید.

برای گرفتن تعداد آیتم‌های یک فهرست، از تابع [`.count()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/count.html) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val readOnlyShapes = listOf("triangle", "square", "circle")
    println("This list has ${readOnlyShapes.count()} items")
    // This list has 3 items
//sampleEnd
}
```

برای بررسی اینکه یک آیتم در فهرست وجود دارد، از [عملگر `in`](../operator-overloading.md#in-operator) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val readOnlyShapes = listOf("triangle", "square", "circle")
    println("circle" in readOnlyShapes)
    // true
//sampleEnd
}
```

برای افزودن یا حذف آیتم‌ها از فهرست تغییرپذیر، به‌ترتیب از تابع‌های [`.add()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list/add.html) و [`.remove()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/remove.html) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val shapes: MutableList<String> = mutableListOf("triangle", "square", "circle")
    // Add "pentagon" to the list
    shapes.add("pentagon")
    println(shapes)
    // [triangle, square, circle, pentagon]

    // Remove the first "pentagon" from the list
    shapes.remove("pentagon")
    println(shapes)
    // [triangle, square, circle]
//sampleEnd
}
```

## مجموعه

برخلاف فهرست‌ها که مرتب‌اند و آیتم تکراری را می‌پذیرند، مجموعه‌ها (**`Set`**) **نامرتب** هستند و فقط آیتم‌های **یکتا** را ذخیره می‌کنند.

برای ساخت مجموعهٔ فقط‌خواندنی ([`Set`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-set/))، از تابع [`setOf()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/set-of.html) استفاده کنید.

برای ساخت مجموعهٔ تغییرپذیر ([`MutableSet`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-set/))، از تابع [`mutableSetOf()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/mutable-set-of.html) استفاده کنید.

هنگام ساخت مجموعه، Kotlin می‌تواند نوع آیتم‌های ذخیره‌شده را استنتاج کند. برای اعلان صریح نوع، آن را پس از اعلان مجموعه و میان کروشه‌های زاویه‌دار `<>` بنویسید:

```kotlin
fun main() {
//sampleStart
    // Read-only set
    val readOnlyFruit = setOf("apple", "banana", "cherry", "cherry")
    // Mutable set with explicit type declaration
    val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry")

    println(readOnlyFruit)
    // [apple, banana, cherry]
//sampleEnd
}
```

همان‌طور که در مثال پیشین می‌بینید، چون مجموعه‌ها فقط عنصرهای یکتا دارند، آیتم تکراریِ `"cherry"` حذف می‌شود.

> [!tip]
> برای جلوگیری از تغییرهای ناخواسته، می‌توانید با انتساب یک مجموعهٔ تغییرپذیر به یک `Set`، نمایی فقط‌خواندنی از آن بسازید:
>
> ```kotlin
> val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry")
> val fruitLocked: Set<String> = fruit
> ```

> [!note]
> چون مجموعه‌ها **نامرتب** هستند، نمی‌توانید به آیتمی در یک اندیس مشخص دسترسی پیدا کنید.

برای گرفتن تعداد آیتم‌های یک مجموعه، از تابع [`.count()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/count.html) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val readOnlyFruit = setOf("apple", "banana", "cherry", "cherry")
    println("This set has ${readOnlyFruit.count()} items")
    // This set has 3 items
//sampleEnd
}
```

برای بررسی اینکه یک آیتم در مجموعه وجود دارد، از [عملگر `in`](../operator-overloading.md#in-operator) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val readOnlyFruit = setOf("apple", "banana", "cherry", "cherry")
    println("banana" in readOnlyFruit)
    // true
//sampleEnd
}
```

برای افزودن یا حذف آیتم‌ها از مجموعهٔ تغییرپذیر، به‌ترتیب از تابع‌های [`.add()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-set/add.html) و [`.remove()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/remove.html) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry")
    fruit.add("dragonfruit")    // Add "dragonfruit" to the set
    println(fruit)              // [apple, banana, cherry, dragonfruit]

    fruit.remove("dragonfruit") // Remove "dragonfruit" from the set
    println(fruit)              // [apple, banana, cherry]
//sampleEnd
}
```

## نگاشت

نگاشت‌ها (`Map`) آیتم‌ها را به‌صورت زوج کلید-مقدار نگه می‌دارند. با ارجاع به کلید، به مقدار دسترسی پیدا می‌کنید. می‌توانید یک نگاشت را مانند منوی غذا تصور کنید: با یافتن غذای دلخواه (کلید)، قیمت آن (مقدار) را پیدا می‌کنید. نگاشت‌ها زمانی مفیدند که بخواهید بدون استفاده از اندیسی شماره‌دار، مانند فهرست، یک مقدار را پیدا کنید.

> [!note]
> - هر کلید در یک نگاشت باید یکتا باشد تا Kotlin بداند کدام مقدار را می‌خواهید بگیرید.
> - مقدارهای تکراری در یک نگاشت مجاز هستند.

برای ساخت نگاشت فقط‌خواندنی ([`Map`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/))، از تابع [`mapOf()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/map-of.html) استفاده کنید.

برای ساخت نگاشت تغییرپذیر ([`MutableMap`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-map/))، از تابع [`mutableMapOf()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/mutable-map-of.html) استفاده کنید.

هنگام ساخت نگاشت، Kotlin می‌تواند نوع آیتم‌های ذخیره‌شده را استنتاج کند. برای اعلان صریح نوع، نوع کلیدها و مقدارها را پس از اعلان نگاشت و میان کروشه‌های زاویه‌دار `<>` بنویسید؛ برای مثال `MutableMap<String, Int>`. کلیدها در این مثال `String` و مقدارها `Int` هستند.

ساده‌ترین روش ساخت نگاشت استفاده از [`to`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/to.html) میان هر کلید و مقدار مربوط به آن است:

```kotlin
fun main() {
//sampleStart
    // Read-only map
    val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
    println(readOnlyJuiceMenu)
    // {apple=100, kiwi=190, orange=100}

    // Mutable map with explicit type declaration
    val juiceMenu: MutableMap<String, Int> = mutableMapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
    println(juiceMenu)
    // {apple=100, kiwi=190, orange=100}
//sampleEnd
}
```

> [!tip]
> برای جلوگیری از تغییرهای ناخواسته، می‌توانید با انتساب یک نگاشت تغییرپذیر به یک `Map`، نمایی فقط‌خواندنی از آن بسازید:
>
> ```kotlin
> val juiceMenu: MutableMap<String, Int> = mutableMapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
> val juiceMenuLocked: Map<String, Int> = juiceMenu
> ```

برای دسترسی به یک مقدار در نگاشت، از عملگر [دسترسی اندیسی](../operator-overloading.md#indexed-access-operator) `[]` و کلید آن استفاده کنید:

```kotlin
fun main() {
//sampleStart
    // Read-only map
    val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
    println("The value of apple juice is: ${readOnlyJuiceMenu["apple"]}")
    // The value of apple juice is: 100
//sampleEnd
}
```

> [!note]
> اگر با کلیدی که در نگاشت وجود ندارد به زوج کلید-مقدار دسترسی پیدا کنید، مقدار `null` می‌بینید:
>
> ```kotlin
> fun main() {
> //sampleStart
>     // Read-only map
>     val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
>     println("The value of pineapple juice is: ${readOnlyJuiceMenu["pineapple"]}")
>     // The value of pineapple juice is: null
> //sampleEnd
> }
> ```
>
> این تور مقدارهای null را بعدتر در فصل [ایمنی null](kotlin-tour-null-safety.md) توضیح می‌دهد.

همچنین می‌توانید از عملگر [دسترسی اندیسی](../operator-overloading.md#indexed-access-operator) `[]` برای افزودن آیتم به نگاشت تغییرپذیر استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val juiceMenu: MutableMap<String, Int> = mutableMapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
    juiceMenu["coconut"] = 150 // Add key "coconut" with value 150 to the map
    println(juiceMenu)
    // {apple=100, kiwi=190, orange=100, coconut=150}
//sampleEnd
}
```

برای حذف آیتم‌ها از نگاشت تغییرپذیر، از تابع [`.remove()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/remove.html) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val juiceMenu: MutableMap<String, Int> = mutableMapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
    juiceMenu.remove("orange")    // Remove key "orange" from the map
    println(juiceMenu)
    // {apple=100, kiwi=190}
//sampleEnd
}
```

برای گرفتن تعداد آیتم‌ها در یک نگاشت، از تابع [`.count()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/count.html) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    // Read-only map
    val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
    println("This map has ${readOnlyJuiceMenu.count()} key-value pairs")
    // This map has 3 key-value pairs
//sampleEnd
}
```

برای بررسی اینکه کلیدی مشخص از قبل در نگاشت وجود دارد، از تابع [`.containsKey()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/contains-key.html) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
    println(readOnlyJuiceMenu.containsKey("kiwi"))
    // true
//sampleEnd
}
```

برای به‌دست‌آوردن مجموعهٔ کلیدها یا مقدارهای نگاشت، به‌ترتیب از ویژگی‌های [`keys`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/keys.html) و [`values`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/values.html) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
    println(readOnlyJuiceMenu.keys)
    // [apple, kiwi, orange]
    println(readOnlyJuiceMenu.values)
    // [100, 190, 100]
//sampleEnd
}
```

> [!note]
> [`keys`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/keys.html) و [`values`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/values.html) نمونه‌هایی از **ویژگی‌ها (properties)**ی یک شیء هستند. برای دسترسی به ویژگی یک شیء، نام ویژگی را پس از شیء و با یک نقطه `.` بنویسید.
>
> ویژگی‌ها در فصل [کلاس‌ها](kotlin-tour-classes.md) با جزئیات بیشتری بررسی می‌شوند. در این مرحله فقط کافی است بدانید چطور به آن‌ها دسترسی پیدا کنید.

برای بررسی اینکه یک کلید یا مقدار در نگاشت وجود دارد، از [عملگر `in`](../operator-overloading.md#in-operator) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
    println("orange" in readOnlyJuiceMenu.keys)
    // true

    // Alternatively, you don't need to use the keys property
    println("orange" in readOnlyJuiceMenu)
    // true

    println(200 in readOnlyJuiceMenu.values)
    // false
//sampleEnd
}
```

برای اطلاعات بیشتر دربارهٔ کارهایی که می‌توانید با مجموعه‌ها انجام دهید، [مرور مجموعه‌ها](../collections-overview.md) را ببینید.

اکنون که با نوع‌های پایه و مدیریت مجموعه‌ها آشنا شده‌اید، زمان بررسی [کنترل جریان](kotlin-tour-control-flow.md) در برنامه‌هایتان است.

## تمرین

### شمارش تعداد کل آیتم‌ها در دو فهرست

یک فهرست از عددهای «سبز» و یک فهرست از عددهای «قرمز» دارید. کد را کامل کنید تا تعداد کل عددها را چاپ کند.

```kotlin
fun main() {
    val greenNumbers = listOf(1, 4, 23)
    val redNumbers = listOf(17, 2)
    // Write your code here
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> fun main() {
>     val greenNumbers = listOf(1, 4, 23)
>     val redNumbers = listOf(17, 2)
>     val totalCount = greenNumbers.count() + redNumbers.count()
>     println(totalCount)
> }
> ```

### بررسی پشتیبانی از پروتکل درخواستی

سرور شما مجموعه‌ای از پروتکل‌های پشتیبانی‌شده دارد و کاربر درخواست استفاده از پروتکلی مشخص را می‌دهد. برنامه را کامل کنید تا بررسی کند پروتکل درخواستی پشتیبانی می‌شود یا نه؛ `isSupported` باید یک مقدار Boolean باشد.

```kotlin
fun main() {
    val SUPPORTED = setOf("HTTP", "HTTPS", "FTP")
    val requested = "smtp"
    val isSupported = // Write your code here
    println("Support for $requested: $isSupported")
}
```

> [!tip]- راهنمایی
> مطمئن شوید پروتکل درخواستی را با حروف بزرگ بررسی می‌کنید. تابع [`.uppercase()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/uppercase.html) به شما کمک می‌کند.

> [!example]- راه‌حل نمونه
> ```kotlin
> fun main() {
>     val SUPPORTED = setOf("HTTP", "HTTPS", "FTP")
>     val requested = "smtp"
>     val isSupported = requested.uppercase() in SUPPORTED
>     println("Support for $requested: $isSupported")
> }
> ```

### نوشتن یک عدد با نگاشت

نگاشتی تعریف کنید که عددهای صحیح ۱ تا ۳ را به شکل نوشتاری متناظر آن‌ها مرتبط کند. با این نگاشت، عدد داده‌شده را به شکل نوشتاری چاپ کنید.

```kotlin
fun main() {
    val number2word = // Write your code here
    val n = 2
    println("$n is spelled as '${<Write your code here >}'")
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> fun main() {
>     val number2word = mapOf(1 to "one", 2 to "two", 3 to "three")
>     val n = 2
>     println("$n is spelled as '${number2word[n]}'")
> }
> ```

[گام پیشین](kotlin-tour-basic-types-fa.md) · [گام بعدی](kotlin-tour-control-flow.md)
