---
cssclasses:
  - persian-rtl
---

# جریان کنترل (Control flow)

کاتلین همانند دیگر زبان‌های برنامه‌نویسی قادر است بر اساس درست (true) بودن ارزیابی یک قطعه کد، تصمیم‌گیری کند. به این قطعه‌کدها **عبارت‌های شرطی (conditional expressions)** گفته می‌شود. همچنین کاتلین قادر است حلقه‌ها را ایجاد کرده و روی آن‌ها تکرار (iterate) کند.

## عبارت‌های شرطی

کاتلین `if` و `when` را برای بررسی عبارت‌های شرطی ارائه می‌دهد.

> [!note]
> اگر ناچارید بین `if` و `when` یکی را انتخاب کنید، پیشنهاد می‌کنیم از `when` استفاده کنید، زیرا:
>
> * خوانایی کد شما را افزایش می‌دهد.
> * افزودن یک شاخهٔ جدید را آسان‌تر می‌کند.
> * باعث کاهش خطاهای کد شما می‌شود.

### دستور if

برای استفاده از `if`، عبارت شرطی را درون پرانتز `()` و عملیاتی را که در صورت درست بودن نتیجه باید انجام شود، درون آکولاد `{}` قرار دهید:

```kotlin
fun main() {
//sampleStart
    val d: Int
    val check = true

    if (check) {
        d = 1
    } else {
        d = 2
    }

    println(d)
    // 1
//sampleEnd
}
```

در کاتلین عملگر سه‌تایی (ternary operator) یعنی `condition ? then : else` وجود ندارد. در عوض، می‌توان از `if` به عنوان یک عبارت (expression) استفاده کرد. اگر برای هر عمل فقط یک خط کد وجود داشته باشد، استفاده از آکولاد `{}` اختیاری است:

```kotlin
fun main() { 
//sampleStart
    val a = 1
    val b = 2

    println(if (a > b) a else b) // Returns a value: 2
//sampleEnd
}
```

### ساختار when

هنگامی که عبارت شرطی با چندین شاخه دارید، از `when` استفاده کنید.

برای استفاده از `when`:

* مقداری را که می‌خواهید ارزیابی شود درون پرانتز `()` قرار دهید.
* شاخه‌ها را درون آکولاد `{}` بگذارید.
* در هر شاخه از `->` برای جداسازی شرط بررسی از عملی که در صورت موفقیت باید انجام شود، استفاده کنید.

از `when` می‌توان هم به عنوان دستور (statement) و هم به عنوان عبارت (expression) استفاده کرد. یک **دستور (statement)** مقداری برنمی‌گرداند، بلکه به جای آن عملیاتی را انجام می‌دهد.

در اینجا مثالی از کاربرد `when` به عنوان دستور آورده شده است:

```kotlin
fun main() {
//sampleStart
    val obj = "Hello"

    when (obj) {
        // Checks whether obj equals to "1"
        "1" -> println("One")
        // Checks whether obj equals to "Hello"
        "Hello" -> println("Greeting")
        // Default statement
        else -> println("Unknown")     
    }
    // Greeting
//sampleEnd
}
```

> [!note]
> توجه داشته باشید که تمام شرط‌های شاخه‌ها به صورت ترتیبی و پی‌درپی بررسی می‌شوند تا زمانی که یکی از آن‌ها برقرار شود؛ بنابراین فقط اولین شاخهٔ مناسب اجرا می‌گردد.

یک **عبارت (expression)** مقداری را برمی‌گرداند که بعداً در کد شما قابل استفاده است.

در ادامه مثالی از کاربرد `when` به عنوان عبارت آمده است. عبارت `when` بلافاصله به یک متغیر نسبت داده می‌شود و سپس با تابع `println()` استفاده می‌گردد:

```kotlin
fun main() {
//sampleStart    
    val obj = "Hello"    
    
    val result = when (obj) {
        // If obj equals "1", sets result to "one"
        "1" -> "One"
        // If obj equals "Hello", sets result to "Greeting"
        "Hello" -> "Greeting"
        // Sets result to "Unknown" if no previous condition is satisfied
        else -> "Unknown"
    }
    println(result)
    // Greeting
//sampleEnd
}
```

