# Tomcat && Jetty

Tomcat总体架构

Tomcat要实现2个核心功能

* 处理Socket连接,负责网络字节流与Request和Response对象的转化
* 处理和加载Servlet,以及具体处理Request请求

Tomcat设计了两个核心组件连接器(Connector)和容器(Container)来分别做这两件事.连接器负责对外交流,容器负责内部处理.

