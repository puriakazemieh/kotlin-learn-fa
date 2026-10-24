---
cssclasses:
  - persian-rtl
---

# نوع‌های پایه

هر متغیر و ساختار داده در Kotlin یک نوع دارد. نوع‌ها مهم‌اند، زیرا به کامپایلر می‌گویند چه کارهایی اجازه دارید با آن متغیر یا ساختار داده انجام دهید؛ به بیان دیگر، چه تابع‌ها و ویژگی‌هایی دارد.

در فصل پیش، Kotlin توانست در مثال قبلی تشخیص دهد که `customers` از نوع [`Int`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-int/) است.
توانایی Kotlin برای **استنتاج** نوع، **استنتاج نوع (type inference)** نام دارد. به `customers` یک مقدار صحیح اختصاص داده شده است؛ Kotlin از این موضوع استنتاج می‌کند که `customers` نوع عددی `Int` دارد. در نتیجه، کامپایلر می‌داند که می‌توانید عملیات حسابی را با `customers` انجام دهید:

```kotlin
fun main() {
//sampleStart
    var customers = 10

    // Some customers leave the queue
    customers = 8

    customers = customers + 3 // Example of addition: 11
    customers += 7            // Example of addition: 18
    customers -= 3            // Example of subtraction: 15
    customers *= 2            // Example of multiplication: 30
    customers /= 3            // Example of division: 10

    println(customers) // 10
//sampleEnd
}
```

> [!tip]
> `+=`، `-=`، `*=`، `/=` و `%=` عملگرهای انتساب ترکیبی هستند. برای اطلاعات بیشتر، [انتساب‌های ترکیبی](../operator-overloading.md#augmented-assignments) را ببینید.

در مجموع، Kotlin نوع‌های پایهٔ زیر را دارد:

| **دسته** | **نوع‌های پایه** | **کد نمونه** |
|---|---|---|
| [اعداد صحیح](../numbers-fa.md) | `Byte`، `Short`، `Int`، `Long` | `val year: Int = 2020`<br/> `val amount: Long = 350_000_000` |
| [اعداد صحیحِ بدون علامت](../unsigned-integer-types-fa.md) | `UByte`، `UShort`، `UInt`، `ULong` | `val score: UInt = 100u` |
| [اعداد ممیز شناور](../numbers-fa.md) | `Float`، `Double` | `val currentTemp: Float = 24.5f`<br/> `val price: Double = 19.99` |
| [بولی‌ها](../booleans-fa.md) | `Boolean` | `val isEnabled: Boolean = true` |
| [نویسه‌ها](../characters-fa.md) | `Char` | `val separator: Char = ','` |
| [رشته‌ها](../strings-fa.md) | `String` | `val message: String = "Hello, world!"` |

برای اطلاعات بیشتر دربارهٔ نوع‌های پایه و ویژگی‌های آن‌ها، [مرور نوع‌ها](../types-overview-fa.md) را ببینید.

با این دانش، می‌توانید متغیرها را اعلان کنید و بعداً مقداردهی اولیه کنید. Kotlin تا زمانی می‌تواند این وضعیت را مدیریت کند که متغیرها پیش از نخستین خواندن مقداردهی اولیه شوند.

برای اعلان متغیر بدون مقداردهی اولیه، نوع آن را با `:` مشخص کنید. برای نمونه:

```kotlin
fun main() {
//sampleStart
    // Variable declared without initialization
    val d: Int
    // Variable initialized
    d = 3

    // Variable explicitly typed and initialized
    val e: String = "hello"

    // Variables can be read because they have been initialized
    println(d) // 3
    println(e) // hello
//sampleEnd
}
```

اگر متغیری را پیش از خواندن مقداردهی اولیه نکنید، خطا می‌بینید:

```kotlin
fun main() {
//sampleStart
    // Variable declared without initialization
    val d: Int

    // Triggers an error
    println(d)
    // Variable 'd' must be initialized
//sampleEnd
}
```

اکنون که می‌دانید چگونه نوع‌های پایه را اعلان کنید، زمان یادگیری دربارهٔ [مجموعه‌ها](kotlin-tour-collections.md) است.

## تمرین

### اعلان نوع‌های صریح برای متغیرها

برای هر متغیر، نوع درست را به‌طور صریح اعلان کنید:

```kotlin
fun main() {
    val a: Int = 1000
    val b = "log message"
    val c = 3.14
    val d = 100_000_000_000_000
    val e = false
    val f = '\n'
}
```

> [!example]- راه‌حل نمونه
> ```kotlin
> fun main() {
>     val a: Int = 1000
>     val b: String = "log message"
>     val c: Double = 3.14
>     val d: Long = 100_000_000_000_000
>     val e: Boolean = false
>     val f: Char = '\n'
> }
> ```

[گام پیشین](kotlin-tour-hello-world-fa.md) · [گام بعدی](kotlin-tour-collections.md)
