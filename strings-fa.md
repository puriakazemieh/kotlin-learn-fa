---
tags:
  - fa
cssclasses:
  - persian-rtl
---

# رشته‌ها

نوع [`String`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-string/) دنباله‌ای از [نویسه‌ها](characters-fa.md) را نمایش می‌دهد. می‌توانید از آن برای مقدارهای متنی، مانند واژه‌ها، جمله‌ها، پیام‌ها یا متن ساخت‌یافته استفاده کنید.

نوع `String` تغییرناپذیر است. پس از ساخت یک شیء `String`، محتوای آن تا پایان عمرش یکسان می‌ماند. هر عملیاتی که ظاهراً رشته را تغییر می‌دهد، در واقع رشتهٔ جدیدی می‌سازد.

## اعلان رشته‌ها

برای اعلان یک لیترال `String`، مقدار را درون علامت نقل‌قول دوتایی (`""`) قرار دهید. می‌توانید نوع `String` را صراحتاً مشخص کنید یا بگذارید Kotlin آن را از مقدار استنتاج کند:

```kotlin
val name: String = "Kotlin"
val message = "Hello, world!" // Kotlin infers String
```

لیترال‌های رشته‌ای با نقل‌قول دوتایی، [دنباله‌های گریز](characters-fa.md) مانند `\n` و `\t` را پشتیبانی می‌کنند:

```kotlin
val message = "Hello,\nworld!"
val quote = "Kotlin says, \"Hi\"."
```

### رشته‌های چندخطی

برای ذخیرهٔ متنی که از چند خط تشکیل شده است یا علامت‌های نقل‌قولی دارد که نمی‌خواهید از آن‌ها گریز دهید، از رشتهٔ چندخطی محصور در سه علامت نقل‌قول (`""" """`) استفاده کنید:

```kotlin
val text = """
Hello,
Kotlin
"""

val quote = """Kotlin says, "Hi"."""
```

> [!note]
> رشته‌های چندخطی از دنباله‌های گریز پشتیبانی نمی‌کنند. Kotlin این نویسه‌ها را متن معمولی در نظر می‌گیرد.

رشته‌های چندخطی، شکست خط‌ها و تورفتگی‌ها را همان‌گونه که در کد منبع نوشته‌اید حفظ می‌کنند. این رفتار زمانی مفید است که می‌خواهید مقدار زمان اجرا با چیدمان متن در فایل شما یکسان باشد.

در مثال زیر، فاصله‌های پیش از هر خط بخشی از رشتهٔ حاصل هستند:

```kotlin
val text = """
    Hello,
    Kotlin
"""
```

برای حذف تورفتگی مشترک آغازین، از تابع [`trimIndent()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/trim-indent.html) استفاده کنید. این تابع کمترین تورفتگی مشترکِ خط‌های غیرخالی را تشخیص می‌دهد و حذف می‌کند:

```kotlin
fun main() {
//sampleStart
    val text = """
        Hello,
        Kotlin
    """.trimIndent()

    println(text)
//sampleEnd
}
```

برای کنترل صریح‌تر حذف تورفتگی، از تابع [`trimMargin()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/trim-margin.html) استفاده کنید. این تابع در هر خط، همه‌چیزِ پیش از پیشوند حاشیه و خودِ آن را حذف می‌کند:

```kotlin
fun main() {
//sampleStart
    val text = """
        |Hello,
        |Kotlin
    """.trimMargin()

    println(text)
//sampleEnd
}
```

تابع `trimMargin()` به‌طور پیش‌فرض از نماد پایپ (`|`) به‌عنوان پیشوند حاشیه استفاده می‌کند، اما می‌توانید نویسهٔ دیگری را به‌عنوان پارامتر بدهید؛ برای نمونه: `trimMargin(">")`.

> [!note]
> وقتی رشته‌ای را با تابع‌هایی مانند `trimIndent()` یا `trimMargin()` پردازش می‌کنید، رشتهٔ حاصل، صرف‌نظر از پلتفرم، فقط از جداکنندهٔ خط جدید (`\n`) استفاده می‌کند.

## قالب‌های رشته‌ای

قالب‌های رشته‌ای (string templates) به شما اجازه می‌دهند متغیرها و عبارت‌ها را مستقیماً درون یک لیترال `String` قرار دهید. این فرایند **درون‌یابی (interpolation)** نام دارد. می‌توانید از قالب‌های رشته‌ای در هر دو نوع رشتهٔ معمولی و چندخطی استفاده کنید.

برای وارد کردن یک متغیر به رشته، از نماد `$` استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val name = "Kotlin"
    println("Hello, $name")
    // Hello, Kotlin
