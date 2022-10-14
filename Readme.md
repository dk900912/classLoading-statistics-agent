当通过`Attach API`蒋该`agent`附着到给定 JVM 实例后，可以输出关于类加载的一些统计信息，比如：有哪些类加载器、每个类加载器有几个实例、每个类加载器分别加载了多少类以及每个类加载器所加载的包有哪些。

### 如何使用
```java
VirtualMachine vm = VirtualMachine.attach(PID);
vm.loadAgent(AGENT_PATH);
vm.detach();
```

### 执行结果一
```
----------------------------------------------------------------------------------------------
classloaderName                                              instanceCount        loadedCount         
jdk.internal.loader.ClassLoaders$AppClassLoader              1                    4081                
jdk.internal.reflect.DelegatingClassLoader                   81                   81                  
BootstrapClassLoader                                         1                    3174                
jdk.internal.loader.ClassLoaders$PlatformClassLoader         1                    46                  
sun.reflect.misc.MethodUtil                                  1                    1                   
----------------------------------------------------------------------------------------------
```
### 执行结果二
```
>>>>>>>>>>>>>>>>>>>> package list loaded by jdk.internal.loader.ClassLoaders$AppClassLoader             
javax.websocket
org.aopalliance
org.slf4j
javax.security
com.mysql
com.intellij
com.ulisesbocchio
javax.annotation
javax.servlet
com.zaxxer
ch.qos
org.springframework
com.sun
io.github
com.example
org.jasypt
org.apache
com.fasterxml

>>>>>>>>>>>>>>>>>>>> package list loaded by jdk.internal.reflect.DelegatingClassLoader                  
jdk.internal

>>>>>>>>>>>>>>>>>>>> package list loaded by BootstrapClassLoader                                        
javax.xml
java.rmi
sun.reflect
java.util
sun.management
sun.net
java.beans
javax.security
javax.naming
java.nio
sun.nio
jdk.jfr
sun.invoke
sun.launcher
java.time
org.xml
jdk.net
java.net
sun.rmi
com.sun
sun.instrument
sun.text
java.math
java.security
sun.security
javax.management
sun.io
jdk.xml
sun.util
java.lang
java.text
jdk.management
java.io
jdk.internal
javax.net
javax.swing

>>>>>>>>>>>>>>>>>>>> package list loaded by jdk.internal.loader.ClassLoaders$PlatformClassLoader        
java.sql
sun.util
sun.security
org.jcp
com.sun
javax.sql
sun.text

>>>>>>>>>>>>>>>>>>>> package list loaded by sun.reflect.misc.MethodUtil                                 
sun.reflect
```