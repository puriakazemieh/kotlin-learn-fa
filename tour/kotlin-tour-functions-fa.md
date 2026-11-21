---
cssclasses:
  - persian-rtl
---

# توابع (Functions)

در کاتلین می‌توانید با استفاده از کلمهٔ کلیدی `fun` توابع سفارشی خود را اعلان کنید.

```kotlin
fun hello() {
    return println("Hello, world!")
}

fun main() {
    hello()
    // Hello, world!
}
```

در کاتلین:

* پارامترهای تابع درون پرانتز `()` نوشته می‌شوند.
* هر پارامتر باید یک نوع داده (type) داشته باشد و پارامترهای چندگانه باید با کاما `,` از یکدیگر جدا شوند.
* نوع بازگشتی تابع بعد از پرانتزهای تابع `()` و با یک دو نقطه `:` مشخص می‌شود.
* بدنهٔ تابع درون آکولادهای `{}` نوشته می‌شود.
* از کلمهٔ کلیدی `return` برای خروج از تابع یا بازگرداندن مقداری از آن استفاده می‌شود.

> [!note]
> اگر تابعی مقدار معناداری برنمی‌گرداند، می‌توان نوع بازگشتی و کلمهٔ کلیدی `return` را حذف کرد. دربارهٔ این موضوع در بخش [توابع بدون مقدار بازگشتی](#توابع-بدون-مقدار-بازگشتی-functions-without-return) بیشتر بخوانید.

در مثال زیر:

* `x` و `y` پارامترهای تابع هستند.
* `x` و `y` دارای نوع `Int` هستند.
* نوع بازگشتی تابع `Int` است.
* تابع هنگام فراخوانی، مجموع `x` و `y` را برمی‌گرداند.

```kotlin
fun sum(x: Int, y: Int): Int {
    return x + y
}

fun main() {
    println(sum(1, 2))
    // 3
}
```

> [!note]
> در [قراردادهای کدنویسی کاتلین](../coding-conventions-fa.md) توصیه می‌کنیم که نام توابع را با حروف کوچک شروع کرده و از شیوهٔ شترمرغی (camelCase) بدون خط زیرین (underscore) استفاده کنید.

## آرگومان‌های نام‌دار (Named arguments)

برای خلاصه شدن کد، هنگام فراخوانی تابع نیازی به ذکر نام پارامترها ندارید. با این حال، گنجاندن نام پارامترها خوانایی کد شما را افزایش می‌دهد. به این روش استفاده از **آرگومان‌های نام‌دار (named arguments)** گفته می‌شود. اگر نام پارامترها را بنویسید، می‌توانید پارامترها را به هر ترتیبی ارسال کنید.

> [!tip]
> در مثال زیر، از [الگوهای رشته‌ای](../strings-fa.md#الگوهای-رشته‌ای-string-templates) (`$`) برای دسترسی به مقادیر پارامترها، تبدیل آن‌ها به نوع `String` و سپس ادغام آن‌ها در یک رشته برای چاپ استفاده شده است.

```kotlin
fun printMessageWithPrefix(message: String, prefix: String) {
    println("[$prefix] $message")
}

fun main() {
    // استفاده از آرگومان‌های نام‌دار با جابه‌جا کردن ترتیب پارامترها
    printMessageWithPrefix(prefix = "Log", message = "Hello")
    // [Log] Hello
}
```

## مقادیر پیش‌فرض برای پارامترها (Default parameter values)

می‌توانید برای پارامترهای تابع خود مقادیر پیش‌فرض تعریف کنید. هر پارامتری که مقدار پیش‌فرض داشته باشد می‌تواند در زمان فراخوانی تابع نادیده گرفته و حذف شود. برای اعلان مقدار پیش‌فرض، بعد از نوع پارامتر از عملگر انتساب `=` استفاده کنید:

```kotlin
fun printMessageWithPrefix(message: String, prefix: String = "Info") {
    println("[$prefix] $message")
}

fun main() {
    // فراخوانی تابع با ارسال هر دو پارامتر
    printMessageWithPrefix("Hello", "Log") 
    // [Log] Hello
    
    // فراخوانی تابع تنها با ارسال پارامتر message
    printMessageWithPrefix("Hello")        
    // [Info] Hello
    
    printMessageWithPrefix(prefix = "Log", message = "Hello")
    // [Log] Hello
}
```

> [!note]
> می‌توانید پارامترهای دارای مقدار پیش‌فرض خاصی را بدون ارسال رها کنید، بدون آنکه مجبور باشید همهٔ آن‌ها را نادیده بگیرید. با این حال، پس از اولین پارامتری که ارسال نمی‌شود، باید تمام پارامترهای بعدی را با ذکر نام مشخص کنید.

## توابع بدون مقدار بازگشتی (Functions without return)

اگر تابع شما مقدار معناداری برنمی‌گرداند، نوع بازگشتی آن `Unit` است. `Unit` نوعی است که تنها یک مقدار به نام `Unit` دارد. نیازی نیست در بدنهٔ تابع خود به صورت صریح اعلام کنید که `Unit` بازگردانده می‌شود. این بدان معنی است که نیازی به استفاده از کلمهٔ کلیدی `return` یا اعلان نوع بازگشتی ندارید:

```kotlin
fun printMessage(message: String) {
    println(message)
    // استفاده از `return Unit` یا `return` اختیاری است
}

fun main() {
    printMessage("Hello")
    // Hello
}
```

## توابع تک‌عبارتی (Single-expression functions)

برای مختصرتر شدن کد، می‌توانید از توابع تک‌عبارتی استفاده کنید. برای نمونه، تابع `sum()` را می‌توان کوتاه‌تر کرد:

```kotlin
fun sum(x: Int, y: Int): Int {
    return x + y
}

fun main() {
    println(sum(1, 2))
    // 3
}
```

می‌توانید آکولادهای `{}` را برداشته و بدنهٔ تابع را با عملگر انتساب `=` اعلان کنید. هنگامی که از عملگر انتساب `=` استفاده می‌کنید، کاتلین از استنتاج نوع (type inference) بهره می‌برد؛ بنابراین می‌توانید نوع بازگشتی را نیز حذف کنید. بدین ترتیب تابع `sum()` در یک خط خلاصه می‌شود:

```kotlin
fun sum(x: Int, y: Int) = x + y

fun main() {
    println(sum(1, 2))
    // 3
}
```

با این وجود، اگر می‌خواهید کدهای شما برای توسعه‌دهندگان دیگر به سرعت قابل فهم باشد، تعیین صریح نوع بازگشتی حتی هنگام استفاده از عملگر انتساب `=` ایدهٔ خوبی است.

> [!note]
> اگر برای اعلان بدنهٔ تابع خود از آکولادهای `{}` استفاده کنید، حتماً باید نوع بازگشتی را مشخص نمایید، مگر اینکه نوع بازگشتی `Unit` باشد.

## بازگشت زودهنگام در توابع (Early returns in functions)

برای جلوگیری از پردازش کد تابع پس از یک نقطهٔ مشخص، از کلمهٔ کلیدی `return` استفاده کنید. در این مثال، از `if` برای خروج زودهنگام از تابع در صورت درست بودن عبارت شرطی استفاده شده است:

```kotlin
// فهرستی از نام‌های کاربری ثبت‌شده
val registeredUsernames = mutableListOf("john_doe", "jane_smith")

// فهرستی از ایمیل‌های ثبت‌شده
val registeredEmails = mutableListOf("john@example.com", "jane@example.com")

fun registerUser(username: String, email: String): String {
    // خروج زودهنگام در صورت تکراری بودن نام کاربری
    if (username in registeredUsernames) {
        return "Username already taken. Please choose a different username."
    }

    // خروج زودهنگام در صورت تکراری بودن ایمیل
    if (email in registeredEmails) {
        return "Email already registered. Please use a different email."
    }

    // ادامهٔ ثبت‌نام در صورت تکراری نبودن نام کاربری و ایمیل
    registeredUsernames.add(username)
    registeredEmails.add(email)

    return "User registered successfully: $username"
}

fun main() {
    println(registerUser("john_doe", "newjohn@example.com"))
    // Username already taken. Please choose a different username.
    println(registerUser("new_user", "newuser@example.com"))
    // User registered successfully: new_user
}
```

## تمرین: توابع

### محاسبهٔ مساحت دایره

تابعی به نام `circleArea` بنویسید که شعاع یک دایره را به صورت یک عدد صحیح (`Int`) دریافت کرده و مساحت آن دایره را خروجی دهد.

> [!tip]
> در این تمرین، بسته‌ای (package) را وارد (import) می‌کنید تا بتوانید از طریق `PI` به مقدار عدد پی دسترسی پیدا کنید. برای اطلاعات بیشتر دربارهٔ وارد کردن بسته‌ها، [پکیج‌ها و ایمپورت‌ها](../packages-fa.md) را ببینید.

> [!tip]- راهنمایی
> فرمول محاسبهٔ مساحت دایره برابر است با $\pi r^2$ که در آن $r$ شعاع دایره است.

```kotlin
import kotlin.math.PI

// Write your code here
fun circleArea(r:Int):Double{
return r *r * PI
}

fun main() {
    println(circleArea(2))
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> import kotlin.math.PI
> 
> fun circleArea(radius: Int): Double {
>     return PI * radius * radius
> }
> 
> fun main() {
>     println(circleArea(2)) // 12.566370614359172
> }
> ```

### بازنویسی تابع به صورت تک‌عبارتی

تابع `circleArea` تمرین پیشین را به صورت یک تابع تک‌عبارتی (single-expression) بازنویسی کنید.

```kotlin
import kotlin.math.PI

// Write your code here

fun main() {
    println(circleArea(2))
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> import kotlin.math.PI
> 
> fun circleArea(radius: Int): Double = PI * radius * radius
> 
> fun main() {
>     println(circleArea(2)) // 12.566370614359172
> }
> ```

### بازنویسی تابع با پارامترهای پیش‌فرض و آرگومان‌های نام‌دار

تابعی دارید که یک بازهٔ زمانی داده‌شده بر حسب ساعت، دقیقه و ثانیه را به ثانیه تبدیل می‌کند. در بیشتر موارد، کافی است تنها یک یا دو پارامتر ارسال شوند و بقیه برابر با ۰ باشند. این تابع و کدهای فراخوانی آن را با استفاده از مقادیر پیش‌فرض پارامترها و آرگومان‌های نام‌دار بازنویسی (refactor) کنید تا خوانایی کد افزایش یابد.

```kotlin
fun intervalInSeconds(hours: Int, minutes: Int, seconds: Int) =
    ((hours * 60) + minutes) * 60 + seconds

fun main() {
    println(intervalInSeconds(1, 20, 15))
    println(intervalInSeconds(0, 1, 25))
    println(intervalInSeconds(2, 0, 0))
    println(intervalInSeconds(0, 10, 0))
    println(intervalInSeconds(1, 0, 1))
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> fun intervalInSeconds(hours: Int = 0, minutes: Int = 0, seconds: Int = 0) =
>     ((hours * 60) + minutes) * 60 + seconds
> 
> fun main() {
>     println(intervalInSeconds(1, 20, 15))
>     println(intervalInSeconds(minutes = 1, seconds = 25))
>     println(intervalInSeconds(hours = 2))
>     println(intervalInSeconds(minutes = 10))
>     println(intervalInSeconds(hours = 1, seconds = 1))
> }
> ```

## عبارت‌های لامبدا (Lambda expressions)

کاتلین به شما اجازه می‌دهد تا با استفاده از عبارت‌های لامبدا (lambda expressions) کدهای بسیار خلاصه و گویاتری برای توابع بنویسید.

به عنوان مثال، تابع `uppercaseString()` زیر:

```kotlin
fun uppercaseString(text: String): String {
    return text.uppercase()
}
fun main() {
    println(uppercaseString("hello"))
    // HELLO
}
```

می‌تواند به صورت یک عبارت لامبدا نیز نوشته شود:

```kotlin
fun main() {
    val upperCaseString = { text: String -> text.uppercase() }
    println(upperCaseString("hello"))
    // HELLO
}
```

عبارت‌های لامبدا ممکن است در نگاه نخست پیچیده به نظر برسند، پس بیایید ساختار آن را باز کنیم. عبارت‌های لامبدا درون آکولادهای `{}` نوشته می‌شوند.

درون عبارت لامبدا:

* ابتدا پارامترها و سپس علامت `->` را می‌نویسید.
* بدنهٔ تابع بعد از علامت `->` قرار می‌گیرد.

در مثال پیشین:

* `text` پارامتر تابع است.
* `text` دارای نوع `String` است.
* تابع نتیجهٔ فراخوانی تابع [`.uppercase()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/uppercase.html) روی `text` را برمی‌گرداند.
* کل عبارت لامبدا با استفاده از عملگر انتساب `=` به متغیر `upperCaseString` نسبت داده شده است.
* عبارت لامبدا با فراخوانی متغیر `upperCaseString` شبیه به یک تابع و با ارسال رشتهٔ `"hello"` به عنوان پارامتر اجرا می‌شود.
* تابع `println()` نتیجه را چاپ می‌کند.

> [!note]
> اگر لامبدایی بدون پارامتر اعلان کنید، نیازی به استفاده از `->` نیست. برای نمونه:
> ```kotlin
> { println("Log message") }
> ```

عبارت‌های لامبدا را می‌توان به شیوه‌های گوناگونی به کار گرفت. شما می‌توانید:

* [یک عبارت لامبدا را به عنوان پارامتر به تابعی دیگر ارسال کنید](#ارسال-به-عنوان-پارامتر-به-تابعی-دیگر-pass-to-another-function)
* [یک عبارت لامبدا را از یک تابع بازگردانید](#بازگرداندن-از-یک-تابع-return-from-a-function)
* [یک عبارت لامبدا را به صورت مستقل فراخوانی کنید](#فراخوانی-مستقل-invoke-separately)

### ارسال به عنوان پارامتر به تابعی دیگر (Pass to another function)

یکی از کاربردهای عالی ارسال عبارت لامبدا به یک تابع، استفاده از تابع [`.filter()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/filter.html) روی مجموعه‌هاست:

```kotlin
fun main() {
    //sampleStart
    val numbers = listOf(1, -2, 3, -4, 5, -6)
    
    val positives = numbers.filter ({ x -> x > 0 })
    
    val isNegative = { x: Int -> x < 0 }
    val negatives = numbers.filter(isNegative)
    
    println(positives)
    // [1, 3, 5]
    println(negatives)
    // [-2, -4, -6]
    //sampleEnd
}
```

تابع `.filter()` یک عبارت لامبدا را به عنوان گزاره (predicate) می‌پذیرد و آن را روی تک‌تک عناصر لیست اعمال می‌کند. تابع عنصری را نگه می‌دارد که گزاره برای آن مقدار `true` بازگرداند:

* `{ x -> x > 0 }` در صورتی که عنصر مثبت باشد `true` برمی‌گرداند.
* `{ x -> x < 0 }` در صورتی که عنصر منفی باشد `true` برمی‌گرداند.

این مثال دو روش برای ارسال عبارت لامبدا به یک تابع را نشان می‌دهد:

* برای اعداد مثبت، مثال لامبدا را مستقیماً درون پرانتز تابع `.filter()` قرار می‌دهد.
* برای اعداد منفی، مثال عبارت لامبدا را به متغیر `isNegative` نسبت داده و سپس متغیر `isNegative` به عنوان پارامتر تابع در `.filter()` استفاده می‌شود. در این حالت، باید نوع پارامترهای تابع (`x`) را در عبارت لامبدا مشخص کنید.

> [!note]
> اگر عبارت لامبدا تنها پارامتر تابع باشد، می‌توانید پرانتزهای تابع `()` را به طور کامل حذف کنید:
> 
> ```kotlin
> val positives = numbers.filter { x -> x > 0 }
> ```
> 
> این نمونه‌ای از **لامبدای دنباله‌دار (trailing lambda)** است که با جزئیات بیشتر در ادامه بررسی می‌شود.

نمونهٔ خوب دیگر استفاده از تابع [`.map()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/map.html) برای تبدیل عناصر یک مجموعه است:

```kotlin
fun main() {
    //sampleStart
    val numbers = listOf(1, -2, 3, -4, 5, -6)
    val doubled = numbers.map { x -> x * 2 }
    
    val isTripled = { x: Int -> x * 3 }
    val tripled = numbers.map(isTripled)
    
    println(doubled)
    // [2, -4, 6, -8, 10, -12]
    println(tripled)
    // [3, -6, 9, -12, 15, -18]
    //sampleEnd
}
```

تابع `.map()` یک عبارت لامبدا را به عنوان تابع تبدیل می‌پذیرد:

* `{ x -> x * 2 }` هر عنصر لیست را گرفته و مقدار دو برابر شدهٔ آن را برمی‌گرداند.
* `{ x -> x * 3 }` هر عنصر لیست را گرفته و مقدار سه برابر شدهٔ آن را برمی‌گرداند.

### نوع‌های تابعی (Function types)

پیش از آنکه بتوانید یک عبارت لامبدا را از یک تابع بازگردانید، ابتدا باید با **نوع‌های تابعی (function types)** آشنا شوید.

شما پیش‌تر با نوع‌های دادهٔ پایه آشنا شده‌اید، اما توابع نیز خود دارای نوع هستند. استنتاج نوع کاتلین می‌تواند نوع یک تابع را از روی پارامترهای آن حدس بزند، اما زمان‌هایی وجود دارد که باید نوع تابع را صریحاً مشخص کنید. کامپایلر به نوع تابع نیاز دارد تا بداند چه مواردی برای آن تابع مجاز و چه مواردی غیرمجاز است.

سینتکس نوع تابعی شامل موارد زیر است:

* نوع هر پارامتر که درون پرانتز `()` نوشته شده و با کاما `,` جدا می‌شود.
* نوع بازگشتی که بعد از فلش `->` نوشته می‌شود.

برای نمونه: `(String) -> String` یا `(Int, Int) -> Int`.

اگر برای `upperCaseString()` یک نوع تابعی تعریف شود، عبارت لامبدا به شکل زیر خواهد بود:

```kotlin
val upperCaseString: (String) -> String = { text -> text.uppercase() }

fun main() {
    println(upperCaseString("hello"))
    // HELLO
}
```

اگر عبارت لامبدای شما فاقد پارامتر باشد، پرانتزها `()` خالی رها می‌شوند؛ برای نمونه: `() -> Unit`.

> [!note]
> شما باید نوع پارامترها و نوع بازگشتی را یا درون خود عبارت لامبدا یا به عنوان نوع تابعی مشخص کنید. در غیر این صورت کامپایلر قادر به تشخیص نوع عبارت لامبدای شما نخواهد بود.
> 
> برای مثال، عبارت زیر کار نخواهد کرد و خطا می‌دهد:
> 
> `val upperCaseString = { str -> str.uppercase() }`

### بازگرداندن از یک تابع (Return from a function)

عبارت‌های لامبدا را می‌توان از یک تابع بازگرداند. برای اینکه کامپایلر متوجه نوع لامبدای بازگشتی شود، باید یک نوع تابعی اعلان کنید.

در مثال زیر، تابع `toSeconds()` دارای نوع تابعی `(Int) -> Int` است، زیرا همواره یک عبارت لامبدا بازمی‌گرداند که پارامتری از نوع `Int` گرفته و مقداری از نوع `Int` تحویل می‌دهد.

این مثال از یک عبارت `when` برای تعیین اینکه کدام عبارت لامبدا هنگام فراخوانی `toSeconds()` بازگردانده شود استفاده می‌کند:

```kotlin
fun toSeconds(time: String): (Int) -> Int = when (time) {
    "hour" -> { value -> value * 60 * 60 }
    "minute" -> { value -> value * 60 }
    "second" -> { value -> value }
    else -> { value -> value }
}

fun main() {
    val timesInMinutes = listOf(2, 10, 15, 1)
    val min2sec = toSeconds("minute")
    val totalTimeInSeconds = timesInMinutes.map(min2sec).sum()
    println("Total time is $totalTimeInSeconds secs")
    // Total time is 1680 secs
}
```

### فراخوانی مستقل (Invoke separately)

عبارت‌های لامبدا را می‌توان به تنهایی و با افزودن پرانتز `()` بلافاصله بعد از آکولادهای `{}` و قرار دادن آرگومان‌ها درون آن فراخوانی کرد:

```kotlin
fun main() {
    //sampleStart
    println({ text: String -> text.uppercase() }("hello"))
    // HELLO
    //sampleEnd
}
```

### لامبداهای دنباله‌دار (Trailing lambdas)

همان‌طور که پیش‌تر دیدید، اگر یک عبارت لامبدا تنها پارامتر تابع باشد، می‌توانید پرانتزهای تابع `()` را حذف کنید. اگر عبارت لامبدا به عنوان آخرین پارامتر یک تابع ارسال شود، می‌توان آن عبارت را بیرون از پرانتزهای تابع `()` نوشت. در هر دو حالت، به این شیوه نگارش **لامبدای دنباله‌دار (trailing lambda)** گفته می‌شود.

برای نمونه، تابع [`.fold()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.sequences/fold.html) یک مقدار اولیه و یک عملیات دریافت می‌کند:

```kotlin
fun main() {
    //sampleStart
    // مقدار اولیه صفر است. 
    // این عملیات مقدار اولیه را به صورت تجمعی با تک‌تک عناصر لیست جمع می‌کند.
    println(listOf(1, 2, 3).fold(0, { x, item -> x + item })) // 6

    // به صورت جایگزین، در قالب یک لامبدای دنباله‌دار:
    println(listOf(1, 2, 3).fold(0) { x, item -> x + item })  // 6
    //sampleEnd
}
```

برای اطلاعات بیشتر دربارهٔ عبارت‌های لامبدا، [عبارت‌های لامبدا و توابع ناشناس](../lambdas.md#lambda-expressions-and-anonymous-functions) را ببینید.

گام بعدی در تور یادگیری، آشنایی با [کلاس‌ها](kotlin-tour-classes.md) در کاتلین است.

## تمرین: عبارت‌های لامبدا

### ساخت فهرستی از URLها با عبارت لامبدا

فهرستی از اکشن‌های پشتیبانی‌شده توسط یک وب‌سرویس، یک پیشوند مشترک برای تمام درخواست‌ها و یک شناسه (ID) برای منبعی خاص دارید. برای درخواست اکشن `title` روی منبعی با شناسهٔ ۵، باید چنین نشانی‌ای بسازید: `https://example.com/book-info/5/title`. با استفاده از یک عبارت لامبدا، فهرستی از URLها را از فهرست اکشن‌ها تولید کنید.

```kotlin
fun main() {
    val actions = listOf("title", "year", "author")
    val prefix = "https://example.com/book-info"
    val id = 5
    val urls = // Write your code here
    println(urls)
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> fun main() {
>     val actions = listOf("title", "year", "author")
>     val prefix = "https://example.com/book-info"
>     val id = 5
>     val urls = actions.map { action -> "$prefix/$id/$action" }
>     println(urls)
> }
> ```

### تکرار یک عمل به دفعات مشخص

تابعی بنویسید که یک مقدار `Int` و یک عمل (تابعی با نوع `() -> Unit`) دریافت کرده و سپس آن عمل را به تعداد مشخص‌شده تکرار کند. سپس با استفاده از این تابع، عبارت «Hello» را ۵ بار چاپ کنید.

```kotlin
fun repeatN(n: Int, action: () -> Unit) {
    // Write your code here
}

fun main() {
    // Write your code here
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> fun repeatN(n: Int, action: () -> Unit) {
>     for (i in 1..n) {
>         action()
>     }
> }
> 
> fun main() {
>     repeatN(5) {
>         println("Hello")
>     }
> }
> ```

[گام پیشین](kotlin-tour-control-flow-fa.md) · [گام بعدی](kotlin-tour-classes.md)

---

## تمرین و مرور

این بخش برای تثبیت و مرور مفاهیم توابع و عبارت‌های لامبدا اضافه شده است.

### پنج پرسش بازیابی فعال

1. ساختار پایهٔ تعریف یک تابع در کاتلین شامل چه بخش‌هایی است و نوع بازگشتی در کجا مشخص می‌شود؟
   > [!check]- پاسخ
   > با کلمهٔ کلیدی `fun` آغاز می‌شود، نام تابع و سپس پارامترها درون پرانتز `(name: Type)` قرار می‌گیرند، نوع بازگشتی پس از دو نقطه `:` بعد از پرانتزها می‌آید و بدنهٔ تابع درون آکولاد `{}` نوشته می‌شود. در صورت بازگرداندن مقدار، از کلمهٔ کلیدی `return` استفاده می‌شود.

2. تفاوت آرگومان‌های نام‌دار (Named Arguments) و مقادیر پیش‌فرض (Default Parameter Values) چیست و چه مزیتی در خوانایی کد دارند؟
   > [!check]- پاسخ
   > مقادیر پیش‌فرض به شما امکان می‌دهند مقداری پیش‌فرض برای پارامتر تعیین کنید تا ارسال آن هنگام فراخوانی اختیاری شود (`prefix: String = "Info"`). آرگومان‌های نام‌دار به شما امکان می‌دهند نام پارامتر را در زمان فراخوانی بنویسید (`prefix = "Log"`) که باعث می‌شود ترتیب ارسال پارامترها اهمیتی نداشته باشد و خوانایی کد به شدت افزایش یابد.

3. مفهوم نوع `Unit` در کاتلین چیست و در چه شرایطی می‌توان نوع بازگشتی و کلمهٔ `return` را حذف کرد؟
   > [!check]- پاسخ
   > نوع `Unit` معادل توابعی است که مقدار معناداری برنمی‌گردانند (مشابه `void` در زبان‌های دیگر). اگر تابعی مقداری برنگرداند، کاتلین به طور پیش‌فرض نوع آن را `Unit` در نظر می‌گیرد و نیازی به نوشتن صریح `: Unit` یا دستور `return` در انتهای تابع نیست.

4. نحو (syntax) توابع تک‌عبارتی (Single-expression functions) چگونه است و چه مزیتی دارند؟
   > [!check]- پاسخ
   > زمانی که بدنهٔ تابع تنها از یک عبارت تشکیل شده باشد، می‌توان آکولادها `{}` و کلمهٔ `return` را حذف کرد و مستقیماً بعد از اعلان تابع علامت مساوی `=` و سپس عبارت را قرار داد (`fun sum(x: Int, y: Int) = x + y`). در این حالت به دلیل استنتاج نوع (type inference) می‌توان نوع بازگشتی را نیز حذف کرد.

5. لامبدای دنباله‌دار (Trailing Lambda) چیست و سینتکس آن چگونه نوشته می‌شود؟
   > [!check]- پاسخ
   > طبق این قاعده در کاتلین، اگر آخرین پارامتر یک تابع یک عبارت لامبدا باشد، می‌توان آن لامبدا را بیرون از پرانتزهای تابع قرار داد (`numbers.map() { ... }`). همچنین اگر لامبدا تنها پارامتر تابع باشد، می‌توان پرانتزهای تابع را به طور کامل حذف کرد (`numbers.map { ... }`).

### سه تمرین تکمیلی

1. **تمرین ساخت تابع فیلتر اعداد زوج با لامبدا:** تابعی به نام `filterEvens` بنویسید که لیستی از اعداد صحیح (`List<Int>`) را دریافت کرده و با استفاده از تابع `.filter()` و یک عبارت لامبدا، تنها اعداد زوج را برگرداند.
   > [!tip]- راهنمایی
   > از عملگر باقی‌مانده `%` برای بررسی زوج بودن (`x % 2 == 0`) درون لامبدا استفاده کنید.
   > [!example]- راه‌حل نمونه
   > ```kotlin
   > fun filterEvens(numbers: List<Int>): List<Int> {
   >     return numbers.filter { x -> x % 2 == 0 }
   > }
   > 
   > fun main() {
   >     val list = listOf(1, 2, 3, 4, 5, 6)
   >     println(filterEvens(list)) // [2, 4, 6]
   > }
   > ```

2. **تمرین تابع قالب‌بندی با مقادیر پیش‌فرض:** تابعی تک‌عبارتی به نام `formatCurrency` تعریف کنید که یک مقدار عددی `amount: Double` و یک واحد پول `currency: String = "USD"` دریافت کند و رشته‌ای به صورت `"$amount $currency"` برگرداند. سپس آن را هم با مقدار پیش‌فرض و هم با آرگومان نام‌دار برای واحد `"EUR"` فراخوانی کنید.
   > [!tip]- راهنمایی
   > از علامت `=` به جای `{}` برای ساخت تابع تک‌عبارتی و از الگوهای رشته‌ای `"$amount $currency"` استفاده کنید.
   > [!example]- راه‌حل نمونه
   > ```kotlin
   > fun formatCurrency(amount: Double, currency: String = "USD") = "$amount $currency"
   > 
   > fun main() {
   >     println(formatCurrency(100.0)) // 100.0 USD
   >     println(formatCurrency(amount = 50.0, currency = "EUR")) // 50.0 EUR
   > }
   > ```

3. **تمرین توابع مرتبه بالاتر (Higher-order Function):** تابعی به نام `transformAndPrint` بنویسید که یک رشته `text: String` و یک تابع تبدیل با نوع `(String) -> String` دریافت کند، تابع تبدیل را روی متن اجرا کند و نتیجه را چاپ کند.
   > [!tip]- راهنمایی
   > نوع پارامتر تابع را `(String) -> String` قرار دهید و در بدنه آن را با `transformer(text)` فراخوانی کنید.
   > [!example]- راه‌حل نمونه
   > ```kotlin
   > fun transformAndPrint(text: String, transformer: (String) -> String) {
   >     val result = transformer(text)
   >     println(result)
   > }
   > 
   > fun main() {
   >     transformAndPrint("kotlin") { it.uppercase() } // KOTLIN
   >     transformAndPrint("Hello World") { ">>> $it <<<" } // >>> Hello World <<<
   > }
   > ```

### دو خطای رایج

1. **فراموش کردن مشخص کردن نوع در اعلان متغیر لامبدا بدون استنتاج:** اگر متغیری را برابر با یک لامبدا قرار دهید و نه نوع متغیر مشخص شده باشد و نه نوع پارامتر لامبدا (مانند `val f = { x -> x * 2 }`)، کاتلین نمی‌تواند نوع پارامتر را حدس بزند و خطای کامپایل می‌دهد. باید حداقل یکی از آن‌ها مشخص باشد: `val f: (Int) -> Int = { x -> x * 2 }` یا `val f = { x: Int -> x * 2 }`.
2. **اشتباه در حذف نوع بازگشتی در توابع دارای بدنهٔ بلوکی `{}`:** تنها در توابع تک‌عبارتی (که با `=` نوشته می‌شوند) می‌توان نوع بازگشتی غیر از `Unit` را حذف کرد. اگر تابعی با بدنهٔ بلوکی `{}` نوشته شود و عبارتی را برگرداند اما نوع بازگشتی برای آن نوشته نشود، کاتلین آن را تابع از نوع `Unit` در نظر گرفته و دستور `return value` منجر به خطای کامپایل خواهد شد.
