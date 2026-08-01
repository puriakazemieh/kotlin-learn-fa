[//]: # (title: بازگشت‌ها و پرش‌ها)

کاتلین دارای سه عبارت پرش ساختاری (structural jump expressions) است:

* `return` به طور پیش‌فرض از نزدیک‌ترین تابع دربرگیرنده یا [تابع ناشناس](https://kotlinlang.org/docs/lambdas.html#anonymous-functions) بازمی‌گردد.
* `break` نزدیک‌ترین حلقه دربرگیرنده را خاتمه می‌دهد.
* `continue` به مرحله بعدی نزدیک‌ترین حلقه دربرگیرنده می‌رود.

تمامی این عبارات می‌توانند به عنوان بخشی از عبارات بزرگتر استفاده شوند:

```kotlin
val s = person.name ?: return
```

نوع این عبارات [نوع Nothing](https://kotlinlang.org/docs/exceptions.html#the-nothing-type) است.

## برچسب‌های Break و continue

هر عبارت در کاتلین می‌تواند با یک _برچسب_ (label) مشخص شود.
برچسب‌ها به شکل یک شناسه‌ به همراه علامت `@` هستند، مانند `abc@` یا `fooBar@`.
برای برچسب‌گذاری یک عبارت، کافی است برچسب را قبل از آن اضافه کنید.

```kotlin
loop@ for (i in 1..100) {
    // ...
}
```

اکنون می‌توانید یک `break` یا `continue` را با یک برچسب واجد شرایط (qualify) کنید:

```kotlin
loop@ for (i in 1..100) {
    for (j in 1..100) {
        if (...) break@loop
    }
}
```

یک `break` که با برچسب واجد شرایط شده است، به نقطه اجرای بلافاصله پس از حلقه‌ای که با آن برچسب مشخص شده است، پرش می‌کند.
یک `continue` به تکرار بعدی آن حلقه می‌رود.

> در برخی موارد، می‌توانید `break` و `continue` را به‌صورت *غیرمحلی* (non-locally) بدون تعریف صریح برچسب‌ها اعمال کنید.
> چنین استفاده‌های غیرمحلی در عبارت‌های لامبدا که در [توابع درون‌برنامه‌ای (inline functions)](https://kotlinlang.org/docs/inline-functions.html#break-and-continue) دربرگیرنده استفاده می‌شوند، مجاز هستند.

## بازگشت به برچسب‌ها

در کاتلین، توابع می‌توانند با استفاده از لیترال‌های تابع (function literals)، توابع محلی و عبارت‌های شیء (object expressions) تو در تو باشند.
یک `return` واجد شرایط به شما اجازه می‌دهد از یک تابع بیرونی بازگردید.

مهم‌ترین مورد استفاده، بازگشت از یک عبارت لامبدا است. برای بازگشت از یک عبارت لامبدا، آن را برچسب‌گذاری کرده و `return` را واجد شرایط کنید:

```kotlin
//sampleStart
fun foo() {
    listOf(1, 2, 3, 4, 5).forEach lit@{
        if (it == 3) return@lit // بازگشت محلی به فراخواننده لامبدا - حلقه forEach
        print(it)
    }
    print(" done with explicit label")
}
//sampleEnd

fun main() {
    foo()
}
```


اکنون، این دستور فقط از عبارت لامبدا بازمی‌گردد. اغلب استفاده از _برچسب‌های ضمنی_ (implicit labels) راحت‌تر است، زیرا چنین برچسبی هم‌نام با تابعی است که لامبدا به آن پاس داده شده است.

```kotlin
//sampleStart
fun foo() {
    listOf(1, 2, 3, 4, 5).forEach {
        if (it == 3) return@forEach // بازگشت محلی به فراخواننده لامبدا - حلقه forEach
        print(it)
    }
    print(" done with implicit label")
}
//sampleEnd

fun main() {
    foo()
}
```


به عنوان جایگزین، می‌توانید عبارت لامبدا را با یک [تابع ناشناس](https://kotlinlang.org/docs/lambdas.html#anonymous-functions) جایگزین کنید.
یک دستور `return` در یک تابع ناشناس، از خود تابع ناشناس بازمی‌گردد.

```kotlin
//sampleStart
fun foo() {
    listOf(1, 2, 3, 4, 5).forEach(fun(value: Int) {
        if (value == 3) return  // بازگشت محلی به فراخواننده تابع ناشناس - حلقه forEach
        print(value)
    })
    print(" done with anonymous function")
}
//sampleEnd

fun main() {
    foo()
}
```


توجه داشته باشید که استفاده از بازگشت‌های محلی در سه مثال قبلی مشابه استفاده از `continue` در حلقه‌های معمولی است.

معادل مستقیمی برای `break` وجود ندارد، اما می‌توان آن را با اضافه کردن یک لامبدا `run` بیرونی و بازگشت غیرمحلی از آن شبیه‌سازی کرد:

```kotlin
//sampleStart
fun foo() {
    run loop@{
        listOf(1, 2, 3, 4, 5).forEach {
            if (it == 3) return@loop // بازگشت غیرمحلی از لامبدا پاس داده شده به run
            print(it)
        }
    }
    print(" done with nested loop")
}
//sampleEnd

fun main() {
    foo()
}
```


بازگشت غیرمحلی در اینجا امکان‌پذیر است زیرا لامبدا `forEach()` تو در تو به عنوان یک [تابع درون‌برنامه‌ای (inline function)](https://kotlinlang.org/docs/inline-functions.html) عمل می‌کند.

هنگام بازگرداندن یک مقدار، تجزیه‌گر (parser) اولویت را به بازگشت واجد شرایط می‌دهد:

```kotlin
return@a 1
```

این به معنای "بازگرداندن `1` در برچسب `@a`" است و نه "بازگرداندن یک عبارت برچسب‌گذاری شده `(@a 1)`".

> در برخی موارد، می‌توانید بدون استفاده از برچسب‌ها از یک عبارت لامبدا بازگردید. چنین بازگشت‌های *غیرمحلی* در یک لامبدا قرار دارند اما از [تابع درون‌برنامه‌ای (inline function)](https://kotlinlang.org/docs/inline-functions.html#returns) دربرگیرنده خارج می‌شوند.
>

