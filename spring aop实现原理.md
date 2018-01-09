Spring核心思想IOC和AOP，IOC很好理解，将bean的生成和依赖注入托管给框架，关于AOP的意义网上各类文章都有说明，
这里推荐的一篇文章和一个问答主要在于说明AOP实现的原理，主要涉及三个部分：
    **1.JDK动态代理** 这部分大家应该都比较熟悉，就是java原生的代理，被代理对象必须实现某个接口
    **2.字节码操作** 主要是为了对没有实现接口的类进行aop操作，spring使用cglib类库实现，其实cglib还是对更底层的字节码操作框架ASM做了封装而已，
ASM也可以单独使用，如果熟练应用将是线上定位问题的利器。
(https://stackoverflow.com/questions/2261947/are-there-alternatives-to-cglib)
这篇问答里讲得比较详细，大部分字节码框架的实现都依赖于ASM，cglib相对来说是执行速度最快的
    **3.spring AOP注解** 由于Spring 允许使用 AspectJ Annotation 用于定义方面（Aspect）、切入点（Pointcut）和增强处理（Advice），Spring 
框架则可识别并根据这些 Annotation 来生成 AOP 代理，使大家很容易产生误解，认为spring直接封装了切面编程框架AspectJ。其实并不是，AspectJ
 AOP是在编译时对class进行增强，本质上是静态代理，Spring 只是使用了和 AspectJ 5 一样的注解，但并没有使用 AspectJ 的编译器或者织入器
 （Weaver），底层依然使用的是 Spring AOP，依然是在运行时动态生成 AOP 代理，并不依赖于 AspectJ 的编译器或者织入器。
(https://www.ibm.com/developerworks/cn/java/j-lo-springaopcglib/index.html)
这篇文章里对AspectJ的原理、cglib的原理，以及spring和AspectJ对注解的处理有比较详细的说明
