## 01 谈谈你对Java平台的理解

> 谈谈你对Java的理解,Java是解释执行,这句话正确吗



* 面向对象(封装继承多态)
* 跨平台
* 垃圾回收
* 语言 泛型 Lambda
* 类库  (集合 并发 网络 IO)
* JDK工具 常用命令



## 02 Exception 和Error 的区别

> 请对比Exception 和Error,另外,运行时异常和一般异常有什么区别

* 都继承了Throwable类
* Exception是程序正常运行中,可以预料的意外情况,可能且应该被捕获,进行相应的处理;
* Error是指在正常情况下,不大可能出现的情况.绝大部分的Error都会导致程序处于非正常,不可恢复的状态.
* Exception分为受检异常和非受检异常

### 考点分析

* throwable Exception Error 的设计和分类
* 理解java语言中操作throwable的元素和实践,比如`try catch finally`,`throw`,`throws`等关键字

### 知识扩展

* 尽量不要捕获类似Exception这样的通用异常,而是应该捕获特定异常
* 不要生吞异常,异常输出不要使用`printStackTrace()`
* throw early , catch late

## final finally finalize 

> 谈谈final finally finalize 有什么不同



## 强引用,软引用,弱引用和幻象引用(虚引用)

> 强引用,软引用,弱引用和幻象引用有什么区别,具体使用场景是什么

不同引用类型主要体现的是**对象不同的可达性状态和对垃圾手机的影响**;

* **强引用** `Strong Reference` 普通的对象引用,强引用的对象不会进行垃圾回收;
* **软引用** `Soft Reference` 相对强引用弱化一些的引用,可以让对象豁免一些垃圾手机,只有当JVM认为内存不足时,才会试图回收软引用指向的对象.
* **弱引用** `Weak Reference`并不能使对象豁免垃圾收集,仅仅是提供一种访问在弱引用状态下对象的途径.
* **虚引用**



## String,StirngBuffer,StringBuilder有什么区别

> 理解Java的字符串,String,StirngBuffer,StringBuilder有什么区别



### 知识扩展

* 字符串设计和实现考量

为了实现修改字序列的目的,StringBuffer和StringBuilder底层都是利用可修改的数组(char,JDK9以后是byte).两者都集成了`AbstractStringBuilder`,里面包含了基本操作,区别仅在于最终的方法是否加了`synchronized`.

数组大小目前的实现是 ,构建时初始化字符串长度加16.(如果没有录入初始字符串,初始长度就是16).如果能确定拼接的字符串长度,可以指定合适的大小,避免多次扩容开销.

* 字符串缓存

jdk6提供的`intern()`方法,目的是提示JVM把相应字符串缓存起来,以备重复使用.

```
一般在使用jdk6时,并不推荐大量使用intern,因为被缓存的字符串放到了永久代(perm space).这个空间是有限的,也基本不会被FullGC之外的垃圾收集器手机,所以使用不当,会造成OOM.
在后续的版本中,这个缓存被放到了堆中.在Jdk8中被metaspacec(元数据区)替代;而且默认缓存大小也在不断的扩大中,从最初的1009,到jdk7u40以后被修改为60013.可以通过 jdk的参数 -XX:+PrintStringTableStatistics 直接打印具体数字.也可以使用 -XX:StringTableSize=N 手动跳整大小.
```



## 动态代理是基于什么原理

> 谈谈Java反射机制,动态代理是基于什么原理



## int 和Integer 有什么区别

> int 和  Integer有什么区别,谈谈Integer的值缓存范围



## 对比Vector ArrayList LinkedList 有何区别

> 对比Vector ArrayList LinkedList 有何区别

推荐书籍 

《算法导论》，《编程珠玑》



## 对比 Hashtable HashMap TreeMap 有什么不同

