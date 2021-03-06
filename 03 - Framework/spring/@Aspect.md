http://blog.csdn.net/jobjava/article/details/44063427

http://blog.csdn.net/wangligong/article/details/53224594

处理日志 

@AspectJ的详细用法
在Spring AOP中目前只有执行方法这一个连接点，Spring AOP支持的AspectJ切入点指示符如下：

@Pointcut
一些常见的切入点的例子
execution(public * * (. .)) 任意公共方法被执行时，执行切入点函数。
execution( * set* (. .)) 任何以一个“set”开始的方法被执行时，执行切入点函数。
execution( * com.demo.service.AccountService.* (. .)) 当接口AccountService 中的任意方法被执行时，执行切入点函数。
execution( * com.demo.service.. (. .)) 当service 包中的任意方法被执行时，执行切入点函数。 within(com.demo.service.) 在service 包里的任意连接点。 within(com.demo.service. .) 在service 包或子包的任意连接点。
this(com.demo.service.AccountService) 实现了AccountService 接口的代理对象的任意连接点。
target(com.demo.service.AccountService) 实现了AccountService 接口的目标对象的任意连接点。
args(java.io.Serializable) 任何一个只接受一个参数，且在运行时传入参数实现了 Serializable 接口的连接点

增强的方式：

@Before ：方法前执行
@AfterReturning ：运行方法后执行
@AfterThrowing ：Throw后执行
@After ：无论方法以何种方式结束，都会执行（类似于finally）
@Around ：环绕执行

例如定义切入点表达式 execution(* com.sample.service.impl..*.*(..))
execution()是最常用的切点函数，其语法如下所示：
 整个表达式可以分为五个部分：
 1. execution(): 表达式主体。
 2. 第一个*号：表示返回类型，* 号表示所有的类型。
 3. 包名：表示需要拦截的包名，后面的两个句点表示当前包和当前包的所有子包，com.sample.service.impl包、子孙包下所有类的方法。
 4. 第二个*号：表示类名，* 号表示所有的类。
 5. * (..):最后这个星号表示方法名，* 号表示所有的方法，后面括弧里面表示方法的参数，两个句点表示任何参数。
