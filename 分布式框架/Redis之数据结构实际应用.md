[参考知乎用户：程序之心](https://zhuanlan.zhihu.com/p/50392209)
# Redis之数据结构实际应用
### String
最常规的 set/get 操作，Value 可以是 String 也可以是数字。一般做一些复杂的`计数功能`的缓存。

### Hash
这里 Value 存放的是结构化的对象，比较方便的就是操作其中的某个字段。我在做`单点登录`的时候，就是用这种数据结构`存储用户信息`，以 CookieId 作为 Key，设置 30 分钟为缓存过期时间，能很好的模拟出类似 Session 的效果。
### List
使用 List 的数据结构，可以做`简单的消息队列`的功能。另外，可以利用 `lrange 命令，做基于 Redis 的分页功能`，性能极佳，用户体验好。
### Set
因为 Set 堆放的是一堆不重复值的集合。所以可以做`全局去重`的功能。我们的系统一般都是集群部署，使用 JVM 自带的 Set 比较麻烦。另外，就是利用交集、并集、差集等操作，可以计算共同喜好，全部的喜好，自己独有的喜好等功能。
### Sorted Set

Sorted Set 多了一个权重参数 Score，集合中的元素能够按 Score 进行排列。可以做`排行榜应用`，取 TOP N 操作。Sorted Set 可以用来做`延时任务`。
