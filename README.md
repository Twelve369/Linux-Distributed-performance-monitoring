# Linux-Distributed-performance-monitoring
实现客户端对Linux 服务器进行**性能监控**，监控内容包括 CPU 状态、内存占用率、软中断等等。另外，为了模拟真实性能问题，使用 stress 进行压力测试，实时分析服务器的各种信息。

– **Docker 模块**：编写 Dockerfile 来指定所需的源码依赖，如 gRPC、Protobuf 和 Qt 等。通过Docker镜像，构建出整个项目的运行环境，并编写容器操作脚本以方便启动和操作项目所需的环境；<br>
– **监控模块**：使用工厂方法设计模式，构造监控类型的接口，实现了 CPU 状态、内存以及网络等监控信息，并且便于后续的扩展；<br>
– **显示模块**：使用 QWidget、QTableView、QStackedLayout 等进行 UI 界面构造；通过继承QAbstractTableModel 构建相应的监控数据模型，实现每三秒刷新一次数据。<br>
– **通信模块**：使用 gRPC 框架，构建出相应的 server，client；server 在所要监控的服务器上部署，client 生成库供监控模块和显示模块调用。模块间使用 gRPC 服务进行通信，各个模块相互独立，具有低耦合性。<br>
– **数据模块**：使用 Protobuf 序列化协议，构建出整个项目的数据结构。<br>
