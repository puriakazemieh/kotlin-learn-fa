[//]: # (title: Packages and imports)

یک فایل سورس می‌تواند با یک اعلان پکیج (package) شروع شود:

```kotlin
package org.example

fun printMessage() { /*...*/ }
class Message { /*...*/ }

// ...
```

تمام محتویات فایل سورس، مانند کلاس‌ها و تابع‌ها، در این پکیج قرار می‌گیرند.  
بنابراین، در مثال بالا، نام کامل تابع `printMessage()` برابر است با `org.example.printMessage`  
و نام کامل کلاس `Message` برابر است با `org.example.Message`.

اگر پکیج مشخص نشود، محتویات چنین فایلی به پکیج پیش‌فرض (_default_) بدون نام تعلق دارند.

## ایمپورت‌های پیش‌فرض

تعدادی از پکیج‌ها به‌صورت پیش‌فرض در هر فایل Kotlin ایمپورت می‌شوند:

- [kotlin.*](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/index.html)
- [kotlin.annotation.*](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.annotation/index.html)
- [kotlin.collections.*](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/index.html)
- [kotlin.comparisons.*](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.comparisons/index.html)
- [kotlin.io.*](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.io/index.html)
- [kotlin.ranges.*](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.ranges/index.html)
- [kotlin.sequences.*](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.sequences/index.html)
- [kotlin.text.*](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/index.html)

بسته به پلتفرم هدف، پکیج‌های اضافی نیز ایمپورت می‌شوند:

- JVM:
    - java.lang.*
    - [kotlin.jvm.*](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.jvm/index.html)
- JS:
    - [kotlin.js.*](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.js/index.html)

## Imports

علاوه بر ایمپورت‌های پیش‌فرض، هر فایل می‌تواند دستورهای `import` مخصوص به خود را داشته باشد.

می‌توانید یک نام مشخص را ایمپورت کنید:

```kotlin
import org.example.Message // Message is now accessible without qualification
```

یا تمام محتویات قابل دسترسی یک محدوده (scope) مانند پکیج، کلاس، آبجکت و غیره را ایمپورت کنید:

```kotlin
import org.example.* // everything in 'org.example' becomes accessible
```

اگر تداخل اسمی وجود داشته باشد، می‌توانید با استفاده از کلمه‌ی کلیدی `as` نام محلی متفاوتی برای موجودیت دارای تداخل تعیین کنید:

```kotlin
import org.example.Message // Message is accessible
import org.test.Message as TestMessage // TestMessage stands for 'org.test.Message'
```

کلمه‌ی کلیدی `import` فقط به ایمپورت کلاس‌ها محدود نمی‌شود؛ همچنین می‌توان از آن برای ایمپورت اعلان‌های دیگر نیز استفاده کرد:

- توابع و پراپرتی‌های سطح بالا (top-level)
- توابع و پراپرتی‌های تعریف‌شده در [object declarations](object-declarations.md#object-declarations-overview)
- [ثابت‌های enum](enum-classes.md)

## سطح دسترسی اعلان‌های top-level

اگر یک اعلان سطح بالا با `private` علامت‌گذاری شود، فقط در همان فایلی که در آن تعریف شده قابل دسترسی است  
(به [Visibility modifiers](visibility-modifiers.md) مراجعه کنید).
