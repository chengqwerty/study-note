1. try finally返回值

```java
    public static int getValue() {
        int i = 1;
        try {
            return i;
        } finally {
            i = 2;
        }
    }
```

finally代码块的代码会执行，但是返回值是1。原因是return i已经获取了一个拷贝值，finally的修改不会影响这个值。

2. @Transactional 如果不使用嵌套无所谓，如果使用了嵌套，需要数据库也支持事务的嵌套。

3. Class.forName和ClassLoader loadClass的区别

```java
    Class<?> aClass = Class.forName("org.example.Main");
    Class<?> bClass = ClassLoader.getSystemClassLoader().loadClass("org.example.Main");
```

Class.forName会加载类并初始化（比如执行static代码块），loadClass只会加载，但不会初始化。Class.forName可以点进去看，有一个是否初始化的参数。


4. spring mvc 如何将路径匹配到requestMapping的

当一个web请求到来时，DispatcherServlet负责接收请求并响应结果。DispatcherServlet首先需要找到当前请求对应的handler（处理器）来处理请求。RequestMappingHandlerMapping用来处理@RequestMapping注解，AntPathMatcher来比对是否匹配。

5. 