//sampleEnd
}
```

برای وارد کردن یک عبارت به رشته، یا قرار دادن متغیر درست در کنار متن دیگر، از `${}` استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val text = "abc"
    println("The length of $text is ${text.length}")
    // The length of abc is 3

    val language = "Kotlin"
    println("${language}Lang")
    // KotlinLang
//sampleEnd
}
```

> [!tip]
> می‌توانید رشته‌ها را با عملگر `+` نیز ترکیب کنید. با این حال، قالب‌های رشته‌ای معمولاً خواناتر و با سبک رایج Kotlin سازگارتر هستند.

عبارت‌های قالب می‌توانند بدون گریز دادن، رشته‌های دارای نقل‌قول دوتایی را نیز دربرداشته باشند:

```kotlin
// Double-quoted string
val test = "${"test".uppercase()}"

// Multiline string
val result = """
Result: ${"OK".lowercase()}
"""
```

### مقدارهای نال‌پذیر در قالب‌های رشته‌ای

اگر عبارت یا متغیر درون‌یابی‌شده به `null` ارزیابی شود، کامپایلر Kotlin متن `null` را در رشتهٔ حاصل قرار می‌دهد. برای جایگزین کردن `null` با مقداری دیگر، از [عملگر Elvis](null-safety.md#elvis-operator) (`?:`) استفاده کنید:

```kotlin
fun main(){
//sampleStart
    val text: String? = null

    println("Hello, $text")
    // Hello, null

    println("Hello, ${text ?: "Kotlin"}")
    // Hello, Kotlin
//sampleEnd
}
```

### درون‌یابی رشته‌ای چنددلاری

در قالب‌های رشته‌ای معمولی، یک علامت دلار (`$`) درون‌یابی را آغاز می‌کند. اگر لازم است علامت‌های دلار تحت‌اللفظی را در رشته قرار دهید، از **درون‌یابی رشته‌ای چنددلاری (multi-dollar string interpolation)** استفاده کنید.

درون‌یابی رشته‌ای چنددلاری به شما اجازه می‌دهد تعیین کنید برای آغاز درون‌یابی، چند علامت دلارِ پیاپی لازم است. تعداد علامت‌های دلار کمتر از آن، نویسه‌های تحت‌اللفظی در نظر گرفته می‌شوند.

برای نمونه، وقتی پیش از لیترال رشته‌ای از `$$` استفاده می‌کنید، درون‌یابی فقط با دو علامت دلارِ پیاپی آغاز می‌شود:

```kotlin
val KClass<*>.jsonSchema : String
    get() = $$"""
    {
      "$schema": "https://json-schema.org/draft/2020-12/schema",
      "$id": "https://example.com/product.schema.json",
      "$dynamicAnchor": "meta",
      "title": "$${simpleName ?: qualifiedName ?: "unknown"}",
      "type": "object"
    }
    """
```

> [!tip]
> اگر از درون‌یابی رشته‌ای تک‌دلاری استفاده می‌کنید، درون‌یابی رشته‌ای چنددلاری بر کد شما اثری نمی‌گذارد. می‌توانید همچنان از یک `$` استفاده کنید و در صورت نیاز علامت‌های چنددلاری را به کار ببرید.

## عملیات پایهٔ رشته

Kotlin مجموعه‌ای از عملیات را برای کار با رشته‌ها فراهم می‌کند. این بخش چند مورد از پرکاربردترین عملیات را معرفی می‌کند.

> [!tip]
> دربارهٔ همهٔ تابع‌های در دسترس در [مرجع API](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-string/) بیشتر بیاموزید.

### دریافت طول رشته

برای به‌دست آوردن شمار نویسه‌های یک رشته، از ویژگی [`length`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-string/length.html) استفاده کنید:

```kotlin
fun main (){
//sampleStart
    val language = "Kotlin"
    println(language.length)
    // 6
//sampleEnd
}
```

### دسترسی به نویسه‌ها

می‌توانید با عملگر اندیس‌گذاری (`[]`) به یک نویسهٔ منفرد در رشته دسترسی پیدا کنید:

```kotlin
fun main (){
//sampleStart
    val language = "Kotlin"

    println(language[0])
    // K
    println(language[5])
    // n
//sampleEnd
}
```

> [!tip]
> اندیس رشته از صفر آغاز می‌شود. اگر بکوشید به اندیسی بیرون از بازهٔ معتبر دسترسی پیدا کنید، Kotlin یک استثنا پرتاب می‌کند.

همچنین می‌توانید روی نویسه‌های یک رشته پیمایش کنید:

```kotlin
fun main(){
//sampleStart
    for (char in "Kotlin") {
      println(char)
    }
//sampleEnd
}
```

### استخراج بخش‌هایی از رشته

برای استخراج بخش‌هایی از یک رشته، از یکی از تابع‌های زیر استفاده کنید:

* [`substring()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/substring.html) برای بازگرداندن رشته‌ای جدید با بخش برگزیده‌شده از متن اصلی.
* [`subSequence()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/sub-sequence.html) برای بازگرداندن یک `CharSequence` با بخش برگزیده‌شده از متن اصلی.

برای نمونه:

```kotlin
fun main() {
//sampleStart
    val text = "Kotlin"
    println(text.substring(1))
    // otlin
    println(text.substring(1, 5))
    // otli
    println(text.subSequence(1, 5))
    // otli
//sampleEnd
}
```

از آنجا که نوع `String` تغییرناپذیر است، این تابع‌ها رشتهٔ اصلی را تغییر نمی‌دهند.

### مقایسهٔ رشته‌ها

می‌توانید با عملگر `==` بررسی کنید که آیا دو رشته محتوای یکسان دارند یا نه:

```kotlin
fun main(){
//sampleStart
    println("kotlin" == "kotlin")
    // true

    println("kotlin" == "Kotlin")
    // false
//sampleEnd
}
```

همچنین می‌توانید با تابع [`compareTo()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-string/compare-to.html)، رشته‌ها را به‌صورت واژه‌نامه‌ای (نویسه‌به‌نویسه) مقایسه کنید. این تابع هر دو رشته را تا یافتن نخستین جفت نویسهٔ متفاوت بررسی می‌کند و بازمی‌گرداند:

* `0` هنگامی که رشته‌ها برابرند.
* مقداری کمتر از `0` هنگامی که گیرنده از آرگومان کوچک‌تر است.
* مقداری بیشتر از `0` هنگامی که گیرنده از آرگومان بزرگ‌تر است.

```kotlin
fun main() {
//sampleStart
    println("abc".compareTo("abd") < 0)
    // true

    println("abc".compareTo("ABC") > 0)
    // true

    // Pass true to ignore case differences
    println("abc".compareTo("ABC", ignoreCase = true) == 0)
    // true
//sampleEnd
}
```

### کار با محتوای رشته

اگر می‌خواهید محتوای یک رشته را تغییر دهید، با تابع‌هایی مانند [`.trim()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/trim.html)، [`.replace()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/replace.html)، [`.uppercase()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/uppercase.html) و [`.lowercase()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/lowercase.html)، نسخه‌ای تغییرکرده از آن بسازید:

```kotlin
fun main() {
//sampleStart
    val text = "  Hello, Kotlin  "

    println(text.trim())
    // Hello, Kotlin

    println(text.replace("Kotlin", "world"))
    //   Hello, world

    println(text.uppercase())
    //   HELLO, KOTLIN

    println(text.lowercase())
    //   hello, kotlin
//sampleEnd
}
```

همچنین می‌توانید محتوای رشته را با تابع‌های [`contains()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/contains.html)، [`startsWith()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/starts-with.html) و [`endsWith()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/ends-with.html) بررسی کنید:

```kotlin
fun main() {
//sampleStart
    val domain = "kotlinlang.org"

    // Checks if the string contains "."
    println(domain.contains("."))
    // true

    // Checks if the string starts with "kotlin"
    println(domain.startsWith("kotlin"))
    // true

    // Checks if the string ends with ".org"
    println(domain.endsWith(".org"))
    // true
//sampleEnd
}
 ```

### جداسازی رشته‌ها

می‌توانید با تابع [`split()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/split.html)، رشته را پیرامون یک جداکننده به بخش‌ها تقسیم کنید:

```kotlin
fun main() {
//sampleStart
    val numbers = "one, two, three"
    println(numbers.split(", "))
    // [one, two, three]
//sampleEnd
}
```

اگر می‌خواهید رشته را به خط‌های منفرد تقسیم کنید، از تابع [`lines()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/lines.html) استفاده کنید:

```kotlin
fun main() {
//sampleStart
    val numbers = "one\ntwo\nthree"
    println(numbers.lines())
    // [one, two, three]
//sampleEnd
}
```

### ساخت و قالب‌بندی رشته‌ها

> [!tip]
> برای بیشتر کارهای قالب‌بندی در Kotlin، از [قالب‌های رشته‌ای](#قالب‌های-رشته‌ای) استفاده کنید.

وقتی رشته‌ها را با عملگر `+` به‌هم می‌چسبانید، Kotlin برای هر عمل یک شیء `String` جدید می‌سازد. با این حال، این رویکرد ممکن است در حلقه‌ها یا هنگام کنار هم گذاشتن قطعه‌های فراوان مناسب نباشد.
برای جلوگیری از چنین مسئله‌هایی، می‌توانید از تابع `buildString()` یا `StringBuilder` استفاده کنید. آن‌ها همهٔ قطعه‌ها را در یک بافر تغییرپذیر گرد می‌آورند و فقط در پایان یک رشته تولید می‌کنند.

هنگامی از تابع [`buildString()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/build-string.html) استفاده کنید که منطق تعیین‌کنندهٔ چیزهای افزوده‌شده پیچیده است؛ برای نمونه، زمانی که چند شرط قطعه‌های متفاوتی را اضافه می‌کنند. با `buildString()` مستقیماً با بافر کار نمی‌کنید. این تابع درونی یک `StringBuilder` می‌سازد، بلوک شما را اجرا می‌کند و رشتهٔ حاصل را برمی‌گرداند.

```kotlin
fun main() {
//sampleStart

    val hasErrors = true
    val hasWarnings = true
    val isComplete = false

    // buildString creates an empty buffer
    val status = buildString {
        // Appends "Errors found" to the buffer
        if (hasErrors) append("Errors found")
        if (hasWarnings) {
            // The buffer is not empty, appends "; "
            if (isNotEmpty()) append("; ")
            // Appends "Warnings found"
            append("Warnings found")
        }
        // isComplete = false, nothing to append
        if (isComplete) {
            if (isNotEmpty()) append("; ")
            append("Completed")
        }
        // The buffer is not empty, skips the fallback
        if (isEmpty()) append("OK")
    }

    println(status)
    // Errors found; Warnings found
//sampleEnd
}
```

هنگامی از [`StringBuilder`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/-string-builder/) استفاده کنید که به بافر به‌عنوان مقداری صریح نیاز دارید؛ برای نمونه، برای تغییر متن موجود:

```kotlin
fun main() {
//sampleStart
    val text = "Hello, Kotlin"
    val builder = StringBuilder(text)

    builder.replace(7, 13, "world")
    println(builder.toString())
    // Hello, world
//sampleEnd
}
```

در JVM، می‌توانید رشته را با تابع [`String.format()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/format.html) نیز قالب‌بندی کنید:

```kotlin
val text = String.format("Hello, %s", "Kotlin")
```

> [!note]
> از تابع `String.format()` فقط هنگامی استفاده کنید که به مشخص‌کننده‌های به سبک formatter در JVM نیاز مشخصی دارید. دربارهٔ مشخص‌کننده‌های قالب در [مستندات Java Class Formatter](https://docs.oracle.com/javase/8/docs/api/java/util/Formatter.html#summary) بیشتر بیاموزید.

## تبدیل رشته

اغلب ممکن است از رشته‌ها برای نمایش مقدارهایی از نوع‌های دیگر، مانند عددها، مقدارهای `Boolean` یا شناسه‌های ورودی استفاده کنید. Kotlin تابع‌هایی برای تبدیل مقدارها به رشته و تجزیهٔ رشته‌ها به نوع‌های دیگر فراهم می‌کند.

برای بازگرداندن نمایش رشته‌ای یک مقدار، از تابع [`toString()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-string/to-string.html) استفاده کنید:

```kotlin
val number = 10
val text = number.toString()
```

Kotlin در قالب‌های رشته‌ای و الحاق رشته، مقدارها را خودکار به رشته تبدیل می‌کند.

برای تبدیل رشته به نوعی دیگر، از تابع‌های تجزیهٔ متناظر استفاده کنید:

* برای مقدارهای صحیح: [`toByte()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/to-byte.html)، [`toShort()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/to-short.html)، [`toInt()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/to-int.html)، [`toLong()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/to-long.html)
* برای مقدارهای ممیز شناور: [`toDouble()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/to-double.html)، [`toFloat()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/to-float.html)
* برای مقدارهای بولی: [`toBoolean()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/to-boolean.html)، [`toBooleanStrict()`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.text/to-boolean-strict.html)

اگر رشته قالب معتبری داشته باشد، این تابع‌ها مقداری از نوع درخواستی را بازمی‌گردانند. اگر ممکن است ورودی نامعتبر باشد، از گونه‌های `OrNull` استفاده کنید. این تابع‌ها به‌جای پرتاب استثنا، `null` برمی‌گردانند؛ بنابراین برای ورودی کاربر یا داده‌ای که کاملاً در کنترل شما نیست، امن هستند:

```kotlin
val toInt = "10".toInt() // 10

// 1000000000000 exceeds maximum value of Int
val toIntInvalid = "1000000000000".toIntOrNull()

val toBoolean = "true".toBooleanStrict() // true
val toBooleanInvalid = "yes".toBooleanStrictOrNull() // null
```