مثال‌هایی از `when` که تاکنون دیده‌اید هر دو دارای یک موضوع (subject) بودند: `obj`. اما `when` می‌تواند بدون موضوع نیز استفاده شود.

این مثال از عبارت `when` **بدون** موضوع برای بررسی زنجیره‌ای از عبارت‌های بولی (Boolean) استفاده می‌کند:

```kotlin
fun main() {
    val trafficLightState = "Red" // This can be "Green", "Yellow", or "Red"

    val trafficAction = when {
        trafficLightState == "Green" -> "Go"
        trafficLightState == "Yellow" -> "Slow down"
        trafficLightState == "Red" -> "Stop"
        else -> "Malfunction"
    }

    println(trafficAction)
    // Stop
}
```

با این حال، می‌توانید همین کد را با قرار دادن `trafficLightState` به عنوان موضوع (subject) بنویسید:

```kotlin
fun main() {
    val trafficLightState = "Red" // This can be "Green", "Yellow", or "Red"

    val trafficAction = when (trafficLightState) {
        "Green" -> "Go"
        "Yellow" -> "Slow down"
        "Red" -> "Stop"
        else -> "Malfunction"
    }

    println(trafficAction)  
    // Stop
}
```

استفاده از `when` به همراه یک موضوع، خوانایی و نگه‌داری کد شما را آسان‌تر می‌کند. همچنین وقتی با یک عبارت `when` از موضوع استفاده می‌کنید، به کاتلین کمک می‌کند بررسی کند که آیا همهٔ حالت‌های ممکن پوشش داده شده‌اند یا خیر. در غیر این صورت، اگر از موضوع در عبارت `when` استفاده نکنید، باید یک شاخهٔ `else` فراهم کنید.

## تمرین: عبارت‌های شرطی

### بررسی تطابق پرتاب دو تاس

یک بازی ساده بسازید که در آن اگر نتیجهٔ پرتاب دو تاس یکسان باشد، برنده می‌شوید. با استفاده از `if`، در صورتی که نتیجهٔ هر دو تاس یکسان بود عبارت `You win :)` و در غیر این صورت `You lose :(` را چاپ کنید.

> [!tip]
> در این تمرین، بسته‌ای (package) را وارد (import) می‌کنید تا بتوانید از تابع `Random.nextInt()` برای تولید یک عدد صحیح تصادفی (`Int`) استفاده کنید. برای اطلاعات بیشتر دربارهٔ وارد کردن بسته‌ها، [بسته‌ها و ایمپورت‌ها](../packages-fa.md) را ببینید.

