# AndroidCoroutine

> Related link: https://www.bilibili.com/video/BV1da411b7N8?spm_id_from=333.999.0.0

## BackGround
- Thread is controlled by jvm, we connot freely modify the state of thread, which cause the waste of computer resource.
- It can improve performance of computer that if we use coroutine. Because we can use a new coroutine to execute other task when current coroutine is blocked. 
- The essece of performance improvement is that thread can execute continuously.
- Kotlin coroutines are actually based on thread pool encapsulation. It encapsulates all coroutines with threads but does not have the ability to reduce CPU switching. A coroutine being suspended is actually a thread being suspended, and it does not achieve the ability to reuse the current thread to continue execution. Because kotlin is based on JVM, when a coroutine is suspended, it cannot continue to resume it because the suspended semaphore cannot be monitored. For example, if an IO interrupt occurs, or a network request or scheduling needs, he cannot obtain such a signal. Kotlin's delay() is actually implemented through the thread's sleep.

## Feature
- This is a custome library which implements the coroutine in C++.
- Limited by jvm, this lib cannot support multiple suspend points .
- When we compare this with kotlin coroutine library, we find that kotlin lib just is the same as a thread pool, limited by jvm, it can only bind one coroutine with one thread.

## ToDo
- Use kotlin suspend to solve callback syntax problems.
- Suspension point implementation at the JVM layer statement level.
- Using C semaphores to monitor IO interrupts and resume execution.

## External Link
- coroutine C++20 lib: It only provide some basic implementations of coroutine.
- setjmp.h setjmp()/longjmp() C Lib
- [ucontext-cloudwu](https://github.com/cloudwu/coroutine): It embeds the assembly through C, stores the current call stack into the register through assembly scheduling, and then switches to the next call stack for execution. It only implements the cpu architecture of x86 and x64, excluding the arm architecture of the mobile terminal.
- [Libco-Tecent](https://github.com/Tencent/libco): It's implementation refers to ucontext, and it only support x86.
