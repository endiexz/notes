## c多线程



### pthread.h

```c++
#inlcude <pthread.h>
pthread_cread(thread, attr, start_routain, arg);
//thread 指向线程标识符指针
//attr 不透明的属性对象， 可以被用来设置线程属性， 可以指定线程属性对象或者默认值NULL
//start_routain 线程运行函数起始地址，一旦线程被创建就会执行
//arg 运行函数的参数，必须通过把引用作为指针强制转化为void类型进行传递。如果没有传递参数则使用NULL
```

### 线程的终止

```c++
pthread_exit(status)
    //用于显示的退出一个线程。通常情况下，pthread_exit()是在线程完成工作后无需继续存在时被调用的如果main函数是再他所创建的线程之前结束，并通过pthread_exit()退出，那么其他线程将继续执行，否则它们将在main()函数结束时自动终止.

```

## c++多线程

classes :thread
namesace:this_thread

```c++
//创建线程
void foo(){
    //do stuff
}
int main(){
    std::thread first (foo);
    first.join();
    return 0;
}
```



```c++
member functions
    std::thread::detach
    //detaches the thread represented by the object from the calling thread, allowing them to execute independently from each other. Both threads continue without blocking not synchronizing in any way. Note that when either one ends executinon, its resources are released. After a call to this function, the thread object bbecoms non-joinable and can be desroyed safely.
    std::thread::get_id
    //return the thread id.
    std::thread::join
   	//join thread
    //the function returns when the thread execution has completed
    //This sunchronizes the moment this function returns with the completion of all the operation in the thread: 
    std::thread::joinable
    bool joinable() const noexcept;
    //check if a thread whether joinable
    

toher
   
```