> [!tip]- راهنمایی
> از [عملگر برابری](../operator-overloading.md#equality-and-inequality-operators) (`==`) برای مقایسهٔ نتایج تاس‌ها استفاده کنید.

```kotlin
import kotlin.random.Random

fun main() {
    val firstResult = Random.nextInt(6)
    val secondResult = Random.nextInt(6)
    // Write your code here
    if (firstResult == secondResult){
    println("You win :)")
    }else{
    println("You lose :(")
    }
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> import kotlin.random.Random
> 
> fun main() {
>     val firstResult = Random.nextInt(6)
>     val secondResult = Random.nextInt(6)
>     if (firstResult == secondResult)
>         println("You win :)")
>     else
>         println("You lose :(")
> }
> ```

### چاپ عملکرد دکمهٔ کنسول بازی

با استفاده از عبارت `when`، برنامهٔ زیر را کامل کنید تا با دریافت نام هر یک از دکمه‌های کنسول بازی، عملکرد متناظر با آن را چاپ کند.

| **دکمه (Button)** | **عملکرد (Action)** |
|---|---|
| A | Yes |
| B | No |
| X | Menu |
| Y | Nothing |
| Other | There is no such button |

```kotlin
fun main() {
    val button = "A"

    println(
        // Write your code here
    )
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> fun main() {
>     val button = "A"
>     
>     println(
>         when (button) {
>             "A" -> "Yes"
>             "B" -> "No"
>             "X" -> "Menu"
>             "Y" -> "Nothing"
>             else -> "There is no such button"
>         }
>     )
> }
> ```

## بازه‌ها

پیش از پرداختن به حلقه‌ها، آشنایی با نحوهٔ ساخت بازه‌ها (ranges) برای تکرار حلقه‌ها روی آن‌ها سودمند است.

رایج‌ترین روش برای ایجاد یک بازه در کاتلین استفاده از عملگر `..` است. برای نمونه، `1..4` معادل `1, 2, 3, 4` است.

برای اعلان بازه‌ای که مقدار پایانی را شامل نمی‌شود، از عملگر `..<` استفاده کنید. برای نمونه، `1..<4` معادل `1, 2, 3` است.

برای اعلان بازه به ترتیب معکوس، از [`downTo`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.ranges/down-to.html) استفاده کنید. برای نمونه، `4 downTo 1` معادل `4, 3, 2, 1` است.

برای اعلان بازه‌ای که گام افزایشی آن عددی غیر از ۱ باشد، از [`step`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.ranges/step.html) و مقدار گام دلخواه خود استفاده کنید. برای نمونه، `1..5 step 2` معادل `1, 3, 5` است.

همین کار را می‌توانید برای بازه‌های نویسه‌ای (`Char`) نیز انجام دهید:

* `'a'..'d'` معادل `'a', 'b', 'c', 'd'` است.
* `'z' downTo 's' step 2` معادل `'z', 'x', 'v', 't'` است.

## حلقه‌ها

دو ساختار رایج برای حلقه در برنامه‌نویسی `for` و `while` هستند. از `for` برای پیمایش روی یک بازه از مقادیر و انجام یک عمل استفاده کنید. از `while` برای ادامهٔ یک عمل تا زمانی که شرط خاصی برآورده شود استفاده کنید.

### حلقهٔ for

با استفاده از دانش جدید خود دربارهٔ بازه‌ها، می‌توانید یک حلقهٔ `for` بسازید که اعداد ۱ تا ۵ را پیمایش کرده و هر بار آن عدد را چاپ کند.

شمارنده (تکرارکننده - iterator) و بازه را همراه با کلمهٔ کلیدی `in` درون پرانتز `()` قرار دهید. عملیاتی را که می‌خواهید انجام شود درون آکولاد `{}` بگذارید:

```kotlin
fun main() {
//sampleStart
    for (number in 1..5) { 
        // number is the iterator and 1..5 is the range
        print(number)
    }
    // 12345
//sampleEnd
}
```

مجموعه‌ها (Collections) نیز می‌توانند توسط حلقه‌ها پیمایش شوند:

```kotlin
fun main() { 
//sampleStart
    val cakes = listOf("carrot", "cheese", "chocolate")

    for (cake in cakes) {
        println("Yummy, it's a $cake cake!")
    }
    // Yummy, it's a carrot cake!
    // Yummy, it's a cheese cake!
    // Yummy, it's a chocolate cake!
//sampleEnd
}
```

### حلقهٔ while

حلقهٔ `while` می‌تواند به دو روش استفاده شود:

* برای اجرای یک بلوک کد تا زمانی که یک عبارت شرطی درست (true) باشد. (`while`)
* برای اجرای بلوک کد در ابتدا و سپس بررسی عبارت شرطی. (`do-while`)

در حالت نخست (`while`):

* عبارت شرطی لازم برای ادامهٔ حلقهٔ `while` را درون پرانتز `()` اعلان کنید.
* عملیاتی را که می‌خواهید انجام شود درون آکولاد `{}` بنویسید.

> [!tip]
> در مثال‌های زیر از [عملگر افزایش](../operator-overloading.md#increments-and-decrements) `++` برای افزایش مقدار متغیر `cakesEaten` استفاده شده است.

```kotlin
fun main() {
//sampleStart
    var cakesEaten = 0
    while (cakesEaten < 3) {
        println("Eat a cake")
        cakesEaten++
    }
    // Eat a cake
    // Eat a cake
    // Eat a cake
//sampleEnd
}
```

در حالت دوم (`do-while`):

* عبارت شرطی لازم برای ادامهٔ حلقه را درون پرانتز `()` اعلان کنید.
* عملیاتی را که می‌خواهید انجام شود را همراه با کلمهٔ کلیدی `do` درون آکولاد `{}` مشخص کنید.

```kotlin
fun main() {
//sampleStart
    var cakesEaten = 0
    var cakesBaked = 0
    while (cakesEaten < 3) {
        println("Eat a cake")
        cakesEaten++
    }
    do {
        println("Bake a cake")
        cakesBaked++
    } while (cakesBaked < cakesEaten)
    // Eat a cake
    // Eat a cake
    // Eat a cake
    // Bake a cake
    // Bake a cake
    // Bake a cake
//sampleEnd
}
```

برای اطلاعات بیشتر و مشاهدهٔ مثال‌های دیگر از عبارت‌های شرطی و حلقه‌ها، [شرط‌ها و حلقه‌ها](../control-flow-fa.md) را ببینید.

اکنون که با مبانی جریان کنترل در کاتلین آشنا شدید، زمان آن رسیده است که نحوهٔ نوشتن [توابع](kotlin-tour-functions.md) سفارشی خود را بیاموزید.

## تمرین: حلقه‌ها

### شمارش برش‌های پیتزا با حلقه‌های while و do-while

برنامه‌ای دارید که برش‌های پیتزا را می‌شمارد تا به یک پیتزای کامل با ۸ برش برسد. این برنامه را به دو روش بازنویسی (refactor) کنید:

* با استفاده از حلقهٔ `while`.
* با استفاده از حلقهٔ `do-while`.

```kotlin
fun main() {
    var pizzaSlices = 0
    // Start refactoring here
    pizzaSlices++
    println("There's only $pizzaSlices slice/s of pizza :(")
    pizzaSlices++
    println("There's only $pizzaSlices slice/s of pizza :(")
    pizzaSlices++
    println("There's only $pizzaSlices slice/s of pizza :(")
    pizzaSlices++
    println("There's only $pizzaSlices slice/s of pizza :(")
    pizzaSlices++
    println("There's only $pizzaSlices slice/s of pizza :(")
    pizzaSlices++
    println("There's only $pizzaSlices slice/s of pizza :(")
    pizzaSlices++
    println("There's only $pizzaSlices slice/s of pizza :(")
    pizzaSlices++
    // End refactoring here
    println("There are $pizzaSlices slices of pizza. Hooray! We have a whole pizza! :D")
}
```

> [!example]- راه‌حل نمونه با while
> ```kotlin
> fun main() {
>     var pizzaSlices = 0
>     while (pizzaSlices < 7) {
>         pizzaSlices++
>         println("There's only $pizzaSlices slice/s of pizza :(")
>     }
>     pizzaSlices++
>     println("There are $pizzaSlices slices of pizza. Hooray! We have a whole pizza! :D")
> }
> ```

> [!example]- راه‌حل نمونه با do-while
> ```kotlin
> fun main() {
>     var pizzaSlices = 0
>     pizzaSlices++
>     do {
>         println("There's only $pizzaSlices slice/s of pizza :(")
>         pizzaSlices++
>     } while (pizzaSlices < 8)
>     println("There are $pizzaSlices slices of pizza. Hooray! We have a whole pizza! :D")
> }
> ```

### بازی فیز باز (Fizz buzz)

برنامه‌ای بنویسید که بازی [Fizz buzz](https://en.wikipedia.org/wiki/Fizz_buzz) را شبیه‌سازی کند. وظیفهٔ شما چاپ اعداد از ۱ تا ۱۰۰ به صورت افزایشی است، با این تفاوت که هر عددی که بر ۳ بخش‌پذیر باشد را با کلمهٔ `"fizz"` و هر عددی که بر ۵ بخش‌پذیر باشد را با کلمهٔ `"buzz"` جایگزین کنید. هر عددی هم که بر هر دو عدد ۳ و ۵ بخش‌پذیر باشد باید با کلمهٔ `"fizzbuzz"` جایگزین شود.

> [!tip]- راهنمایی ۱
> از یک حلقهٔ `for` برای شمارش اعداد و از یک عبارت `when` برای تصمیم‌گیری دربارهٔ آنچه باید در هر مرحله چاپ شود استفاده کنید.

> [!tip]- راهنمایی ۲
> از عملگر باقی‌ماندهٔ تقسیم (`%`) برای محاسبهٔ باقی‌مانده استفاده کنید. از [عملگر برابری](../operator-overloading.md#equality-and-inequality-operators) (`==`) برای بررسی اینکه آیا باقی‌مانده برابر با صفر است یا خیر استفاده نمایید.

```kotlin
fun main() {
    // Write your code here
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> fun main() {
>     for (number in 1..100) {
>         println(
>             when {
>                 number % 15 == 0 -> "fizzbuzz"
>                 number % 3 == 0 -> "fizz"
>                 number % 5 == 0 -> "buzz"
>                 else -> "$number"
>             }
>         )
>     }
> }
> ```

### چاپ کلماتی که با یک حرف مشخص شروع می‌شوند

فهرستی از کلمات دارید. با استفاده از `for` و `if` تنها کلماتی را چاپ کنید که با حرف `l` شروع می‌شوند.

> [!tip]- راهنمایی
> از تابع [`.startsWith()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/starts-with.html) برای نوع `String` استفاده کنید.

```kotlin
fun main() {
    val words = listOf("dinosaur", "limousine", "magazine", "language")
    // Write your code here
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> fun main() {
>     val words = listOf("dinosaur", "limousine", "magazine", "language")
>     for (w in words) {
>         if (w.startsWith("l"))
>             println(w)
>     }
> }
> ```

[گام پیشین](kotlin-tour-collections-fa.md) · [گام بعدی](kotlin-tour-functions-fa.md)

---

## تمرین و مرور

این بخش برای تثبیت و مرور مطالب جریان کنترل اضافه شده است.

### پنج پرسش بازیابی فعال

1. تفاوت اصلی بین دستور (statement) و عبارت (expression) در کاتلین چیست و ساختارهای `if` و `when` چگونه می‌توانند به عنوان عبارت عمل کنند؟
   > [!check]- پاسخ
   > یک دستور (statement) کاری یا عملیاتی را انجام می‌دهد ولی مقداری برنمی‌گرداند؛ اما یک عبارت (expression) ارزیابی شده و مقداری را تولید می‌کند که می‌توان آن را به یک متغیر نسبت داد یا در توابعی مثل `println()` استفاده کرد. اگر خروجی `if` یا `when` مستقیماً به یک متغیر نسبت داده شود یا به عنوان ورودی استفاده شود، در نقش عبارت عمل می‌کنند و باید حتماً تمام حالات را با شاخهٔ `else` یا شاخه‌های جامع پوشش دهند.

2. چرا استفاده از `when` به جای ساختارهای چندگانهٔ `if-else` ترجیح داده می‌شود؟
   > [!check]- پاسخ
   > ساختار `when` خوانایی بسیار بالاتری به کد می‌دهد، افزودن شاخه‌های جدید به آن ساده‌تر است و از بروز اشتباهات در شاخه‌بندی‌های پیچیده شرطی جلوگیری می‌کند.

3. در ساختار `when` بدون موضوع (subject)، شرایط شاخه‌ها بر چه اساسی ارزیابی می‌شوند و در چه صورتی شاخهٔ `else` الزامی است؟
   > [!check]- پاسخ
   > شرایط شاخه‌ها صرفاً عبارت‌های بولی (`Boolean`) هستند که به ترتیب از بالا به پایین بررسی می‌شوند و اولین شاخه‌ای که به `true` ارزیابی شود اجرا می‌شود. اگر از `when` بدون موضوع به عنوان یک عبارت (Expression) استفاده شود، داشتن شاخهٔ `else` الزامی است.

4. تفاوت عملگر `..` با `..<` در ایجاد بازه‌ها چیست و برای ساخت بازهٔ کاهشی با گام مشخص از چه توابعی استفاده می‌شود؟
   > [!check]- پاسخ
   > عملگر `..` یک بازهٔ بسته شامل مقدار پایانی ایجاد می‌کند (مثلاً `1..4` برابر با ۱، ۲، ۳، ۴ است)، در حالی که عملگر `..<` مقدار پایانی را در نظر نمی‌گیرد (مثلاً `1..<4` برابر با ۱، ۲، ۳ است). برای بازهٔ معکوس از تابع `downTo` و برای تعیین اندازهٔ گام از `step` استفاده می‌شود.

5. تفاوت بنیادین در ترتیب اجرای حلقهٔ `while` و حلقهٔ `do-while` چیست؟
   > [!check]- پاسخ
   > حلقهٔ `while` ابتدا شرط را بررسی می‌کند و در صورت برقرار بودن، بدنه را اجرا می‌کند (ممکن است بدنه اصلاً اجرا نشود)، اما حلقهٔ `do-while` ابتدا بدنه را بدون قید و شرط یک بار اجرا کرده و سپس شرط را برای تکرارهای بعدی بررسی می‌کند؛ بنابراین حداقل یک بار اجرا می‌شود.

### سه تمرین تکمیلی

1. **تمرین تعیین وضعیت نمره:** با استفاده از عبارت `when` با موضوع، برنامه‌ای بنویسید که یک متغیر `score` (بین ۰ تا ۱۰۰) دریافت کند و بر اساس بازه‌ها وضعیت دانشجو را در متغیری به نام `grade` به صورت `"A"` (برای ۹۰ تا ۱۰۰)، `"B"` (برای ۸۰ تا ۸۹)، `"C"` (برای ۷۰ تا ۷۹) و `"F"` (برای کمتر از ۷۰) قرار داده و چاپ کند.
   > [!tip]- راهنمایی
   > از کلمهٔ کلیدی `in` به همراه بازه‌ها در شاخه‌های `when (score)` استفاده کنید.
   > [!example]- راه‌حل نمونه
   > ```kotlin
   > fun main() {
   >     val score = 85
   >     val grade = when (score) {
   >         in 90..100 -> "A"
   >         in 80..89 -> "B"
   >         in 70..79 -> "C"
   >         in 0..69 -> "F"
   >         else -> "Invalid Score"
   >     }
   >     println("نمرهٔ شما: $grade")
   > }
   > ```

2. **تمرین معکوس‌سازی شمارش:** با استفاده از حلقهٔ `for` و بازهٔ کاهشی، برنامه‌ای بنویسید که اعداد زوج بین ۱۰ تا ۲ را به صورت معکوس در خروجی چاپ کند (۱۰، ۸، ۶، ۴، ۲).
   > [!tip]- راهنمایی
   > از ترکیب تابع `downTo` و `step 2` برای ایجاد بازهٔ کاهشی روی حلقهٔ `for` استفاده کنید.
   > [!example]- راه‌حل نمونه
   > ```kotlin
   > fun main() {
   >     for (number in 10 downTo 2 step 2) {
   >         print("$number ")
   >     }
   > }
   > ```

3. **تمرین مجموع ارقام با حلقه:** متغیری با مقدار عددی مثبت دلخواه (مثلاً `var number = 1234`) تعریف کنید. با استفاده از یک حلقهٔ `while`، عملگر تقسیم صحیح `/` و باقی‌مانده `%`، مجموع ارقام این عدد را محاسبه کرده و چاپ کنید.
   > [!tip]- راهنمایی
   > در هر گام از حلقهٔ `while (number > 0)`، باقی‌ماندهٔ تقسیم عدد بر ۱۰ (`number % 10`) را به متغیر مجموع اضافه کرده و عدد را بر ۱۰ تقسیم کنید (`number /= 10`).
   > [!example]- راه‌حل نمونه
   > ```kotlin
   > fun main() {
   >     var number = 1234
   >     var sum = 0
   >     while (number > 0) {
   >         sum += number % 10
   >         number /= 10
   >     }
   >     println("مجموع ارقام: $sum")
   >     // مجموع ارقام: 10
   > }
   > ```

### دو خطای رایج

1. **فراموش کردن شاخهٔ `else` در زمان استفاده از `if` یا `when` به عنوان عبارت (Expression):** وقتی `if` یا `when` مقداری را برمی‌گردانند، کامپایلر کاتلین باید مطمئن باشد که تحت هر شرایطی مقداری تولید می‌شود؛ بنابراین اگر همهٔ حالت‌های ممکن پوشش داده نشده باشند و شاخهٔ `else` نوشته نشود، خطای کامپایل دریافت خواهید کرد.
2. **اشتباه در شرط پایانی حلقه‌های `while` و ایجاد حلقهٔ بی‌نهایت (Infinite Loop):** در حلقه‌های `while` اگر متغیر کنترل‌کنندهٔ حلقه در بدنه تغییر نکند یا شرط به گونه‌ای باشد که هیچ‌گاه به `false` ارزیابی نشود، برنامه در حلقه‌ای بی‌نهایت گیر می‌افتد.
