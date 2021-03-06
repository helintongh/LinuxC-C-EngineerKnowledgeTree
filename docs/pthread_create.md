在调用这个函数的进程中创建一个新的线程
## 函数原型
```c
#include <pthread.h>

int pthread_create(pthread_t *thread, const pthread_attr_t *attr,
                   void *(*start_routine) (void *), void *arg);
```
## 参数
### thread
属于**结果参数**。函数结束时，返回线程ID并存储到thread中。  
`pthread_t`被定义成`unsigned long int`类型。
### attr
设置线程的属性，主要是栈相关的属性。一般为NULL也可通过属性设置**线程分离**。不常用
### start_routine
start_routine是一个回调函数（函数指针实现）。指明了线程要执行的函数。
### arg
回调函数start_routine()执行时的参数（实参--传递给回调函数的）。
## 返回值
成返回0，失败返回非0值。

注:主线程退出,子线程会被强制结束

```c
pthread_t pthid;
pthread_create(&pthid, NULL, myfunc, NULL);
printf("child thread id: %lu\n", pthread_self());
```