# AndroidCoroutine

> related link: https://www.bilibili.com/video/BV1da411b7N8?spm_id_from=333.999.0.0

- This is a custome coroutine library which achieve the basic function of coroutine by c. 
- But this lib cannot implement multiple suspend points limited by jvm.
- When we compare this with kotlin coroutine library, we find that kotlin lib just is the same as a thread pool, because it bind only one coroutine with one thread limted by jvm.
