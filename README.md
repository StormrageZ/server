# WEB_SERVER
## Technical points
* 采用 Reactor 的事件处理模式
* 使用 Epoll 的 ET 模式实现高效的 I/O 多路复用，NoblockIO
* 通过设置 TCP LINGER 选项支持优雅关闭连接
* 使用了 C++ 中 priority_queue 数据结构 ，以小根堆的形式管理定时器，处理超时连接 
* 使用了多线程处理并发连接，提高 CPU 的利用率，通过线程池管理工作线程，减少了线程创建和销毁的开销
* 使用了Linux内核中的 eventfd 进行线程间的通信， 实现线程的异步唤醒
* 参考陈硕的 muduo 网络库使用双缓冲区技术实现了异步日志系统，保存程序运行状态以及连接信息
* 通过 shared_ptr 智能指针的RAII机制减少内存泄露
* 使用状态机解析了 HTTP 请求,支持管线化
